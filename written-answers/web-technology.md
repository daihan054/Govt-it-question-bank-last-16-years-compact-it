<!-- TOC START -->
**Table of Contents** — 7 subtopics · 53 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [HTML & Web Fundamentals](#html--web-fundamentals-17) | 17 |
| 2 | [HTTP Protocol](#http-protocol-10) | 10 |
| 3 | [JavaScript & jQuery (DOM & Validation)](#javascript--jquery-dom--validation-8) | 8 |
| 4 | [Web Services & APIs (SOAP vs REST)](#web-services--apis-soap-vs-rest-7) | 7 |
| 5 | [Full Stack & Backend Web Development](#full-stack--backend-web-development-5) | 5 |
| 6 | [CSS & Styling (Inline, Internal, External)](#css--styling-inline-internal-external-4) | 4 |
| 7 | [Web Security & Browser Same-Origin Policy (Iframe)](#web-security--browser-same-origin-policy-iframe-2) | 2 |

<!-- TOC END -->

---

## HTML & Web Fundamentals (17)

1. **What is HTML Image tag?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: The HTML image tag is `<img>`. It is used to embed an image in a web page.

   Syntax:

   ```html
   <img src="photo.jpg" alt="A red rose" width="300" height="200">
   ```

   Key points:
   - It is an empty or void element: it has no closing tag and no content of its own.
   - The image is not inserted into the page; the tag creates a holding space and the browser fetches the image from the given address and displays it there.

   Important attributes:
   - src, source: the path or URL of the image. This is compulsory.
   - alt, alternative text: the text shown if the image fails to load, and the text read out by a screen reader. It is compulsory for accessibility and helps search engines.
   - width and height: the display size in pixels. Giving both prevents the page from jumping while the image loads.
   - title: the tooltip shown when the mouse rests on the image.
   - loading="lazy": tells the browser to load the image only when it is about to come into view.

   Example with a link on the image:

   ```html
   <a href="https://www.example.com">
     <img src="images/logo.png" alt="Company logo" width="150">
   </a>
   ```

   Common image formats used: JPEG for photographs, PNG for images needing transparency, GIF for simple animation, SVG for scalable vector graphics, and WebP for smaller file size.
2. **What is URL? Give an Example.** *[BKSP Assistant Programmer 13.07.2024 compact it 1457 (ET: N/A)]*


   Answer: URL stands for Uniform Resource Locator. It is the complete address of a resource on the internet, which tells the browser what protocol to use, which server to contact, and which file or resource to ask for.

   Example:

   ```
   https://www.example.com:443/products/laptop.html?id=45&color=black#specs
   ```

   Parts of a URL:

   | Part | In the example | Meaning |
   |---|---|---|
   | Scheme or protocol | `https` | How to communicate: http, https, ftp, mailto, file |
   | Subdomain | `www` | A division of the domain |
   | Domain name | `example.com` | The name of the server, resolved to an IP address by DNS |
   | Port | `443` | The port on the server; 80 for HTTP and 443 for HTTPS are assumed if omitted |
   | Path | `/products/laptop.html` | The location of the resource on the server |
   | Query string | `?id=45&color=black` | Parameters passed to the server, in name=value pairs joined by `&` |
   | Fragment | `#specs` | A position within the page; handled by the browser and never sent to the server |

   More examples:
   - `https://www.google.com`
   - `https://bpsc.gov.bd/notice/result.pdf`
   - `ftp://files.example.com/data.zip`
   - `mailto:info@example.com`

   Related terms:
   - URI, Uniform Resource Identifier, is the general term; a URL is a URI that also gives the location.
   - URN, Uniform Resource Name, names a resource without saying where it is, for example `urn:isbn:0451450523`.
3. **(খ) নিচের টেবিলটি তৈরি করার জন্য HTML কোড লিখুন :** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 413 (ET: N/A)]*

| Std name | Compulsory | Optional |
|---|---|---|
| Hasan | Bangla | English | ICT | Math |
| Nafis | Bangla | English | ICT | Biology |


   Answer: The table has three columns, and the Optional column of each row holds several subjects.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
     <title>Student Subject Table</title>
     <style>
       table { border-collapse: collapse; }
       th, td { border: 1px solid black; padding: 8px; text-align: left; }
       th { background-color: #dddddd; }
     </style>
   </head>
   <body>

     <table>
       <tr>
         <th>Std name</th>
         <th>Compulsory</th>
         <th>Optional</th>
       </tr>
       <tr>
         <td>Hasan</td>
         <td>Bangla, English</td>
         <td>ICT, Math</td>
       </tr>
       <tr>
         <td>Nafis</td>
         <td>Bangla, English</td>
         <td>ICT, Biology</td>
       </tr>
     </table>

   </body>
   </html>
   ```

   HTML table tags used:

   | Tag | কাজ |
   |---|---|
   | `<table>` | সমগ্র টেবিল ধারণ করে |
   | `<tr>` | table row — একটি সারি |
   | `<th>` | table heading — শিরোনামের ঘর, লেখা মোটা ও মাঝখানে থাকে |
   | `<td>` | table data — সাধারণ ঘর |
   | `<caption>` | টেবিলের শিরোনাম |
   | `<thead>`, `<tbody>`, `<tfoot>` | টেবিলের মাথা, দেহ ও পা আলাদা করে |

   গুরুত্বপূর্ণ দুটি attribute:
   - `colspan="n"` — একটি ঘরকে n সংখ্যক কলাম জুড়ে বিস্তৃত করে।
   - `rowspan="n"` — একটি ঘরকে n সংখ্যক সারি জুড়ে বিস্তৃত করে।

   colspan ব্যবহার করে যদি Optional এর নিচে দুটি উপ-কলাম দেখাতে হয়:

   ```html
   <table border="1">
     <tr>
       <th rowspan="2">Std name</th>
       <th rowspan="2">Compulsory</th>
       <th colspan="2">Optional</th>
     </tr>
     <tr>
       <th>Subject 1</th>
       <th>Subject 2</th>
     </tr>
     <tr>
       <td>Hasan</td>
       <td>Bangla, English</td>
       <td>ICT</td>
       <td>Math</td>
     </tr>
     <tr>
       <td>Nafis</td>
       <td>Bangla, English</td>
       <td>ICT</td>
       <td>Biology</td>
     </tr>
   </table>
   ```
4. **একটি ওয়েবসাইটের (Website) কয়টি অংশ থাকে এবং কী কী?** *[সাধারণ জ্ঞান: বিজ্ঞান ও প্রযুক্তি, বিষয় কোড: ১০৪, মান: ৪০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*


   Answer: একটি ওয়েবসাইট প্রধানত দুইভাবে বিভক্ত করে দেখানো যায় — কাঠামোগত অংশ এবং কারিগরি উপাদান।

   কাঠামোগত দিক থেকে একটি ওয়েবসাইটের অংশ পাঁচটি:

   ১. Header (শিরোনাম অংশ): পৃষ্ঠার একেবারে উপরের অংশ। এতে থাকে প্রতিষ্ঠানের লোগো, নাম, স্লোগান, অনুসন্ধানের ঘর ও যোগাযোগের তথ্য। এটি সব পৃষ্ঠায় একই থাকে।

   ২. Navigation Menu (দিকনির্দেশনা অংশ): সাইটের প্রধান বিভাগগুলোর লিঙ্ক — যেমন Home, About, Services, Contact। এর মাধ্যমেই দর্শক এক পৃষ্ঠা থেকে অন্য পৃষ্ঠায় যান।

   ৩. Body বা Content Area (মূল অংশ): পৃষ্ঠার প্রধান বিষয়বস্তু — লেখা, ছবি, ভিডিও, তালিকা ও ফর্ম। এটিই ওয়েবসাইটের আসল উদ্দেশ্য এবং প্রতিটি পৃষ্ঠায় ভিন্ন হয়।

   ৪. Sidebar (পার্শ্ব অংশ): মূল অংশের পাশে অতিরিক্ত তথ্য — বিভাগের তালিকা, সাম্প্রতিক সংবাদ, বিজ্ঞাপন বা সংক্ষিপ্ত লিঙ্ক। এটি ঐচ্ছিক।

   ৫. Footer (পাদ অংশ): পৃষ্ঠার একেবারে নিচের অংশ। এতে থাকে কপিরাইট ঘোষণা, ঠিকানা ও ফোন নম্বর, গোপনীয়তা নীতি, সাইটম্যাপ ও সামাজিক যোগাযোগমাধ্যমের লিঙ্ক।

   ```
   +-------------------------------------------+
   |                 HEADER                    |
   |          (লোগো, নাম, অনুসন্ধান)            |
   +-------------------------------------------+
   |            NAVIGATION MENU                |
   |   Home | About | Services | Contact       |
   +--------------------------+----------------+
   |                          |                |
   |      CONTENT AREA        |    SIDEBAR     |
   |     (মূল বিষয়বস্তু)      |  (অতিরিক্ত)    |
   |                          |                |
   +--------------------------+----------------+
   |                 FOOTER                    |
   |    (কপিরাইট, ঠিকানা, লিঙ্ক)               |
   +-------------------------------------------+
   ```

   কারিগরি দিক থেকে একটি ওয়েবসাইটের উপাদান:
   - Domain Name: সাইটের ঠিকানা, যেমন www.example.com।
   - Web Hosting বা Server: যেখানে সাইটের ফাইলগুলো রাখা হয়।
   - Web Pages: HTML ফাইল, যার মধ্যে প্রথম পৃষ্ঠাটিকে বলে Home Page।
   - Front-end: HTML, CSS ও JavaScript — যা দর্শক দেখেন।
   - Back-end: PHP, Node.js, Python ইত্যাদি সার্ভার-সাইড কোড।
   - Database: তথ্য সংরক্ষণের জন্য, যেমন MySQL।
   - Hyperlink: পৃষ্ঠাগুলোকে যুক্তকারী লিঙ্ক।

   Home Page সম্পর্কে বিশেষভাবে উল্লেখযোগ্য: এটি ওয়েবসাইটের প্রথম ও প্রধান পৃষ্ঠা, যা ডোমেইন নাম লিখলেই খোলে। এর ফাইলের নাম সাধারণত index.html বা index.php হয়।
5. **(ক) ওয়েব ডিজাইন কী? স্ট্যাটিক ও ডায়নামিক ওয়েবসাইটের পার্থক্য ব্যাখ্যা করুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*


   Answer: ওয়েব ডিজাইন হলো একটি ওয়েবসাইটের চেহারা, বিন্যাস ও ব্যবহারযোগ্যতা পরিকল্পনা ও তৈরি করার প্রক্রিয়া। এতে নির্ধারণ করা হয় পৃষ্ঠার কাঠামো কেমন হবে, কোথায় কী থাকবে, রং ও ফন্ট কী হবে, ছবি ও লেখার বিন্যাস কেমন হবে এবং দর্শক কীভাবে সাইটটি ব্যবহার করবেন।

   ওয়েব ডিজাইনের প্রধান দিকসমূহ:
   - Layout: পৃষ্ঠার কাঠামোগত বিন্যাস — header, menu, content, sidebar ও footer এর অবস্থান।
   - Color scheme: রঙের সমন্বয়, যা প্রতিষ্ঠানের পরিচয়ের সঙ্গে মানানসই হয়।
   - Typography: ফন্ট, আকার ও লেখার ব্যবধান, যাতে পড়তে আরাম হয়।
   - Graphics ও Images: ছবি, আইকন ও লোগোর ব্যবহার।
   - Navigation: দর্শক যাতে সহজে ও দ্রুত কাঙ্ক্ষিত তথ্য পান।
   - Responsive design: মোবাইল, ট্যাব ও ডেস্কটপ — সব পর্দায় সঠিকভাবে দেখানো।
   - Accessibility: দৃষ্টিপ্রতিবন্ধী ও অন্যান্য বিশেষ চাহিদাসম্পন্ন ব্যবহারকারীর উপযোগী করা।
   - User Experience (UX): সমগ্র ব্যবহারের অভিজ্ঞতা যাতে সহজ ও স্বচ্ছন্দ হয়।

   ব্যবহৃত প্রযুক্তি: HTML গঠনের জন্য, CSS সাজসজ্জার জন্য, JavaScript মিথস্ক্রিয়ার জন্য; Bootstrap ও Tailwind এর মতো framework; এবং নকশার জন্য Figma, Adobe XD বা Photoshop।

   ওয়েব ডিজাইন ও ওয়েব ডেভেলপমেন্টের পার্থক্য: ডিজাইন সাইটটি দেখতে ও ব্যবহার করতে কেমন হবে তা নির্ধারণ করে; ডেভেলপমেন্ট সেই নকশাকে কার্যকর কোডে রূপ দেয় এবং সার্ভার ও ডেটাবেজের কাজ করে।

   স্ট্যাটিক ও ডায়নামিক ওয়েবসাইটের পার্থক্য:

   | বিষয় | Static Website | Dynamic Website |
   |---|---|---|
   | বিষয়বস্তু | সব ব্যবহারকারীর জন্য একই, নির্দিষ্ট | ব্যবহারকারী, সময় ও অবস্থাভেদে পরিবর্তিত |
   | তৈরির প্রযুক্তি | কেবল HTML, CSS ও সামান্য JavaScript | HTML, CSS, JavaScript এর সঙ্গে PHP, ASP.NET, Node.js, Python ইত্যাদি সার্ভার-সাইড ভাষা |
   | Database | ব্যবহৃত হয় না | অবশ্যই ব্যবহৃত হয় — MySQL, PostgreSQL, MongoDB |
   | Server-side processing | নেই; সার্ভার কেবল ফাইলটি পাঠিয়ে দেয় | আছে; প্রতিটি অনুরোধে সার্ভার পৃষ্ঠাটি তৈরি করে |
   | পরিবর্তন | প্রতিটি পৃষ্ঠার কোড হাতে সম্পাদনা করতে হয় | Admin panel বা CMS থেকে বিষয়বস্তু বদলানো যায়, কোড ছুঁতে হয় না |
   | গতি | দ্রুত, কারণ কোনো প্রক্রিয়াকরণ নেই | তুলনামূলক ধীর, কারণ প্রতিবার তৈরি করতে হয় |
   | খরচ | কম — তৈরি ও হোস্টিং দুটোই সস্তা | বেশি — উন্নয়ন, সার্ভার ও রক্ষণাবেক্ষণ ব্যয়বহুল |
   | জটিলতা | সরল | জটিল |
   | মিথস্ক্রিয়া | সীমিত; ব্যবহারকারী কেবল পড়তে পারেন | পূর্ণ; লগইন, অনুসন্ধান, মন্তব্য, কেনাকাটা সম্ভব |
   | নিরাপত্তা ঝুঁকি | কম, কারণ ডেটাবেজ ও ইনপুট নেই | বেশি — SQL injection, XSS, session hijacking |
   | SEO | সহজ, তবে বিষয়বস্তু নতুন হয় না | নিয়মিত নতুন বিষয়বস্তুর কারণে সুবিধাজনক |
   | Scalability | সীমিত সংখ্যক পৃষ্ঠার জন্য উপযুক্ত | হাজার হাজার পৃষ্ঠা স্বয়ংক্রিয়ভাবে তৈরি হয় |
   | উদাহরণ | ছোট প্রতিষ্ঠানের পরিচিতিমূলক সাইট, ব্যক্তিগত পোর্টফোলিও, ব্রochure সাইট | Facebook, Amazon, Daraz, অনলাইন ব্যাংকিং, সংবাদপত্র, ই-কমার্স |

   কোথায় কোনটি ব্যবহার করা উচিত: বিষয়বস্তু যদি খুব কম বদলায় এবং ব্যবহারকারীর সঙ্গে মিথস্ক্রিয়ার প্রয়োজন না থাকে, তবে static site যথেষ্ট ও সাশ্রয়ী। ব্যবহারকারীর অ্যাকাউন্ট, অনুসন্ধান, লেনদেন বা নিয়মিত হালনাগাদ প্রয়োজন হলে dynamic site অপরিহার্য।
6. **What is the popular way of linking many documents?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*


   Answer: The popular way of linking many documents is the hyperlink, created with the anchor tag `<a>` and its `href` attribute. Linking documents to one another in this way is what makes the collection a hypertext system, and it is the foundation of the World Wide Web.

   Syntax:

   ```html
   <a href="page2.html">Go to page 2</a>
   ```

   Types of link by the kind of address used:
   - Absolute link: gives the full URL, used for another site.
     `<a href="https://www.example.com/about.html">About</a>`
   - Relative link: gives the path relative to the current document, used within the same site.
     `<a href="products/laptop.html">Laptops</a>` and `<a href="../index.html">Home</a>`
   - Internal or bookmark link: jumps to a position within the same page, using an id.
     `<a href="#contact">Contact section</a>` together with `<section id="contact">`
   - Email link: `<a href="mailto:info@example.com">Send email</a>`
   - Telephone link: `<a href="tel:+8801711111111">Call us</a>`
   - Download link: `<a href="report.pdf" download>Download report</a>`

   Useful attributes:
   - `target="_blank"` opens the link in a new tab. When it is used, `rel="noopener noreferrer"` should be added for security.
   - `title` gives a tooltip.

   A navigation menu, which is the usual way many documents in a site are linked together:

   ```html
   <nav>
     <ul>
       <li><a href="index.html">Home</a></li>
       <li><a href="about.html">About</a></li>
       <li><a href="services.html">Services</a></li>
       <li><a href="contact.html">Contact</a></li>
     </ul>
   </nav>
   ```

   For a very large site the same purpose is served by a sitemap page, which lists links to every document, and by an XML sitemap submitted to search engines.
7. **Which tag is used for creating button in html?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*


   Answer: Two tags create a button in HTML: `<button>` and `<input>` with a button type.

   1. The `<button>` element:

   ```html
   <button type="button" onclick="alert('Clicked!')">Click Me</button>
   <button type="submit">Submit</button>
   <button type="reset">Reset</button>
   ```

   2. The `<input>` element with a button type:

   ```html
   <input type="button" value="Click Me">
   <input type="submit" value="Submit">
   <input type="reset" value="Reset">
   <input type="image" src="go.png" alt="Submit">
   ```

   Difference between the two:

   | Point | `<button>` | `<input type="button">` |
   |---|---|---|
   | Tag type | Paired: has a closing tag | Empty: no closing tag |
   | Label | The content between the tags | The `value` attribute |
   | Content allowed | Text, images, icons and other HTML | Plain text only |
   | Default type | `submit` inside a form | `button` |
   | Styling | More flexible | Limited |

   Because `<button>` can contain other HTML, an icon can be placed inside it:

   ```html
   <button type="submit">
     <img src="search-icon.png" alt=""> Search
   </button>
   ```

   Note on the default type: inside a `<form>`, a `<button>` with no `type` attribute acts as a submit button, which is a very common source of unexpected page reloads. Always write the type explicitly.
8. **(ক) HTML Element কী? উদাহরণসহ বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 607 (ET: N/A)]*


   Answer: HTML Element হলো একটি HTML নথির একক গঠনগত উপাদান, যা একটি opening tag, তার ভেতরের বিষয়বস্তু এবং একটি closing tag নিয়ে গঠিত। ব্রাউজার এই element গুলো পড়েই বুঝতে পারে পৃষ্ঠার কোন অংশ কী।

   গঠন:

   ```
   <p class="intro">This is a paragraph.</p>
   |            |            |            |
   opening tag  attribute   content    closing tag
   ```

   একটি element এর অংশ চারটি:
   - Opening tag: `<p>` — element এর শুরু নির্দেশ করে।
   - Attribute: `class="intro"` — element সম্পর্কে অতিরিক্ত তথ্য দেয়। এটি সবসময় opening tag এর ভেতরে থাকে এবং name="value" আকারে লেখা হয়।
   - Content: `This is a paragraph.` — element এর ভেতরের বিষয়বস্তু।
   - Closing tag: `</p>` — element এর শেষ নির্দেশ করে; এতে একটি slash থাকে।

   Element এর প্রকারভেদ:

   ১. Container বা Paired element: যাদের শুরু ও শেষ দুটি ট্যাগই থাকে।

   ```html
   <h1>এটি একটি শিরোনাম</h1>
   <p>এটি একটি অনুচ্ছেদ।</p>
   <div>এটি একটি বিভাগ</div>
   <a href="page.html">এটি একটি লিঙ্ক</a>
   ```

   ২. Empty বা Void element: যাদের কোনো বিষয়বস্তু নেই, তাই closing tag ও নেই।

   ```html
   <br>       <!-- নতুন লাইন -->
   <hr>       <!-- অনুভূমিক রেখা -->
   <img src="a.jpg" alt="ছবি">
   <input type="text" name="user">
   <meta charset="UTF-8">
   <link rel="stylesheet" href="style.css">
   ```

   প্রদর্শনের ভিত্তিতে আরেকটি বিভাজন:
   - Block-level element: নিজের জন্য পুরো লাইন দখল করে এবং আগে-পরে নতুন লাইন তৈরি করে। যেমন `<div>`, `<p>`, `<h1>` থেকে `<h6>`, `<ul>`, `<ol>`, `<li>`, `<table>`, `<form>`, `<section>`।
   - Inline element: কেবল প্রয়োজনীয় জায়গাটুকু নেয় এবং একই লাইনে থাকে। যেমন `<span>`, `<a>`, `<img>`, `<b>`, `<i>`, `<strong>`, `<em>`, `<input>`।

   Nesting বা একটি element এর ভেতরে আরেকটি:

   ```html
   <ul>
     <li><a href="#">প্রথম লিঙ্ক</a></li>
     <li><a href="#">দ্বিতীয় লিঙ্ক</a></li>
   </ul>
   ```

   এখানে `<a>` element টি `<li>` এর ভেতরে, এবং `<li>` গুলো `<ul>` এর ভেতরে রয়েছে। নিয়ম হলো — যে element পরে খোলা হয়, তাকে আগে বন্ধ করতে হয়। `<b><i>text</b></i>` লেখা ভুল; সঠিক হলো `<b><i>text</i></b>`।

   Element ও Tag এর পার্থক্য: Tag হলো কেবল কোণাকৃতি বন্ধনীর ভেতরের চিহ্ন, যেমন `<p>` বা `</p>`। আর Element হলো opening tag, content ও closing tag মিলে সম্পূর্ণ একক। অর্থাৎ tag হলো element এর সীমানা।
9. **(খ) Static ও Dynamic ওয়েবসাইটের মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 607 (ET: N/A)]*


   Answer: Static ও Dynamic ওয়েবসাইটের পার্থক্য:

   | বিষয় | Static Website | Dynamic Website |
   |---|---|---|
   | বিষয়বস্তু | সব ব্যবহারকারীর জন্য একই, নির্দিষ্ট | ব্যবহারকারী, সময় ও অবস্থাভেদে পরিবর্তিত |
   | তৈরির প্রযুক্তি | কেবল HTML, CSS ও সামান্য JavaScript | HTML, CSS, JavaScript এর সঙ্গে PHP, ASP.NET, Node.js, Python ইত্যাদি সার্ভার-সাইড ভাষা |
   | Database | ব্যবহৃত হয় না | অবশ্যই ব্যবহৃত হয় — MySQL, PostgreSQL, MongoDB |
   | Server-side processing | নেই; সার্ভার কেবল ফাইলটি পাঠিয়ে দেয় | আছে; প্রতিটি অনুরোধে সার্ভার পৃষ্ঠাটি তৈরি করে |
   | পরিবর্তন | প্রতিটি পৃষ্ঠার কোড হাতে সম্পাদনা করতে হয় | Admin panel বা CMS থেকে বিষয়বস্তু বদলানো যায়, কোড ছুঁতে হয় না |
   | গতি | দ্রুত, কারণ কোনো প্রক্রিয়াকরণ নেই | তুলনামূলক ধীর, কারণ প্রতিবার তৈরি করতে হয় |
   | খরচ | কম — তৈরি ও হোস্টিং দুটোই সস্তা | বেশি — উন্নয়ন, সার্ভার ও রক্ষণাবেক্ষণ ব্যয়বহুল |
   | জটিলতা | সরল | জটিল |
   | মিথস্ক্রিয়া | সীমিত; ব্যবহারকারী কেবল পড়তে পারেন | পূর্ণ; লগইন, অনুসন্ধান, মন্তব্য, কেনাকাটা সম্ভব |
   | নিরাপত্তা ঝুঁকি | কম, কারণ ডেটাবেজ ও ইনপুট নেই | বেশি — SQL injection, XSS, session hijacking |
   | SEO | সহজ, তবে বিষয়বস্তু নতুন হয় না | নিয়মিত নতুন বিষয়বস্তুর কারণে সুবিধাজনক |
   | Scalability | সীমিত সংখ্যক পৃষ্ঠার জন্য উপযুক্ত | হাজার হাজার পৃষ্ঠা স্বয়ংক্রিয়ভাবে তৈরি হয় |
   | উদাহরণ | ছোট প্রতিষ্ঠানের পরিচিতিমূলক সাইট, ব্যক্তিগত পোর্টফোলিও, ব্রochure সাইট | Facebook, Amazon, Daraz, অনলাইন ব্যাংকিং, সংবাদপত্র, ই-কমার্স |

   কোথায় কোনটি ব্যবহার করা উচিত: বিষয়বস্তু যদি খুব কম বদলায় এবং ব্যবহারকারীর সঙ্গে মিথস্ক্রিয়ার প্রয়োজন না থাকে, তবে static site যথেষ্ট ও সাশ্রয়ী। ব্যবহারকারীর অ্যাকাউন্ট, অনুসন্ধান, লেনদেন বা নিয়মিত হালনাগাদ প্রয়োজন হলে dynamic site অপরিহার্য।

   কার্যপ্রণালীর পার্থক্য:
   - Static: ব্রাউজার অনুরোধ পাঠায় → সার্ভার সংরক্ষিত HTML ফাইলটি হুবহু পাঠিয়ে দেয় → ব্রাউজার দেখায়।
   - Dynamic: ব্রাউজার অনুরোধ পাঠায় → সার্ভার-সাইড কোড চলে → ডেটাবেজ থেকে তথ্য আনা হয় → সেই তথ্য দিয়ে HTML তৈরি হয় → সেই তৈরি করা HTML পাঠানো হয়।
10. **অথবা, (ক) উদাহরণসহ HTML webpage এর গঠন ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 608 (ET: N/A)]*


    Answer: একটি HTML webpage এর গঠন তিনটি প্রধান অংশ নিয়ে — DOCTYPE ঘোষণা, head এবং body।

    ```html
    <!DOCTYPE html>
    <html lang="bn">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta name="description" content="একটি নমুনা ওয়েব পৃষ্ঠা">
      <title>আমার প্রথম ওয়েব পৃষ্ঠা</title>
      <link rel="stylesheet" href="style.css">
    </head>
    <body>

      <header>
        <h1>আমার ওয়েবসাইট</h1>
      </header>

      <nav>
        <a href="index.html">হোম</a> |
        <a href="about.html">পরিচিতি</a> |
        <a href="contact.html">যোগাযোগ</a>
      </nav>

      <main>
        <h2>স্বাগতম</h2>
        <p>এটি মূল বিষয়বস্তুর অংশ।</p>
        <img src="photo.jpg" alt="একটি ছবি" width="300">
        <ul>
          <li>প্রথম বিষয়</li>
          <li>দ্বিতীয় বিষয়</li>
        </ul>
      </main>

      <footer>
        <p>&copy; ২০২৬ সর্বস্বত্ব সংরক্ষিত</p>
      </footer>

      <script src="script.js"></script>
    </body>
    </html>
    ```

    প্রতিটি অংশের ব্যাখ্যা:

    `<!DOCTYPE html>` — নথির ধরন ঘোষণা। এটি ব্রাউজারকে জানায় নথিটি HTML5 এ লেখা, ফলে ব্রাউজার standards mode এ চলে। এটি কোনো ট্যাগ নয় এবং সবার আগে থাকতে হয়।

    `<html>` — মূল বা root element। DOCTYPE ছাড়া সব কিছু এর ভেতরে থাকে। `lang` attribute দিয়ে পৃষ্ঠার ভাষা জানানো হয়, যা search engine ও screen reader এর জন্য প্রয়োজন।

    `<head>` — পৃষ্ঠা সম্পর্কে তথ্য বা metadata ধারণ করে। এই অংশের কিছুই পৃষ্ঠায় দেখা যায় না, কেবল `<title>` ব্রাউজারের ট্যাবে দেখায়। এর ভেতরে থাকে:
    - `<meta charset="UTF-8">` — অক্ষর সংকেতায়ন। বাংলা লেখা দেখানোর জন্য এটি অপরিহার্য।
    - `<meta name="viewport">` — মোবাইল পর্দায় সঠিকভাবে দেখানোর জন্য।
    - `<title>` — ব্রাউজারের ট্যাবে ও search engine এর ফলাফলে দেখানো শিরোনাম।
    - `<link>` — বাইরের CSS ফাইল যুক্ত করে।
    - `<style>` — ভেতরের CSS।
    - `<script>` — JavaScript।

    `<body>` — পৃষ্ঠার দৃশ্যমান সব বিষয়বস্তু এখানে থাকে — লেখা, ছবি, লিঙ্ক, তালিকা, টেবিল ও ফর্ম।

    HTML5 এর semantic element গুলো, যা body কে অর্থবহভাবে ভাগ করে:
    - `<header>` — পৃষ্ঠা বা বিভাগের উপরের অংশ।
    - `<nav>` — দিকনির্দেশনার লিঙ্ক।
    - `<main>` — প্রধান বিষয়বস্তু, প্রতি পৃষ্ঠায় একবার।
    - `<section>` — বিষয়ভিত্তিক বিভাগ।
    - `<article>` — স্বয়ংসম্পূর্ণ লেখা, যেমন একটি সংবাদ বা ব্লগ পোস্ট।
    - `<aside>` — পাশের অতিরিক্ত তথ্য।
    - `<footer>` — পাদ অংশ।

    এই semantic ট্যাগগুলো ব্যবহারের সুবিধা: search engine পৃষ্ঠার গঠন বুঝতে পারে, screen reader দৃষ্টিপ্রতিবন্ধী ব্যবহারকারীকে সঠিকভাবে পথ দেখাতে পারে, এবং কোড পড়ে বোঝা সহজ হয়। কেবল `<div>` ব্যবহার করলে এই সুবিধাগুলো পাওয়া যায় না।
11. **(খ) নিচের লিস্টটি তৈরি করার জন্য HTML কোড লিখুন :** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 609 (ET: N/A)]*
   1. Fruits
      (a) Mango
      (b) Orange
   2. Vagetables
      - Green Capsicum
      - Yellow Capsicum
      - Red Capsicum


    Answer: তালিকাটিতে একটি ordered list আছে, যার প্রথম আইটেমের নিচে ছোট হাতের অক্ষরের ordered list এবং দ্বিতীয় আইটেমের নিচে unordered list রয়েছে।

    ```html
    <!DOCTYPE html>
    <html>
    <head>
      <meta charset="UTF-8">
      <title>Nested List</title>
    </head>
    <body>

      <ol type="1">
        <li>Fruits
          <ol type="a">
            <li>Mango</li>
            <li>Orange</li>
          </ol>
        </li>
        <li>Vegetables
          <ul>
            <li>Green Capsicum</li>
            <li>Yellow Capsicum</li>
            <li>Red Capsicum</li>
          </ul>
        </li>
      </ol>

    </body>
    </html>
    ```

    লক্ষণীয় নিয়ম: ভেতরের তালিকাটি অবশ্যই বাইরের `<li>` এর ভেতরে বসাতে হবে, `</li>` এর পরে নয়। অন্যথায় HTML অবৈধ হয় এবং ব্রাউজার ভিন্নভাবে দেখায়।

    HTML এ তালিকা তিন প্রকার:

    | প্রকার | ট্যাগ | ব্যবহার |
    |---|---|---|
    | Ordered List | `<ol>` ও `<li>` | ক্রম গুরুত্বপূর্ণ হলে; সংখ্যা বা অক্ষর দেখায় |
    | Unordered List | `<ul>` ও `<li>` | ক্রম গুরুত্বপূর্ণ নয়; বুলেট দেখায় |
    | Description List | `<dl>`, `<dt>`, `<dd>` | পদ ও তার সংজ্ঞা |

    `<ol>` এর `type` attribute এর মান:
    - `type="1"` — ১, ২, ৩ (এটিই default)
    - `type="a"` — a, b, c
    - `type="A"` — A, B, C
    - `type="i"` — i, ii, iii
    - `type="I"` — I, II, III
    - `start="5"` — গণনা ৫ থেকে শুরু হবে
    - `reversed` — উল্টো ক্রমে গণনা

    `<ul>` এর বুলেটের আকার CSS দিয়ে নির্ধারণ করা হয়: `list-style-type: disc | circle | square | none;`

    Description list এর উদাহরণ:

    ```html
    <dl>
      <dt>HTML</dt>
      <dd>ওয়েব পৃষ্ঠার গঠন নির্ধারণকারী markup ভাষা।</dd>
      <dt>CSS</dt>
      <dd>ওয়েব পৃষ্ঠার সাজসজ্জা নির্ধারণকারী ভাষা।</dd>
    </dl>
    ```
12. **অথবা, নিম্নোক্ত উপাদানগুলোসহ একটি HTML page লিখুন। Hyperlink, Ordered list, Unordered list, Form (Tent box, Check box, Option Button).** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*


    Answer: প্রশ্নে চাওয়া সব উপাদান — hyperlink, ordered list, unordered list এবং text box, check box ও radio button সহ একটি form — একটি HTML পৃষ্ঠায়:

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Student Registration Page</title>
      <style>
        body   { font-family: Arial, sans-serif; margin: 30px; }
        fieldset { border: 1px solid #999; padding: 15px; width: 420px; }
        label  { display: inline-block; width: 130px; }
        input, select { margin-bottom: 10px; }
      </style>
    </head>
    <body>

      <h1>Student Registration</h1>

      <!-- 1. HYPERLINK -->
      <h2>Useful Links</h2>
      <p>
        <a href="https://www.bpsc.gov.bd" target="_blank" rel="noopener noreferrer">BPSC Website</a> |
        <a href="index.html">Home Page</a> |
        <a href="#form">Go to Form</a> |
        <a href="mailto:info@college.edu.bd">Email Us</a>
      </p>

      <!-- 2. ORDERED LIST -->
      <h2>Admission Steps</h2>
      <ol>
        <li>Collect the application form</li>
        <li>Fill in all required information</li>
        <li>Attach the necessary documents</li>
        <li>Pay the application fee</li>
        <li>Submit the form before the deadline</li>
      </ol>

      <!-- 3. UNORDERED LIST -->
      <h2>Required Documents</h2>
      <ul>
        <li>SSC certificate and transcript</li>
        <li>HSC certificate and transcript</li>
        <li>National ID or birth certificate</li>
        <li>Two passport-size photographs</li>
      </ul>

      <!-- 4. FORM -->
      <h2 id="form">Registration Form</h2>
      <form action="/register" method="post">
        <fieldset>
          <legend>Personal Information</legend>

          <!-- TEXT BOX -->
          <label for="fullname">Full Name:</label>
          <input type="text" id="fullname" name="fullname" placeholder="Enter your name" required><br>

          <label for="email">Email:</label>
          <input type="email" id="email" name="email" required><br>

          <label for="password">Password:</label>
          <input type="password" id="password" name="password" minlength="8" required><br>

          <label for="dob">Date of Birth:</label>
          <input type="date" id="dob" name="dob"><br>

          <!-- RADIO BUTTON (OPTION BUTTON) -->
          <p>Gender:</p>
          <input type="radio" id="male" name="gender" value="male" checked>
          <label for="male">Male</label>
          <input type="radio" id="female" name="gender" value="female">
          <label for="female">Female</label>
          <input type="radio" id="other" name="gender" value="other">
          <label for="other">Other</label>

          <!-- CHECK BOX -->
          <p>Subjects (choose one or more):</p>
          <input type="checkbox" id="ict" name="subject" value="ICT">
          <label for="ict">ICT</label><br>
          <input type="checkbox" id="math" name="subject" value="Math">
          <label for="math">Mathematics</label><br>
          <input type="checkbox" id="physics" name="subject" value="Physics">
          <label for="physics">Physics</label><br>

          <!-- DROPDOWN -->
          <label for="district">District:</label>
          <select id="district" name="district">
            <option value="">-- Select --</option>
            <option value="dhaka">Dhaka</option>
            <option value="chattogram">Chattogram</option>
            <option value="rajshahi">Rajshahi</option>
          </select><br>

          <!-- TEXT AREA -->
          <label for="address">Address:</label>
          <textarea id="address" name="address" rows="3" cols="30"></textarea><br>

          <!-- AGREEMENT CHECKBOX -->
          <input type="checkbox" id="agree" name="agree" required>
          <label for="agree" style="width:auto">I agree to the terms and conditions</label><br><br>

          <!-- BUTTONS -->
          <input type="submit" value="Register">
          <input type="reset" value="Clear">
        </fieldset>
      </form>

    </body>
    </html>
    ```

    গুরুত্বপূর্ণ বিষয়গুলো:

    - Radio button ও Check box এর পার্থক্য: একই `name` দেওয়া radio button গুলোর মধ্যে কেবল একটি নির্বাচন করা যায়; check box এ একাধিক নির্বাচন করা যায়। এজন্য radio button এ `name` একই রাখা বাধ্যতামূলক, না রাখলে সবগুলো আলাদা দল হয়ে যায় এবং সবই নির্বাচন করা যায়।

    - `<label>` এর `for` attribute টি input এর `id` এর সঙ্গে মিলিয়ে দিলে লেখার ওপর ক্লিক করলেও input টি নির্বাচিত হয়, যা ব্যবহারযোগ্যতা ও accessibility দুটোই বাড়ায়।

    - Form এর দুটি প্রধান attribute: `action` বলে দেয় তথ্য কোথায় পাঠানো হবে, আর `method` বলে দেয় কীভাবে — GET হলে তথ্য URL এ যায়, POST হলে অনুরোধের শরীরে যায়। পাসওয়ার্ড বা গোপন তথ্যের জন্য অবশ্যই POST ব্যবহার করতে হবে।

    - HTML5 এর built-in validation: `required`, `minlength`, `maxlength`, `pattern`, এবং `type="email"` বা `type="number"` ব্যবহার করলে ব্রাউজার নিজেই যাচাই করে। তবে এটি নিরাপত্তা নয় — সার্ভারেও যাচাই করা বাধ্যতামূলক, কারণ ব্রাউজারের যাচাই সহজেই এড়ানো যায়।
13. **(ক) HTML এবং CSS কী? সংক্ষেপে ব্যাখ্যা করুন। শুধুমাত্র HTML এবং CSS ব্যবহার করে Web Site তৈরির ক্ষেত্রে সীমাবদ্ধতা আলোচনা করুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 705 (ET: N/A)]*


    Answer:    HTML (HyperText Markup Language): ওয়েব পৃষ্ঠার গঠন ও বিষয়বস্তু নির্ধারণকারী markup ভাষা। এটি প্রোগ্রামিং ভাষা নয় — এতে শর্ত, লুপ বা গণনা নেই। HTML ট্যাগ ব্যবহার করে বলে দেওয়া হয় কোনটি শিরোনাম, কোনটি অনুচ্ছেদ, কোনটি তালিকা, কোনটি ছবি ও কোনটি লিঙ্ক। বর্তমান সংস্করণ HTML5।

    CSS (Cascading Style Sheets): ওয়েব পৃষ্ঠার উপস্থাপন ও সাজসজ্জা নির্ধারণকারী ভাষা — রং, ফন্ট, আকার, ব্যবধান, অবস্থান ও বিন্যাস। এটি HTML থেকে নকশাকে আলাদা করে, ফলে একটি CSS ফাইল বদলালেই সমগ্র সাইটের চেহারা বদলে যায়।

    দুইয়ের সম্পর্ক: HTML হলো ভবনের কাঠামো, CSS হলো তার রং ও সাজসজ্জা। HTML বলে "এটি একটি শিরোনাম", CSS বলে "শিরোনামটি নীল রঙের, ২৪ পিক্সেল এবং মাঝখানে থাকবে"।

    শুধুমাত্র HTML ও CSS ব্যবহার করে ওয়েবসাইট তৈরির সীমাবদ্ধতা:

    - কোনো যুক্তি বা গণনা করা যায় না। HTML ও CSS দুটোই ঘোষণামূলক ভাষা; এতে শর্ত, লুপ, চলক বা ফাংশন নেই। ফলে যোগফল বের করা, শতকরা হিসাব করা বা কোনো সিদ্ধান্ত নেওয়া অসম্ভব।

    - Database ব্যবহার করা যায় না। তথ্য সংরক্ষণ, সংশোধন বা অনুসন্ধান করা যায় না। সব লেখা কোডের ভেতরে স্থির অবস্থায় থাকে।

    - Form জমা নেওয়া যায় না। ফর্মটি দেখানো যায়, কিন্তু জমা দেওয়া তথ্য গ্রহণ ও সংরক্ষণ করার জন্য সার্ভার-সাইড ভাষা লাগে। ফলে যোগাযোগের ফর্ম, নিবন্ধন বা মতামত গ্রহণ কিছুই কাজ করে না।

    - User authentication সম্ভব নয়। লগইন, পাসওয়ার্ড যাচাই বা ব্যবহারকারীভেদে ভিন্ন বিষয়বস্তু দেখানো যায় না।

    - কোনো মিথস্ক্রিয়া নেই। ক্লিক করলে ফর্ম যাচাই হওয়া, পপ-আপ দেখানো, ছবি স্লাইড হওয়া, ড্রপডাউন মেনু খোলা, লাইভ অনুসন্ধান — এসবের জন্য JavaScript প্রয়োজন। CSS দিয়ে কিছু hover ও transition সম্ভব, কিন্তু তা খুবই সীমিত।

    - বিষয়বস্তু হালনাগাদ করা কষ্টসাধ্য। নতুন একটি সংবাদ যোগ করতে হলে HTML ফাইল খুলে হাতে কোড লিখতে হয়। ১০০ পৃষ্ঠার সাইটে menu তে একটি লিঙ্ক যোগ করতে হলে ১০০টি ফাইলই সম্পাদনা করতে হয়, কারণ কোনো template ব্যবস্থা নেই।

    - পৃষ্ঠা পুনরায় ব্যবহারযোগ্য নয়। ১০০০টি পণ্যের জন্য ১০০০টি আলাদা HTML ফাইল লিখতে হয়; dynamic সাইটে একটি template ও একটি ডেটাবেজ দিয়েই কাজ হয়।

    - কোনো API বা বাইরের সেবার সঙ্গে যোগাযোগ নেই। আবহাওয়ার তথ্য আনা, মূল্য পরিশোধ, মানচিত্র বা এসএমএস পাঠানো — কিছুই সম্ভব নয়।

    - Search ও filter নেই। ব্যবহারকারী কোনো কিছু খুঁজতে পারেন না।

    - কোনো ব্যক্তিগতকরণ নেই। প্রত্যেক দর্শক হুবহু একই পৃষ্ঠা দেখেন।

    - Content Management System নেই। কারিগরি জ্ঞান ছাড়া কেউ সাইটটি হালনাগাদ করতে পারেন না।

    - ফাইল আপলোড বা ডাউনলোডের ব্যবস্থাপনা নেই।

    সীমাবদ্ধতা দূর করার উপায়: ক্লায়েন্ট-সাইড মিথস্ক্রিয়ার জন্য JavaScript, সার্ভার-সাইড প্রক্রিয়াকরণের জন্য PHP, Node.js, Python বা ASP.NET, এবং তথ্য সংরক্ষণের জন্য MySQL বা MongoDB এর মতো ডেটাবেজ যুক্ত করতে হয়।

    তবু কোথায় HTML ও CSS যথেষ্ট: ব্যক্তিগত পোর্টফোলিও, ছোট প্রতিষ্ঠানের পরিচিতিমূলক সাইট, অনুষ্ঠানের ঘোষণাপত্র, নথিপত্র বা টিউটোরিয়াল সাইট — যেখানে বিষয়বস্তু স্থির এবং কোনো মিথস্ক্রিয়া দরকার নেই। এসব ক্ষেত্রে static সাইট দ্রুততর, সস্তা ও নিরাপদ।
14. **(খ) Static Web Page এবং Dynamic Web Page এর মধ্যে পার্থক্য আলোচনা করুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 705 (ET: N/A)]*


    Answer: Static Web Page ও Dynamic Web Page এর পার্থক্য:

    | বিষয় | Static Web Page | Dynamic Web Page |
    |---|---|---|
    | সংজ্ঞা | সার্ভারে সংরক্ষিত অপরিবর্তিত HTML ফাইল, যা হুবহু পাঠানো হয় | প্রতিটি অনুরোধে সার্ভারে তৈরি হওয়া পৃষ্ঠা |
    | বিষয়বস্তু | সবার জন্য এক, সবসময় এক | ব্যবহারকারী, সময় ও ইনপুট অনুযায়ী ভিন্ন |
    | ভাষা | HTML, CSS, সামান্য JavaScript | HTML, CSS, JavaScript এর সঙ্গে PHP, JSP, ASP.NET, Node.js, Python |
    | Database | নেই | আছে |
    | Server-side প্রক্রিয়াকরণ | নেই | আছে |
    | Client-side script | ঐচ্ছিক | প্রায়ই থাকে |
    | Loading গতি | দ্রুত | তুলনামূলক ধীর |
    | সার্ভারের ওপর চাপ | খুব কম | বেশি |
    | পরিবর্তন | HTML ফাইল হাতে সম্পাদনা করতে হয় | Admin panel বা CMS থেকে করা যায় |
    | তৈরির খরচ | কম | বেশি |
    | রক্ষণাবেক্ষণ | পৃষ্ঠা বাড়লে কঠিন হয়ে পড়ে | সহজ, কারণ template ও ডেটাবেজ আলাদা |
    | নিরাপত্তা | তুলনামূলক নিরাপদ | ঝুঁকি বেশি; SQL injection, XSS প্রতিরোধ করতে হয় |
    | Caching | পুরো পৃষ্ঠা সহজে cache করা যায় | সীমিতভাবে cache করা যায় |
    | উপযুক্ত ক্ষেত্র | পোর্টফোলিও, ছোট প্রতিষ্ঠানের সাইট, নথিপত্র | ই-কমার্স, সামাজিক মাধ্যম, সংবাদপত্র, ব্যাংকিং |
    | উদাহরণ | একটি স্কুলের তথ্যপৃষ্ঠা | Facebook, Daraz, Amazon, Prothom Alo |

    কার্যপ্রণালীর তুলনা:

    ```
    STATIC:
    Browser --request--> Web Server --> সংরক্ষিত .html ফাইল খুঁজে পায়
                                     --> ফাইলটি হুবহু পাঠায়
    Browser <--HTML-- Web Server

    DYNAMIC:
    Browser --request--> Web Server --> Application Server (PHP/Node)
                                         |--> Database এ query পাঠায়
                                         |<-- ফল ফিরে আসে
                                         |--> template + ডেটা মিলিয়ে HTML তৈরি
    Browser <--তৈরি করা HTML-- Web Server
    ```

    একটি মূল বিষয়: Dynamic হওয়া মানে কেবল অ্যানিমেশন বা নড়াচড়া নয়। JavaScript দিয়ে ছবি স্লাইড করানো একটি static পৃষ্ঠাতেও সম্ভব; সেটি dynamic পৃষ্ঠা নয়। Dynamic বলতে বোঝায় পৃষ্ঠার বিষয়বস্তু সার্ভারে প্রতিবার নতুন করে তৈরি হয়।
15. **(ক) কোন প্রতিষ্ঠানের Web page development এ HTML এবং CSS এর ভূমিকা কি? শুধুমাত্র HTML এবং CSS ব্যবহার করে কোন ধরনের Web Page Development করা যেতে পারে?** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 771 (ET: N/A)]*


    Answer:    HTML (HyperText Markup Language): ওয়েব পৃষ্ঠার গঠন ও বিষয়বস্তু নির্ধারণকারী markup ভাষা। এটি প্রোগ্রামিং ভাষা নয় — এতে শর্ত, লুপ বা গণনা নেই। HTML ট্যাগ ব্যবহার করে বলে দেওয়া হয় কোনটি শিরোনাম, কোনটি অনুচ্ছেদ, কোনটি তালিকা, কোনটি ছবি ও কোনটি লিঙ্ক। বর্তমান সংস্করণ HTML5।

    CSS (Cascading Style Sheets): ওয়েব পৃষ্ঠার উপস্থাপন ও সাজসজ্জা নির্ধারণকারী ভাষা — রং, ফন্ট, আকার, ব্যবধান, অবস্থান ও বিন্যাস। এটি HTML থেকে নকশাকে আলাদা করে, ফলে একটি CSS ফাইল বদলালেই সমগ্র সাইটের চেহারা বদলে যায়।

    দুইয়ের সম্পর্ক: HTML হলো ভবনের কাঠামো, CSS হলো তার রং ও সাজসজ্জা। HTML বলে "এটি একটি শিরোনাম", CSS বলে "শিরোনামটি নীল রঙের, ২৪ পিক্সেল এবং মাঝখানে থাকবে"।

    একটি প্রতিষ্ঠানের Web page development এ HTML ও CSS এর ভূমিকা:

    HTML এর ভূমিকা:
    - পৃষ্ঠার কাঠামো গড়ে তোলে — header, navigation, content, sidebar ও footer।
    - প্রতিষ্ঠানের সব তথ্য উপস্থাপন করে: পরিচিতি, সেবা, পণ্য, যোগাযোগের ঠিকানা।
    - পৃষ্ঠাগুলোকে hyperlink দিয়ে যুক্ত করে, ফলে সমগ্র সাইটটি একটি ঐক্যবদ্ধ ব্যবস্থা হয়ে ওঠে।
    - ছবি, ভিডিও, নথি ও মানচিত্র যুক্ত করে।
    - তথ্য সংগ্রহের জন্য form তৈরি করে — যোগাযোগ ফর্ম, চাকরির আবেদন, মতামত।
    - টেবিল ও তালিকা দিয়ে তথ্য সুবিন্যস্ত করে, যেমন মূল্যতালিকা বা নোটিশের তালিকা।
    - Semantic ট্যাগ ও meta tag এর মাধ্যমে search engine optimization এ সহায়তা করে, যাতে প্রতিষ্ঠানটি Google এ সহজে পাওয়া যায়।
    - Accessibility নিশ্চিত করে alt text ও সঠিক শিরোনাম কাঠামোর মাধ্যমে।

    CSS এর ভূমিকা:
    - প্রতিষ্ঠানের ব্র্যান্ড পরিচয় প্রতিষ্ঠা করে — নির্দিষ্ট রং, ফন্ট ও শৈলী সব পৃষ্ঠায় এক রাখে।
    - পেশাদার ও আকর্ষণীয় চেহারা দেয়, যা দর্শকের আস্থা তৈরি করে।
    - Layout নিয়ন্ত্রণ করে Flexbox ও Grid এর মাধ্যমে।
    - Responsive design এর মাধ্যমে মোবাইল, ট্যাব ও ডেস্কটপ — সব পর্দায় সাইটটি সঠিকভাবে দেখায়। বর্তমানে অধিকাংশ দর্শক মোবাইলে আসেন, তাই এটি অপরিহার্য।
    - একটি বাইরের CSS ফাইল ব্যবহার করলে একটি ফাইল বদলেই সমগ্র সাইটের চেহারা বদলে যায়, ফলে রক্ষণাবেক্ষণ সহজ ও সাশ্রয়ী হয়।
    - Hover, transition ও animation দিয়ে সীমিত মিথস্ক্রিয়ার অনুভূতি দেয়।
    - Print stylesheet দিয়ে ছাপার উপযোগী সংস্করণ তৈরি করা যায়।

    শুধুমাত্র HTML ও CSS দিয়ে যে ধরনের Web Page তৈরি করা যায়:

    - Static informational website: প্রতিষ্ঠানের পরিচিতি, ইতিহাস, লক্ষ্য ও উদ্দেশ্য, সেবার তালিকা, ঠিকানা ও ফোন নম্বর।
    - Portfolio ও Resume site: ব্যক্তিগত পরিচিতি, কাজের নমুনা ও অভিজ্ঞতা।
    - Brochure বা Landing page: একটি পণ্য বা অনুষ্ঠানের জন্য একক পৃষ্ঠা।
    - Product catalogue: পণ্যের ছবি ও বিবরণ, তবে কেনার ব্যবস্থা ছাড়া।
    - Documentation ও tutorial site: নথিপত্র ও শিক্ষামূলক লেখা।
    - Notice board: বিজ্ঞপ্তি ও সংবাদের তালিকা, যা হাতে হালনাগাদ করতে হয়।
    - Event page: অনুষ্ঠানের সময়সূচি, স্থান ও বক্তাদের পরিচিতি।
    - Contact page: মানচিত্র ও যোগাযোগের তথ্যসহ, তবে ফর্মটি কেবল দেখানো যাবে, জমা নেওয়া যাবে না।

    যা তৈরি করা যাবে না: লগইন ব্যবস্থা, অনুসন্ধান, অনলাইন কেনাকাটা, মন্তব্য, ডেটাবেজভিত্তিক যেকোনো তালিকা, ব্যবহারকারীভেদে ভিন্ন বিষয়বস্তু, বা কার্যকর যোগাযোগ ফর্ম। এসবের জন্য JavaScript, সার্ভার-সাইড ভাষা ও ডেটাবেজ প্রয়োজন।
16. **(ii) HTML ও CSS কী?** *[BPSC Assistant Network Engineer 2020 compact it 950-951 (ET: N/A)]*


    Answer:    HTML (HyperText Markup Language): ওয়েব পৃষ্ঠার গঠন ও বিষয়বস্তু নির্ধারণকারী markup ভাষা। এটি প্রোগ্রামিং ভাষা নয় — এতে শর্ত, লুপ বা গণনা নেই। HTML ট্যাগ ব্যবহার করে বলে দেওয়া হয় কোনটি শিরোনাম, কোনটি অনুচ্ছেদ, কোনটি তালিকা, কোনটি ছবি ও কোনটি লিঙ্ক। বর্তমান সংস্করণ HTML5।

    CSS (Cascading Style Sheets): ওয়েব পৃষ্ঠার উপস্থাপন ও সাজসজ্জা নির্ধারণকারী ভাষা — রং, ফন্ট, আকার, ব্যবধান, অবস্থান ও বিন্যাস। এটি HTML থেকে নকশাকে আলাদা করে, ফলে একটি CSS ফাইল বদলালেই সমগ্র সাইটের চেহারা বদলে যায়।

    দুইয়ের সম্পর্ক: HTML হলো ভবনের কাঠামো, CSS হলো তার রং ও সাজসজ্জা। HTML বলে "এটি একটি শিরোনাম", CSS বলে "শিরোনামটি নীল রঙের, ২৪ পিক্সেল এবং মাঝখানে থাকবে"।

    HTML এর মূল বিষয়:
    - এটি ট্যাগ ব্যবহার করে লেখা হয়, যেমন `<h1>`, `<p>`, `<a>`, `<img>`, `<table>`, `<form>`।
    - একটি পৃষ্ঠার দুটি প্রধান অংশ — `<head>` এ তথ্য বা metadata, আর `<body>` তে দৃশ্যমান বিষয়বস্তু।
    - ফাইলের বর্ধিতাংশ `.html` বা `.htm`।
    - এটি কেবল গঠন বলে; কীভাবে দেখাবে তা বলে না।

    ```html
    <!DOCTYPE html>
    <html>
    <head>
      <meta charset="UTF-8">
      <title>My Page</title>
    </head>
    <body>
      <h1>Welcome</h1>
      <p>This is a paragraph.</p>
    </body>
    </html>
    ```

    CSS এর মূল বিষয়:
    - এর গঠন: `selector { property: value; }`
    - তিনভাবে যুক্ত করা যায় — inline, internal ও external।
    - ফাইলের বর্ধিতাংশ `.css`।
    - Cascading শব্দটির অর্থ: একই element এ একাধিক নিয়ম প্রযোজ্য হলে নির্দিষ্ট অগ্রাধিকার অনুযায়ী একটি বেছে নেওয়া হয় — inline সবচেয়ে শক্তিশালী, তারপর id, তারপর class, তারপর element selector।

    ```css
    body {
      font-family: Arial, sans-serif;
      background-color: #f5f5f5;
    }
    h1 {
      color: navy;
      text-align: center;
    }
    .highlight {
      background-color: yellow;
    }
    #header {
      padding: 20px;
    }
    ```

    দুইয়ের তুলনা:

    | বিষয় | HTML | CSS |
    |---|---|---|
    | পূর্ণরূপ | HyperText Markup Language | Cascading Style Sheets |
    | কাজ | গঠন ও বিষয়বস্তু নির্ধারণ | উপস্থাপন ও সাজসজ্জা নির্ধারণ |
    | ধরন | Markup language | Style sheet language |
    | ফাইল | `.html` | `.css` |
    | ছাড়া চলে কি | HTML ছাড়া CSS এর কোনো অর্থ নেই | CSS ছাড়া HTML চলে, তবে সাদামাটা দেখায় |
    | লেখার ধরন | `<tag attribute="value">content</tag>` | `selector { property: value; }` |

    কেন দুটি আলাদা রাখা হয়: গঠন ও উপস্থাপন পৃথক রাখলে একটি CSS ফাইল বদলেই সমগ্র সাইটের চেহারা বদলানো যায়, একই HTML বিভিন্ন যন্ত্রের জন্য ভিন্নভাবে দেখানো যায়, ফাইলের আকার ছোট হয় ও cache হয়, এবং কোড পড়া ও রক্ষণাবেক্ষণ সহজ হয়। একে বলা হয় separation of concerns।
17. **একটি Image ও একটি Web site URL HTML প্রদর্শন করার জন্য প্রয়োজনীয় code লিখুন?** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1022 (ET: N/A)]*


    Answer: একটি ছবি এবং একটি ওয়েবসাইটের URL দেখানোর HTML কোড:

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <title>Image and Link Example</title>
    </head>
    <body>

      <!-- একটি ছবি দেখানো -->
      <h2>Image</h2>
      <img src="images/flower.jpg" alt="A red flower" width="400" height="300">

      <!-- একটি ওয়েবসাইটের URL দেখানো -->
      <h2>Website Link</h2>
      <a href="https://www.bpsc.gov.bd" target="_blank" rel="noopener noreferrer">
        Visit BPSC Website
      </a>

      <!-- ছবির ওপরেই লিঙ্ক দেওয়া -->
      <h2>Clickable Image</h2>
      <a href="https://www.bpsc.gov.bd" target="_blank" rel="noopener noreferrer">
        <img src="images/logo.png" alt="BPSC Logo" width="150">
      </a>

    </body>
    </html>
    ```

    ব্যাখ্যা:

    `<img>` ট্যাগ — ছবি দেখানোর জন্য। এটি empty element, তাই closing tag নেই।
    - `src` — ছবির পথ বা ঠিকানা। বাধ্যতামূলক। এটি হতে পারে আপেক্ষিক পথ (`images/flower.jpg`) অথবা সম্পূর্ণ URL (`https://example.com/pic.jpg`)।
    - `alt` — ছবি লোড না হলে যে লেখা দেখাবে, এবং screen reader যা পড়ে শোনাবে। Accessibility ও SEO দুইয়ের জন্যই বাধ্যতামূলক।
    - `width` ও `height` — প্রদর্শনের মাপ পিক্সেলে।

    `<a>` ট্যাগ — লিঙ্ক তৈরির জন্য।
    - `href` — গন্তব্যের URL। বাধ্যতামূলক।
    - ট্যাগের ভেতরের লেখাটিই ক্লিকযোগ্য অংশ হিসেবে দেখা যায়।
    - `target="_blank"` — নতুন ট্যাবে খোলে।
    - `rel="noopener noreferrer"` — নতুন ট্যাবে খোলার সময় নিরাপত্তার জন্য দিতে হয়, কারণ এটি ছাড়া নতুন পৃষ্ঠাটি `window.opener` এর মাধ্যমে মূল পৃষ্ঠাটিকে নিয়ন্ত্রণ করতে পারে।

    URL কেবল লেখা হিসেবে দেখাতে হলে:

    ```html
    <p>Our website: <a href="https://www.example.com">https://www.example.com</a></p>
    ```

## HTTP Protocol (10)

1. What do the following specific HTTP status codes mean? Write down the exact standard text phrase for each: (a) 200 (b) 403 (c) 503 [SO IT 25-07-2026]


   Answer: The three status codes and their exact standard reason phrases.

   (a) 200 — OK
   (b) 403 — Forbidden
   (c) 503 — Service Unavailable

   | Code | Standard reason phrase | Meaning |
   |---|---|---|
   | 200 | OK | The request succeeded. The response body contains the requested resource. This is the normal reply to a successful GET. |
   | 403 | Forbidden | The server understood the request but refuses to fulfil it. The client's identity is known; it simply does not have permission. Repeating the request with the same credentials will not help. |
   | 503 | Service Unavailable | The server is temporarily unable to handle the request, because it is overloaded or is down for maintenance. The condition is temporary, and the server may send a `Retry-After` header saying when to try again. |

   Points that distinguish these from the codes they are confused with:
   - 403 Forbidden against 401 Unauthorized: 401 means the client has not authenticated, so sending credentials may succeed; 403 means the client is authenticated but not permitted, so credentials will not help.
   - 403 against 404 Not Found: 404 says the resource does not exist; 403 says it exists but access is denied. Some servers deliberately return 404 instead of 403 to avoid revealing that a protected resource exists.
   - 503 against 500 Internal Server Error: 500 means the server hit an unexpected fault while processing; 503 means the server is deliberately not serving right now and expects to recover.
   - 503 against 502 Bad Gateway and 504 Gateway Timeout: 502 means an upstream server sent an invalid response; 504 means the upstream server did not answer in time.

   The five classes of HTTP status code:

   | Class | Meaning | Common examples |
   |---|---|---|
   | 1xx | Informational | 100 Continue, 101 Switching Protocols |
   | 2xx | Success | 200 OK, 201 Created, 204 No Content |
   | 3xx | Redirection | 301 Moved Permanently, 302 Found, 304 Not Modified |
   | 4xx | Client error | 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 429 Too Many Requests |
   | 5xx | Server error | 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable, 504 Gateway Timeout |
2. Describe any two key differences between the HTTP GET and HTTP POST methods used for communication between a web browser and a web server. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*


   Answer: Two key differences between HTTP GET and HTTP POST.

   1. Where the data is carried, and therefore whether it is visible. GET appends the data to the URL as a query string, so it appears in the address bar, in the browser history, in the server access log and in any proxy log along the way. POST places the data in the body of the request, so it does not appear in the URL or in those logs. This is why a login form must use POST: with GET the password would be written into the address bar and stored in the browser history.

   2. Whether the request changes anything on the server, that is safety and idempotence. GET is defined as a safe method: it only reads, and it must never change server state. Because of that it is also idempotent, so repeating it any number of times gives the same result, and browsers and proxies are free to cache it and to repeat it automatically. POST is neither safe nor idempotent: it is meant to change state, and repeating it may create a second record. This is why pressing reload after a POST makes the browser warn that the data will be resubmitted, and why a payment submitted with GET could be charged twice by a simple page refresh.

   The full comparison:

   | Point | GET | POST |
   |---|---|---|
   | Purpose | Retrieve data from the server | Send data to the server to create or change something |
   | Where the data goes | Appended to the URL as a query string, `page.php?name=Karim&id=5` | Placed in the body of the HTTP request |
   | Visibility | Visible in the address bar, browser history, server logs and proxy logs | Not visible in the address bar |
   | Length limit | Limited by the maximum URL length, about 2,048 characters in practice | No practical limit; large files can be sent |
   | Data type | ASCII text only | Text and binary; supports file upload with `enctype="multipart/form-data"` |
   | Bookmark and share | Can be bookmarked and shared, because the whole request is in the URL | Cannot be bookmarked |
   | Caching | Can be cached by browsers and proxies | Not cached by default |
   | Back button and reload | Harmless; the page simply reloads | The browser warns that the data will be resubmitted |
   | Idempotent | Yes; repeating it produces the same result | No; repeating it may create a duplicate record |
   | Safe | Yes; it must not change server state | No; it changes server state |
   | Security | Unsuitable for passwords or sensitive data | Better, though only HTTPS actually protects the data in transit |
   | Typical use | Search results, filters, pagination, reading a page | Login, registration, payment, file upload, posting a comment |

   Examples:

   ```html
   <!-- GET: a search, which only reads -->
   <form action="/search" method="get">
     <input type="text" name="q">
     <input type="submit" value="Search">
   </form>
   <!-- produces:  GET /search?q=laptop  -->

   <!-- POST: a login, which must not expose the password -->
   <form action="/login" method="post">
     <input type="text" name="username">
     <input type="password" name="password">
     <input type="submit" value="Login">
   </form>
   <!-- produces:  POST /login   with username and password in the body -->
   ```
3. **6.7 What do the following specific HTTP status codes mean? Write down the exact standard text phrase for each: (a) 200 (b) 403 (c) 503** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*


   Answer: The three status codes and their exact standard reason phrases.

   (a) 200 — OK
   (b) 403 — Forbidden
   (c) 503 — Service Unavailable

   | Code | Standard reason phrase | Meaning |
   |---|---|---|
   | 200 | OK | The request succeeded. The response body contains the requested resource. This is the normal reply to a successful GET. |
   | 403 | Forbidden | The server understood the request but refuses to fulfil it. The client's identity is known; it simply does not have permission. Repeating the request with the same credentials will not help. |
   | 503 | Service Unavailable | The server is temporarily unable to handle the request, because it is overloaded or is down for maintenance. The condition is temporary, and the server may send a `Retry-After` header saying when to try again. |

   Points that distinguish these from the codes they are confused with:
   - 403 Forbidden against 401 Unauthorized: 401 means the client has not authenticated, so sending credentials may succeed; 403 means the client is authenticated but not permitted, so credentials will not help.
   - 403 against 404 Not Found: 404 says the resource does not exist; 403 says it exists but access is denied. Some servers deliberately return 404 instead of 403 to avoid revealing that a protected resource exists.
   - 503 against 500 Internal Server Error: 500 means the server hit an unexpected fault while processing; 503 means the server is deliberately not serving right now and expects to recover.
   - 503 against 502 Bad Gateway and 504 Gateway Timeout: 502 means an upstream server sent an invalid response; 504 means the upstream server did not answer in time.

   The five classes of HTTP status code:

   | Class | Meaning | Common examples |
   |---|---|---|
   | 1xx | Informational | 100 Continue, 101 Switching Protocols |
   | 2xx | Success | 200 OK, 201 Created, 204 No Content |
   | 3xx | Redirection | 301 Moved Permanently, 302 Found, 304 Not Modified |
   | 4xx | Client error | 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 429 Too Many Requests |
   | 5xx | Server error | 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable, 504 Gateway Timeout |
4. **(ক) ফর্ম জমা দেয়ার পদ্ধতি GET এবং POST এর মধ্যে পার্থক্য কী, কখন কোন পদ্ধতি ব্যবহার করতে হয় উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*


   Answer: GET ও POST — ফর্মের তথ্য সার্ভারে পাঠানোর দুটি পদ্ধতি, যা HTML ফর্মের `method` attribute দিয়ে নির্ধারণ করা হয়।

   | Point | GET | POST |
   |---|---|---|
   | Purpose | Retrieve data from the server | Send data to the server to create or change something |
   | Where the data goes | Appended to the URL as a query string, `page.php?name=Karim&id=5` | Placed in the body of the HTTP request |
   | Visibility | Visible in the address bar, browser history, server logs and proxy logs | Not visible in the address bar |
   | Length limit | Limited by the maximum URL length, about 2,048 characters in practice | No practical limit; large files can be sent |
   | Data type | ASCII text only | Text and binary; supports file upload with `enctype="multipart/form-data"` |
   | Bookmark and share | Can be bookmarked and shared, because the whole request is in the URL | Cannot be bookmarked |
   | Caching | Can be cached by browsers and proxies | Not cached by default |
   | Back button and reload | Harmless; the page simply reloads | The browser warns that the data will be resubmitted |
   | Idempotent | Yes; repeating it produces the same result | No; repeating it may create a duplicate record |
   | Safe | Yes; it must not change server state | No; it changes server state |
   | Security | Unsuitable for passwords or sensitive data | Better, though only HTTPS actually protects the data in transit |
   | Typical use | Search results, filters, pagination, reading a page | Login, registration, payment, file upload, posting a comment |

   উদাহরণ — GET পদ্ধতি:

   ```html
   <form action="search.php" method="get">
     <input type="text" name="keyword">
     <input type="text" name="category">
     <input type="submit" value="খুঁজুন">
   </form>
   ```

   ব্যবহারকারী keyword এ "laptop" ও category তে "electronics" লিখে জমা দিলে ব্রাউজার যায়:

   ```
   http://example.com/search.php?keyword=laptop&category=electronics
   ```

   উদাহরণ — POST পদ্ধতি:

   ```html
   <form action="login.php" method="post">
     <input type="text" name="username">
     <input type="password" name="password">
     <input type="submit" value="প্রবেশ">
   </form>
   ```

   এখানে ঠিকানার ঘরে কেবল `http://example.com/login.php` দেখা যাবে; ব্যবহারকারীর নাম ও পাসওয়ার্ড অনুরোধের শরীরে যাবে।

   কখন কোনটি ব্যবহার করতে হবে:

   GET ব্যবহার করুন যখন —
   - কেবল তথ্য পড়া হচ্ছে, সার্ভারে কিছু বদলাচ্ছে না। যেমন অনুসন্ধান, ছাঁকনি, পৃষ্ঠা নম্বর।
   - ফলাফলের পৃষ্ঠাটি bookmark করা বা লিঙ্ক হিসেবে অন্যকে পাঠানো দরকার।
   - পাঠানো তথ্য অল্প ও গোপন নয়।
   - উদাহরণ: `results.php?roll=123456` — পরীক্ষার ফল দেখা, যা লিঙ্ক আকারে ভাগ করা যায়।

   POST ব্যবহার করুন যখন —
   - সার্ভারে কিছু তৈরি বা পরিবর্তন হচ্ছে — নিবন্ধন, লগইন, মন্তব্য, অর্ডার, টাকা পরিশোধ।
   - পাসওয়ার্ড, জাতীয় পরিচয়পত্র নম্বর, কার্ডের তথ্যের মতো সংবেদনশীল ডেটা পাঠানো হচ্ছে।
   - বড় পরিমাণ তথ্য বা ফাইল আপলোড করা হচ্ছে।
   - একই কাজ দুইবার হয়ে গেলে ক্ষতি হবে, যেমন দুইবার টাকা কাটা।

   একটি গুরুত্বপূর্ণ সতর্কতা: POST ব্যবহার করলেই তথ্য নিরাপদ হয় না। POST এর ডেটাও সাধারণ HTTP তে খোলা অবস্থায় নেটওয়ার্কে যায় এবং যে কেউ ধরে ফেলতে পারে। প্রকৃত নিরাপত্তার জন্য HTTPS ব্যবহার করা বাধ্যতামূলক। POST কেবল ঠিকানার ঘর ও ব্রাউজারের ইতিহাস থেকে তথ্য আড়াল করে।

   আরেকটি বিষয়: POST করার পর সরাসরি পৃষ্ঠা না দেখিয়ে একটি redirect পাঠানো উচিত, একে বলে Post/Redirect/Get প্যাটার্ন। এতে ব্যবহারকারী পৃষ্ঠাটি refresh করলেও ফর্মটি দ্বিতীয়বার জমা হয় না।
5. **What is cookie? What is its purpose?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*


   Answer: A cookie is a small piece of text data, normally not more than about 4 KB, that a web server sends to the browser, and that the browser stores on the user's computer and sends back with every subsequent request to the same site.

   How it works:
   - The server includes a `Set-Cookie` header in its response: `Set-Cookie: sessionId=abc123; Path=/; HttpOnly; Secure; SameSite=Strict`
   - The browser stores it.
   - On every later request to that site the browser automatically adds: `Cookie: sessionId=abc123`
   - The server therefore recognises the returning visitor.

   Why cookies exist: HTTP is a stateless protocol, so the server has no memory of a previous request. Cookies are the mechanism that adds state on top of a stateless protocol.

   Purposes of cookies:

   - Session management. The commonest use. After a successful login the server creates a session and stores its identifier in a cookie, so the user stays logged in as he moves from page to page. Shopping carts, form progress across several pages and game scores work the same way.

   - Personalisation. Remembering the user's chosen language, theme, currency, font size and region, so the site looks the same on the next visit.

   - Tracking and analytics. Recording which pages a visitor viewed, how long the visit lasted and whether the visitor has been here before. Google Analytics uses cookies for this.

   - Advertising. Third-party cookies set by an advertising network follow a user across many sites to build an interest profile and show targeted advertisements. This is the use that has caused most privacy concern, and browsers are now blocking it.

   - Security. Storing a CSRF token, and remembering that a device has already passed two-factor authentication.

   Types of cookie:

   | Type | Description |
   |---|---|
   | Session cookie | Has no expiry date; deleted when the browser closes |
   | Persistent cookie | Has an `Expires` or `Max-Age`; survives until that date |
   | First-party cookie | Set by the site the user is visiting |
   | Third-party cookie | Set by another domain, typically an advertiser, embedded in the page |
   | Secure cookie | Sent only over HTTPS |
   | HttpOnly cookie | Cannot be read by JavaScript, which protects it from XSS |
   | SameSite cookie | Restricts sending on cross-site requests, which protects against CSRF |

   Important attributes: `Expires` or `Max-Age` for lifetime, `Domain` and `Path` for scope, `Secure`, `HttpOnly` and `SameSite` for protection.

   Limitations and concerns: about 4 KB per cookie and roughly 50 cookies per domain; they are stored in plain text on the user's machine, so no sensitive data such as a password should ever be placed in one; the user can delete or block them; they add to the size of every request; and their use for tracking is now regulated, which is why sites display a cookie consent notice.

   Related storage that must be distinguished: `localStorage` holds about 5 to 10 MB, has no expiry and is never sent to the server automatically; `sessionStorage` is the same but cleared when the tab closes. Both are read by JavaScript and are unsuitable for authentication tokens for the same reason.
6. **What is the difference between http and https?** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 648 (ET: BUET)], [BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 796 (ET: N/A)]*


   Answer: Difference between HTTP and HTTPS.

   | Point | HTTP | HTTPS |
   |---|---|---|
   | Full form | HyperText Transfer Protocol | HyperText Transfer Protocol Secure |
   | Security | None; data travels as plain text | Encrypted with SSL/TLS |
   | Default port | 80 | 443 |
   | URL prefix | `http://` | `https://` |
   | Certificate | Not needed | Requires an SSL/TLS certificate issued by a Certificate Authority |
   | Browser indication | Marked "Not secure" | Padlock icon shown |
   | Data integrity | None; data can be altered in transit without detection | Guaranteed by a message authentication code |
   | Server authentication | None; the client cannot verify who it is talking to | The certificate proves the server's identity |
   | Vulnerable to eavesdropping | Yes; anyone on the path can read the traffic | No; the traffic is unreadable |
   | Vulnerable to man-in-the-middle | Yes | Protected, provided the certificate is validated |
   | Speed | Marginally faster, since there is no handshake or encryption | Slightly slower on the first connection; negligible afterwards, and HTTP/2 over TLS is usually faster overall |
   | SEO | Ranked lower | Ranked higher; Google treats HTTPS as a ranking signal |
   | Cost | Free | Certificates can be free through Let's Encrypt, or paid |
   | Suitable for | Nothing in modern practice | All websites |

   The three guarantees HTTPS provides, which is the point worth stating clearly:
   - Confidentiality: an eavesdropper on the network, on public Wi-Fi for example, sees only ciphertext.
   - Integrity: any alteration of the data in transit is detected and the connection is dropped.
   - Authentication: the certificate, signed by a trusted Certificate Authority, proves that the server really is the one named in the URL.

   How HTTPS works, in outline: HTTPS is simply HTTP running inside a TLS tunnel. During the TLS handshake the client and server agree on a cipher suite, the server presents its certificate, the client verifies it against its store of trusted authorities, and the two sides establish a shared symmetric session key using asymmetric cryptography. All the HTTP messages that follow are encrypted with that symmetric key, because symmetric encryption is far faster.

   ```mermaid
   sequenceDiagram
     participant C as Client
     participant S as Server
     C->>S: ClientHello (supported cipher suites)
     S-->>C: ServerHello + Certificate (public key)
     C->>C: Verify certificate against trusted CAs
     C->>S: Key exchange, encrypted with server's public key
     C->>S: Finished (now encrypted)
     S-->>C: Finished (now encrypted)
     Note over C,S: All HTTP traffic now encrypted with the session key
   ```

   Practical note: HTTPS protects data while it travels. It says nothing about whether the site itself is honest — a phishing site can also hold a valid certificate. The padlock means the connection is private, not that the owner is trustworthy.
7. **(গ) URL কী? একটি URL ক্লিক করার পর Web Page Show করার পূর্ব পর্যন্ত যে কয়টি Step হয় সেগুলির নাম লিখুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 705 (ET: N/A)]*


   Answer: URL হলো Uniform Resource Locator — ইন্টারনেটে কোনো সম্পদের সম্পূর্ণ ঠিকানা, যা বলে দেয় কোন protocol ব্যবহার করে, কোন সার্ভারে গিয়ে, কোন ফাইলটি চাইতে হবে।

   একটি URL এর অংশ:

   ```
   https://www.example.com:443/products/laptop.html?id=45#specs
   |____|  |_____________| |_| |__________________| |____| |___|
   scheme      host       port        path          query fragment
   ```

   URL এ ক্লিক করার পর ওয়েব পৃষ্ঠা দেখানো পর্যন্ত যেসব ধাপ ঘটে:

   ১. URL parsing: ব্রাউজার URL টিকে ভেঙে protocol, domain, port, path ও query আলাদা করে নেয় এবং বৈধতা যাচাই করে।

   ২. DNS resolution: domain নামটিকে IP ঠিকানায় রূপান্তর করা হয়। ব্রাউজার ক্রমে খোঁজে — নিজের DNS cache, অপারেটিং সিস্টেমের cache, hosts ফাইল, তারপর ISP এর DNS resolver। না পেলে resolver ধারাবাহিকভাবে root server, TLD server ও authoritative name server কে জিজ্ঞাসা করে IP ঠিকানাটি নিয়ে আসে।

   ৩. TCP connection: প্রাপ্ত IP ঠিকানার ৮০ বা ৪৪৩ নম্বর port এ three-way handshake করে সংযোগ স্থাপন করা হয় — SYN, SYN-ACK, ACK।

   ৪. TLS handshake, যদি HTTPS হয়: সার্ভার তার certificate দেখায়, ব্রাউজার তা যাচাই করে, এবং দুই পক্ষ একটি গোপন session key তৈরি করে। এরপর থেকে সব যোগাযোগ এনক্রিপ্ট হয়।

   ৫. HTTP request: ব্রাউজার অনুরোধ পাঠায়, যেমন —

   ```
   GET /products/laptop.html HTTP/1.1
   Host: www.example.com
   User-Agent: Mozilla/5.0 ...
   Accept: text/html
   Cookie: sessionId=abc123
   ```

   ৬. Server processing: ওয়েব সার্ভার অনুরোধটি গ্রহণ করে। Static ফাইল হলে সরাসরি পড়ে নেয়; dynamic হলে PHP বা Node.js এর মতো application চালায়, প্রয়োজনে database এ query করে এবং HTML তৈরি করে।

   ৭. HTTP response: সার্ভার status line, header ও body সহ উত্তর পাঠায় —

   ```
   HTTP/1.1 200 OK
   Content-Type: text/html; charset=UTF-8
   Content-Length: 5120

   <!DOCTYPE html> ...
   ```

   ৮. HTML parsing ও DOM নির্মাণ: ব্রাউজার HTML পড়ে DOM tree তৈরি করে।

   ৯. অতিরিক্ত সম্পদ আনা: HTML এর ভেতরে থাকা CSS, JavaScript, ছবি, ফন্ট ইত্যাদির জন্য আলাদা আলাদা অনুরোধ পাঠানো হয়। এগুলো সমান্তরালে আসে।

   ১০. CSSOM নির্মাণ ও Render tree তৈরি: CSS পড়ে CSSOM তৈরি হয়, তারপর DOM ও CSSOM মিলিয়ে render tree তৈরি হয়, যাতে কেবল দৃশ্যমান উপাদানগুলো থাকে।

   ১১. Layout বা reflow: প্রতিটি উপাদানের সঠিক আকার ও অবস্থান হিসাব করা হয়।

   ১২. Painting ও Compositing: পিক্সেল আঁকা হয় এবং স্তরগুলো একত্র করে পর্দায় দেখানো হয়।

   ১৩. JavaScript execution: script চলে, যা DOM পরিবর্তন করতে পারে এবং প্রয়োজনে নতুন layout ও paint ঘটায়।

   ১৪. সংযোগ বন্ধ বা পুনঃব্যবহার: keep-alive থাকলে একই TCP সংযোগ পরবর্তী অনুরোধের জন্য ব্যবহৃত হয়, নইলে চার ধাপের handshake দিয়ে সংযোগ বন্ধ হয়।

   ```mermaid
   flowchart TD
     A[URL এ ক্লিক] --> B[URL parsing]
     B --> C[DNS resolution → IP]
     C --> D[TCP three-way handshake]
     D --> E{HTTPS?}
     E -->|হ্যাঁ| F[TLS handshake]
     E -->|না| G[HTTP request]
     F --> G
     G --> H[Server processing + DB query]
     H --> I[HTTP response]
     I --> J[HTML parse → DOM]
     J --> K[CSS, JS, images আনা]
     K --> L[CSSOM + Render tree]
     L --> M[Layout]
     M --> N[Paint & Composite]
     N --> O[পৃষ্ঠা দৃশ্যমান]
   ```
8. **(c) Explain the difference between Stateless and Stateful protocols. Which type of protocol http is?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 885-886 (ET: N/A)]*


   Answer: Stateless and stateful protocols, and which one HTTP is.

   A stateless protocol is one in which the server keeps no information about previous requests. Every request must carry all the information needed to understand and process it, and the server treats each request as completely independent of every other.

   A stateful protocol is one in which the server maintains information about the ongoing interaction across several requests. The meaning of a request may depend on what came before it.

   | Point | Stateless | Stateful |
   |---|---|---|
   | Server memory of past requests | None | Maintained for the whole session |
   | Independence of requests | Each request is complete in itself | A request may depend on earlier ones |
   | Server resources | Low; nothing stored per client | High; memory held for every connected client |
   | Scalability | Excellent; any server can handle any request, so load balancing is trivial | Poor; the client must return to the same server, or state must be shared |
   | Recovery after a crash | Simple; the client just repeats the request | Difficult; the session state is lost |
   | Complexity of design | Simple | Complex |
   | Overhead per request | Higher, because context is resent every time | Lower, because context is already known |
   | Examples | HTTP, UDP, DNS, IP | FTP, TCP, Telnet, SSH, SMTP |

   HTTP is a stateless protocol.

   Each HTTP request is self-contained. When a browser asks for page2.html, the server has no recollection that the same browser asked for page1.html a second earlier. That is why the request must carry its own headers, cookies and authentication every time.

   Why HTTP was designed to be stateless:
   - Simplicity: the server does not have to track millions of clients.
   - Scalability: any one of a hundred servers behind a load balancer can serve any request, because none of them holds state that the others lack. This is what allows the web to scale.
   - Reliability: if a server fails, the client simply retries; nothing has been lost.
   - Low memory use: no per-client structures are held between requests.

   How state is added on top of a stateless HTTP, since real applications need to remember users:
   - Cookies: the server sends a small piece of data that the browser returns with every later request.
   - Sessions: the server keeps the actual data and gives the browser only a session identifier in a cookie.
   - URL rewriting: the session identifier is appended to every link. Rarely used now.
   - Hidden form fields: state carried inside the form.
   - Tokens such as JWT: the state itself is signed and carried by the client, which preserves statelessness on the server.
   - Client-side storage: `localStorage` and `sessionStorage`.

   Two clarifications that are commonly confused:
   - HTTP is stateless, but it runs over TCP, which is a stateful, connection-oriented protocol. Statelessness at the application layer does not imply statelessness at the transport layer.
   - HTTP keep-alive, which reuses one TCP connection for several requests, does not make HTTP stateful. It reuses the connection; the server still remembers nothing about the earlier requests.

   REST, the architectural style used for web APIs, deliberately keeps this statelessness as one of its constraints, for exactly the scalability reason given above.
9. **What is the difference between http session and http cookies?** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 911 (ET: BUET)]*


   Answer: Difference between an HTTP session and HTTP cookies.

   | Point | Cookie | Session |
   |---|---|---|
   | Where the data is stored | On the client, in the browser | On the server, in memory, a file or a database |
   | What the client holds | The actual data | Only the session identifier, itself usually kept in a cookie |
   | Size limit | About 4 KB per cookie, roughly 50 per domain | Limited only by server storage; can hold large objects |
   | Security | Lower; stored in plain text on the user's machine, and the user can read and alter it | Higher; the data never leaves the server, and the client sees only an opaque identifier |
   | Lifetime | Set by `Expires` or `Max-Age`; a persistent cookie can survive for years | Ends when the browser closes or after an inactivity timeout, typically 20 to 30 minutes |
   | Survives browser restart | Yes, if persistent | No, normally |
   | Sent over the network | Sent with every request to the domain, adding to each request | Only the small identifier is sent |
   | Server resources | None | Consumes memory for every active user |
   | Accessible to JavaScript | Yes, unless marked HttpOnly | No |
   | Depends on the other | Works on its own | Normally depends on a cookie to carry its identifier |
   | Typical use | Language preference, theme, "remember me", analytics identifiers | Logged-in user identity, shopping cart, permissions, form wizard progress |

   How the two work together, which is the point of the question:

   ```mermaid
   sequenceDiagram
     participant B as Browser
     participant S as Server
     B->>S: POST /login (username, password)
     S->>S: Verify credentials, create session object in server memory
     S-->>B: Set-Cookie: PHPSESSID=x9f2k7; HttpOnly; Secure
     Note over S: Server stores: x9f2k7 → {userId: 501, role: admin, cart: [...]}
     B->>S: GET /dashboard  (Cookie: PHPSESSID=x9f2k7)
     S->>S: Look up x9f2k7, find the user
     S-->>B: Dashboard page for that user
   ```

   The session holds the real data on the server; the cookie only carries the key to it. This is why a session is the correct place for anything sensitive, and a cookie is not.

   A concrete illustration of the security difference: storing `role=admin` in a cookie is a serious flaw, because the user can simply edit the cookie in the browser and become an administrator. Storing the role in the session is safe, because the browser holds only the meaningless identifier `x9f2k7` and cannot change what that identifier maps to on the server.

   Session hijacking is the corresponding risk: if an attacker steals the session identifier, from an unencrypted connection, from an XSS flaw, or from a shared computer, he becomes that user. The defences are HTTPS everywhere, the `HttpOnly` and `Secure` and `SameSite` cookie flags, regenerating the session identifier immediately after login to prevent session fixation, a short inactivity timeout, and binding the session loosely to the client's characteristics.

   A third approach worth mentioning: token-based authentication with a JWT, where the signed token carries the user's identity and is verified by signature rather than looked up in server storage. It gives the scalability of cookies with much of the safety of sessions, at the cost of not being revocable until it expires.
10. **It is a small price of data stored on a user's computer by the web browser while browsing a website. What we are talking about?** *[Sadharan Bima Corporation Programmer/ AP/AME 2020 compact it 1002 (ET: DU)], [BSEC Assistant Director (MIS) 2021 compact it 938 (ET: IBA)]*


    Answer: A cookie, more precisely an HTTP cookie, also called a web cookie or a browser cookie.

    Definition: a small piece of data, up to about 4 KB, that a website sends to the browser, and that the browser stores on the user's computer and sends back with every later request to that site.

    Why it exists: HTTP is stateless, so the server has no memory of earlier requests. The cookie is the mechanism that lets a website recognise a returning visitor and so maintain state.

    Main uses: keeping a user logged in through a session identifier, holding a shopping cart, remembering preferences such as language and theme, and tracking visits for analytics and advertising.

    Types: session cookies, which are deleted when the browser closes; persistent cookies, which have an expiry date; first-party cookies, set by the site being visited; and third-party cookies, set by another domain such as an advertising network.

## JavaScript & jQuery (DOM & Validation) (8)

1. **Jquery for email validation** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*


   Answer: Email validation with jQuery.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
     <meta charset="UTF-8">
     <title>Email Validation</title>
     <script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>
     <style>
       .error { color: red; font-size: 13px; }
       .ok    { color: green; font-size: 13px; }
     </style>
   </head>
   <body>

     <form id="myForm">
       <label for="email">Email:</label>
       <input type="text" id="email" name="email">
       <span id="msg"></span>
       <br><br>
       <input type="submit" value="Submit">
     </form>

     <script>
     $(document).ready(function () {

         // regular expression for a valid email address
         var pattern = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;

         function validateEmail() {
             var email = $.trim($("#email").val());

             if (email === "") {
                 $("#msg").removeClass("ok").addClass("error").text("Email is required");
                 return false;
             }
             if (!pattern.test(email)) {
                 $("#msg").removeClass("ok").addClass("error").text("Invalid email address");
                 return false;
             }
             $("#msg").removeClass("error").addClass("ok").text("Valid email");
             return true;
         }

         // validate while the user types
         $("#email").on("keyup blur", validateEmail);

         // validate again on submit
         $("#myForm").on("submit", function (e) {
             if (!validateEmail()) {
                 e.preventDefault();   // stop the form from being submitted
             }
         });
     });
     </script>

   </body>
   </html>
   ```

   Explanation of the regular expression `/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/`:

   | Part | Meaning |
   |---|---|
   | `^` | Start of the string |
   | `[a-zA-Z0-9._%+-]+` | One or more letters, digits, dot, underscore, percent, plus or hyphen — the local part before the @ |
   | `@` | A literal at sign, exactly one |
   | `[a-zA-Z0-9.-]+` | The domain name: letters, digits, dots and hyphens |
   | `\.` | A literal dot; the backslash escapes it, because an unescaped dot matches any character |
   | `[a-zA-Z]{2,}` | The top-level domain: at least two letters, such as com, org, bd |
   | `$` | End of the string |

   Test results with this pattern:

   | Input | Result |
   |---|---|
   | `karim@example.com` | valid |
   | `a.b_c+d@mail.co.uk` | valid |
   | `karim@example` | invalid, no top-level domain |
   | `karim.example.com` | invalid, no @ |
   | `@example.com` | invalid, no local part |
   | `karim@@example.com` | invalid, two @ signs |

   The same thing using the jQuery Validation plugin, which is shorter:

   ```html
   <script src="https://cdn.jsdelivr.net/npm/jquery-validation@1.19.5/dist/jquery.validate.min.js"></script>
   <script>
   $(document).ready(function () {
       $("#myForm").validate({
           rules: {
               email: { required: true, email: true }
           },
           messages: {
               email: {
                   required: "Please enter your email",
                   email: "Please enter a valid email address"
               }
           }
       });
   });
   </script>
   ```

   Essential note: client-side validation is for the user's convenience, not for security. Anyone can disable JavaScript or send the request directly, so the email must be validated again on the server before it is stored.
2. **Write Javascript code to check NID validity?** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1359 (ET: BUET)]*


   Answer: JavaScript code to check the validity of a Bangladeshi National ID (NID) number.

   Rules used: a Bangladeshi NID number is 10, 13 or 17 digits. The 17-digit form begins with a 4-digit year of birth, which must be a sensible year. The 13-digit form is the old 17-digit number without the year prefix. The 10-digit form is the current smart card number.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
     <meta charset="UTF-8">
     <title>NID Validation</title>
   </head>
   <body>

     <label for="nid">NID Number:</label>
     <input type="text" id="nid" maxlength="17">
     <button onclick="checkNID()">Check</button>
     <p id="result"></p>

     <script>
     function validateNID(nid) {
         // remove spaces and hyphens the user may have typed
         nid = nid.replace(/[\s-]/g, "");

         if (nid === "") {
             return { valid: false, message: "NID number is required" };
         }

         // must contain digits only
         if (!/^[0-9]+$/.test(nid)) {
             return { valid: false, message: "NID must contain digits only" };
         }

         // length must be 10, 13 or 17
         if (nid.length !== 10 && nid.length !== 13 && nid.length !== 17) {
             return { valid: false, message: "NID must be 10, 13 or 17 digits" };
         }

         // for the 17-digit form, the first 4 digits are the birth year
         if (nid.length === 17) {
             var year = parseInt(nid.substring(0, 4), 10);
             var thisYear = new Date().getFullYear();
             if (year < 1900 || year > thisYear) {
                 return { valid: false, message: "Invalid birth year in NID" };
             }
         }

         // the number must not be all the same digit
         if (/^(\d)\1+$/.test(nid)) {
             return { valid: false, message: "NID cannot be all the same digit" };
         }

         return { valid: true, message: "Valid NID number (" + nid.length + " digits)" };
     }

     function checkNID() {
         var value  = document.getElementById("nid").value;
         var result = validateNID(value);
         var out    = document.getElementById("result");

         out.textContent = result.message;
         out.style.color = result.valid ? "green" : "red";
     }
     </script>

   </body>
   </html>
   ```

   Test results:

   | Input | Output |
   |---|---|
   | `1234567890` | Valid NID number (10 digits) |
   | `1990123456789` | Valid NID number (13 digits) |
   | `19901234567890123` | Valid NID number (17 digits) |
   | `12345` | NID must be 10, 13 or 17 digits |
   | `12345abcde` | NID must contain digits only |
   | `29901234567890123` | Invalid birth year in NID |
   | `1111111111` | NID cannot be all the same digit |
   | (empty) | NID number is required |

   A compact version using only a regular expression, if a single expression is asked for:

   ```javascript
   function isValidNID(nid) {
       return /^(\d{10}|\d{13}|(19|20)\d{2}\d{13})$/.test(nid.trim());
   }
   ```

   Points worth stating:
   - The 17-digit format is: 4 digits for the year of birth, then 13 digits made up of district, upazila, union and a serial number.
   - Format validation only proves that the number is well formed. Whether the number actually exists and belongs to that person can be confirmed only by querying the Election Commission's verification service.
   - This check must be repeated on the server; client-side JavaScript can be bypassed.
3. **Which tag is used to write JavaScript in html?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*


   Answer: The `<script>` tag is used to write or include JavaScript in HTML.

   Three ways of using it:

   1. Internal JavaScript, written inside the page:

   ```html
   <script>
     document.getElementById("demo").innerHTML = "Hello World";
   </script>
   ```

   2. External JavaScript, kept in a separate `.js` file:

   ```html
   <script src="script.js"></script>
   ```

   3. Inline, in an event attribute. This is not the `<script>` tag, but it is a way of writing JavaScript in HTML:

   ```html
   <button onclick="alert('Clicked!')">Click Me</button>
   ```

   Where to place the `<script>` tag:
   - Just before the closing `</body>` tag is the usual choice, so that the HTML is parsed and displayed first and the elements the script refers to already exist.
   - In the `<head>` with the `defer` attribute is the modern preference: the file downloads in parallel with parsing but runs only after the document is ready.
   - `async` downloads in parallel and runs as soon as it arrives, in no guaranteed order. Suitable only for independent scripts such as analytics.

   ```html
   <script src="app.js" defer></script>   <!-- runs after parsing, in order -->
   <script src="ads.js" async></script>   <!-- runs whenever it arrives -->
   ```

   Note: the `<script>` tag always needs a closing `</script>`, even when `src` is used. Writing `<script src="a.js" />` does not work in HTML.
4. **Write Javascript function to validate a customer number where the customer number in 3 uppercase letter and district code followed by 8 digits.** *[BICIC Assistant Programmer 2022 compact it 630 (ET: BUET)]*


   Answer: The customer number consists of 3 uppercase letters, then a district code, then 8 digits.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
     <meta charset="UTF-8">
     <title>Customer Number Validation</title>
   </head>
   <body>

     <label for="cust">Customer Number:</label>
     <input type="text" id="cust" placeholder="ABCDHK12345678">
     <button onclick="check()">Validate</button>
     <p id="out"></p>

     <script>
     // list of valid district codes
     var districtCodes = ["DHK", "CTG", "RAJ", "KHU", "BAR", "SYL", "RAN", "MYM"];

     function validateCustomerNumber(cust) {

         cust = cust.trim().toUpperCase();

         if (cust === "") {
             return "Customer number is required";
         }

         // 3 letters + 3 letters district code + 8 digits = 14 characters
         var pattern = /^[A-Z]{3}([A-Z]{3})[0-9]{8}$/;
         var match   = cust.match(pattern);

         if (match === null) {
             return "Invalid format. Required: 3 uppercase letters + district code + 8 digits";
         }

         // check that the district code is one of the recognised codes
         var code = match[1];
         if (districtCodes.indexOf(code) === -1) {
             return "Unknown district code: " + code;
         }

         return "Valid customer number";
     }

     function check() {
         var value = document.getElementById("cust").value;
         var msg   = validateCustomerNumber(value);
         var out   = document.getElementById("out");
         out.textContent = msg;
         out.style.color = (msg === "Valid customer number") ? "green" : "red";
     }
     </script>

   </body>
   </html>
   ```

   Explanation of the regular expression `/^[A-Z]{3}([A-Z]{3})[0-9]{8}$/`:

   | Part | Meaning |
   |---|---|
   | `^` | Start of the string |
   | `[A-Z]{3}` | Exactly 3 uppercase letters |
   | `([A-Z]{3})` | Exactly 3 more uppercase letters, captured as group 1, which is the district code |
   | `[0-9]{8}` | Exactly 8 digits |
   | `$` | End of the string |

   Test results:

   | Input | Output |
   |---|---|
   | `ABCDHK12345678` | Valid customer number |
   | `XYZCTG87654321` | Valid customer number |
   | `abcdhk12345678` | Valid, because the code converts to uppercase first |
   | `ABCXXX12345678` | Unknown district code: XXX |
   | `ABDHK12345678` | Invalid format, only 2 leading letters |
   | `ABCDHK1234567` | Invalid format, only 7 digits |
   | `ABCDHK1234567A` | Invalid format, a letter among the digits |

   If the district code is numeric rather than alphabetic, for example a two-digit code, the only change needed is in the pattern:

   ```javascript
   var pattern = /^[A-Z]{3}([0-9]{2})[0-9]{8}$/;
   ```

   The same validation in a form, so that submission is blocked when the value is wrong:

   ```html
   <form onsubmit="return validateCustomerNumber(this.cust.value) === 'Valid customer number';">
     <input type="text" name="cust" pattern="[A-Za-z]{6}[0-9]{8}" required>
     <input type="submit" value="Submit">
   </form>
   ```
5. **Write HTML and Javascript code of following box.** *[EGCB Assistant Engineer (CSE) 2022 compact it 716 (ET: BUET)]*


   Answer: A "box" in this context is an input box with a button that produces a result, which is the standard form of such a question. The code below builds a bordered box that takes two numbers and displays their sum. <!-- verify: the original figure is not reproduced in the question -->

   ```html
   <!DOCTYPE html>
   <html>
   <head>
     <meta charset="UTF-8">
     <title>Input Box</title>
     <style>
       .box {
         width: 300px;
         border: 2px solid #333;
         border-radius: 6px;
         padding: 20px;
         font-family: Arial, sans-serif;
         margin: 40px auto;
       }
       .box h3   { margin-top: 0; text-align: center; }
       .box label { display: inline-block; width: 90px; }
       .box input[type="text"] { width: 150px; margin-bottom: 10px; }
       .box button { width: 100%; padding: 8px; cursor: pointer; }
       #answer { margin-top: 12px; font-weight: normal; text-align: center; }
     </style>
   </head>
   <body>

     <div class="box">
       <h3>Addition</h3>

       <label for="num1">Number 1:</label>
       <input type="text" id="num1"><br>

       <label for="num2">Number 2:</label>
       <input type="text" id="num2"><br>

       <button onclick="calculate()">Add</button>

       <p id="answer"></p>
     </div>

     <script>
     function calculate() {
         var a = parseFloat(document.getElementById("num1").value);
         var b = parseFloat(document.getElementById("num2").value);
         var out = document.getElementById("answer");

         if (isNaN(a) || isNaN(b)) {
             out.style.color = "red";
             out.textContent = "Please enter numbers in both boxes";
             return;
         }

         out.style.color = "green";
         out.textContent = "Result: " + (a + b);
     }
     </script>

   </body>
   </html>
   ```

   The three built-in dialogue boxes of JavaScript, in case the question means one of those:

   ```html
   <script>
     // 1. Alert box: shows a message with an OK button
     alert("Data saved successfully");

     // 2. Confirm box: OK and Cancel; returns true or false
     var yes = confirm("Do you want to delete this record?");
     if (yes) {
         alert("Deleted");
     } else {
         alert("Cancelled");
     }

     // 3. Prompt box: takes input; returns the text, or null if cancelled
     var name = prompt("What is your name?", "");
     if (name !== null && name !== "") {
         document.write("Hello " + name);
     }
   </script>
   ```

   | Box | Buttons | Returns |
   |---|---|---|
   | `alert()` | OK | nothing |
   | `confirm()` | OK, Cancel | `true` or `false` |
   | `prompt()` | OK, Cancel | the entered string, or `null` |

   All three are blocking: they stop the page until the user responds, which is why modern pages use custom modal boxes built from HTML and CSS instead.
6. **Explain hoisting in JavaScript?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 761 (ET: N/A)]*


   Answer: Hoisting is JavaScript's behaviour of moving the declarations of variables, functions and classes to the top of their scope before the code is executed. Only the declaration is moved; the assignment stays where it was written.

   What actually happens: JavaScript executes in two phases. In the creation phase the engine scans the scope and registers every declaration in memory. In the execution phase it runs the statements line by line. Hoisting is a description of that first phase.

   1. Hoisting of `var`

   ```javascript
   console.log(x);   // undefined, not an error
   var x = 10;
   console.log(x);   // 10
   ```

   The engine treats this as:

   ```javascript
   var x;            // declaration hoisted, initialised to undefined
   console.log(x);   // undefined
   x = 10;           // assignment stays in place
   console.log(x);   // 10
   ```

   2. Hoisting of `let` and `const`

   ```javascript
   console.log(y);   // ReferenceError: Cannot access 'y' before initialization
   let y = 20;
   ```

   `let` and `const` are hoisted too, but they are not initialised. From the top of the block until the declaration is reached they sit in what the specification calls the Temporal Dead Zone, and any access throws a ReferenceError. This is deliberate: it turns a silent `undefined` bug into a visible error.

   3. Hoisting of function declarations

   ```javascript
   greet();          // "Hello" — works

   function greet() {
       console.log("Hello");
   }
   ```

   A function declaration is hoisted completely, both its name and its body, so it can be called before the line on which it is written.

   4. Function expressions and arrow functions are not hoisted as functions

   ```javascript
   sayHi();          // TypeError: sayHi is not a function
   var sayHi = function () { console.log("Hi"); };

   sayBye();         // ReferenceError: Cannot access 'sayBye' before initialization
   const sayBye = () => console.log("Bye");
   ```

   Here only the variable is hoisted, not the function. With `var` the variable exists but holds `undefined`, and calling `undefined` gives a TypeError.

   Summary

   | Declaration | Hoisted | Initialised on hoist | Access before the declaration |
   |---|---|---|---|
   | `var` | Yes | Yes, to `undefined` | Gives `undefined` |
   | `let` | Yes | No | ReferenceError (Temporal Dead Zone) |
   | `const` | Yes | No | ReferenceError (Temporal Dead Zone) |
   | Function declaration | Yes | Yes, fully | Works normally |
   | Function expression | As a variable only | Follows `var`/`let` rules | TypeError or ReferenceError |
   | `class` | Yes | No | ReferenceError |

   A further point about scope: `var` is function-scoped, so it is hoisted to the top of the enclosing function, not the enclosing block. `let` and `const` are block-scoped.

   ```javascript
   function test() {
       if (true) {
           var a = 1;    // function-scoped
           let b = 2;    // block-scoped
       }
       console.log(a);   // 1
       console.log(b);   // ReferenceError: b is not defined
   }
   ```

   Practical advice: declare variables at the top of their scope and use `let` and `const` rather than `var`. Then hoisting never surprises anyone, which is exactly why `let` and `const` were introduced.
7. **Display element by id in JavaScript?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 762 (ET: N/A)]*


   Answer: An element is selected by its id with `document.getElementById()`.

   ```javascript
   var element = document.getElementById("demo");
   ```

   Displaying and changing its content:

   ```html
   <!DOCTYPE html>
   <html>
   <body>

     <p id="demo">Original text</p>
     <input type="text" id="username" value="Karim">
     <button onclick="show()">Show</button>

     <script>
     function show() {
         // read the element
         var p = document.getElementById("demo");

         // 1. change the HTML content
         p.innerHTML = "<b>New bold text</b>";

         // 2. change the plain text content (safer, tags are not interpreted)
         // p.textContent = "New plain text";

         // 3. read the value of an input element
         var name = document.getElementById("username").value;
         alert("Name is " + name);

         // 4. change the style
         p.style.color = "blue";
         p.style.fontSize = "20px";

         // 5. change an attribute
         p.setAttribute("title", "A tooltip");

         // 6. add or remove a CSS class
         p.classList.add("highlight");

         // 7. show the element itself in the console
         console.log(p);
     }
     </script>

   </body>
   </html>
   ```

   Which property to use for which purpose:

   | Property | Use |
   |---|---|
   | `innerHTML` | Read or write the content including HTML tags. Never assign untrusted user input to it, because that allows XSS |
   | `textContent` | Read or write plain text; tags are shown literally. The safe choice |
   | `innerText` | Like `textContent` but respects CSS visibility and is slower |
   | `value` | The content of an input, textarea or select element |

   Other ways of selecting elements:

   ```javascript
   document.getElementById("demo")            // one element, by id
   document.getElementsByClassName("item")    // an HTMLCollection, by class
   document.getElementsByTagName("p")         // an HTMLCollection, by tag
   document.querySelector("#demo")            // the first match for a CSS selector
   document.querySelectorAll(".item")         // a NodeList of all matches
   ```

   Two points that cause frequent errors:
   - `getElementById` takes the id without a `#`; `querySelector` takes a CSS selector, so it needs the `#`.
   - If the script runs before the element exists in the document, `getElementById` returns `null` and the next line throws "Cannot set property of null". The remedy is to place the script just before `</body>`, or to use `defer`, or to wrap the code in a `DOMContentLoaded` listener:

   ```javascript
   document.addEventListener("DOMContentLoaded", function () {
       document.getElementById("demo").textContent = "Ready";
   });
   ```
8. **if-else ব্যবহার করে Javascript দিয়ে নিচের কোডটি সম্পন্ন কর, যেন Output ডান পাশের মত আসে।** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 865 (ET: BUET)]*
```html
<html>
<body>
<script>
    for(var x=1;x<=9; x++) {
        if(x%2==0) {
            console.log(x+"is an even value.");
        }
        else{
            console.log(x+ "is an odd value.");
        }
    }
</script>
</body>
</html>
```


   Answer: কোডটি ইতিমধ্যে সম্পূর্ণ — এটি ১ থেকে ৯ পর্যন্ত প্রতিটি সংখ্যা জোড় না বিজোড় তা if-else দিয়ে যাচাই করে দেখায়।

   সম্পূর্ণ কোড:

   ```html
   <html>
   <body>
   <script>
       for (var x = 1; x <= 9; x++) {
           if (x % 2 == 0) {
               document.write(x + " is an even value.<br>");
           }
           else {
               document.write(x + " is an odd value.<br>");
           }
       }
   </script>
   </body>
   </html>
   ```

   Output:

   ```
   1 is an odd value.
   2 is an even value.
   3 is an odd value.
   4 is an even value.
   5 is an odd value.
   6 is an even value.
   7 is an odd value.
   8 is an even value.
   9 is an odd value.
   ```

   কোডটির ব্যাখ্যা:

   - `for (var x = 1; x <= 9; x++)` — লুপটি x এর মান ১ থেকে শুরু করে, প্রতিবার ১ করে বাড়িয়ে ৯ পর্যন্ত মোট ৯ বার চলে।
   - `x % 2` — modulus বা ভাগশেষ operator। কোনো সংখ্যাকে ২ দিয়ে ভাগ করলে ভাগশেষ ০ হলে সংখ্যাটি জোড়, ১ হলে বিজোড়।
   - `if (x % 2 == 0)` — শর্তটি সত্য হলে জোড়ের বার্তা, মিথ্যা হলে `else` অংশে বিজোড়ের বার্তা দেখানো হয়।

   `console.log` ও `document.write` এর পার্থক্য: `console.log` ব্রাউজারের developer console এ দেখায়, যা ব্যবহারকারী সাধারণত দেখেন না; `document.write` সরাসরি পৃষ্ঠায় লেখে। পরীক্ষার খাতায় আউটপুট পৃষ্ঠায় দেখাতে চাইলে `document.write` লেখা উচিত, এবং প্রতিটি লাইন আলাদা করতে `<br>` যোগ করতে হয়।

   একই কাজ আধুনিক রীতিতে, যেখানে ফলাফল একটি HTML element এ দেখানো হয়:

   ```html
   <html>
   <body>
     <p id="output"></p>
     <script>
       let result = "";
       for (let x = 1; x <= 9; x++) {
           if (x % 2 === 0) {
               result += x + " is an even value.<br>";
           } else {
               result += x + " is an odd value.<br>";
           }
       }
       document.getElementById("output").innerHTML = result;
     </script>
   </body>
   </html>
   ```

   এখানে দুটি উন্নতি করা হয়েছে: `var` এর বদলে `let` ব্যবহার করা হয়েছে, যা block-scoped; এবং `==` এর বদলে `===` ব্যবহার করা হয়েছে, যা মান ও ধরন — দুটোই মিলিয়ে দেখে, ফলে অপ্রত্যাশিত রূপান্তর ঘটে না।

## Web Services & APIs (SOAP vs REST) (7)

1. **What are SOAP and RESTful APIs in web services? State one main difference between SOAP and REST in terms of how they exchange data.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1426 (ET: E-Zone)]*


   Answer: SOAP and RESTful APIs in web services.

   SOAP, Simple Object Access Protocol, is a formal messaging protocol. Every message is an XML document with a fixed structure: an Envelope containing an optional Header and a mandatory Body. The service publishes a WSDL file that formally describes every operation, its parameters and its return type, so a client can be generated automatically from it.

   REST, Representational State Transfer, is not a protocol but an architectural style. A RESTful API exposes resources at URLs and uses the standard HTTP methods on them: GET to read, POST to create, PUT to replace, PATCH to update and DELETE to remove. The data is normally exchanged as JSON.

   One main difference in how they exchange data:

   SOAP must use XML, wrapped in a rigid SOAP Envelope, for every message. REST is not tied to any one format and normally uses JSON, sent as a plain HTTP body with no envelope at all. The consequence is that a SOAP message carrying a single value may run to several hundred bytes of markup, while the equivalent REST message is a few dozen bytes, so REST is markedly lighter and faster over the network.

   The same request in both styles:

   ```xml
   <!-- SOAP request -->
   POST /BankService HTTP/1.1
   Content-Type: text/xml; charset=utf-8
   SOAPAction: "getBalance"

   <?xml version="1.0"?>
   <soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
     <soap:Header>
       <auth:Credentials xmlns:auth="http://bank.com/auth">
         <auth:Token>abc123</auth:Token>
       </auth:Credentials>
     </soap:Header>
     <soap:Body>
       <getBalance xmlns="http://bank.com/">
         <accountNumber>1234567890</accountNumber>
       </getBalance>
     </soap:Body>
   </soap:Envelope>
   ```

   ```http
   # REST request
   GET /api/accounts/1234567890/balance HTTP/1.1
   Host: api.bank.com
   Authorization: Bearer abc123
   Accept: application/json
   ```

   ```json
   // REST response
   { "accountNumber": "1234567890", "balance": 45000.50, "currency": "BDT" }
   ```

   Full comparison:

   | Point | SOAP | REST |
   |---|---|---|
   | What it is | A protocol with a strict specification | An architectural style with a set of constraints |
   | Full form | Simple Object Access Protocol | Representational State Transfer |
   | Message format | XML only | JSON, XML, HTML, plain text or any format; JSON is usual |
   | Transport | HTTP, SMTP, TCP, JMS | HTTP and HTTPS only |
   | Message structure | Envelope with Header and Body, defined by the SOAP schema | A plain HTTP request and response |
   | Contract | Formal, published as a WSDL file | Informal, usually documented with OpenAPI or Swagger |
   | Bandwidth and speed | Heavy; the XML envelope adds a great deal of overhead | Light and fast |
   | State | Can be stateful or stateless | Stateless by definition |
   | Caching | Not cacheable | GET responses are cacheable |
   | Security | Built-in WS-Security, offering message-level encryption and signing | Relies on HTTPS, OAuth 2.0, JWT and API keys, which is transport-level |
   | Transactions | Supports ACID transactions through WS-AtomicTransaction | No built-in transaction support |
   | Error handling | Standard SOAP Fault element | HTTP status codes: 200, 201, 400, 401, 404, 500 |
   | Learning curve | Steep | Gentle |
   | Flexibility | Rigid; any change to the WSDL affects every client | Flexible; new fields can be added without breaking clients |
   | Suitable for | Banking, payment, telecom and enterprise systems needing guaranteed reliability and formal contracts | Web and mobile applications, public APIs, microservices |
   | Example | A bank's fund transfer service | The Twitter, Google Maps or Facebook Graph API |
2. **What is API?** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*


   Answer:    API stands for Application Programming Interface. It is a defined set of rules, functions and endpoints through which one piece of software talks to another. It states what requests can be made, in what format, and what response will come back, while hiding entirely how the work is done inside.

   The everyday analogy: an API is like a restaurant waiter. The customer does not enter the kitchen; he gives an order to the waiter, the waiter carries it to the kitchen and brings back the food. The customer needs to know only the menu, which is the API contract, not how the kitchen works.

   How it works, with a concrete case: a weather application on a phone does not measure the temperature itself. It sends a request to a weather service's API, and the service replies with the data.

   ```http
   GET https://api.weather.com/v1/current?city=Dhaka&key=YOUR_API_KEY
   ```

   ```json
   {
     "city": "Dhaka",
     "temperature": 32,
     "unit": "celsius",
     "humidity": 78,
     "condition": "Partly cloudy"
   }
   ```

   The application takes that response and displays it. It never learns where the weather stations are or how the forecast is computed.

   Types of API:
   - Web API or REST API: accessed over HTTP, for example a weather service or a payment gateway.
   - Library or framework API: the set of functions a library exposes, such as `Math.random()` in JavaScript.
   - Operating system API: system calls such as `open()`, `read()` and `write()` on Linux, and the Win32 API on Windows.
   - Database API: JDBC and ODBC, through which a program queries a database.
   - Hardware API: device drivers that let software use a printer or a camera.

   By openness: public or open APIs, available to anyone; partner APIs, given to selected business partners; internal or private APIs, used only inside an organisation; and composite APIs, which combine several calls into one.

   Why APIs matter:
   - Reuse: a developer need not build a payment system, a map or a translation engine; he calls an existing one.
   - Abstraction: the caller works with a simple interface and is shielded from the complexity behind it.
   - Integration: separate systems, written in different languages by different companies, can work together.
   - Independent change: as long as the interface stays the same, the provider can rewrite the implementation entirely.
   - Security: the API controls exactly what a caller can see and do; direct access to the database is never given.
   - Speed of development, which is why almost every modern application is assembled largely from APIs.

   Familiar examples in daily use: Google Maps embedded in a delivery app, "Log in with Google" or "Log in with Facebook", bKash and SSLCOMMERZ payment APIs, an SMS gateway API, and the ChatGPT API.
3. **What is an API?** *[BBA Assistant Programmer 12.07.2025 compact it 1432 (ET: BUET)]*


   Answer:    API stands for Application Programming Interface. It is a defined set of rules, functions and endpoints through which one piece of software talks to another. It states what requests can be made, in what format, and what response will come back, while hiding entirely how the work is done inside.

   The everyday analogy: an API is like a restaurant waiter. The customer does not enter the kitchen; he gives an order to the waiter, the waiter carries it to the kitchen and brings back the food. The customer needs to know only the menu, which is the API contract, not how the kitchen works.

   An example that shows the contract clearly. A REST API for a student record system might publish these endpoints:

   | Method and endpoint | What it does |
   |---|---|
   | `GET /api/students` | Return the list of all students |
   | `GET /api/students/101` | Return the student whose id is 101 |
   | `POST /api/students` | Create a new student from the JSON body |
   | `PUT /api/students/101` | Replace the record of student 101 |
   | `DELETE /api/students/101` | Delete student 101 |

   ```json
   // GET /api/students/101  →  200 OK
   {
     "id": 101,
     "name": "Karim Rahman",
     "department": "CSE",
     "cgpa": 3.75
   }
   ```

   The caller needs to know only these URLs and this JSON shape. Whether the data sits in MySQL or MongoDB, and whether the service is written in Java or Python, is invisible and can be changed at any time.

   Types of API:
   - Web API or REST API: accessed over HTTP, for example a weather service or a payment gateway.
   - Library or framework API: the set of functions a library exposes, such as `Math.random()` in JavaScript.
   - Operating system API: system calls such as `open()`, `read()` and `write()` on Linux, and the Win32 API on Windows.
   - Database API: JDBC and ODBC, through which a program queries a database.
   - Hardware API: device drivers that let software use a printer or a camera.

   By openness: public or open APIs, available to anyone; partner APIs, given to selected business partners; internal or private APIs, used only inside an organisation; and composite APIs, which combine several calls into one.

   Key benefits: reuse of existing services, abstraction of complexity, integration between systems built by different organisations, controlled and auditable access to data, and much faster development.
4. **Write difference between REST API and SOAP API.** *[BKSP Assistant Programmer 13.07.2024 compact it 1460 (ET: N/A)]*


   Answer: Difference between REST API and SOAP API.

   | Point | SOAP | REST |
   |---|---|---|
   | What it is | A protocol with a strict specification | An architectural style with a set of constraints |
   | Full form | Simple Object Access Protocol | Representational State Transfer |
   | Message format | XML only | JSON, XML, HTML, plain text or any format; JSON is usual |
   | Transport | HTTP, SMTP, TCP, JMS | HTTP and HTTPS only |
   | Message structure | Envelope with Header and Body, defined by the SOAP schema | A plain HTTP request and response |
   | Contract | Formal, published as a WSDL file | Informal, usually documented with OpenAPI or Swagger |
   | Bandwidth and speed | Heavy; the XML envelope adds a great deal of overhead | Light and fast |
   | State | Can be stateful or stateless | Stateless by definition |
   | Caching | Not cacheable | GET responses are cacheable |
   | Security | Built-in WS-Security, offering message-level encryption and signing | Relies on HTTPS, OAuth 2.0, JWT and API keys, which is transport-level |
   | Transactions | Supports ACID transactions through WS-AtomicTransaction | No built-in transaction support |
   | Error handling | Standard SOAP Fault element | HTTP status codes: 200, 201, 400, 401, 404, 500 |
   | Learning curve | Steep | Gentle |
   | Flexibility | Rigid; any change to the WSDL affects every client | Flexible; new fields can be added without breaking clients |
   | Suitable for | Banking, payment, telecom and enterprise systems needing guaranteed reliability and formal contracts | Web and mobile applications, public APIs, microservices |
   | Example | A bank's fund transfer service | The Twitter, Google Maps or Facebook Graph API |

   The six architectural constraints that make an API RESTful:
   - Client-server: the interface separates the client from the data storage.
   - Stateless: every request carries all the information needed; the server keeps no session.
   - Cacheable: responses declare whether they may be cached.
   - Uniform interface: resources are identified by URLs and manipulated through the standard HTTP methods.
   - Layered system: the client cannot tell whether it is connected to the end server or to an intermediary.
   - Code on demand, optional: the server may send executable code.

   When to choose which:
   - Choose SOAP where a formal contract, message-level security, guaranteed delivery or distributed transactions are required. Interbank transfers, telecom provisioning and government-to-government exchanges are typical.
   - Choose REST for public APIs, mobile and web front ends, and microservices, where speed, simplicity and low bandwidth matter more than formal guarantees. This is the default for new work.
   - GraphQL and gRPC are the newer alternatives: GraphQL lets the client ask for exactly the fields it needs in one request, and gRPC uses binary Protocol Buffers over HTTP/2 for very fast internal service-to-service calls.
5. **What is API? Explain with example.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*


   Answer:    API stands for Application Programming Interface. It is a defined set of rules, functions and endpoints through which one piece of software talks to another. It states what requests can be made, in what format, and what response will come back, while hiding entirely how the work is done inside.

   The everyday analogy: an API is like a restaurant waiter. The customer does not enter the kitchen; he gives an order to the waiter, the waiter carries it to the kitchen and brings back the food. The customer needs to know only the menu, which is the API contract, not how the kitchen works.

   Example 1 — a payment gateway API. An online shop does not process card payments itself. It calls the gateway's API:

   ```http
   POST https://api.sslcommerz.com/v3/payment
   Content-Type: application/json
   Authorization: Bearer STORE_API_KEY

   {
     "store_id": "shop123",
     "amount": 2500.00,
     "currency": "BDT",
     "tran_id": "ORD-90871",
     "success_url": "https://myshop.com/success",
     "fail_url": "https://myshop.com/fail"
   }
   ```

   ```json
   {
     "status": "SUCCESS",
     "sessionkey": "F7A2C91B3D",
     "GatewayPageURL": "https://securepay.sslcommerz.com/gwprocess/v4/F7A2C91B3D"
   }
   ```

   The shop redirects the customer to that page. It never touches the card number, which is precisely why using the API is safer and cheaper than building the payment system.

   Example 2 — a library API inside a program. Every function a library exposes is an API:

   ```javascript
   Math.max(5, 9, 3);              // 9
   JSON.parse('{"a":1}');          // { a: 1 }
   document.getElementById("x");   // the DOM API
   ```

   The caller uses `Math.max` without knowing how the comparison is implemented.

   Example 3 — a REST API for a student record system:

   | Method and endpoint | What it does |
   |---|---|
   | `GET /api/students` | Return all students |
   | `GET /api/students/101` | Return student 101 |
   | `POST /api/students` | Create a student |
   | `PUT /api/students/101` | Replace student 101 |
   | `DELETE /api/students/101` | Delete student 101 |

   Types of API:
   - Web API or REST API: accessed over HTTP, for example a weather service or a payment gateway.
   - Library or framework API: the set of functions a library exposes, such as `Math.random()` in JavaScript.
   - Operating system API: system calls such as `open()`, `read()` and `write()` on Linux, and the Win32 API on Windows.
   - Database API: JDBC and ODBC, through which a program queries a database.
   - Hardware API: device drivers that let software use a printer or a camera.

   By openness: public or open APIs, available to anyone; partner APIs, given to selected business partners; internal or private APIs, used only inside an organisation; and composite APIs, which combine several calls into one.

   Advantages: reuse of ready-made services, abstraction of internal complexity, integration between systems written in different languages, freedom to change the implementation without breaking callers, controlled and auditable access to data instead of direct database access, and much faster development.
6. **What is the two prime advantages of RESTful API?** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 756 (ET: N/A)]*


   Answer: The two prime advantages of a RESTful API are statelessness, which gives scalability, and the uniform interface, which gives simplicity and wide interoperability.

   1. Statelessness, and therefore scalability

   Every request carries all the information the server needs, and the server stores nothing about the client between requests. The consequences are the decisive practical advantages:
   - Any server in a farm can serve any request, so a load balancer can send traffic anywhere. Adding capacity is simply a matter of adding servers, which is horizontal scaling.
   - No server memory is consumed per connected client, so one machine serves far more users.
   - If a server crashes, nothing is lost; the client simply repeats the request against another server.
   - Responses to GET are cacheable, at the browser, at a proxy and at a CDN, which removes load from the server entirely.

   2. Uniform interface, and therefore simplicity and interoperability

   A RESTful API exposes resources at URLs and acts on them with the standard HTTP methods, using standard status codes and normally JSON.
   - Any client that speaks HTTP can use it: a browser, a mobile application, a desktop program, another server, or a command-line tool. No special library and no generated stub is needed.
   - The API is largely self-explanatory. `GET /api/students/101` needs no documentation to be understood, whereas a SOAP operation name does.
   - The same back end serves a web front end, an Android app and an iOS app, so the business logic is written once.
   - JSON is light, so requests and responses are small, which matters greatly on mobile networks.
   - It is language-independent: the server may be in Java and the client in JavaScript, and neither needs to know.

   Further advantages worth listing if the question allows more than two: it is lightweight compared with SOAP's XML envelopes; the layered architecture allows proxies, gateways and caches to be inserted transparently; it evolves easily, since new fields can be added without breaking existing clients; and it is the natural fit for a microservices architecture.
7. **What is API?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 865 (ET: BUET)]*


   Answer:    API stands for Application Programming Interface. It is a defined set of rules, functions and endpoints through which one piece of software talks to another. It states what requests can be made, in what format, and what response will come back, while hiding entirely how the work is done inside.

   The everyday analogy: an API is like a restaurant waiter. The customer does not enter the kitchen; he gives an order to the waiter, the waiter carries it to the kitchen and brings back the food. The customer needs to know only the menu, which is the API contract, not how the kitchen works.

   A concrete example: a shopping application shows the delivery route on a map. It does not draw the map itself; it calls the Google Maps API with the two addresses and receives back the route, which it then displays.

   Types of API:
   - Web API or REST API: accessed over HTTP, for example a weather service or a payment gateway.
   - Library or framework API: the set of functions a library exposes, such as `Math.random()` in JavaScript.
   - Operating system API: system calls such as `open()`, `read()` and `write()` on Linux, and the Win32 API on Windows.
   - Database API: JDBC and ODBC, through which a program queries a database.
   - Hardware API: device drivers that let software use a printer or a camera.

   By openness: public or open APIs, available to anyone; partner APIs, given to selected business partners; internal or private APIs, used only inside an organisation; and composite APIs, which combine several calls into one.

   Why APIs are used: they let a developer reuse an existing service instead of rebuilding it, hide complexity behind a simple interface, allow systems written in different languages by different organisations to work together, and give controlled, auditable access to data without exposing the database.

## Full Stack & Backend Web Development (5)

1. **Write appropriate program client and database using any language and a login page using ID and password. [Approximate Web page login code]** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 320 (ET: N/A)]*


   Answer: A complete login system with a client page, server-side code and a database, written in PHP with MySQL.

   1. Database — create the table

   ```sql
   CREATE DATABASE bankdb;
   USE bankdb;

   CREATE TABLE users (
       id           INT AUTO_INCREMENT PRIMARY KEY,
       username     VARCHAR(50)  NOT NULL UNIQUE,
       password     VARCHAR(255) NOT NULL,      -- stores a bcrypt hash, never plain text
       full_name    VARCHAR(100),
       email        VARCHAR(100) UNIQUE,
       role         VARCHAR(20)  DEFAULT 'user',
       failed_count INT          DEFAULT 0,
       is_locked    TINYINT(1)   DEFAULT 0,
       last_login   DATETIME,
       created_at   TIMESTAMP    DEFAULT CURRENT_TIMESTAMP
   );
   ```

   2. Client — the login page, `login.html`

   ```html
   <!DOCTYPE html>
   <html>
   <head>
     <meta charset="UTF-8">
     <title>Login</title>
     <style>
       body  { font-family: Arial, sans-serif; background: #f0f0f0; }
       .box  { width: 320px; margin: 80px auto; background: #fff;
               padding: 25px; border-radius: 6px; box-shadow: 0 0 10px #ccc; }
       h2    { text-align: center; }
       input[type=text], input[type=password] {
               width: 100%; padding: 10px; margin: 6px 0 14px 0; box-sizing: border-box; }
       button { width: 100%; padding: 10px; background: #1a73e8;
                color: #fff; border: none; cursor: pointer; }
       .error { color: red; font-size: 13px; }
     </style>
   </head>
   <body>

     <div class="box">
       <h2>User Login</h2>
       <form id="loginForm" action="login.php" method="post">
         <label for="username">Username</label>
         <input type="text" id="username" name="username" required>

         <label for="password">Password</label>
         <input type="password" id="password" name="password" required>

         <button type="submit">Login</button>
         <p id="msg" class="error"></p>
       </form>
     </div>

     <script>
     document.getElementById("loginForm").addEventListener("submit", function (e) {
         var u = document.getElementById("username").value.trim();
         var p = document.getElementById("password").value;

         if (u === "" || p === "") {
             e.preventDefault();
             document.getElementById("msg").textContent = "Both fields are required";
             return;
         }
         if (p.length < 8) {
             e.preventDefault();
             document.getElementById("msg").textContent = "Password must be at least 8 characters";
         }
     });
     </script>

   </body>
   </html>
   ```

   3. Server — `db.php`, the database connection

   ```php
   <?php
   $host = "localhost";
   $user = "root";
   $pass = "";
   $db   = "bankdb";

   $conn = new mysqli($host, $user, $pass, $db);

   if ($conn->connect_error) {
       die("Connection failed: " . $conn->connect_error);
   }
   $conn->set_charset("utf8mb4");
   ?>
   ```

   4. Server — `login.php`, which checks the credentials

   ```php
   <?php
   session_start();
   require 'db.php';

   if ($_SERVER["REQUEST_METHOD"] !== "POST") {
       header("Location: login.html");
       exit();
   }

   $username = trim($_POST['username']);
   $password = $_POST['password'];

   if ($username === "" || $password === "") {
       header("Location: login.html?error=empty");
       exit();
   }

   // prepared statement: prevents SQL injection
   $stmt = $conn->prepare("SELECT id, username, password, full_name, role, is_locked
                           FROM users WHERE username = ?");
   $stmt->bind_param("s", $username);
   $stmt->execute();
   $result = $stmt->get_result();

   if ($result->num_rows === 1) {
       $row = $result->fetch_assoc();

       if ($row['is_locked'] == 1) {
           header("Location: login.html?error=locked");
           exit();
       }

       // verify the password against the stored bcrypt hash
       if (password_verify($password, $row['password'])) {

           // prevent session fixation
           session_regenerate_id(true);

           $_SESSION['user_id']   = $row['id'];
           $_SESSION['username']  = $row['username'];
           $_SESSION['full_name'] = $row['full_name'];
           $_SESSION['role']      = $row['role'];

           $upd = $conn->prepare("UPDATE users SET last_login = NOW(), failed_count = 0 WHERE id = ?");
           $upd->bind_param("i", $row['id']);
           $upd->execute();

           header("Location: dashboard.php");
           exit();
       }
   }

   // same generic message whether the user does not exist or the password is wrong,
   // so that an attacker cannot discover which usernames are valid
   $upd = $conn->prepare("UPDATE users SET failed_count = failed_count + 1,
                          is_locked = IF(failed_count + 1 >= 5, 1, 0) WHERE username = ?");
   $upd->bind_param("s", $username);
   $upd->execute();

   header("Location: login.html?error=invalid");
   exit();
   ?>
   ```

   5. Server — `dashboard.php`, the protected page

   ```php
   <?php
   session_start();

   // anyone not logged in is sent back
   if (!isset($_SESSION['user_id'])) {
       header("Location: login.html");
       exit();
   }
   ?>
   <!DOCTYPE html>
   <html>
   <head><meta charset="UTF-8"><title>Dashboard</title></head>
   <body>
     <h2>Welcome, <?php echo htmlspecialchars($_SESSION['full_name']); ?></h2>
     <p>Role: <?php echo htmlspecialchars($_SESSION['role']); ?></p>
     <a href="logout.php">Logout</a>
   </body>
   </html>
   ```

   6. Server — `logout.php`

   ```php
   <?php
   session_start();
   $_SESSION = array();
   session_destroy();
   header("Location: login.html");
   exit();
   ?>
   ```

   7. Creating a user with a hashed password

   ```php
   <?php
   require 'db.php';
   $hash = password_hash("MyStrongPass123", PASSWORD_BCRYPT);
   $stmt = $conn->prepare("INSERT INTO users (username, password, full_name, email)
                           VALUES (?, ?, ?, ?)");
   $stmt->bind_param("ssss", $u, $hash, $n, $e);
   $u = "karim"; $n = "Karim Rahman"; $e = "karim@example.com";
   $stmt->execute();
   ?>
   ```

   Security measures built into this code, which must be stated in the answer:
   - Prepared statements with bound parameters, so SQL injection is impossible. Building the query by concatenating `$_POST` values is the classic fatal error.
   - `password_hash()` and `password_verify()` with bcrypt, so the database never holds a plain-text or reversibly encrypted password.
   - `session_regenerate_id(true)` immediately after a successful login, which defeats session fixation.
   - A single generic error message for both "no such user" and "wrong password", so usernames cannot be enumerated.
   - Account lock after five failed attempts, which blocks brute force.
   - `htmlspecialchars()` on every value printed into the page, which prevents cross-site scripting.
   - Client-side validation for convenience, with the real validation always repeated on the server.
   - In production, HTTPS is mandatory, and the session cookie must carry `HttpOnly`, `Secure` and `SameSite`.
2. **(খ) Client-side scripting এর তুলনায় Server-side scripting এর সুবিধাগুলো কী কী?** *[Software Assistant Programmer 13.10.2022 compact it 709 (ET: N/A)]*


   Answer: Server-side scripting এর সুবিধাসমূহ, client-side scripting এর তুলনায়:

   - নিরাপত্তা: কোডটি সার্ভারে চলে এবং ব্যবহারকারী তা কখনো দেখতে পান না। ব্রাউজারে কেবল ফলাফল পৌঁছায়। ফলে ব্যবসায়িক যুক্তি, ডেটাবেজের গঠন, পাসওয়ার্ড ও API key গোপন থাকে। Client-side script এর সব কোড ব্যবহারকারী "View Source" দিয়ে পড়তে পারেন, তাই সেখানে কোনো গোপন তথ্য রাখা যায় না।

   - Database এর সঙ্গে সরাসরি সংযোগ: কেবল সার্ভার-সাইড কোডই ডেটাবেজে সংযোগ করে তথ্য পড়তে, লিখতে ও পরিবর্তন করতে পারে। Client-side script কখনো সরাসরি ডেটাবেজে যেতে পারে না এবং যাওয়া উচিতও নয়।

   - বিশ্বাসযোগ্য যাচাইকরণ: ব্যবহারকারী JavaScript বন্ধ করে দিতে পারেন, ব্রাউজারের developer tool দিয়ে কোড বদলে দিতে পারেন, বা সরাসরি অনুরোধ পাঠাতে পারেন। তাই client-side validation কেবল সুবিধার জন্য; প্রকৃত যাচাইকরণ সবসময় সার্ভারে করতে হয়।

   - ব্রাউজার-নিরপেক্ষতা: সার্ভার-সাইড কোড সব ব্রাউজারে একই ফল দেয়, কারণ ব্রাউজার কেবল তৈরি করা HTML পায়। Client-side script বিভিন্ন ব্রাউজার ও সংস্করণে ভিন্ন আচরণ করতে পারে, এবং ব্যবহারকারী তা বন্ধ করে দিলে কাজ করে না।

   - ব্যবহারকারীর যন্ত্রের ওপর নির্ভরতা নেই: ভারী গণনা, বড় ডেটা প্রক্রিয়াকরণ, ছবি রূপান্তর বা প্রতিবেদন তৈরি সার্ভারের শক্তিশালী হার্ডওয়্যারে হয়। পুরনো বা দুর্বল মোবাইলেও সাইটটি সমান দ্রুত চলে।

   - Session ও authentication ব্যবস্থাপনা: লগইন, ব্যবহারকারীর পরিচয় ও অনুমতি নিরাপদে কেবল সার্ভারেই রাখা সম্ভব। ভূমিকা বা অধিকার client-side এ রাখলে ব্যবহারকারী তা বদলে ফেলতে পারেন।

   - ফাইল ব্যবস্থাপনা: সার্ভারে ফাইল তৈরি, পড়া, লেখা, মুছে ফেলা ও আপলোড গ্রহণ কেবল সার্ভার-সাইড কোড দিয়েই সম্ভব।

   - Dynamic content তৈরি: ডেটাবেজ থেকে তথ্য নিয়ে প্রতিটি ব্যবহারকারীর জন্য আলাদা পৃষ্ঠা তৈরি করা যায়।

   - ইমেইল ও বাইরের সেবা: ইমেইল পাঠানো, এসএমএস গেটওয়ে, পেমেন্ট গেটওয়ে ও তৃতীয় পক্ষের API এর গোপন key ব্যবহার করে যোগাযোগ — সবই সার্ভারে করতে হয়।

   - SEO সুবিধা: সার্ভারে তৈরি সম্পূর্ণ HTML search engine সহজে পড়তে পারে। কেবল JavaScript দিয়ে তৈরি বিষয়বস্তু search engine সবসময় ঠিকভাবে পড়তে পারে না।

   - কেন্দ্রীভূত হালনাগাদ: সার্ভারের কোড একবার বদলালেই সব ব্যবহারকারী সঙ্গে সঙ্গে নতুন সংস্করণ পান। কোনো কিছু আবার বিতরণ করতে হয় না।

   - উন্নত ত্রুটি নিয়ন্ত্রণ ও লগ: সব ত্রুটি সার্ভারে নথিভুক্ত হয় এবং ব্যবহারকারীকে কেবল সাধারণ বার্তা দেখানো হয়, যাতে ভেতরের তথ্য ফাঁস না হয়।

   Client-side scripting এর যেসব সুবিধা সার্ভার-সাইডে নেই, যা তুলনার জন্য উল্লেখ করা উচিত:
   - তাৎক্ষণিক প্রতিক্রিয়া, কারণ সার্ভারে যাওয়া-আসার বিলম্ব নেই।
   - সার্ভারের ওপর চাপ কম।
   - পৃষ্ঠা পুনরায় লোড না করেই অংশবিশেষ পরিবর্তন করা যায়।
   - নেটওয়ার্কের ব্যবহার কম।

   বাস্তব সিদ্ধান্ত: দুটোই একসঙ্গে ব্যবহার করা হয়। তাৎক্ষণিক প্রতিক্রিয়া ও মিথস্ক্রিয়ার জন্য client-side, আর নিরাপত্তা, ডেটা ও প্রকৃত যাচাইকরণের জন্য server-side। মূল নিয়মটি হলো — client-side যাচাইকরণ ব্যবহারকারীর সুবিধার জন্য, server-side যাচাইকরণ নিরাপত্তার জন্য; দ্বিতীয়টি কখনো বাদ দেওয়া যাবে না।
3. **(খ) PHP কি? Web Development এ Java Script এর প্রয়োজনীয়তা সম্পর্কে বিবরণ দিন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 771 (ET: N/A)]*


   Answer: PHP এবং Web Development এ JavaScript এর প্রয়োজনীয়তা।

   PHP কী: PHP এর পূর্ণরূপ PHP: Hypertext Preprocessor, যা একটি recursive acronym; আগে এর অর্থ ছিল Personal Home Page। এটি একটি open-source server-side scripting ভাষা, যা মূলত dynamic ওয়েব পৃষ্ঠা তৈরির জন্য ব্যবহৃত হয়। ১৯৯৪ সালে Rasmus Lerdorf এটি তৈরি করেন।

   PHP এর বৈশিষ্ট্য:
   - এটি সার্ভারে চলে; ব্রাউজারে কেবল তৈরি হওয়া HTML পৌঁছায়, PHP কোড নয়।
   - HTML এর ভেতরে সরাসরি লেখা যায়, `<?php ... ?>` চিহ্নের মধ্যে।
   - ফাইলের বর্ধিতাংশ `.php`।
   - এটি loosely typed — চলকের ধরন আগে ঘোষণা করতে হয় না; চলকের নাম `$` দিয়ে শুরু হয়।
   - Open source ও বিনামূল্যে; Windows, Linux, macOS — সব প্ল্যাটফর্মে চলে।
   - MySQL, PostgreSQL, Oracle, MongoDB — সব ডেটাবেজের সঙ্গে কাজ করে।
   - Apache ও Nginx সার্ভারে চলে।

   ```php
   <!DOCTYPE html>
   <html>
   <body>
     <h1><?php echo "Hello, World!"; ?></h1>
     <?php
       $name = "Karim";
       $marks = 85;
       if ($marks >= 80) {
           echo "<p>$name has got grade A+</p>";
       } else {
           echo "<p>$name has got a lower grade</p>";
       }
     ?>
   </body>
   </html>
   ```

   PHP এর ব্যবহার: ফর্মের তথ্য গ্রহণ ও প্রক্রিয়াকরণ, ডেটাবেজের সঙ্গে কাজ, লগইন ও session ব্যবস্থাপনা, ফাইল আপলোড, ইমেইল পাঠানো, cookie নিয়ন্ত্রণ, এবং dynamic পৃষ্ঠা তৈরি। WordPress, Facebook এর প্রাথমিক সংস্করণ, Wikipedia ও Laravel — সবই PHP ভিত্তিক। জনপ্রিয় framework: Laravel, CodeIgniter, Symfony, CakePHP।

   Web Development এ JavaScript এর প্রয়োজনীয়তা:

   JavaScript হলো ব্রাউজারে চলা প্রধান প্রোগ্রামিং ভাষা, যা ওয়েব পৃষ্ঠাকে স্থির নথি থেকে সক্রিয় প্রয়োগে রূপান্তরিত করে। HTML গঠন দেয়, CSS সাজসজ্জা দেয়, আর JavaScript আচরণ দেয়।

   - মিথস্ক্রিয়া তৈরি: বোতামে ক্লিক, মেনু খোলা, ছবি স্লাইড হওয়া, ট্যাব বদলানো, accordion খোলা-বন্ধ — সবই JavaScript দিয়ে হয়।

   - DOM পরিবর্তন: পৃষ্ঠা পুনরায় লোড না করেই যেকোনো element এর লেখা, রং, আকার বা অবস্থান বদলানো যায়, নতুন element যোগ বা মুছে ফেলা যায়।

   - তাৎক্ষণিক ফর্ম যাচাইকরণ: ব্যবহারকারী টাইপ করার সঙ্গে সঙ্গেই ভুল ধরিয়ে দেওয়া যায়, সার্ভারে যাওয়ার আগেই। এতে ব্যবহারকারীর সময় বাঁচে এবং সার্ভারের ওপর অপ্রয়োজনীয় চাপ কমে।

   - AJAX ও Fetch API: পৃষ্ঠা পুনরায় লোড না করেই সার্ভার থেকে তথ্য এনে পৃষ্ঠার অংশবিশেষ হালনাগাদ করা যায়। লাইভ অনুসন্ধানের পরামর্শ, চ্যাট, বিজ্ঞপ্তি, অবিরাম স্ক্রল — সবই এভাবে কাজ করে।

   - Single Page Application তৈরি: React, Angular ও Vue এর মাধ্যমে সম্পূর্ণ অ্যাপ্লিকেশন তৈরি করা যায়, যা ডেস্কটপ সফটওয়্যারের মতো আচরণ করে।

   - Animation ও দৃশ্যগত প্রভাব: CSS এর সীমার বাইরের জটিল অ্যানিমেশন, ক্যানভাসে আঁকা ও গ্রাফ তৈরি।

   - Client-side storage: `localStorage` ও `sessionStorage` তে তথ্য রেখে ব্যবহারকারীর পছন্দ মনে রাখা।

   - Browser API ব্যবহার: অবস্থান নির্ণয় (Geolocation), ক্যামেরা ও মাইক্রোফোন, বিজ্ঞপ্তি, ফাইল পড়া, drag and drop।

   - Server-side ব্যবহার: Node.js এর মাধ্যমে JavaScript এখন সার্ভারেও চলে, ফলে একই ভাষায় সম্পূর্ণ full-stack অ্যাপ্লিকেশন লেখা যায়।

   - মোবাইল ও ডেস্কটপ অ্যাপ: React Native ও Electron দিয়ে একই কোড থেকে মোবাইল ও ডেস্কটপ অ্যাপ তৈরি করা যায়।

   PHP ও JavaScript এর তুলনা:

   | বিষয় | PHP | JavaScript |
   |---|---|---|
   | কোথায় চলে | সার্ভারে | ব্রাউজারে; Node.js হলে সার্ভারেও |
   | ব্যবহারকারী কোড দেখতে পান | না | হ্যাঁ, ব্রাউজারে চললে |
   | Database সংযোগ | সরাসরি | সরাসরি নয়; API এর মাধ্যমে |
   | পৃষ্ঠা পুনরায় লোড | সাধারণত প্রয়োজন হয় | প্রয়োজন হয় না |
   | প্রধান কাজ | ডেটা প্রক্রিয়াকরণ ও পৃষ্ঠা তৈরি | ব্যবহারকারীর সঙ্গে মিথস্ক্রিয়া |
   | নিরাপত্তা | গোপন তথ্য রাখা নিরাপদ | কখনোই গোপন তথ্য রাখা যাবে না |

   সিদ্ধান্ত: দুটি ভাষা প্রতিদ্বন্দ্বী নয়, পরিপূরক। PHP সার্ভারে তথ্য প্রক্রিয়াকরণ ও নিরাপত্তার কাজ করে; JavaScript ব্রাউজারে ব্যবহারকারীর অভিজ্ঞতা তৈরি করে। একটি আধুনিক ওয়েব অ্যাপ্লিকেশনে দুটোই প্রয়োজন।
4. **(b) What are the resources you need to access a web enabled application?** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 796 (ET: N/A)]*


   Answer: Resources needed to access a web-enabled application.

   Hardware
   - A client device: a desktop computer, laptop, tablet or smartphone, with enough processor, memory and storage to run a modern browser.
   - A network interface: an Ethernet card, Wi-Fi adapter or mobile data modem.
   - Input and output devices: keyboard, mouse or touch screen, and a display.
   - For the provider: a server with adequate CPU, RAM and disk, plus a UPS and cooling.

   Network connectivity
   - An internet connection through an ISP, of sufficient bandwidth for the application. A dashboard needs little; a video application needs a great deal.
   - For an internal application, a LAN or an intranet connection, possibly over a VPN.
   - Networking equipment along the way: router, switch, modem, access point.
   - A DNS service, to translate the domain name into an IP address.
   - An IP address for the client, obtained by DHCP or set statically.

   Software on the client
   - An operating system: Windows, Linux, macOS, Android or iOS.
   - A web browser: Chrome, Firefox, Edge or Safari, of a version the application supports.
   - JavaScript enabled, and cookies allowed, since almost every application depends on both.
   - Any required plug-in or runtime, such as a PDF viewer for reports.
   - Up-to-date TLS support, so that the HTTPS connection can be established.

   Server-side resources, which the provider must have
   - A web server: Apache, Nginx or IIS.
   - An application server or runtime: PHP, Node.js, Tomcat, .NET.
   - A database server: MySQL, PostgreSQL, Oracle, SQL Server or MongoDB.
   - Hosting: a physical server, a virtual private server, or cloud infrastructure.
   - A domain name, and an SSL/TLS certificate.
   - Backup storage and a monitoring system.

   Access credentials and authorisation
   - The URL of the application.
   - A user account: username and password, and increasingly a second factor such as an OTP or an authenticator app.
   - The correct role or permission, since authentication only proves identity while authorisation decides what may be done.
   - For an internal application, being on the permitted network or connected through the VPN, and sometimes a client certificate or a registered device.

   Security requirements
   - HTTPS, so that credentials and data are encrypted in transit.
   - Antivirus and a firewall on the client.
   - An operating system and browser that are patched, since an out-of-date browser may be blocked by the server for lacking modern TLS.

   Human and organisational resources
   - A user who knows how to operate the application, which usually means some training.
   - User documentation and a help desk.
   - An administrator to create accounts and assign roles.
   - Technical support for problems.

   Summarised as the minimum a single user needs: a device, an internet connection, a modern browser, the URL, and valid credentials with the right permissions.
5. **Apache কোন ধরনের Server এক কথায় লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 866 (ET: BUET)]*


   Answer: Apache একটি Web Server, নির্দিষ্টভাবে বললে HTTP Server।

   এর সম্পূর্ণ নাম Apache HTTP Server, যা সংক্ষেপে httpd নামে পরিচিত। এটি Apache Software Foundation এর তৈরি একটি open-source, বিনামূল্যের সফটওয়্যার, যা ১৯৯৫ সালে প্রকাশিত হয় এবং দীর্ঘকাল বিশ্বের সবচেয়ে বেশি ব্যবহৃত ওয়েব সার্ভার ছিল।

   কাজ: এটি ক্লায়েন্টের HTTP অনুরোধ গ্রহণ করে, প্রয়োজনীয় ফাইল বা তৈরি করা পৃষ্ঠা খুঁজে বের করে এবং HTTP response আকারে ব্রাউজারে ফেরত পাঠায়।

   বৈশিষ্ট্য:
   - Cross-platform — Linux, Windows, macOS ও Unix এ চলে।
   - Module ভিত্তিক গঠন, যেমন `mod_rewrite` URL পুনর্লিখনের জন্য, `mod_ssl` HTTPS এর জন্য, `mod_php` PHP চালানোর জন্য।
   - Virtual hosting — একটি সার্ভারেই একাধিক ওয়েবসাইট চালানো যায়।
   - `.htaccess` ফাইলের মাধ্যমে ডিরেক্টরিভিত্তিক নিয়ন্ত্রণ।
   - LAMP stack এর "A" — Linux, Apache, MySQL, PHP।

   অন্যান্য ওয়েব সার্ভার: Nginx, Microsoft IIS, LiteSpeed, Caddy ও Node.js এর নিজস্ব সার্ভার।

   একটি বিভ্রান্তি এড়ানো দরকার: Apache Software Foundation এর অধীনে আরও অনেক প্রকল্প আছে — Apache Tomcat একটি Java servlet container বা application server; Apache Hadoop একটি বড় ডেটা প্রক্রিয়াকরণ কাঠামো; Apache Kafka একটি বার্তা প্রবাহ ব্যবস্থা। কেবল "Apache" বললে বোঝায় Apache HTTP Server।

## CSS & Styling (Inline, Internal, External) (4)

1. **(ক) CSS কী? CSS এর প্রকারভেদসমূহ উদাহরণসহ আলোচনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 411 (ET: N/A)]*


   Answer:    CSS এর পূর্ণরূপ Cascading Style Sheets। এটি একটি style sheet ভাষা, যা দিয়ে HTML নথির উপস্থাপন ও সাজসজ্জা নির্ধারণ করা হয় — রং, ফন্ট, আকার, ব্যবধান, সীমানা, অবস্থান ও সমগ্র বিন্যাস।

   HTML বলে "এটি একটি শিরোনাম"; CSS বলে "শিরোনামটি নীল রঙের, ২৪ পিক্সেল আকারের এবং মাঝখানে থাকবে"। এভাবে গঠন ও উপস্থাপন পৃথক রাখাকে বলে separation of concerns।

   CSS এর গঠন:

   ```
   selector {
       property: value;
       property: value;
   }
   ```

   ```css
   h1 {
       color: navy;
       font-size: 28px;
       text-align: center;
   }
   ```

   এখানে `h1` হলো selector, `color` ও `font-size` হলো property, আর `navy` ও `28px` হলো value।

   "Cascading" শব্দটির অর্থ: একই element এ একাধিক নিয়ম প্রযোজ্য হলে একটি নির্দিষ্ট অগ্রাধিকার ক্রম অনুসারে কোনটি কার্যকর হবে তা ঠিক হয়। অগ্রাধিকার, সবচেয়ে শক্তিশালী থেকে দুর্বল: `!important` → inline style → id selector (`#id`) → class, attribute ও pseudo-class selector (`.class`) → element selector (`h1`) → ব্রাউজারের নিজস্ব default। একই মাত্রার দুটি নিয়ম থাকলে পরেরটি জেতে।

   CSS ব্যবহারের তিনটি পদ্ধতি:

   ১. Inline CSS — সরাসরি element এর `style` attribute এ লেখা।

   ```html
   <h1 style="color: blue; text-align: center;">এটি একটি শিরোনাম</h1>
   <p style="font-size: 16px; color: gray;">এটি একটি অনুচ্ছেদ।</p>
   ```

   - সুবিধা: দ্রুত প্রয়োগ করা যায়; কেবল একটি element এ ব্যতিক্রমী শৈলী দিতে হলে সুবিধাজনক; অগ্রাধিকার সর্বোচ্চ, তাই অন্য সব নিয়মকে ছাপিয়ে যায়।
   - অসুবিধা: HTML ও CSS মিশে যায়, ফলে কোড অগোছালো হয়; পুনর্ব্যবহারযোগ্য নয়, প্রতিটি element এ আলাদা লিখতে হয়; ফাইলের আকার বাড়ে; রক্ষণাবেক্ষণ কঠিন — রং বদলাতে হলে প্রতিটি ট্যাগ খুঁজে বদলাতে হয়; cache হয় না।

   ২. Internal বা Embedded CSS — একই HTML ফাইলের `<head>` অংশে `<style>` ট্যাগের ভেতরে লেখা।

   ```html
   <!DOCTYPE html>
   <html>
   <head>
     <meta charset="UTF-8">
     <title>Internal CSS</title>
     <style>
       body { font-family: Arial, sans-serif; background-color: #f5f5f5; }
       h1   { color: navy; text-align: center; }
       p    { font-size: 16px; line-height: 1.6; }
       .highlight { background-color: yellow; }
     </style>
   </head>
   <body>
     <h1>শিরোনাম</h1>
     <p class="highlight">এটি একটি অনুচ্ছেদ।</p>
   </body>
   </html>
   ```

   - সুবিধা: একটি পৃষ্ঠার সব element এ একসঙ্গে প্রয়োগ হয়; আলাদা ফাইল লাগে না, তাই অতিরিক্ত HTTP অনুরোধ নেই; একক পৃষ্ঠার সাইটের জন্য উপযুক্ত।
   - অসুবিধা: কেবল ওই একটি পৃষ্ঠায় কাজ করে; একাধিক পৃষ্ঠায় একই শৈলী দিতে হলে প্রতিটিতে অনুলিপি করতে হয়; পৃথকভাবে cache হয় না, তাই প্রতিবার পুরো কোডটি ডাউনলোড হয়।

   ৩. External CSS — আলাদা `.css` ফাইলে লিখে `<link>` ট্যাগ দিয়ে যুক্ত করা। এটিই সুপারিশকৃত পদ্ধতি।

   ```css
   /* style.css */
   body { font-family: Arial, sans-serif; background-color: #f5f5f5; margin: 0; }
   h1   { color: navy; text-align: center; }
   p    { font-size: 16px; line-height: 1.6; }
   .btn { background: #1a73e8; color: #fff; padding: 10px 20px; border-radius: 4px; }
   ```

   ```html
   <head>
     <meta charset="UTF-8">
     <title>External CSS</title>
     <link rel="stylesheet" href="style.css">
   </head>
   ```

   - সুবিধা: একটি ফাইল হাজারো পৃষ্ঠায় ব্যবহার করা যায়; একটি ফাইল বদলালেই সমগ্র সাইটের চেহারা বদলে যায়; ব্রাউজার ফাইলটি cache করে রাখে, তাই পরবর্তী পৃষ্ঠাগুলো দ্রুত লোড হয়; HTML পরিচ্ছন্ন থাকে; দলগতভাবে কাজ করা সহজ, কারণ ডিজাইনার ও ডেভেলপার আলাদা ফাইলে কাজ করতে পারেন।
   - অসুবিধা: প্রথমবার একটি অতিরিক্ত HTTP অনুরোধ লাগে; ফাইলটি লোড হওয়ার আগমুহূর্তে পৃষ্ঠাটি সাজসজ্জাহীন দেখা যেতে পারে।

   তুলনা:

   | বিষয় | Inline | Internal | External |
   |---|---|---|---|
   | অবস্থান | element এর `style` attribute এ | `<head>` এর `<style>` ট্যাগে | আলাদা `.css` ফাইলে |
   | পরিসর | কেবল ওই একটি element | কেবল ওই একটি পৃষ্ঠা | অসংখ্য পৃষ্ঠা |
   | অগ্রাধিকার | সর্বোচ্চ | মধ্যম | সর্বনিম্ন |
   | পুনর্ব্যবহার | নেই | সীমিত | পূর্ণ |
   | Caching | হয় না | হয় না | হয় |
   | রক্ষণাবেক্ষণ | খুব কঠিন | মাঝারি | সহজ |
   | কখন ব্যবহার | জরুরি ব্যতিক্রম, বা ইমেইল টেমপ্লেট | একক পৃষ্ঠা বা দ্রুত পরীক্ষা | প্রকৃত ওয়েবসাইট |

   চতুর্থ একটি পদ্ধতি, যা কম ব্যবহৃত — `@import`:

   ```css
   @import url("typography.css");
   ```

   এটি একটি CSS ফাইলের ভেতর থেকে আরেকটি আনে, কিন্তু ফাইলগুলো ধারাবাহিকভাবে লোড হয় বলে গতি কমে যায়। তাই `<link>` ব্যবহারই ভালো।
2. **What is CSS? What is CSS framework? Write down 3 CSS framework name?** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*


   Answer: CSS and CSS frameworks.

   CSS stands for Cascading Style Sheets. It is a style sheet language used to control the presentation of an HTML document: colours, fonts, sizes, spacing, borders, positioning and the whole layout. HTML defines the structure and content; CSS defines how that content looks.

   Its syntax is `selector { property: value; }`:

   ```css
   h1 {
       color: navy;
       font-size: 28px;
       text-align: center;
   }
   ```

   The word "cascading" refers to the order of precedence used when several rules apply to the same element: `!important`, then inline styles, then id selectors, then class selectors, then element selectors, then the browser's own defaults.

   CSS can be applied in three ways: inline, in the element's `style` attribute; internal, in a `<style>` block in the `<head>`; and external, in a separate `.css` file linked with `<link rel="stylesheet" href="style.css">`. The external form is the one used in real projects, because one file styles the whole site and the browser caches it.

   What a CSS framework is

   A CSS framework is a ready-made library of CSS, and often a little JavaScript, that provides a grid system, standardised typography, and pre-built components such as buttons, navigation bars, cards, forms, tables and modal dialogues. Instead of writing every rule from nothing, the developer applies the framework's class names to the HTML.

   ```html
   <!-- Bootstrap: a responsive two-column layout and a styled button -->
   <div class="container">
     <div class="row">
       <div class="col-md-6">Left column</div>
       <div class="col-md-6">Right column</div>
     </div>
     <button class="btn btn-primary">Submit</button>
   </div>
   ```

   Three CSS framework names:
   1. Bootstrap
   2. Tailwind CSS
   3. Foundation

   Other well-known ones: Bulma, Materialize, Semantic UI, Pure CSS, Skeleton and Ant Design.

   Brief description of the three named:

   | Framework | Approach | Notes |
   |---|---|---|
   | Bootstrap | Component-based | Developed at Twitter; the most widely used. Provides a 12-column responsive grid and a full set of ready components. Very fast to build with, but sites tend to look alike unless customised |
   | Tailwind CSS | Utility-first | Provides small single-purpose classes such as `text-center`, `p-4`, `bg-blue-500`, which are combined in the HTML. Gives complete design freedom and very small production files, because unused classes are stripped out. The HTML becomes verbose |
   | Foundation | Component-based | Developed by ZURB. More flexible and less opinionated than Bootstrap, with strong accessibility support and a separate version for HTML email |

   Advantages of using a framework: development is much faster; the layout is responsive without extra work; the design is consistent across the site; cross-browser differences are already handled; accessibility is usually built in; and any developer who knows the framework can join the project immediately.

   Disadvantages: the file is larger than hand-written CSS unless it is trimmed; many sites end up looking the same; there is a learning curve for the framework's own conventions; a great deal of unused code may be shipped; and heavy customisation can end up costing more effort than writing the CSS directly.
3. **(খ) CSS Box Model এ ‘Padding’ এবং ‘Margin’ এরিয়ার মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*


   Answer: CSS Box Model অনুযায়ী প্রতিটি HTML element একটি আয়তাকার বাক্স, যার চারটি স্তর — ভেতর থেকে বাইরের দিকে content, padding, border ও margin।

   ```
   +-------------------------------------------------+
   |                    MARGIN                       |  ← স্বচ্ছ, বাইরের ফাঁক
   |   +-----------------------------------------+   |
   |   |                 BORDER                  |   |  ← সীমারেখা
   |   |   +---------------------------------+   |   |
   |   |   |            PADDING              |   |   |  ← ভেতরের ফাঁক
   |   |   |   +-------------------------+   |   |   |
   |   |   |   |         CONTENT         |   |   |   |  ← লেখা বা ছবি
   |   |   |   |    (width × height)     |   |   |   |
   |   |   |   +-------------------------+   |   |   |
   |   |   +---------------------------------+   |   |
   |   +-----------------------------------------+   |
   +-------------------------------------------------+
   ```

   Padding ও Margin এর পার্থক্য:

   | বিষয় | Padding | Margin |
   |---|---|---|
   | অবস্থান | Border এর ভেতরে, content ও border এর মাঝখানে | Border এর বাইরে, দুটি element এর মাঝখানে |
   | কাজ | Element এর ভেতরে ফাঁকা জায়গা তৈরি করে | Element এর বাইরে ফাঁকা জায়গা তৈরি করে |
   | Background | Element এর background রং বা ছবি padding এলাকায় দেখা যায় | সবসময় স্বচ্ছ; পেছনের বা মূল পৃষ্ঠার রং দেখা যায় |
   | ঋণাত্মক মান | দেওয়া যায় না | দেওয়া যায়, যেমন `margin-top: -10px` |
   | Collapsing | হয় না | হয়; দুটি element এর উল্লম্ব margin পাশাপাশি এলে বড়টিই কেবল কার্যকর হয়, যোগ হয় না |
   | Auto মান | `padding: auto` কাজ করে না | `margin: 0 auto` দিয়ে element কে অনুভূমিকভাবে মাঝখানে আনা যায় |
   | ক্লিকযোগ্য এলাকা | Padding এলাকায় ক্লিক করলে element এ ক্লিক হিসেবে গণ্য হয় | Margin এলাকায় ক্লিক element এ পৌঁছায় না |
   | মোট আকারে প্রভাব | Element এর নিজের আকার বাড়ায় | Element এর আকার বাড়ায় না, কেবল সরিয়ে রাখে |

   উদাহরণ:

   ```css
   .box {
       width: 300px;
       height: 100px;
       padding: 20px;              /* ভেতরের ফাঁক, চারদিকে ২০px */
       border: 5px solid black;    /* সীমারেখা */
       margin: 30px;               /* বাইরের ফাঁক, চারদিকে ৩০px */
       background-color: lightblue;
   }
   ```

   এখানে হালকা নীল রংটি content ও padding — দুই এলাকাতেই দেখা যাবে, কিন্তু margin এলাকায় দেখা যাবে না। এটিই দুইয়ের সবচেয়ে সহজে দেখা যাওয়া পার্থক্য।

   মোট প্রস্থের হিসাব (default `box-sizing: content-box` এ):

   মোট প্রস্থ = width + বাম padding + ডান padding + বাম border + ডান border + বাম margin + ডান margin

   = 300 + 20 + 20 + 5 + 5 + 30 + 30
   = 410 পিক্সেল

   এর মধ্যে element টি নিজে দখল করে = 300 + 40 + 10 = 350 পিক্সেল, এবং বাকি ৬০ পিক্সেল বাইরের ফাঁক।

   `box-sizing` property এর ভূমিকা:

   ```css
   * { box-sizing: border-box; }
   ```

   - `content-box` (default): `width` কেবল content কে বোঝায়; padding ও border আলাদাভাবে যোগ হয়। ফলে ৩০০px দিতে চাইলেও প্রকৃত প্রস্থ ৩৫০px হয়ে যায়।
   - `border-box`: `width` এর মধ্যেই padding ও border ধরা হয়। উপরের উদাহরণে element টির মোট প্রস্থ ঠিক ৩০০px থাকবে, আর content পাবে 300 − 40 − 10 = ২৫০px। প্রায় সব আধুনিক প্রকল্পে এটি ব্যবহার করা হয়, কারণ এতে হিসাব সহজ হয়।

   Margin collapsing এর উদাহরণ, যা বিশেষভাবে উল্লেখযোগ্য: একটি অনুচ্ছেদের `margin-bottom: 30px` এবং পরের অনুচ্ছেদের `margin-top: 20px` হলে দুইয়ের মাঝে ফাঁক হবে ৩০px, ৫০px নয়। Padding এ এমন হয় না; সেখানে দুটি মান যোগ হয়।

   কখন কোনটি ব্যবহার করবেন:
   - Padding — একটি বোতামের লেখা ও তার সীমারেখার মাঝে ফাঁক দিতে, বা একটি কার্ডের ভেতরের বিষয়বস্তুকে প্রান্ত থেকে দূরে রাখতে।
   - Margin — দুটি অনুচ্ছেদ বা দুটি কার্ডের মাঝে ফাঁক দিতে, বা একটি বাক্সকে পৃষ্ঠার মাঝখানে আনতে।
4. **(খ) CSS কী? কতভাবে একজন Website develop কারী তার page-এ CSS ব্যবহার করতে পারে।** *[Software Assistant Programmer 13.10.2022 compact it 708 (ET: N/A)]*


   Answer:    CSS এর পূর্ণরূপ Cascading Style Sheets। এটি একটি style sheet ভাষা, যা দিয়ে HTML নথির উপস্থাপন ও সাজসজ্জা নির্ধারণ করা হয় — রং, ফন্ট, আকার, ব্যবধান, সীমানা, অবস্থান ও সমগ্র বিন্যাস।

   HTML বলে "এটি একটি শিরোনাম"; CSS বলে "শিরোনামটি নীল রঙের, ২৪ পিক্সেল আকারের এবং মাঝখানে থাকবে"। এভাবে গঠন ও উপস্থাপন পৃথক রাখাকে বলে separation of concerns।

   CSS এর গঠন:

   ```
   selector {
       property: value;
       property: value;
   }
   ```

   ```css
   h1 {
       color: navy;
       font-size: 28px;
       text-align: center;
   }
   ```

   এখানে `h1` হলো selector, `color` ও `font-size` হলো property, আর `navy` ও `28px` হলো value।

   "Cascading" শব্দটির অর্থ: একই element এ একাধিক নিয়ম প্রযোজ্য হলে একটি নির্দিষ্ট অগ্রাধিকার ক্রম অনুসারে কোনটি কার্যকর হবে তা ঠিক হয়। অগ্রাধিকার, সবচেয়ে শক্তিশালী থেকে দুর্বল: `!important` → inline style → id selector (`#id`) → class, attribute ও pseudo-class selector (`.class`) → element selector (`h1`) → ব্রাউজারের নিজস্ব default। একই মাত্রার দুটি নিয়ম থাকলে পরেরটি জেতে।

   CSS ব্যবহারের তিনটি পদ্ধতি:

   ১. Inline CSS — সরাসরি element এর `style` attribute এ লেখা।

   ```html
   <h1 style="color: blue; text-align: center;">এটি একটি শিরোনাম</h1>
   <p style="font-size: 16px; color: gray;">এটি একটি অনুচ্ছেদ।</p>
   ```

   - সুবিধা: দ্রুত প্রয়োগ করা যায়; কেবল একটি element এ ব্যতিক্রমী শৈলী দিতে হলে সুবিধাজনক; অগ্রাধিকার সর্বোচ্চ, তাই অন্য সব নিয়মকে ছাপিয়ে যায়।
   - অসুবিধা: HTML ও CSS মিশে যায়, ফলে কোড অগোছালো হয়; পুনর্ব্যবহারযোগ্য নয়, প্রতিটি element এ আলাদা লিখতে হয়; ফাইলের আকার বাড়ে; রক্ষণাবেক্ষণ কঠিন — রং বদলাতে হলে প্রতিটি ট্যাগ খুঁজে বদলাতে হয়; cache হয় না।

   ২. Internal বা Embedded CSS — একই HTML ফাইলের `<head>` অংশে `<style>` ট্যাগের ভেতরে লেখা।

   ```html
   <!DOCTYPE html>
   <html>
   <head>
     <meta charset="UTF-8">
     <title>Internal CSS</title>
     <style>
       body { font-family: Arial, sans-serif; background-color: #f5f5f5; }
       h1   { color: navy; text-align: center; }
       p    { font-size: 16px; line-height: 1.6; }
       .highlight { background-color: yellow; }
     </style>
   </head>
   <body>
     <h1>শিরোনাম</h1>
     <p class="highlight">এটি একটি অনুচ্ছেদ।</p>
   </body>
   </html>
   ```

   - সুবিধা: একটি পৃষ্ঠার সব element এ একসঙ্গে প্রয়োগ হয়; আলাদা ফাইল লাগে না, তাই অতিরিক্ত HTTP অনুরোধ নেই; একক পৃষ্ঠার সাইটের জন্য উপযুক্ত।
   - অসুবিধা: কেবল ওই একটি পৃষ্ঠায় কাজ করে; একাধিক পৃষ্ঠায় একই শৈলী দিতে হলে প্রতিটিতে অনুলিপি করতে হয়; পৃথকভাবে cache হয় না, তাই প্রতিবার পুরো কোডটি ডাউনলোড হয়।

   ৩. External CSS — আলাদা `.css` ফাইলে লিখে `<link>` ট্যাগ দিয়ে যুক্ত করা। এটিই সুপারিশকৃত পদ্ধতি।

   ```css
   /* style.css */
   body { font-family: Arial, sans-serif; background-color: #f5f5f5; margin: 0; }
   h1   { color: navy; text-align: center; }
   p    { font-size: 16px; line-height: 1.6; }
   .btn { background: #1a73e8; color: #fff; padding: 10px 20px; border-radius: 4px; }
   ```

   ```html
   <head>
     <meta charset="UTF-8">
     <title>External CSS</title>
     <link rel="stylesheet" href="style.css">
   </head>
   ```

   - সুবিধা: একটি ফাইল হাজারো পৃষ্ঠায় ব্যবহার করা যায়; একটি ফাইল বদলালেই সমগ্র সাইটের চেহারা বদলে যায়; ব্রাউজার ফাইলটি cache করে রাখে, তাই পরবর্তী পৃষ্ঠাগুলো দ্রুত লোড হয়; HTML পরিচ্ছন্ন থাকে; দলগতভাবে কাজ করা সহজ, কারণ ডিজাইনার ও ডেভেলপার আলাদা ফাইলে কাজ করতে পারেন।
   - অসুবিধা: প্রথমবার একটি অতিরিক্ত HTTP অনুরোধ লাগে; ফাইলটি লোড হওয়ার আগমুহূর্তে পৃষ্ঠাটি সাজসজ্জাহীন দেখা যেতে পারে।

   তুলনা:

   | বিষয় | Inline | Internal | External |
   |---|---|---|---|
   | অবস্থান | element এর `style` attribute এ | `<head>` এর `<style>` ট্যাগে | আলাদা `.css` ফাইলে |
   | পরিসর | কেবল ওই একটি element | কেবল ওই একটি পৃষ্ঠা | অসংখ্য পৃষ্ঠা |
   | অগ্রাধিকার | সর্বোচ্চ | মধ্যম | সর্বনিম্ন |
   | পুনর্ব্যবহার | নেই | সীমিত | পূর্ণ |
   | Caching | হয় না | হয় না | হয় |
   | রক্ষণাবেক্ষণ | খুব কঠিন | মাঝারি | সহজ |
   | কখন ব্যবহার | জরুরি ব্যতিক্রম, বা ইমেইল টেমপ্লেট | একক পৃষ্ঠা বা দ্রুত পরীক্ষা | প্রকৃত ওয়েবসাইট |

   চতুর্থ একটি পদ্ধতি, যা কম ব্যবহৃত — `@import`:

   ```css
   @import url("typography.css");
   ```

   এটি একটি CSS ফাইলের ভেতর থেকে আরেকটি আনে, কিন্তু ফাইলগুলো ধারাবাহিকভাবে লোড হয় বলে গতি কমে যায়। তাই `<link>` ব্যবহারই ভালো।

## Web Security & Browser Same-Origin Policy (Iframe) (2)

1. **A & B two frames in a browser loaded from different origins. Why is it a reasonable security policy to allow A to navigate B to another origin base only on whether the display area of A contains dis-pare of B and A has the control over area.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 494 (ET: N/A)]*

2. **What is CORS in web development?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 761 (ET: N/A)]*
