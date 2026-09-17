<!-- TOC START -->
**Table of Contents** — 5 subtopics · 7 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Computer Graphics (Vector & Raster)](#computer-graphics-vector--raster-3) | 3 |
| 2 | [Color Models](#color-models-1) | 1 |
| 3 | [Frequency Domain Filtering](#frequency-domain-filtering-1) | 1 |
| 4 | [Edge Detection](#edge-detection-1) | 1 |
| 5 | [Morphological Operations](#morphological-operations-1) | 1 |

<!-- TOC END -->

---

## Computer Graphics (Vector & Raster) (3)

1. **(ক) Vector এবং Raster graphics- এর সংজ্ঞাসহ পার্থক্য লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

Answer: (Answered in English, as required for IT topics.) `Vector graphics` describes an image with `mathematical objects` — points, lines, curves and polygons — each with its own coordinates, colour and thickness. The file stores instructions to draw the picture, not the picture itself, so it is redrawn from equations at any size with `no loss of quality`. Formats: `SVG, AI, EPS, PDF, CDR`.

   `Raster graphics` stores an image as a `grid of pixels`, each holding a colour value (a bitmap). Pixel count is fixed at creation, so enlarging stretches the pixels and looks blocky — `pixelation`. Formats: `JPEG, PNG, GIF, BMP, TIFF`.

   ```
      Vector : a circle = centre (50,50), radius 25, red
               -> a few bytes, redrawn perfectly at any size

      Raster : the same circle as pixel values
               +--+--+--+--+--+
               |  |##|##|  |  |
               +--+--+--+--+--+     -> fixed resolution
               |##|##|##|##|  |
               +--+--+--+--+--+
   ```

   | Point | Vector graphics | Raster graphics |
   |---|---|---|
   | Stored as | Mathematical paths and shapes | A grid of pixels |
   | Scaling | Any size, no quality loss | Enlarging causes pixelation |
   | Resolution | Independent | Fixed at creation |
   | File size | Small for simple artwork | Large, grows with resolution |
   | Editing | Each object edited separately | Pixels edited; not separable |
   | Best for | Logos, text, icons, CAD drawings | Photographs, scanned images |
   | Rendering | Computed each time — slower | Displayed directly — faster |
   | Software | Illustrator, CorelDRAW, Inkscape | Photoshop, GIMP, MS Paint |

   - A logo stays `vector` so it prints sharp on a business card and a billboard from the same file; a photograph must be `raster`, since no equation can describe the millions of subtly different colours in a real scene.

2. **(b) Differentiate between vector graphics and raster graphics. What are the applications of computer Graphics?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 888-889 (ET: N/A)]*

Answer: `Vector graphics` describes an image with mathematical objects — points, lines, curves and polygons — each with coordinates, colour and thickness. It is redrawn from equations at any size, so it scales with `no loss of quality`. Formats: `SVG, AI, EPS, PDF, CDR`.

   `Raster graphics` stores an image as a `grid of pixels` (a bitmap), each holding a colour value. Pixel count is fixed at creation, so enlarging stretches the pixels and causes `pixelation`. Formats: `JPEG, PNG, GIF, BMP, TIFF`.

   | Point | Vector graphics | Raster graphics |
   |---|---|---|
   | Stored as | Mathematical paths | A grid of pixels |
   | Scaling | Any size, no quality loss | Enlarging causes pixelation |
   | Resolution | Independent | Fixed at creation |
   | File size | Small for simple artwork | Large, grows with resolution |
   | Editing | Objects edited individually | Pixel-level editing only |
   | Best for | Logos, icons, text, maps, CAD | Photographs, scans, realistic images |
   | Display speed | Slower — must be computed | Faster — shown directly |
   | Software | Illustrator, CorelDRAW, Inkscape | Photoshop, GIMP |

   Applications of computer graphics
   - `User interfaces` — windows, icons, menus, buttons (the largest use).
   - `CAD/CAM` — designing buildings, machines, circuits, vehicles.
   - `Entertainment` — games, animated films, visual effects, real-time 3D rendering.
   - `Medical imaging` — CT/MRI/ultrasound reconstruction for diagnosis.
   - `Scientific visualisation` — weather models, fluid flow, molecular structure.
   - `Presentation graphics` — charts and infographics.
   - `GIS/cartography` — digital maps, satellite imagery, navigation.
   - `Simulation/training` — flight and driving simulators, surgical training.
   - `Virtual/augmented reality` — immersive training, design review, gaming.
   - `Image processing` — enhancing and analysing photographs, satellite images.
   - `Desktop publishing` — layout of books, posters, packaging.

   - In practice both are combined: an advertisement uses `vector` for the sharp logo/text and `raster` for the photograph.

3. **Raster Image কাকে বলে?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) A `raster image` is an image stored as a rectangular `grid of pixels`, where each pixel holds a colour value. It is also called a `bitmap` image.

   - The word raster comes from the way the picture is drawn — row by row, left to right and top to bottom, exactly as a CRT screen scans.
   ```
      A 5 x 4 raster image = 20 pixels

      +----+----+----+----+----+
      | W  | W  | K  | K  | W  |     each cell holds one colour value
      +----+----+----+----+----+
      | W  | K  | K  | K  | K  |
      +----+----+----+----+----+
      | K  | K  | W  | W  | K  |
      +----+----+----+----+----+
      | W  | K  | K  | K  | W  |
      +----+----+----+----+----+
   ```

   Key properties
   - `Resolution` — the number of pixels, written as width x height, for example 1920 x 1080. It is fixed when the image is created.
   - `Bit depth` — the number of bits per pixel, which decides how many colours are possible.
   ```
      1 bit   :  2 colours (black and white)
      8 bit   :  256 colours or 256 grey levels
      24 bit  :  16.7 million colours (8 bits each for R, G and B)
      32 bit  :  24-bit colour plus an 8-bit alpha (transparency) channel
   ```
   - `File size` grows with both: `Size = width x height x bit depth / 8` bytes, e.g. 1920x1080x24/8 ~= 6 MB uncompressed.
   - `Scaling` — enlarging stretches the fixed pixels, causing `pixelation`, the format's main limitation.

   Formats
   ```
      JPEG : lossy compression, best for photographs, no transparency
      PNG  : lossless, supports transparency, best for screenshots and graphics
      GIF  : 256 colours, supports simple animation
      BMP  : uncompressed, very large
      TIFF : lossless, used in printing and scanning
   ```

   - Raster images come from digital cameras, scanners, screenshots and painting programs — anything capturing real-world detail. The alternative, `vector` graphics, stores mathematical shapes instead of pixels and scales without loss; raster suits photographs, vector suits logos and diagrams.

## Color Models (1)

1. **(ক) বিভিন্ন Color model-এর নাম লিখুন। CMY color model-এর ব্যবহার কী?** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

Answer: (Answered in English, as required for IT topics.) A `colour model` is a mathematical way of describing a colour as a set of numbers, so a computer can store, transmit and reproduce it.

   Names of the main colour models
   - `RGB` (Red, Green, Blue) — additive; light is added, so full gives white, none gives black. Used by monitors, TVs, cameras, projectors (anything that emits light).
   - `CMY/CMYK` (Cyan, Magenta, Yellow, Key=black) — subtractive; wavelengths are removed with ink. Used by printers.
   - `HSV/HSI/HSB` (Hue, Saturation, Value/Intensity) — describes colour as people do; used in editing tools and colour pickers.
   - `YUV/YCbCr/YIQ` — separates luminance (Y, brightness) from chrominance (colour); used in TV broadcasting, JPEG/MPEG compression since the eye is more sensitive to brightness than colour.
   - `CIE XYZ / CIE Lab` — device-independent, based on human eye response; `Lab` is perceptually uniform; used as the reference for colour management.
   - `Grayscale` — a single intensity value (0-255) per pixel; used in medical imaging and document scanning.

   Use of the CMY colour model
   - Ink does not emit light; it `absorbs` some wavelengths and reflects the rest, so mixing is subtractive — its purpose is `colour printing`.
   ```
      Cyan    absorbs RED     ->  reflects green + blue
      Magenta absorbs GREEN   ->  reflects red + blue
      Yellow  absorbs BLUE    ->  reflects red + green

      Conversion from RGB:  C = 1-R,  M = 1-G,  Y = 1-B   (values normalised 0-1)
   ```
   - Printers actually use `CMYK`, not CMY: mixing all three inks gives a muddy dark brown rather than true black, wastes costly colour ink, and blurs black text needing perfect registration. A separate `K` (black) ink is added instead — cheaper and genuinely black (`black generation`/`under-colour removal`).
   - Consequence: a design bright on an RGB monitor looks duller printed, because the CMYK `gamut` is smaller than RGB's — so designers work in CMYK for print.

## Frequency Domain Filtering (1)

1. **How does Butterworth High pass Filter works?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*

Answer: A `high-pass filter` in the frequency domain keeps the `high frequencies` — edges, fine detail and noise — and suppresses the `low frequencies`, which carry the smooth, slowly varying background. The result is a sharpened image with edges standing out.

   The Butterworth high-pass filter transfer function
   ```
                        1
      H(u,v) = ---------------------------
                1 + [ D0 / D(u,v) ]^(2n)
   ```
   ```
      D(u,v) = sqrt( (u - M/2)^2 + (v - N/2)^2 )
               the distance of the point (u,v) from the centre of the
               frequency rectangle

      D0 = cut-off frequency (the radius of the stop band)
      n  = order of the filter
   ```

   Behaviour
   ```
      D(u,v) = 0    ->  H = 0        the DC term is removed
      D(u,v) = D0   ->  H = 0.5      the half-power point
      D(u,v) >> D0  ->  H -> 1       high frequencies pass unchanged
   ```

   Response curve
   ```
      H(u,v)
        1 |                    _____________________
          |               ___/
      0.5 |............../....................... n = 4 (sharp)
          |          ___/
          |      ___/                              n = 1 (gentle)
        0 |____/________________________________ D(u,v)
          0        D0
   ```
   - The `order n` controls how sharp the transition is. A low n gives a gradual roll-off; a high n approaches the ideal brick-wall filter.

   How it is applied
   ```
      1. Read the image f(x,y)
      2. Multiply by (-1)^(x+y) to centre the spectrum
      3. Take the 2-D FFT  ->  F(u,v)
      4. Multiply point by point :  G(u,v) = H(u,v) . F(u,v)
      5. Take the inverse FFT
      6. Take the real part and multiply by (-1)^(x+y) again
      7. The result g(x,y) is the sharpened image
   ```

   ```mermaid
   flowchart LR
       A[Input image] --> B[2-D FFT]
       B --> C[Multiply by H u,v]
       C --> D[Inverse FFT]
       D --> E[Sharpened image]
   ```

   Why Butterworth over the ideal filter
   - An `ideal` HPF cuts everything below D0 abruptly, which produces visible `ringing` in the spatial domain. Butterworth's response is `smooth and monotonic`, so ringing is greatly reduced (a `Gaussian` HPF removes it fully but cuts less sharply — Butterworth is the usual compromise).

   Uses
   - Sharpening and edge enhancement, removing slow illumination variation, medical/satellite image enhancement, and `homomorphic filtering`.

   - Since the DC term is zero, output loses average brightness and looks dark; a `high-frequency emphasis` filter (`H' = a + b.H(u,v)`) fixes this by retaining some low frequencies.

## Edge Detection (1)

1. **What are the basic objectives of canny edge detection method?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*

Answer: The `Canny edge detector` (John F. Canny, 1986) was designed around three mathematical objectives, which the algorithm's steps exist to satisfy.

   1. `Good detection` (low error rate) — find as many real edges as possible with as few false edges as possible. Achieved by smoothing with a `Gaussian filter` first, to remove noise that would otherwise be reported as edges.

   2. `Good localization` — the marked edge pixel must lie as close as possible to the centre of the true edge. Achieved by computing the gradient after smoothing, then `non-maximum suppression`, keeping only the pixel at the exact ridge.

   3. `Minimal response` (single response per edge) — a real edge is marked only once, not as a thick band. Achieved again by non-maximum suppression, thinning the ridge to one pixel wide.

   The five steps that implement these objectives
   ```mermaid
   flowchart LR
       A[Input image] --> B[1. Gaussian smoothing]
       B --> C[2. Gradient magnitude<br/>and direction]
       C --> D[3. Non-maximum<br/>suppression]
       D --> E[4. Double thresholding]
       E --> F[5. Hysteresis<br/>edge tracking]
       F --> G[Final edges]
   ```
   ```
      1. Smooth with a Gaussian of standard deviation sigma  -> removes noise
      2. Compute the gradient, usually with Sobel masks

            G = sqrt(Gx^2 + Gy^2)        theta = arctan(Gy / Gx)

      3. Non-maximum suppression : along the gradient direction, keep a pixel
         only if it is larger than both its neighbours; otherwise set it to 0
      4. Double threshold : classify each surviving pixel

            G > T(high)              -> strong edge, definitely keep
            T(low) < G < T(high)     -> weak edge, keep only if connected
            G < T(low)               -> discard

      5. Hysteresis : keep a weak edge only if it touches a strong edge,
         directly or through a chain of weak ones
   ```

   - Hysteresis matters because a single threshold either breaks edges (too high) or lets noise through (too low); with two thresholds, strong evidence starts an edge and weak evidence is kept only where it connects to one. Usual ratio `T(high):T(low) = 2:1 or 3:1`.
   - Trade-off: a large `sigma` removes more noise but blurs/displaces edges; a small sigma keeps detail but lets noise through.

## Morphological Operations (1)

1. **Define: (i) Erosion and Dilation; (ii) Opening and Closing.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*

Answer: `Morphological operations` process the `shape` of objects in a binary (or grayscale) image. Each one slides a small shape called a `structuring element (SE)` over the image and decides each output pixel from the neighbourhood the SE covers.

   (i) Erosion and Dilation

   `Erosion` — written `A (-) B`
   - Output pixel = 1 only if the SE fits `entirely inside` the object at that position (grayscale: `minimum` of the neighbourhood).
   - Effect: objects `shrink`, thin connections break, small isolated specks of noise disappear.
   ```
      Before erosion              After erosion (3x3 SE)
      0 0 0 0 0 0 0               0 0 0 0 0 0 0
      0 1 1 1 1 1 0               0 0 0 0 0 0 0
      0 1 1 1 1 1 0               0 0 1 1 1 0 0
      0 1 1 1 1 1 0               0 0 0 0 0 0 0
      0 0 0 0 0 0 0               0 0 0 0 0 0 0
      0 0 1 0 0 0 0               0 0 0 0 0 0 0   <- the lone speck is gone
   ```
   - Uses: removing salt noise, separating objects that touch, and finding the boundary by `A - erosion(A)`.

   `Dilation` — written `A (+) B`
   - Output pixel = 1 if the SE `overlaps` the object at all (grayscale: `maximum` of the neighbourhood).
   - Effect: objects `grow`, small holes and narrow gaps are filled, broken lines are joined.
   ```
      Before dilation             After dilation (3x3 SE)
      0 0 0 0 0                   0 1 1 1 0
      0 0 1 0 0                   1 1 1 1 1
      0 1 1 1 0        ->         1 1 1 1 1
      0 0 1 0 0                   1 1 1 1 1
      0 0 0 0 0                   0 1 1 1 0
   ```
   - Uses: filling small holes, bridging gaps in broken characters before OCR, and thickening thin features.
   - The two are `duals`: eroding the object is the same as dilating the background.

   (ii) Opening and Closing

   `Opening` — written `A o B = dilate( erode(A, B), B )`
   - `Erosion followed by dilation` with the same SE: erosion removes small objects/thin bridges, dilation restores survivors to roughly original size.
   - Effect: removes small objects, thin protrusions and narrow bridges while keeping larger objects' shape/size; smooths the outside of a contour.
   ```
      Two blobs joined by a thin neck  ->  opening separates them
      Small specks of noise            ->  opening removes them completely
   ```
   - Uses: removing salt noise, separating touching objects, size-based filtering.

   `Closing` — written `A . B = erode( dilate(A, B), B )`
   - `Dilation followed by erosion` with the same SE: dilation fills small holes/gaps, erosion shrinks the object back to original size.
   - Effect: fills small holes and narrow gaps and joins nearby objects, keeping overall size; smooths the inside of a contour.
   ```
      A letter with a broken stroke    ->  closing repairs it
      Small holes inside a shape       ->  closing fills them
   ```
   - Uses: removing pepper noise, closing gaps in broken text before OCR, filling small internal holes.

   Summary

   | Operation | Definition | Effect on object size | Removes |
   |---|---|---|---|
   | Erosion | SE must fit inside | Shrinks | Small objects, thin lines |
   | Dilation | SE must overlap | Grows | Small holes, gaps |
   | Opening | Erode then dilate | Roughly unchanged | Small objects, thin bridges, outward spikes |
   | Closing | Dilate then erode | Roughly unchanged | Small holes, narrow gaps, inward notches |

   - Both are `idempotent` (applying twice = applying once), so they are used as shape filters. `Top-hat = A - opening(A)` extracts small bright details; `bottom-hat = closing(A) - A` does the same for dark details — both correct uneven illumination.
