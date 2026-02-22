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


