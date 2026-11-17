# Session 23 Reflection: Pixel Representation, Memory Layout, Channel Ordering, Endianness
**Date:** 03 November 2026

### 1. Pixel Color Representation: RGB vs. RGBA
While Session 22 focused on processing and filtering images, this session looked at how pixel color data is physically represented and stored in memory. Each color channel uses $8\text{ bits}$ ($1\text{ byte}$), giving an intensity range of $0$ to $255$.

| Format | Channels | Bytes per Pixel | Details |
| :--- | :--- | :--- | :--- |
| **RGB** | Red, Green, Blue | $3\text{ bytes}$ ($24\text{ bits}$) | Represents $256^3 \approx 16.7\text{ million}$ distinct colors |
| **RGBA** | Red, Green, Blue, Alpha | $4\text{ bytes}$ ($32\text{ bits}$) | Adds an Alpha channel for transparency ($0$ = fully transparent, $255$ = fully opaque) |

### 2. Image Memory Layout & 1D Array Indexing
Visually, a raster image is a 2D grid of rows and columns, but in computer memory, all pixel values are flattened and stored sequentially in a single continuous 1D byte array.

```text
2D Image Grid (Rows x Columns)  ->  Flattened 1D Byte Array in Memory: [R, G, B, R, G, B, ...]
```

To locate the starting byte index of a pixel at row $i$ and column $j$ in an image with width $n$ (number of columns):
- **RGB ($3\text{ bytes/pixel}$):** $\text{Index} = (i \times n + j) \times 3$
- **RGBA ($4\text{ bytes/pixel}$):** $\text{Index} = (i \times n + j) \times 4$

**How the formula works:**
1. $i \times n$ counts all the pixels in the previous full rows.
2. $+ j$ adds the horizontal offset within the current row.
3. Multiplying by $3$ (or $4$) scales the pixel count by the number of bytes each pixel occupies in memory.

### 3. Channel Ordering (RGBA, BGRA, ARGB)
The actual visual color of a pixel does not change, but different platforms and libraries store the color channels in different sequences:
- **Common layouts:** `RGBA`, `BGRA`, `ARGB`, `BGR`.
- **Framework differences:** HTML `Canvas` works with `RGBA` pixel arrays, whereas Java's `BufferedImage` supports multiple internal layouts such as `ARGB` and `BGR`.
- **Why it matters:** If an application expects `RGBA` data but receives `BGRA` data without converting it, the Red and Blue channels get swapped, causing the image to render with inverted red/blue colors.

### 4. Endianness & Network Byte Order
**Endianness** defines how bytes are ordered in memory when storing a single multi-byte value (such as a 32-bit integer representing an `ARGB` pixel). Using the 4-byte hexadecimal value `0x12345678`:

| Byte Order | Storage Rule | Memory Sequence (`0x12345678`) | Common Usage |
| :--- | :--- | :--- | :--- |
| **Big-Endian** | Most significant byte stored first | `12 34 56 78` | **Network Byte Order** (standard across network protocols) |
| **Little-Endian** | Least significant byte stored first | `78 56 34 12` | **Intel processors** (x86/x64 hardware architectures) |

**Channel Ordering vs. Endianness:**
- Even though both deal with byte arrangement, they operate at different levels. Before this session, it was easy to assume that writing an `ARGB` value meant the bytes would always sit in memory in that exact order—but on a little-endian machine, a 32-bit integer is stored in reverse byte order in memory.
- **File Format Headers (TIFF Example):** Because different machines use different endianness, the **TIFF** image format places a specific marker at the very beginning of the file to declare its byte order, allowing the reading software to parse the remaining image data properly.

### 5. Connections to Prior Sessions
- **Early Raster Graphics Sessions:** Earlier in the course, we treated raster images conceptually as 2D grids of pixels; this session explained how those grids are mapped into linear byte arrays in memory.
- **Session 22 (Spatial Filtering & Convolution):** In Session 22 (and in our median filter project), we manipulated pixel intensity values across neighborhoods. Understanding 1D byte arrays and channel offsets explains how an image processing program actually fetches and modifies those pixel values in memory.
- **Session 7 (UTF-8 vs. UTF-16 Character Encoding):** Just like text encodings require strict rules for converting characters into byte sequences, image formats require agreed-upon channel orderings and endianness so bytes are not misinterpreted across systems.

### Summary of Technical Points
- **Pixel depth:** RGB uses $3\text{ bytes}$ per pixel ($\approx 16.7\text{ million}$ colors, $0\text{--}255$ per channel); RGBA uses $4\text{ bytes}$ to include an Alpha transparency channel.
- **1D memory indexing:** A 2D image of width $n$ is stored as a continuous 1D array; pixel $(i, j)$ starts at $(i \times n + j) \times 3$ for RGB and $(i \times n + j) \times 4$ for RGBA.
- **Channel ordering:** Formats like `RGBA`, `BGRA`, and `ARGB` store the same color data in different sequences (e.g., HTML Canvas uses `RGBA`, while Java `BufferedImage` supports `ARGB` and `BGR`). Mismatched channel orders cause color swapping.
- **Endianness:** Dictates byte order for multi-byte values (`0x12345678`). **Big-endian** stores the most significant byte first (used as **network byte order**); **little-endian** stores the least significant byte first (used by **Intel CPUs**).
- **Cross-system compatibility:** File formats like **TIFF** embed a byte-order header marker so different architectures can read multi-byte pixel data accurately.
