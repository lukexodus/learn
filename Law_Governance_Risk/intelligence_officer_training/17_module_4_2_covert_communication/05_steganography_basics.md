## Steganography Basics


Steganography is the practice of concealing a message, file, or data within another ordinary-looking carrier medium so that the existence of the hidden communication is not apparent to an observer. Unlike cryptography, which obscures _content_, steganography obscures _presence_.

---

### Distinction from Cryptography and Encoding

|Concept|Goal|Detection Risk|
|---|---|---|
|Cryptography|Hide meaning|Message presence is visible|
|Encoding|Transform format|No secrecy implied|
|Steganography|Hide existence|Ideally undetectable|

These are not mutually exclusive. A robust covert communication system may encrypt a message first, then steganographically embed the ciphertext — combining both layers.

---

### Core Concepts

#### The Carrier (Cover Medium)

The carrier is the file or signal used to hide data. Common carrier types include:

- **Digital images** (JPEG, PNG, BMP)
- **Audio files** (WAV, MP3)
- **Video files**
- **Text documents**
- **Network traffic** (protocol-level steganography)
- **Physical media** (microdots, invisible ink — analog steganography)

The carrier must be plausible in context. A high-resolution image sent between two parties who never exchange images is operationally suspicious regardless of technical success.

#### The Payload

The payload is the hidden data — a message, file, or signal embedded within the carrier. The payload-to-carrier ratio matters: embedding too much data relative to carrier size degrades statistical and perceptual properties, increasing detectability.

#### The Stego Object

The output after embedding: the carrier with the payload concealed inside. Ideally indistinguishable from the original carrier to both human observers and automated analysis.

#### The Key

Many steganographic systems require a shared key or passphrase to embed and extract data. Without the key, an observer cannot extract the payload even if they suspect its presence.

---

### Digital Image Steganography

This is the most widely documented domain, and the most practically relevant for an operational baseline.

#### Least Significant Bit (LSB) Substitution

In a standard 24-bit color image, each pixel contains three channels — Red, Green, Blue — each represented by 8 bits (values 0–255).

The **least significant bit** of each channel contributes only 1 unit of 256 to the color value. Altering it produces a color change of less than 0.4%, which is imperceptible to the human eye.

**Example:**

Original pixel Red channel: `11001010` (202) Payload bit to embed: `1` Modified Red channel: `11001011` (203)

The visual change is imperceptible. Across an image with millions of pixels, significant data can be embedded this way.

**Capacity calculation** [Inference — formula is standard; specific tool implementations vary]:

> For a 1920×1080 RGB image: 1920 × 1080 × 3 channels × 1 bit = 6,220,800 bits ≈ 755 KB of payload capacity at 1-bit LSB depth

Embedding in 2 or 3 LSBs increases capacity but also increases statistical detectability.

#### LSB Spread Spectrum Variants

Rather than embedding sequentially, spread-spectrum methods distribute payload bits pseudo-randomly across the carrier using a key-derived sequence. This makes detection harder because the signal is dispersed rather than localized.

#### DCT-Based Steganography (JPEG)

JPEG images do not store raw pixel values — they use **Discrete Cosine Transform** compression, dividing the image into 8×8 blocks and storing frequency coefficients. Steganography in JPEG operates by modifying the **least significant bits of DCT coefficients** rather than pixel values.

This is more complex than raw LSB but more resistant to JPEG recompression artifacts. Tools like **Steghide** and **OutGuess** use DCT-domain embedding.

**Key limitation**: JPEG recompression (e.g., uploading to a social media platform that re-encodes images) destroys DCT-based payloads. PNG (lossless) is more stable for LSB embedding if the carrier survives transit intact.

---

### Audio Steganography

#### LSB in Audio

Similar to image LSB, audio samples (typically 16-bit PCM) can have their least significant bits replaced with payload bits. The audible difference is inaudible noise at the threshold of perception.

#### Phase Coding

Encodes data in the **phase relationships** between audio segments rather than amplitude. More robust to noise addition but more complex to implement.

#### Echo Hiding

Introduces imperceptible echo signals into audio with varying delay parameters that encode binary data. Difficult to detect statistically.

---

### Text Steganography

Operationally relevant where digital files cannot be transmitted — relies on cover text as carrier.

#### Whitespace Methods

- Trailing spaces appended to lines encode bits
- Tab vs. space substitution encodes bits
- Line spacing or word spacing in formatted documents

#### Linguistic / Semantic Steganography

Payload is encoded in word choice, sentence structure, or specific lexical patterns. Examples:

- Every nth word encodes a letter
- First letters of sentences spell a message
- Synonym substitution governed by a key

**Operational note**: Linguistic steganography is high-effort, low-capacity, and brittle. It requires the cover text to read naturally, which constrains it severely. [Inference — this is a widely held assessment in the open literature, not a guaranteed performance ceiling.]

#### Format-Based

- Font changes (imperceptible size differences, color near-white on white)
- Zero-width characters (Unicode contains multiple zero-width codepoints that are invisible but machine-readable)
- HTML comment fields, metadata fields in document formats

---

### Network / Protocol Steganography

Data is concealed in network traffic rather than files. This is relevant for covert channel establishment.

#### Methods

- **IP header fields**: Unused or rarely-inspected fields (TTL variation, ID field, reserved bits)
- **TCP/IP timing**: Inter-packet timing encodes bits (difficult to detect, difficult to implement reliably)
- **DNS steganography**: Payload encoded in DNS query subdomains or TXT records — traffic appears as normal DNS lookups
- **HTTP steganography**: Data hidden in HTTP headers, cookie values, or URL parameters
- **ICMP**: Payload embedded in ping packet data fields

**Operational relevance**: Protocol steganography is harder to detect passively than file-based methods because it requires correlation of traffic over time, but it is fragile — network equipment, proxies, and NAT may alter headers or timing.

---

### Steganalysis: Detection of Steganography

Understanding detection is essential for both operational security and for assessing whether a system is viable.

#### Visual / Auditory Inspection

Naive: simply looking or listening for anomalies. Effective only against very poor implementations or massive payload ratios.

#### Statistical Analysis

The most operationally serious threat. Statistical steganalysis compares the carrier's statistical properties against known baseline distributions.

- **Chi-square attack**: Effective against sequential LSB embedding. Measures deviation from expected pixel value pair frequencies. A clean image has a characteristic pair frequency distribution; LSB embedding disrupts it.
- **RS Analysis** (Regular-Singular): Detects LSB flipping by measuring the proportion of regular, singular, and unusable pixel groups. Reliable against LSB substitution even at low embedding rates.
- **Sample Pair Analysis**: Refines RS for better accuracy at low payload ratios.

#### Machine Learning Steganalysis

Modern steganalysis uses trained classifiers (CNNs, ensemble classifiers) on feature sets extracted from images. These can detect steganography at very low embedding rates with high accuracy against known algorithms.

**Key implication** [Inference — based on published academic literature; operational deployment status of adversarial steganalysis tools is not publicly confirmed]: Any single steganographic algorithm with a known signature is potentially detectable if an adversary applies targeted steganalysis. Security through obscurity of the _algorithm used_ adds a layer — but should not be the primary defense.

#### Metadata Analysis

Steganographic tools often leave artifacts:

- File size anomalies
- Metadata field inconsistencies
- Compression artifact patterns inconsistent with declared creation software

**Countermeasure**: Strip metadata before embedding. Reconstruct metadata to match expected output of a plausible creation tool.

---

### Operational Principles

These are synthesized from open-source tradecraft literature. [Inference — their effectiveness in specific adversarial environments is not guaranteed and depends heavily on the threat model.]

#### Carrier Selection

- Use carriers that are contextually plausible — photos a person would genuinely send
- Use carriers with high entropy content (complex photos, not solid-color images) — high entropy provides more hiding capacity and makes statistical deviation less detectable
- Avoid reusing carriers. Each reuse creates a comparison baseline for an analyst.

#### Payload Ratio Discipline

Keep the payload small relative to carrier capacity. Embedding 5% of carrier capacity is significantly harder to detect than embedding 50%. Prefer multiple small transmissions over one large one.

#### Encrypt Before Embedding

Even if the steganographic layer fails, an encrypted payload reveals nothing. Use strong symmetric encryption (AES-256) on the payload before embedding. [Unverified — specific tool implementations of combined encryption+steganography vary; verify the implementation of any tool you use.]

#### Channel Discipline

The steganographic channel is only as secure as the transmission channel. Posting a stego image on a monitored platform that logs metadata, compresses images, or scans for known stego signatures eliminates most of the operational benefit.

#### One-Way Carriers Where Possible

If the carrier medium is expected to flow one direction (e.g., public image posts), an analyst cannot request the original carrier for comparison. Direct file transfer allows carrier comparison — original vs. received — which is a powerful detection method.

---

### Practical Open-Source Tools (for study and understanding)

|Tool|Domain|Method|Notes|
|---|---|---|---|
|Steghide|Image, Audio|DCT / LSB + encryption|Passphrase-protected; JPEG/BMP/WAV|
|OpenStego|Image|LSB|Open-source, GUI available|
|zsteg|Image|Detection/analysis|Used for steganalysis of PNG/BMP|
|stegsolve|Image|Visual analysis|Multiple filter planes for detection|
|Outguess|Image|DCT|Designed to resist chi-square attack|
|mp3stego|Audio|MP3|Embeds during MP3 encoding|
|snow|Text|Whitespace|Trailing whitespace in text files|

---

### Steganalysis as a Defensive Skill

Practitioners should be able to detect as well as employ. Workflow for analyzing a suspected carrier:

1. **Metadata inspection** — `exiftool` to review all metadata fields for anomalies
2. **File structure analysis** — `binwalk` to detect appended data or embedded files
3. **Statistical analysis** — `zsteg` (PNG), `stegdetect` (JPEG) for algorithmic signatures
4. **Visual analysis** — `stegsolve` to examine individual bit planes (LSB plane of an embedded image often shows structured noise rather than random noise)
5. **String extraction** — `strings` command on binary files for plaintext fragments in payloads
6. **Comparison** — if the original carrier is available, byte-by-byte comparison is definitive

---

### Relationship to OPSEC and Covert Communication

Steganography alone is not a covert communication system — it is one layer. A complete system requires:

- A **key exchange** mechanism (how do both parties share the embedding key?)
- A **channel** that does not degrade, monitor, or transform the carrier
- A **plausible cover story** for the carrier's transmission (who sends this, why, to whom)
- **Payload encryption** independent of the steganographic layer
- **Compartmentalization** — neither party should use the same method across multiple unrelated operations

The weakest link is rarely the steganographic algorithm itself. It is almost always the human behavior surrounding its use: reusing carriers, sending implausibly large files, using the same platform repeatedly, or failing to encrypt the payload.

---

**Key Points**

- Steganography hides the _existence_ of a message, not just its content
- LSB substitution is the foundational technique; DCT-domain embedding is more robust to compression
- Statistical steganalysis (chi-square, RS analysis) is a credible threat against naive LSB implementations
- Carrier selection, payload ratio discipline, and pre-embedding encryption are the primary operational controls
- No steganographic system is undetectable under all conditions — the goal is to be undetectable to the expected threat, not universally [Inference — absolute undetectability is not claimed in the academic literature]

---

