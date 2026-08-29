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


   Answer: Vector graphics: ছবিটি গাণিতিক সূত্র ও জ্যামিতিক আকৃতি (বিন্দু, রেখা, বক্ররেখা, বহুভুজ) দিয়ে সংজ্ঞায়িত হয়। প্রতিটি উপাদানের স্থানাঙ্ক, রং ও পুরুত্ব সংরক্ষিত থাকে, পিক্সেল নয়।

   Raster graphics: ছবিটি পিক্সেল নামে ক্ষুদ্র বর্গাকার বিন্দুর গ্রিড দিয়ে গঠিত। প্রতিটি পিক্সেলের নিজস্ব রঙের মান সংরক্ষিত থাকে। একে বিটম্যাপ গ্রাফিক্সও বলা হয়।

   | বিষয় | Vector Graphics | Raster Graphics |
   |---|---|---|
   | গঠন | গাণিতিক সূত্র ও জ্যামিতিক আকৃতি | পিক্সেলের গ্রিড |
   | রেজল্যুশন | রেজল্যুশন-নিরপেক্ষ; যত বড় করা হোক, মান অপরিবর্তিত থাকে | রেজল্যুশন-নির্ভর; বড় করলে ঝাপসা ও দানাদার (pixelated) হয় |
   | ফাইলের আকার | ছোট, কারণ কেবল সমীকরণ সংরক্ষিত হয় | বড়, কারণ প্রতিটি পিক্সেলের তথ্য সংরক্ষণ করতে হয় |
   | সম্পাদনা | প্রতিটি বস্তু আলাদাভাবে নাড়ানো ও পরিবর্তন করা যায় | পিক্সেল ধরে সম্পাদনা করতে হয়, বস্তু আলাদা করা কঠিন |
   | রঙের গভীরতা | সীমিত; ছায়া ও রঙের সূক্ষ্ম পরিবর্তন ফুটিয়ে তোলা কঠিন | চমৎকার; ছবির প্রতিটি রঙের সূক্ষ্ম পার্থক্য ধরা পড়ে |
   | ফাইল ফরম্যাট | SVG, AI, EPS, CDR, PDF | JPEG, PNG, GIF, BMP, TIFF |
   | সফটওয়্যার | Adobe Illustrator, CorelDRAW, Inkscape | Adobe Photoshop, GIMP, MS Paint |
   | উপযুক্ত ক্ষেত্র | লোগো, আইকন, টাইপোগ্রাফি, নকশা, মানচিত্র, ইঞ্জিনিয়ারিং ড্রয়িং | ছবি (ফটোগ্রাফ), স্ক্যান করা নথি, ডিজিটাল পেইন্টিং |
   | মুদ্রণ | যেকোনো আকারে নিখুঁত ছাপা যায়, তাই ব্যানার ও বিলবোর্ডে ব্যবহৃত | নির্দিষ্ট DPI-এর বেশি বড় করলে মান নষ্ট হয় |

   মূল পার্থক্য এক বাক্যে: ভেক্টর ছবি "কীভাবে আঁকতে হবে" তা সংরক্ষণ করে, আর র‍্যাস্টার ছবি "কোন বিন্দুতে কী রং আছে" তা সংরক্ষণ করে।

   বাস্তব উদাহরণ: একটি প্রতিষ্ঠানের লোগো ভেক্টরে তৈরি করা হয়, যাতে ভিজিটিং কার্ড থেকে বিলবোর্ড পর্যন্ত সব আকারে একই মানে ব্যবহার করা যায়। অন্যদিকে ক্যামেরায় তোলা ছবি সবসময় র‍্যাস্টার, কারণ সেন্সরের প্রতিটি বিন্দু আলাদা রঙের তথ্য ধারণ করে।
2. **(b) Differentiate between vector graphics and raster graphics. What are the applications of computer Graphics?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 888-889 (ET: N/A)]*


   Answer:

   | Point | Vector Graphics | Raster Graphics |
   |---|---|---|
   | Basic element | Mathematical formulae and geometric primitives: points, lines, curves, polygons | Pixels arranged in a rectangular grid |
   | Resolution | Resolution independent; can be scaled to any size with no loss of quality | Resolution dependent; enlarging produces a blurred, pixelated image |
   | File size | Small, since only equations and attributes are stored | Large, since a colour value is stored for every pixel |
   | Editing | Each object can be selected, moved and modified independently | Editing is done pixel by pixel; objects cannot easily be separated |
   | Colour depth and detail | Limited; smooth tonal gradation and photographic detail are difficult | Excellent; captures every shade and texture |
   | Conversion | Converting vector to raster (rasterisation) is easy | Converting raster to vector (vectorisation or tracing) is difficult and imperfect |
   | File formats | SVG, AI, EPS, CDR, PDF | JPEG, PNG, GIF, BMP, TIFF |
   | Software | Adobe Illustrator, CorelDRAW, Inkscape | Adobe Photoshop, GIMP |
   | Best used for | Logos, icons, typography, maps, CAD drawings, illustrations | Photographs, scanned documents, digital paintings, web images |

   Applications of computer graphics:
   - Design and engineering: CAD and CAM for machine parts, buildings, circuit boards and vehicles, with 3D modelling and simulation before manufacture.
   - Entertainment: animation, visual effects in film, video games and virtual reality.
   - Education and training: interactive learning material, simulations, and flight, driving and surgical simulators, where practice on a real system would be dangerous or expensive.
   - Medicine: reconstruction and visualisation of CT, MRI and ultrasound data, three-dimensional models for surgical planning.
   - Scientific visualisation: representation of large datasets such as weather models, fluid flow, molecular structures and astronomical data.
   - Business and presentation graphics: charts, dashboards, infographics and reports that make numerical data intelligible.
   - Geographic Information Systems (GIS): digital maps, satellite image overlays, land-use planning and disaster mapping.
   - Publishing and advertising: page layout, typography, posters, packaging design and web design.
   - User interfaces: every window, icon, menu and pointer in a modern operating system is computer graphics.
   - Cartography and remote sensing: processing and displaying satellite imagery, which in Bangladesh is used by SPARRSO for cyclone tracking and crop surveys.
   - Art and image processing: digital painting, photo editing, restoration of damaged images and forensic image analysis.
3. **Raster Image কাকে বলে?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*


   Answer: র‍্যাস্টার ইমেজ (Raster Image) বলতে এমন ছবিকে বোঝায় যা পিক্সেল নামক ক্ষুদ্র বর্গাকার বিন্দুর একটি আয়তাকার গ্রিড দিয়ে গঠিত, যেখানে প্রতিটি পিক্সেলের নিজস্ব রঙের মান সংরক্ষিত থাকে। একে বিটম্যাপ ইমেজও বলা হয়।

   বৈশিষ্ট্য:
   - ছবিটিকে একটি দ্বিমাত্রিক অ্যারে হিসেবে দেখা যায়, যেখানে f(x, y) হলো (x, y) স্থানাঙ্কের পিক্সেলের তীব্রতা বা রঙের মান।
   - রেজল্যুশন প্রকাশ করা হয় প্রস্থ x উচ্চতা আকারে, যেমন ১৯২০ x ১০৮০ পিক্সেল, অথবা মুদ্রণের ক্ষেত্রে DPI (dots per inch) দিয়ে।
   - বিট ডেপথ ঠিক করে প্রতিটি পিক্সেল কয়টি রং ধারণ করতে পারে: ১ বিট হলে সাদা-কালো, ৮ বিট হলে ২৫৬টি ধূসর মাত্রা, ২৪ বিট হলে প্রায় ১.৬ কোটি রং (ট্রু কালার)।
   - ফাইলের আকারের আনুমানিক হিসাব: আকার = প্রস্থ x উচ্চতা x বিট ডেপথ ÷ ৮ বাইট। যেমন ১৯২০ x ১০৮০ x ২৪ বিট = প্রায় ৬.২ মেগাবাইট (সংকোচন ছাড়া)।
   - প্রধান সীমাবদ্ধতা: রেজল্যুশন-নির্ভর হওয়ায় ছবিটি বড় করলে পিক্সেলগুলো দৃশ্যমান হয়ে ওঠে এবং ছবি ঝাপসা ও দানাদার দেখায়।

   ফরম্যাট: JPEG (ক্ষতিসহ সংকোচন, ছবির জন্য), PNG (ক্ষতিহীন সংকোচন, স্বচ্ছতা সমর্থন করে), GIF (২৫৬ রং, অ্যানিমেশন), BMP (সংকোচনহীন), TIFF (উচ্চ মান, মুদ্রণ ও স্ক্যানিংয়ে ব্যবহৃত)।

   উৎস: ডিজিটাল ক্যামেরা, স্ক্যানার, স্যাটেলাইট সেন্সর, মেডিকেল ইমেজিং যন্ত্র এবং স্ক্রিনশট—সবই র‍্যাস্টার ইমেজ তৈরি করে।

   ব্যবহার: ফটোগ্রাফি, ওয়েব ছবি, ডিজিটাল পেইন্টিং, স্ক্যান করা নথি, চিকিৎসা ও রিমোট সেন্সিং ইমেজ। ডিজিটাল ইমেজ প্রসেসিংয়ের প্রায় সব কৌশল—ফিল্টারিং, হিস্টোগ্রাম সমতাকরণ, প্রান্ত শনাক্তকরণ—র‍্যাস্টার ছবির ওপরেই প্রয়োগ করা হয়।

## Color Models (1)

1. **(ক) বিভিন্ন Color model-এর নাম লিখুন। CMY color model-এর ব্যবহার কী?** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*


   Answer: কালার মডেল (Color Model) হলো রংকে সংখ্যায় প্রকাশ করার একটি গাণিতিক পদ্ধতি, সাধারণত তিন বা চারটি মৌলিক উপাদানের মান দিয়ে।

   বিভিন্ন কালার মডেলের নাম:
   - RGB (Red, Green, Blue): সংযোজন পদ্ধতির (additive) মডেল। আলো যোগ করে রং তৈরি হয়; তিনটিই পূর্ণ মাত্রায় থাকলে সাদা এবং তিনটিই শূন্য হলে কালো। মনিটর, টেলিভিশন, ক্যামেরা ও স্ক্যানারে ব্যবহৃত।
   - CMY / CMYK (Cyan, Magenta, Yellow, Key/Black): বিয়োজন পদ্ধতির (subtractive) মডেল। মুদ্রণে ব্যবহৃত।
   - HSI / HSV / HSB (Hue, Saturation, Intensity বা Value বা Brightness): মানুষের রং দেখার অভিজ্ঞতার সঙ্গে সবচেয়ে মিল রেখে তৈরি। ইমেজ প্রসেসিং ও রং নির্বাচনে সুবিধাজনক।
   - YIQ / YUV / YCbCr: উজ্জ্বলতা (luminance) ও বর্ণ (chrominance) আলাদা রাখে। টেলিভিশন সম্প্রচার এবং JPEG ও MPEG সংকোচনে ব্যবহৃত, কারণ মানুষের চোখ উজ্জ্বলতার পরিবর্তনে বেশি সংবেদনশীল।
   - CIE XYZ ও CIE L*a*b*: যন্ত্র-নিরপেক্ষ (device independent) আদর্শ মডেল, যা রঙের সঠিক মিল যাচাই ও রূপান্তরে ব্যবহৃত।
   - Grayscale: কেবল উজ্জ্বলতার মান, সাধারণত ০ থেকে ২৫৫।

   CMY কালার মডেলের ব্যবহার:
   - এটি বিয়োজন পদ্ধতির মডেল, অর্থাৎ সাদা আলো থেকে নির্দিষ্ট রং শোষণ বা বিয়োগ করে রং তৈরি হয়। সায়ান লাল আলো শোষণ করে, ম্যাজেন্টা সবুজ শোষণ করে এবং হলুদ নীল শোষণ করে।
   - RGB এর সঙ্গে সম্পর্ক: C = 1 - R, M = 1 - G, Y = 1 - B (মান ০ থেকে ১ এর মধ্যে ধরে)।
   - প্রধান ব্যবহার মুদ্রণ শিল্পে: রঙিন প্রিন্টার, ফটোকপিয়ার, অফসেট প্রেস, ম্যাগাজিন, বই, পোস্টার, প্যাকেজিং ও বিজ্ঞাপন।
   - কারণ: কাগজ নিজে আলো নিঃসরণ করে না, বরং আপতিত আলো প্রতিফলিত করে। তাই মুদ্রণে কালি দিয়ে অবাঞ্ছিত তরঙ্গদৈর্ঘ্য শোষণ করাই একমাত্র উপায়, যা বিয়োজন পদ্ধতি।
   - কালো (K) যোগ করার কারণ: তত্ত্ব অনুযায়ী C, M ও Y সমান মাত্রায় মেশালে কালো পাওয়ার কথা, কিন্তু বাস্তবে কালির অপূর্ণতার জন্য একটি ঘোলাটে বাদামি রং পাওয়া যায়। তাই আলাদা কালো কালি যোগ করে CMYK করা হয়। এতে লেখা ও ছায়া গাঢ় ও পরিষ্কার হয় এবং তিনটি রঙিন কালি সাশ্রয় হয়, যা খরচ কমায়।
   - "K" অক্ষরটি Key plate থেকে এসেছে, যা মুদ্রণে বিস্তারিত ও কনট্রাস্ট নির্ধারণ করত; নীল (Blue) এর B এর সঙ্গে বিভ্রান্তি এড়াতেও K ব্যবহৃত হয়।

## Frequency Domain Filtering (1)

1. **How does Butterworth High pass Filter works?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*


   Answer: A Butterworth High Pass Filter (BHPF) is a frequency domain filter used to sharpen an image by attenuating low frequencies and passing high frequencies, with a smooth rather than an abrupt transition between the two.

   Background: in an image, low frequencies correspond to slowly varying regions, that is, smooth areas and the overall background, while high frequencies correspond to rapid intensity changes, that is, edges, fine detail and noise. Removing the low frequencies therefore leaves the edges, which sharpens the image.

   Transfer function:

   H(u, v) = 1 / [1 + (D0 / D(u, v))^(2n)]

   where
   - D(u, v) is the distance of the point (u, v) from the centre of the frequency rectangle, D(u, v) = sqrt((u - M/2)^2 + (v - N/2)^2)
   - D0 is the cut-off frequency, the radius at which the filter response falls to 0.5
   - n is the order of the filter, which controls how sharp the transition is

   How it works, step by step:
   1. The input image f(x, y) is transformed into the frequency domain using the two-dimensional Discrete Fourier Transform, giving F(u, v).
   2. The spectrum is shifted so that the zero-frequency component (the DC term, which carries the average brightness) lies at the centre.
   3. The filter H(u, v) is applied by point-by-point multiplication: G(u, v) = H(u, v) . F(u, v).
   4. At the centre, where D(u, v) is small, H approaches 0, so low frequencies are suppressed. Far from the centre, where D(u, v) is large, H approaches 1, so high frequencies pass unchanged. At D(u, v) = D0, H = 0.5 exactly.
   5. The inverse Fourier transform converts the result back to the spatial domain, giving the sharpened image g(x, y).

   Effect of the order n:
   - n = 1 gives a very gradual transition, so the result is smooth but the sharpening is mild.
   - As n increases the transition becomes steeper, and the filter approaches the behaviour of an ideal high pass filter.
   - A very large n reintroduces the ringing artefact that the Butterworth filter was designed to avoid.

   Advantage over the ideal high pass filter: the ideal filter cuts off abruptly at D0, and this sharp cut-off in the frequency domain corresponds to a sinc function in the spatial domain, which produces visible ringing or ripple around edges. The Butterworth filter has a smooth roll-off, so ringing is largely eliminated while sharpening is still achieved.

   Comparison with the Gaussian high pass filter: the Gaussian filter has no ringing at all but sharpens less strongly. The Butterworth filter with a moderate order sits between the ideal and the Gaussian, offering a controllable trade-off.

   Applications: edge enhancement, sharpening of blurred images, feature extraction, enhancement of medical and satellite images, and removal of slow illumination variation from a scene.

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
