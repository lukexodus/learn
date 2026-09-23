## Metadata Stripping


Metadata is data about data. It is generated automatically, embedded invisibly, and persists through actions — saving, copying, sending — that the user experiences as neutral. In operational contexts, metadata is frequently more dangerous than content because it is not considered, not seen, and not treated as sensitive by people who would immediately recognize the sensitivity of the content it describes. A document with all identifying text removed can still carry the author's name, organization, editing history, GPS coordinates, device identifiers, and software environment in its metadata layer.

---

### What Metadata Is and Where It Lives

**File System Metadata**

Every file on any operating system carries file system metadata maintained by the OS independently of the file's content:

- Creation timestamp
- Modification timestamp
- Access timestamp
- File owner (user account)
- File permissions
- File size
- Inode number (Unix/Linux) or file reference number (Windows NTFS)

These are not embedded in the file itself but in the file system's index. They travel with the file when it is copied to another file system and are readable by anyone with filesystem access. Timestamps in particular are operationally significant — they can establish when a document was created or modified relative to known events, and they reflect the local system clock, which may encode timezone information.

**Document Metadata (Office Formats)**

Microsoft Office formats (.docx, .xlsx, .pptx) and their Open Document equivalents store extensive metadata within the file container:

- Author name (from OS user account at time of creation)
- Last modified by
- Company or organization name (from Office installation)
- Creation date and time
- Last modification date and time
- Total editing time
- Document revision number
- Template used
- Software version
- Custom document properties (variable, set by user or organization)

Track changes and comments — even deleted ones — are retained in the document XML unless explicitly removed. A document that appears clean may contain the full editing history, including deleted text, prior author names, and comment threads, in its revision data.

**PDF Metadata**

PDFs carry metadata in two locations: the Document Information Dictionary (older format) and XMP (Extensible Metadata Platform) data embedded as XML. Fields include:

- Author
- Creator application (the software that generated the source document)
- Producer application (the software that converted it to PDF)
- Creation date
- Modification date
- Subject, title, keywords
- PDF/A or PDF/X compliance markers

PDFs generated from Word or LibreOffice carry the original application's metadata into the PDF layer. A PDF that has been "cleaned" at the document level may still carry XMP metadata that was not addressed.

**Image Metadata (EXIF)**

EXIF (Exchangeable Image File Format) data is embedded in JPEG, TIFF, and some PNG files by the capturing device:

- Camera make and model
- Lens information
- Exposure settings (aperture, shutter speed, ISO)
- Date and time of capture (device clock)
- GPS coordinates (latitude, longitude, altitude) — if location services were enabled
- GPS timestamp (often UTC, independent of device timezone setting)
- Device serial number (some manufacturers)
- Software version used for processing

GPS coordinates are the most operationally critical field. An image taken at a safe house, a meeting location, or an operator's residence and transmitted without EXIF stripping carries the precise coordinates of that location to any recipient. This has caused real-world operational and personal security compromises across multiple documented cases. [Verified as a documented class of OPSEC failure; specific case citations are open-source available.]

Social media platforms strip EXIF data before display on most major platforms. Messaging applications vary — some strip, some do not. Direct file transfer (email attachment, file sharing service, encrypted messenger file transfer) typically preserves EXIF data intact.

**Audio and Video Metadata**

Audio files (MP3, FLAC, WAV) carry ID3 tags or equivalent metadata including software used for recording, timestamps, and device information. Video files carry container metadata (creation time, encoding software, GPS if captured on a mobile device) separate from any embedded subtitles or chapter data. Screen recordings capture software version and sometimes username in container metadata.

**Email Metadata**

Email headers contain:

- Originating IP address (for direct sends; suppressed by major webmail providers but present in some configurations)
- Mail client and version
- Send timestamp with timezone
- Message ID (unique identifier linkable across forwarded copies)
- Routing hops (each mail server that handled the message)
- MIME boundary identifiers (can fingerprint specific mail clients)

An email's visible fields — From, To, Subject, Body — are a small fraction of the data transmitted with each message.

**Archive and Compressed File Metadata**

ZIP, TAR, and similar archive formats preserve the metadata of their contained files including file paths (which may reveal directory structure and usernames), timestamps, and OS-specific permission data. A ZIP archive created on a Windows machine and transferred to a Linux recipient may expose the original Windows username in file path data.

---

### Metadata as an Intelligence Source

**Identity Attribution**

Author fields in Office documents and PDF creator fields directly name the individual who created the document, using the name registered in the software installation or OS account. Organizations that do not enforce generic account names on operational systems produce documents that attribute directly to individuals by name, and sometimes by organizational unit.

**Device Fingerprinting**

Software version strings, EXIF camera model data, and mail client identifiers allow the same device to be linked across multiple documents or communications. If two documents produced on the same machine are obtained separately, their metadata may establish that they share a common origin even if their content is unrelated.

**Location Reconstruction**

GPS EXIF data provides precise location. Timezone data embedded in timestamps provides approximate location. IP address data in email headers provides approximate location at network level. Combined across multiple documents and communications, these data points allow location pattern reconstruction that is independent of any content the operator intended to communicate.

**Timeline Reconstruction**

Document creation and modification timestamps, email send times, and GPS timestamps allow reconstruction of an operator's activity timeline. A document created at 0300 local time, modified twice over the following four hours, and sent at 0715 establishes a behavioral pattern. Timezone information embedded in these timestamps may be inconsistent with the cover story's claimed location.

**Organizational Attribution**

Company fields in Office metadata, email routing through organizational mail servers, and software license registration data can attribute a document to an organization even when the content is carefully sanitized of organizational identifiers.

---

### Stripping Approaches by File Type

**Microsoft Office Documents**

The built-in Document Inspector (File → Info → Check for Issues → Inspect Document) identifies and removes:

- Comments and revisions
- Document properties and personal information
- Hidden text
- Embedded data
- Custom XML data

Limitations: Document Inspector does not always catch all metadata fields, and its behavior varies across Office versions. [Verified as a known limitation; specific version behavior is [Inference] without current testing.] It should be treated as a first pass, not a final verification.

The more reliable approach for Office formats is to save the document content into a new file created under a clean account with sanitized software installation settings, rather than cleaning the existing file. The new file will carry the new account's metadata from creation.

LibreOffice provides metadata removal under Tools → Macros or via the built-in option during save — "Remove personal information on saving" — which can be set permanently in security settings. LibreOffice's metadata footprint is generally smaller than Microsoft Office's, but it is not zero.

**PDF Files**

_ExifTool_ is the most widely used command-line tool for PDF metadata inspection and removal:

```bash
exiftool -all= input.pdf -o output.pdf
```

This removes all metadata fields ExifTool can address. However, some PDF metadata — particularly in complex PDFs with embedded objects — may survive ExifTool processing. Verification after stripping is required.

_qpdf_ can linearize and rewrite PDFs in ways that remove some metadata structures:

```bash
qpdf --linearize input.pdf output.pdf
```

_Ghostscript_ can re-render a PDF, which strips most metadata through the rendering process, but can alter visual fidelity and is not appropriate for all document types.

The most reliable approach for PDFs containing sensitive content is to print to a new PDF from a clean application instance with sanitized metadata settings, rather than post-processing an existing file.

**Images**

_ExifTool_ is the standard tool:

```bash
# Inspect
exiftool image.jpg

# Remove all metadata
exiftool -all= image.jpg

# Remove all metadata, output to new file
exiftool -all= input.jpg -o output.jpg
```

ExifTool handles JPEG, TIFF, PNG, and numerous other formats. For PNG files, note that metadata handling differs from JPEG — ExifTool addresses the primary metadata blocks but PNG has multiple chunk types, some of which may require separate handling.

_mat2_ (Metadata Anonymisation Toolkit 2) is a command-line and GUI tool that handles multiple file formats:

```bash
mat2 image.jpg
```

mat2 produces a cleaned copy with the suffix `.cleaned` and is designed specifically for metadata removal across document and image types.

**Verification After Stripping**

Stripping without verification is insufficient. After processing, the output file must be inspected to confirm removal:

```bash
exiftool output.jpg
```

Or for documents:

```bash
exiftool output.pdf
```

The output should show only fields that are expected and acceptable. Any residual author, GPS, software, or timestamp data that was not intended to remain must be addressed before the file is transmitted.

**Bulk Processing**

For multiple files:

```bash
exiftool -all= /path/to/directory/
```

ExifTool processes directories recursively with the `-r` flag. Bulk processing must still be followed by spot-check verification — processing errors, unsupported metadata formats, or edge cases in specific files will not always produce error output.

---

### Operational Practices

**Strip at Creation, Not at Transmission**

The most reliable practice is to configure the operational environment to minimize metadata generation from the point of file creation. This includes:

- Operating system accounts with non-attributing usernames
- Office software registered without real name or organization
- Camera and device location services disabled at the OS level, not only the application level
- System clock set to UTC or to a timezone consistent with cover

Stripping at transmission is a second-line control. It fails when the operator forgets, when the tool misses a metadata type, or when the file is transmitted through an intermediary that reintroduces metadata. Creation-time control is more robust.

**The Clean Machine Principle**

A device used for operational document production should not be the same device used for personal or professional activities under real identity. Device-level metadata — software licenses, account names, registered organizational data — cannot be fully stripped from produced files if the device is registered to a real identity. The operational device must be operationally clean from initial configuration.

**Format Conversion as a Stripping Method**

Converting a document through a format that does not support the original metadata structure can strip metadata as a side effect. Converting a Word document to plain text (.txt) removes all Office metadata because the format does not support it. Converting back to a new Word document then carries only the new creation metadata. This approach loses formatting but is reliable for text-content documents where formatting is not operationally significant.

Similarly, re-photographing a screen displaying an image — rather than transmitting the image file — strips all EXIF data. The re-photographed image carries only the second device's metadata. This is operationally crude but functionally reliable for static content.

**Steganographic Metadata**

Beyond standard metadata fields, some software embeds invisible watermarking or steganographic identifiers in document content itself — not in metadata fields but in the content layer. This is used by some organizations for leak attribution. It is not addressable by standard metadata stripping tools because it does not exist in metadata fields. Detection and removal of steganographic content requires specialized analysis and is outside the scope of standard OPSEC metadata practice. [Inference: The presence and prevalence of document steganography in operational environments varies and cannot be verified without specific organizational knowledge.]

**Metadata in Transmitted Data**

File transmission itself generates metadata: server logs, delivery receipts, access logs, and network timing data that exist outside the file and cannot be addressed by stripping the file. A file stripped of all internal metadata and transmitted via an unencrypted or logged channel still generates an external metadata record of the transmission. File-level metadata stripping and transmission channel security are separate controls that must both be addressed.

---

### Tools Reference

|Tool|Platform|Formats|Interface|
|---|---|---|---|
|ExifTool|Cross-platform|Images, PDF, audio, video, Office|CLI|
|mat2|Linux, macOS|Images, Office, PDF, audio|CLI, GUI|
|Document Inspector|Windows (Office)|.docx, .xlsx, .pptx|GUI|
|qpdf|Cross-platform|PDF|CLI|
|Ghostscript|Cross-platform|PDF|CLI|
|MAT (v1)|Linux|Multiple|GUI (deprecated; mat2 preferred)|

---

**Key Points**

- Metadata is generated automatically and invisibly; it does not require operator action to be created and does not require operator awareness to be transmitted.
- GPS EXIF data in images is among the highest-risk metadata categories in operational contexts — it can directly locate personnel and sites.
- Stripping tools must be verified after use; no tool addresses all metadata in all file types under all conditions.
- Creation-time control — clean accounts, clean devices, location services disabled — is more reliable than post-processing stripping.
- File-level metadata stripping does not address transmission-level metadata; both must be managed as separate controls.
- Steganographic watermarking in document content is not addressable by standard metadata tools and requires separate consideration. [Inference]
- Format conversion through a metadata-incompatible format is a reliable stripping method for content where formatting loss is acceptable.

---

