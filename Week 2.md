## Lecture 1
### Markup & Information Representation
##### Description: Introduction to markup as part of user interface design, and the fundamental question of how information (especially text) is represented inside a computer using bits and standard encodings.

#### Markup and User Interface
- Markup controls how information is displayed on screen.
- It is part of the user interface (UI) — the layer that interacts with the user.
- Markup affects:
  - Presentation
  - Aesthetics
  - Visual clarity
  - Perceived quality of a website

- A developer uses markup to change how content appears to users.
- Important distinction introduced:
  - Raw data vs Semantics
  - Logical structure vs Styling

- Technologies to be studied (high-level introduction):
  - HTML5
  - CSS

#### Information Representation in Computers
- Computers work only with bits:
  - Binary digits: 0 and 1
- Physically represented using voltage levels.
- Advantages:
  - Robust to noise
  - Enables binary algebra and computation

- Interpretation requires context.
  - Same bit pattern can mean different things.

Example:
- 0110 (binary) = 6 (decimal)
- 1010:
  - If unsigned → 10
  - If 4-bit 2’s complement → -6
  - Without context → just a bit sequence

Key Insight:
- Meaning is not in the bits.
- Meaning comes from interpretation + context.

#### Representing Text
- Numbers have structured representation.
- Letters do NOT have natural numeric meaning.
- Therefore, standard encodings are required.

Information Interchange:
- Between machines
- Between humans and machines
- Machines only understand bits → need encoding standard

Example:
- 0100 0001 can represent:
  - Bit string
  - Number 65
  - Character 'A'
- All are correct depending on context.

Inside programs:
- Memory locations have defined meaning.
- Context determines interpretation (e.g., string vs integer).

#### ASCII
- American Standard Code for Information Interchange.
- 7-bit encoding → 128 possible characters.
- Includes:
  - A–Z
  - a–z
  - 0–9
  - Special characters (!@#$%^&)
  - Control characters (newline, carriage return, etc.)

Why 7 bits?
- Early systems optimized bit usage.
- 6 bits (64 values) insufficient.
- 7 bits → 128 combinations.

Extended ASCII:
- 8-bit → 256 characters.
- Supported European accented characters.
- Still insufficient for global scripts.

Limitation:
- Cannot represent thousands of world language characters.

#### Unicode and UCS
- Created by international consortium.
- Goal: Universal Character Set.

UCS-2:
- 2 bytes per character.
- 65,536 possible characters.

Limitation:
- Too small for all world scripts.

UCS-4:
- 4 bytes per character.
- 4+ billion possible combinations.
- Currently ~100,000+ defined characters.
- Remaining space unused (sparse allocation).

Tradeoff:
- More characters → more memory required.
- Efficiency vs Expressive power.

Example:
- 1000 words ≈ 5000 characters
- ASCII (7-bit): 35,000 bits
- UCS-4 (32-bit): 160,000 bits

Large increase in storage requirement.

#### Design Tension
Core engineering problem:
- How many characters should be supported?
- How much memory overhead is acceptable?
- Should we optimize for common languages?
- What about extinct or future scripts?

Encoding is a balance between:
- Efficiency
- Scalability
- Universality

**Key Idea**  
Bits themselves have no inherent meaning. Meaning arises from context and standardized encoding. Markup and character encodings form the foundation of how computers represent, interpret, and display human-readable information.

### Notes to be taken for `Activity Question 1`

1. "Markup” is not necessarily computer readable. (Question: 5)
---
## Lecture 2

### Encoding Efficiency and UTF-8
##### Description: - Understanding the efficiency trade-offs in character encoding, why fixed-length Unicode (UCS-4) is inefficient for common text, and how UTF-8 uses variable-length prefix encoding to balance universality and storage efficiency.

#### Encoding Efficiency Problem
- English is currently the most common language on the web.
- Many European languages use similar scripts.
- ASCII worked well for a long time.
Problem:
- UCS-4 uses 4 bytes (32 bits) per character.
- This is inefficient for simple English documents.

Example:
- 1,000 words ≈ 5,000 characters.
- UCS-4:
  - 32 bits × 5,000 = 160,000 bits.
- ASCII:
  - 8 bits × 5,000 = 40,000 bits.
- 7-bit ASCII:
  - 35,000 bits.

Conclusion:
- Fixed 4-byte encoding wastes space for common text.
- Impacts:
  - Storage
  - Memory usage
  - String comparisons
  - Performance

#### Frequency-Based Encoding
Observation:
- Some letters occur more frequently (E, T, A).
- Others are rare (Z, Q, J).

Idea:
- Use fewer bits for common letters.
- Use more bits for rare letters.
- Example: Huffman Encoding.

Result:
- More efficient average encoding.
- Could reduce 5,000-character document to ~10–20k bits.

Limitation:
- Optimal encoding depends on the specific document.
- If document has unusual distribution, encoding may perform poorly.

Compression Tools:
- zip uses frequency-based encoding.
- Works independent of meaning.
- Same algorithm on both sides → guaranteed reconstruction.

But:
- Compression solves storage.
- Does not solve in-memory character representation problem.

#### Need for Variable-Length Unicode Encoding
Question:
- Can we balance universality and efficiency?

Goal:
- 1 byte for common characters.
- More bytes only when necessary.
- Must be self-identifying (prefix-based).

This leads to prefix encoding.

#### UTF-8 Prefix Encoding Logic
Core Idea:
- Encoding must allow detection of:
  - Start of character
  - Continuation bytes

Rules (conceptual):

- If first bit = 0:
  - Single byte character (ASCII).
  - Remaining 7 bits represent value.

- If first bits = 110:
  - Two-byte character.
  - First byte starts with 110.
  - Continuation byte starts with 10.

- If first bits = 1110:
  - Three-byte character.

- If first bits = 11110:
  - Four-byte character.

Important Property:
- Any byte starting with 10:
  - Cannot be first byte.
  - Must be continuation.

This guarantees:
- Self-synchronizing encoding.
- Can scan byte stream and detect character boundaries.

Free Bits:

- 2-byte sequence → 11 usable bits.
- 3-byte sequence → 16 usable bits.
- 4-byte sequence → 21 usable bits (restricted in Unicode standard).

Supports:
- Over 1 million possible code points.

#### Code Points and UTF Representations
Each character has a Unicode code point:
- Format: U+XXXX (hexadecimal)

Examples:
- U+0041 → 'A'
- U+05D0 → Hebrew letter
- U+597D → Chinese character
- U+233B4 → Larger code point (requires 4 bytes)

Encodings:

UTF-32:
- Always 4 bytes.
- Direct representation.
- Simple but wasteful.

UTF-16:
- Usually 2 bytes.
- Some characters require 4 bytes.

UTF-8:
- 1 to 4 bytes.
- ASCII-compatible.
- Most efficient for English-heavy text.
- Most widely used encoding today.

#### Advantages and Tradeoffs
UTF-32:
- Simple parsing.
- Fixed size.
- Large memory usage.

UTF-8:
- Efficient for common languages.
- ASCII compatible.
- Variable-length parsing required.
- Slightly more complex processing.

UTF-16:
- Middle ground.
- Used in some systems (e.g., internal OS implementations).

#### Why UTF-8 Matters for Web Developers
- Users may access apps from any region.
- Browsers expect standard encoding.
- Most websites specify:

  `<meta charset="UTF-8">`

Benefits:
- Maximum compatibility.
- Handles global scripts.
- Built-in browser support.
- Standardized parsing and text processing.

UTF-8 is the de facto web standard.

### Notes to be taken for `Activity Question 2`

1. 2<sup>16</sup> characters can be encoded in UCS-2. (Question: 1)
2. If a document has 1000 characters. It will require 32000 bits to encode the entire document in UCS-4. (Question: 5)
---
