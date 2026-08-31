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


   Answer: The Canny edge detector, developed by John F. Canny in 1986, was designed as an optimal edge detector. Canny stated three explicit objectives, often called the three criteria, and the algorithm is constructed to satisfy them simultaneously.

   The basic objectives:

   - Good detection (low error rate): the detector must find as many real edges as possible while producing as few false edges as possible. In other words, it must not miss genuine edges and must not mark noise as an edge. This is achieved by smoothing the image with a Gaussian filter before differentiation, which suppresses noise.
   - Good localisation: the edge points marked by the detector must be as close as possible to the true position of the edge in the original image. This is achieved by non-maximum suppression, which thins the gradient ridges down to the exact ridge line.
   - Minimal response (single response to a single edge): each real edge must be marked only once, and the detector must not produce multiple pixels where only one edge exists. This too is enforced by non-maximum suppression together with hysteresis thresholding.

   Steps of the algorithm, and how each serves an objective:

   1. Noise reduction: convolve the image with a Gaussian filter to smooth it. This serves the first objective, since differentiation amplifies noise. The standard deviation sigma controls the amount of smoothing: a larger sigma removes more noise but also blurs weak edges.
   2. Gradient computation: apply a gradient operator, typically Sobel, to compute Gx and Gy. The gradient magnitude is
      G = sqrt(Gx^2 + Gy^2)
      and the direction is
      theta = arctan(Gy / Gx),
      which is then rounded to one of four directions: 0, 45, 90 or 135 degrees.
   3. Non-maximum suppression: examine each pixel along the gradient direction and keep it only if its magnitude is greater than that of its two neighbours in that direction; otherwise set it to zero. This thins thick gradient ridges into one-pixel-wide edges, serving the second and third objectives.
   4. Double thresholding: apply two thresholds, a high one and a low one. Pixels above the high threshold are strong edges, pixels below the low threshold are discarded, and pixels between the two are weak edges.
   5. Edge tracking by hysteresis: a weak edge is retained only if it is connected to a strong edge; otherwise it is removed. This recovers genuine but faint edge segments while rejecting isolated noise responses, which serves the first objective.

   Why it is preferred over Sobel, Prewitt or Roberts: those operators only compute the gradient, so they give thick edges, are highly sensitive to noise and mark an edge several pixels wide. Canny adds smoothing, thinning and connectivity analysis, so it produces thin, well-located, connected and noise-resistant edges.

   Limitations: it is computationally more expensive, it requires tuning of sigma and the two thresholds, and heavy smoothing can round corners and lose junctions.

## Morphological Operations (1)

1. **Define: (i) Erosion and Dilation; (ii) Opening and Closing.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*


   Answer: Morphological operations process an image on the basis of shape. They apply a small binary mask called a structuring element (SE) to an image, usually a binary image, and produce an output image of the same size. The four fundamental operations are given below, where A is the image and B is the structuring element.

   (i) Erosion and Dilation

   Erosion (A eroded by B), written A minus-sign B:
   - Definition: the set of all points z such that when B is placed with its origin at z, B fits entirely inside A.
   - Effect: it shrinks or thins the objects in the image. Boundary pixels are removed, so the object becomes smaller by roughly the radius of the structuring element.
   - Uses: removing small isolated noise specks, separating two objects that are joined by a thin bridge, and finding the skeleton or the interior of an object.
   - Rule for a binary image: an output pixel is set to 1 only if every pixel under the structuring element is 1; otherwise it is 0.

   Dilation (A dilated by B), written A plus-sign B:
   - Definition: the set of all points z such that the reflection of B, translated to z, overlaps at least one pixel of A.
   - Effect: it grows or thickens the objects in the image. Pixels are added to the boundary, so the object becomes larger.
   - Uses: filling small holes and narrow gaps inside an object, joining broken parts of a character or a line, and bridging small breaks after edge detection.
   - Rule for a binary image: an output pixel is set to 1 if at least one pixel under the structuring element is 1.

   Duality: erosion and dilation are dual operations. Eroding the object is the same as dilating the background, and vice versa.

   (ii) Opening and Closing

   Opening (A opened by B), written A o B:
   - Definition: erosion followed by dilation with the same structuring element. A o B = (A eroded by B) dilated by B.
   - Effect: it removes small objects, thin protrusions and narrow bridges, while preserving the overall size and shape of the larger objects. The erosion removes the small features and the dilation restores the size of what survived.
   - Uses: removing salt noise (small bright specks) from a binary image, separating touching objects, and smoothing the outer contour of an object.

   Closing (A closed by B), written A dot B:
   - Definition: dilation followed by erosion with the same structuring element. A dot B = (A dilated by B) eroded by B.
   - Effect: it fills small holes, narrow gaps and thin cracks inside an object, while preserving the overall size and shape. The dilation fills the gaps and the erosion restores the original size.
   - Uses: removing pepper noise (small dark holes), joining broken strokes of a character before OCR, and smoothing the inner contour of an object.

   Important properties:
   - Both opening and closing are idempotent: applying either of them a second time produces no further change, that is (A o B) o B = A o B.
   - Opening removes what is smaller than the structuring element; closing fills what is smaller than the structuring element.
   - Opening and closing are also dual: opening the object corresponds to closing the background.

   Practical application: in document image processing, closing joins the broken strokes of scanned characters, and opening then removes the leftover speckle noise, so that optical character recognition works reliably. In medical imaging the same pair is used to clean up segmented regions before measurement.
