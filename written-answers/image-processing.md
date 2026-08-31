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


   Answer:

   Vector graphics: the image is stored as a set of mathematical instructions, that is points, lines, curves and shapes, each with its own coordinates, colour and thickness. Nothing is stored pixel by pixel. When we display it, the computer computes the shapes again for the current size, so the picture stays sharp at any zoom level.

   Raster graphics: the image is stored as a grid of tiny squares called pixels. Each pixel holds one intensity or colour value, and all the values sit together in a frame buffer. The picture is simply that grid of values, so enlarging it only makes the squares bigger.

   Difference between the two:

   | Point | Vector graphics | Raster graphics |
   |---|---|---|
   | How the image is stored | As mathematical instructions: points, lines, curves and shapes | As a grid of pixels, each holding an intensity or colour value |
   | Storage form | A set of drawing commands | A set of intensity values held in a frame buffer |
   | Scaling | We can enlarge it any amount with no loss of quality, because the maths is recomputed | It becomes blurred and blocky when enlarged, because the pixels are just stretched |
   | Resolution | Does not depend on resolution | Depends on resolution, measured in DPI or PPI |
   | Line quality | Crisp and smooth. Good for polygons and line drawings | Lines can look jagged, because they are drawn from square pixels |
   | Best suited for | Logos, icons, diagrams, maps, fonts, technical drawings | Photographs and realistic scenes with continuous shades |
   | File size | Small, because only the instructions are stored | Large, and it grows with the resolution |
   | Editing | Each object can be selected and edited on its own | We edit pixel by pixel |
   | Filling a solid area | Harder to fill | Easy to fill |
   | Cost of hardware | Higher, because the beam must be steered directly | Cheaper |
   | File formats | SVG, AI, EPS, PDF, DXF | JPEG, PNG, BMP, GIF, TIFF |
   | Software | Adobe Illustrator, CorelDRAW, Inkscape | Adobe Photoshop, GIMP, MS Paint |

   Simple way to remember: a vector image is a recipe for drawing the picture. A raster image is a photograph of the finished picture.

2. **(b) Differentiate between vector graphics and raster graphics. What are the applications of computer Graphics?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 888-889 (ET: N/A)]*


   Answer:

   Difference between vector graphics and raster graphics:

   | Point | Vector graphics | Raster graphics |
   |---|---|---|
   | How the image is stored | As mathematical instructions: points, lines, curves and shapes | As a grid of pixels, each holding an intensity or colour value |
   | Storage form | A set of drawing commands | A set of intensity values held in a frame buffer |
   | Scaling | We can enlarge it any amount with no loss of quality, because the maths is recomputed | It becomes blurred and blocky when enlarged, because the pixels are just stretched |
   | Resolution | Does not depend on resolution | Depends on resolution, measured in DPI or PPI |
   | Line quality | Crisp and smooth. Good for polygons and line drawings | Lines can look jagged, because they are drawn from square pixels |
   | Best suited for | Logos, icons, diagrams, maps, fonts, technical drawings | Photographs and realistic scenes with continuous shades |
   | File size | Small, because only the instructions are stored | Large, and it grows with the resolution |
   | Editing | Each object can be selected and edited on its own | We edit pixel by pixel |
   | Filling a solid area | Harder to fill | Easy to fill |
   | Cost of hardware | Higher, because the beam must be steered directly | Cheaper |
   | File formats | SVG, AI, EPS, PDF, DXF | JPEG, PNG, BMP, GIF, TIFF |
   | Software | Adobe Illustrator, CorelDRAW, Inkscape | Adobe Photoshop, GIMP, MS Paint |

   Applications of computer graphics:
   - User interfaces: every window, icon, menu and button on a screen is computer graphics. This is the largest single use.
   - Computer Aided Design (CAD) and Computer Aided Manufacturing: engineering drawings, building plans, machine parts, circuit layouts.
   - Entertainment: animation, film special effects, and video games.
   - Presentation graphics: charts, graphs and diagrams that turn numbers into a picture people can read quickly.
   - Medical imaging: CT scan, MRI and ultrasound images, and 3D reconstruction of organs for surgical planning.
   - Scientific visualisation: weather models, fluid flow, molecular structures, and simulation results.
   - Geographic Information Systems (GIS): maps, satellite images and route planning.
   - Education and training: simulators for pilots, drivers and surgeons, where real practice would be dangerous or costly.
   - Virtual reality and augmented reality.
   - Image processing and photo editing.
   - Desktop publishing: page layout for books, newspapers and advertising.

3. **Raster Image কাকে বলে?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*


   Answer: A raster image is an image made of a grid of tiny squares called pixels. Each pixel holds one colour or intensity value, and all the values together form the picture. It is also called a bitmap image.

   Key points:
   - The image is stored as a set of intensity values of the pixels, kept in a frame buffer.
   - Resolution means how many pixels the image has, written as width × height, for example 1920 × 1080.
   - Because the picture is a fixed grid, enlarging it does not add any new detail. The pixels simply get bigger, so the image looks blurred and blocky. We call this pixelation.
   - It is resolution dependent. A raster image looks good only at or below the size it was made for.
   - The file size grows with the resolution and with the colour depth, so raster files are usually large. Compression such as JPEG is used to control this.

   Types of raster image by colour depth:
   - Binary or monochrome: each pixel is 0 or 1, that is black or white.
   - Grayscale: each pixel is 0 to 255, from black through the greys to white.
   - Colour (RGB): each pixel has three values, one each for red, green and blue, which mix to give the final colour.

   Where raster images are used: photographs, scanned documents, web images and any picture with continuous shading, because a photograph has no clean shapes that could be described by mathematics.

   File formats: JPEG, PNG, BMP, GIF, TIFF.

   The opposite type is vector graphics, which stores drawing instructions instead of pixels, and can be scaled to any size with no loss of quality.

## Color Models (1)

1. **(ক) বিভিন্ন Color model-এর নাম লিখুন। CMY color model-এর ব্যবহার কী?** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*


   Answer: A colour model is a way of describing a colour with numbers. The common models are RGB, CMY and CMYK, HSV, HSI, YIQ and YCbCr.

   Names of the colour models:
   - RGB, Red Green Blue: an additive model. The three light beams are added together, and their spectra add wavelength by wavelength to make the final colour. Zero intensity in all three gives black; full intensity in all three gives white. Used for sensing, showing and displaying images in electronic systems, that is monitors, televisions, cameras and scanners.
   - CMY, Cyan Magenta Yellow: a subtractive model, used for printing.
   - CMYK: the CMY model with black, written as K for key, added to it. Printers use this one.
   - HSV, Hue Saturation Value: it describes a colour the way a human would. Hue is the colour itself, saturation is how pure it is, and value is how bright it is. It gives an easier way for a person to pick a colour than RGB does. HSI, with Intensity instead of Value, is the same idea.
   - YIQ: used in the old analog television system, where Y is the brightness and I and Q carry the colour. Keeping brightness separate is what let colour television stay compatible with black and white sets.
   - YCbCr: the digital version of the same idea, used in JPEG and in video compression.

   Use of the CMY colour model:
   - CMY is used in printing, that is for any device that puts ink on paper: printers, photocopiers and printing presses.
   - It is subtractive, which is the opposite of RGB. The paper starts white and reflects all the light. Each ink subtracts, that is absorbs, one part of the spectrum. Cyan absorbs red, magenta absorbs green, and yellow absorbs blue.
   - So in CMY, (0,0,0) means no ink, which leaves white paper. And (1,1,1) means all three inks together, which in theory gives black.
   - Conversion from RGB is simple: C = 1 − R, M = 1 − G, Y = 1 − B.
   - Why K, that is black, is added in practice: mixing all three inks does not give a true black. It gives a muddy dark brown, it costs three inks, and it soaks the paper. So a separate black ink is used. That is why a real printer uses CMYK and not CMY.

   Why RGB cannot be used for printing: a monitor emits light, so adding more light makes it brighter and finally white. Paper only reflects light, so adding more ink makes it darker and finally black. The two work in opposite directions, which is why we need two different models.

## Frequency Domain Filtering (1)

1. **How does Butterworth High pass Filter works?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*


   Answer: A Butterworth High Pass Filter (BHPF) works in the frequency domain. It removes the low frequencies of an image and keeps the high ones, so the edges and the fine detail stay while the smooth areas fade away.

   The idea behind it:
   - In an image, low frequency means the slowly changing parts, that is the flat background and the smooth regions.
   - High frequency means the quickly changing parts, that is the edges, the lines, the fine texture and also the noise.
   - A high pass filter therefore sharpens the image, because it keeps only the parts that change fast.

   Transfer function:

   H(u,v) = 1 / [ 1 + (D₀ / D(u,v))^(2n) ]

   where
   - D(u,v) is the distance of the point (u,v) from the centre of the frequency rectangle.
   - D₀ is the cutoff frequency, that is the radius at which the filter is half on.
   - n is the order of the filter, which controls how sharp the transition is.

   How it behaves:
   - When D(u,v) is much smaller than D₀, that is at low frequency, the ratio D₀/D is large, so the denominator is large and H is close to 0. The low frequencies are blocked.
   - When D(u,v) is much larger than D₀, that is at high frequency, the ratio is small, so H is close to 1. The high frequencies pass through.
   - At D(u,v) = D₀ exactly, H = 1/2. That is the half power point.
   - The order n controls the steepness. A low n, such as 1 or 2, gives a gentle slope. A high n makes the curve steeper, and at very high n it approaches an ideal high pass filter.

   Steps to apply it:
   - Take the 2D Fourier transform of the image to move it into the frequency domain.
   - Shift the zero frequency to the centre of the spectrum.
   - Build H(u,v) with the formula above, for the chosen D₀ and n.
   - Multiply the shifted spectrum by H(u,v), point by point.
   - Shift back, then take the inverse Fourier transform to get the filtered image.

   Why Butterworth rather than an ideal filter: an ideal high pass filter cuts sharply at D₀. That sharp cut in the frequency domain produces ringing in the image, that is ripples around every edge. The Butterworth filter changes smoothly from 0 to 1, so it produces very little ringing. A Gaussian high pass filter is even smoother and has no ringing at all, but it gives less control over the sharpness of the cut.

   Uses: sharpening an image, detecting edges, and removing slow uneven illumination from a scanned document.

## Edge Detection (1)

1. **What are the basic objectives of canny edge detection method?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*


   Answer: John Canny designed his edge detector in 1986 around three stated objectives, which are also called the three Canny criteria.

   The three basic objectives:
   - Good detection, that is a low error rate. The detector must find as many real edges as possible, and it must not report edges where there are none. So it must minimise both false negatives, that is missed edges, and false positives, that is noise reported as an edge.
   - Good localisation. The edge point the detector marks must be as close as possible to the true centre of the real edge in the image. The distance between the marked pixel and the actual edge must be minimum.
   - Single response per edge. One real edge must produce exactly one detected edge point. A thick or noisy edge must not be reported several times. This criterion was added because the first two alone still allowed multiple responses.

   How the algorithm meets these objectives, step by step:
   - Step 1, noise reduction: smooth the image with a Gaussian filter. Edge detection uses derivatives, and a derivative amplifies noise badly, so the noise must be removed first. This serves the good detection objective.
   - Step 2, gradient calculation: find the intensity gradient with a Sobel operator in the x and y directions. Then compute the magnitude, √(Gx² + Gy²), which says how strong the edge is, and the direction, arctan(Gy/Gx), which says which way it runs.
   - Step 3, non-maximum suppression: walk along the gradient direction and keep a pixel only if it is the local maximum there. Everything else is set to zero. This thins a thick edge down to one pixel wide, which serves the single response objective and also improves localisation.
   - Step 4, double thresholding: use two thresholds, a high one and a low one. A pixel above the high threshold is a strong edge. A pixel below the low threshold is discarded. A pixel between the two is a weak edge, kept for now.
   - Step 5, edge tracking by hysteresis: keep a weak edge only if it is connected to a strong edge. A weak edge standing alone is noise and is removed. This is what lets the detector keep a faint but genuine edge while still rejecting isolated noise, and it is the key to the low error rate.

   Why Canny is preferred over Sobel or Prewitt: those operators only compute a gradient and apply one threshold, so they give thick, broken, noisy edges. Canny adds smoothing, thinning and hysteresis, so it gives thin, continuous, well placed edges. That is why it is still the standard edge detector.

## Morphological Operations (1)

1. **Define: (i) Erosion and Dilation; (ii) Opening and Closing.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*


   Answer: These are the four basic morphological operations. They work on a binary image, using a small shape called a structuring element that slides over the image.

   (i) Erosion and Dilation

   Erosion:
   - It shrinks the object. A pixel of the object is kept only if the structuring element fits completely inside the object at that position. Otherwise it is removed.
   - Written as A ⊖ B, that is A eroded by B.
   - Effect: the object gets thinner, small objects vanish, and thin bridges between two objects break apart.
   - Use: removing small white specks of noise, and separating two objects that are touching.

   Dilation:
   - It grows the object. A pixel becomes part of the object if the structuring element, placed there, touches the object anywhere.
   - Written as A ⊕ B, that is A dilated by B.
   - Effect: the object gets thicker, small holes inside it get filled, and small gaps in a broken line get joined.
   - Use: filling small holes, joining broken parts of a character in OCR.

   The two are dual operations: eroding an object is the same as dilating the background, and the reverse. But they are not inverses. Erosion followed by dilation does not give back the original image, and that fact is exactly what makes the next two operations useful.

   (ii) Opening and Closing

   Opening:
   - Erosion first, then dilation, with the same structuring element.
   - Written as A ∘ B = (A ⊖ B) ⊕ B.
   - Effect: it removes small objects and thin projections, and it smooths the outline from the outside. The erosion deletes the small stuff; the dilation restores the size of what survived.
   - Use: removing salt noise, that is small white specks, without shrinking the main object.

   Closing:
   - Dilation first, then erosion, with the same structuring element.
   - Written as A • B = (A ⊕ B) ⊖ B.
   - Effect: it fills small holes and narrow gaps, and it smooths the outline from the inside. The dilation closes the gaps; the erosion brings the size back.
   - Use: removing pepper noise, that is small black holes inside an object, and joining a character broken by a scanning fault.

   Summary:

   | Operation | Order | What it does |
   |---|---|---|
   | Erosion | — | Shrinks the object, removes small specks |
   | Dilation | — | Grows the object, fills small holes |
   | Opening | Erode, then dilate | Removes small objects, keeps the main object's size |
   | Closing | Dilate, then erode | Fills small holes and gaps, keeps the main object's size |

   Both opening and closing are idempotent: applying either one a second time changes nothing further.
