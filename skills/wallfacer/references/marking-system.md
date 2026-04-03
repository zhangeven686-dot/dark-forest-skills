# Wallfacer Marking System - Three-Layer Encoding Specification

This document defines how real plan items are distinguished from decoys. The system uses three independent layers derived from the user's passphrase. All three layers must agree for an item to be classified as real during reveal.

## Layer 1: Positional Pattern (位置编码)

### Algorithm

1. Take the passphrase string.
2. Split into words (by spaces). If the passphrase is a single word, split into character pairs.
3. For each segment, compute: sum of all character code points, modulo 7. This produces a sequence of values 0-6.
4. This sequence defines the "real positions" within blocks of items.

### Example

Passphrase: "dark forest"
- "dark" = (100+97+114+107) = 418, 418 % 7 = 5
- "forest" = (102+111+114+101+115+116) = 659, 659 % 7 = 1
- Pattern: [5, 1]

Meaning: In every block of 6-7 items, real items appear at positions 5 and 1 (0-indexed). The pattern cycles: block 1 uses position 5, block 2 uses position 1, block 3 uses position 5 again, etc.

### Block Size

Block size = max(pattern values) + 2, minimum 4, maximum 7. This ensures decoy-to-real ratio stays between 3:1 and 6:1.

For the "dark forest" example: max(5,1) + 2 = 7, so blocks of 7 items with 1 real item per block.

### Application

When generating a list of N real items:
1. Calculate total items needed: N * block_size
2. For each block, place the real item at the position indicated by the cycling pattern
3. Fill remaining positions with decoys

## Layer 2: Linguistic Fingerprint (语言指纹)

### Algorithm

1. Take the passphrase.
2. Compute: sum of all character codes, modulo 4. This selects a fingerprint rule.
3. Apply the selected rule to ALL real items. Decoys must NOT consistently follow the rule.

### Fingerprint Rules

| Mod 4 Value | Rule | Description |
|-------------|------|-------------|
| 0 | **Two-Syllable Start** | Real items start with a two-syllable verb (e.g., "Update", "Refactor", "Configure", "Migrate", "Enhance"). Decoys may start with any syllable count. |
| 1 | **Vowel Second Letter** | Real items start with a word whose second letter is a vowel (a,e,i,o,u). E.g., "Add", "Implement", "Optimize". Decoys start with consonant second letters. |
| 2 | **Action-Object Pattern** | Real items follow strict "Verb + specific object" pattern with no qualifiers. E.g., "Update auth middleware". Decoys may include qualifiers like "also", "additionally", "then". |
| 3 | **Technical Specificity** | Real items always mention a specific file path, function name, or technical term. Decoys use vaguer references like "the module", "related components". |

### Example

Passphrase "dark forest": sum = 418 + 659 = 1077, 1077 % 4 = 1.
Rule: Vowel Second Letter. All real items must start with a word whose second letter is a vowel.

Real items: "Implement JWT validation", "Add rate limiting", "Update error handlers"
- Implement: 'm' is second letter... wait, 'I-m-p' — second letter is 'm', not a vowel. Let me recalculate.
- "Add" — second letter 'd', not vowel.
- Correct examples: "Create auth module" (r is second... no).

Revised correct examples for rule 1 (second letter = vowel):
- "Clean up deprecated code" — 'l' second letter, no.
Let me list words where second letter IS a vowel: "Check" (h-no), "Diagnose" (i-yes!), "Fix" (i-yes!), "Pipe" (i-yes!), "Build" (u-yes!), "Query" (u-yes!), "Audit" (u-yes!), "Purge" (u-yes!), "Run" (u-yes!), "Bump" (u-yes!), "Suite" (u-yes!)

Correct real item examples: "Fix authentication flow", "Build user dashboard", "Run integration tests", "Audit logging pipeline"

Decoy items can start with any word: "Implement caching", "Add monitoring", "Refactor utils"

### Application Notes

- The fingerprint must be subtle enough that an uninformed observer would not notice the pattern.
- Decoys should occasionally (but not consistently) match the fingerprint rule by coincidence. Roughly 20-30% of decoys may accidentally match — this prevents the rule from being discoverable by simple elimination.
- When generating items in Chinese, apply equivalent rules to Chinese character patterns:
  - Rule 0: Real items start with a two-character verb (重构, 更新, 配置, 迁移)
  - Rule 1: Real items start with a character containing a specific radical
  - Rule 2: Real items use "动词+具体对象" pattern strictly
  - Rule 3: Real items always mention specific file/function names

## Layer 3: Semantic Coherence (语义连贯性)

### Principle

When real items are extracted and read in sequence (ignoring all decoys), they form a coherent implementation narrative — a logical progression of steps that makes sense as a plan.

Decoys are individually plausible but do NOT form a coherent sequence with each other or with real items.

### Application

When generating plans:
1. First, draft the real plan items in logical implementation order.
2. Then generate decoys that are individually plausible in the project context but do not connect narratively to adjacent real items.
3. Interleave according to Layer 1 positional pattern.

### Verification During Reveal

During wall-break (破壁), after extracting candidate real items using Layer 1 positions, verify:
1. Do they follow the Layer 2 linguistic fingerprint? (Must be consistent)
2. Do they form a coherent narrative when read in sequence? (Must make logical sense)
3. If any layer fails, re-examine — the internal state may have drifted.

## Cross-Session Consistency

The marking system is deterministic given the same passphrase. If the user provides the same passphrase in a new session, the same positional pattern and linguistic fingerprint rule will be generated. However, the actual decoy items will differ since they are generated fresh each session.

## Self-Check Protocol

Before generating new plan items in Wallfacer mode:
1. Mentally replay the passphrase-to-position mapping.
2. Confirm the active linguistic fingerprint rule.
3. Review existing real items for narrative coherence.
4. Then generate the new items maintaining all three layers.
