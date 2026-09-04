<!-- TOC START -->
**Table of Contents** — 7 subtopics · 80 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [HTML & Web Fundamentals](#html--web-fundamentals-33) | 33 |
| 2 | [JavaScript & jQuery (DOM & Validation)](#javascript--jquery-dom--validation-16) | 16 |
| 3 | [HTTP Protocol](#http-protocol-10) | 10 |
| 4 | [Web Services & APIs (SOAP vs REST)](#web-services--apis-soap-vs-rest-8) | 8 |
| 5 | [Full Stack & Backend Web Development](#full-stack--backend-web-development-7) | 7 |
| 6 | [CSS & Styling (Inline, Internal, External)](#css--styling-inline-internal-external-4) | 4 |
| 7 | [Web Security & Browser Same-Origin Policy (Iframe)](#web-security--browser-same-origin-policy-iframe-2) | 2 |

<!-- TOC END -->

---

## HTML & Web Fundamentals (33)

1. **What is HTML Image tag?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

Answer: The HTML image tag is `<img>`. It embeds an image in a web page.
   ```html
      <img src="photo.jpg" alt="A red rose" width="300" height="200">
   ```
   ```
      It is an EMPTY (void) tag - there is NO closing </img>.
      In XHTML it is written self-closing :  <img ... />
   ```

   The attributes
   ```
      src     REQUIRED. The path or URL of the image file.
              relative :  src="images/photo.jpg"
              absolute :  src="https://example.com/photo.jpg"

      alt     REQUIRED in practice. Alternative text, shown if the
              image fails to load, and READ ALOUD BY A SCREEN
              READER. It is what makes the page accessible, and it
              is also used by search engines.

      width , height   the size in pixels. Setting BOTH prevents the
              page from jumping about while the image loads.

      title   tooltip text shown on hover
      loading="lazy"   the image is fetched only when it is about to
              scroll into view - a real performance gain on a long
              page
      srcset  a list of alternative files for different screen
              sizes, for responsive images
   ```

   Examples
   ```html
      <!-- basic -->
      <img src="logo.png" alt="Company logo">

      <!-- an image that is also a link -->
      <a href="home.html">
          <img src="logo.png" alt="Go to home page">
      </a>

      <!-- with a caption, the semantic HTML5 way -->
      <figure>
          <img src="chart.png" alt="Sales by region, 2025">
          <figcaption>Figure 1: Sales by region</figcaption>
      </figure>
   ```
   - Supported formats: `JPG` for photographs, `PNG` for images needing transparency, `GIF` for simple animation, `SVG` for logos and icons that must scale, and `WebP` for smaller files at the same quality.
   - The point worth stating: `alt` is not optional in practice. Without it a blind user hears nothing, the page fails accessibility rules, and nothing is shown if the file is missing. A purely decorative image should carry `alt=""` — an empty value, which tells the screen reader to skip it — not no attribute at all.

2. **What is URL? Give an Example.** *[BKSP Assistant Programmer 13.07.2024 compact it 1457 (ET: N/A)]*

Answer: What a URL is
   - `URL` stands for `Uniform Resource Locator`. It is the complete address that identifies `where a resource is on the internet and how to fetch it`.
   ```
      EXAMPLE

      https://www.example.com:443/products/list.php?id=25&sort=price#top
      |____|   |_____________| |_| |______________| |______________| |_|
        1            2          3         4                5         6

      1  SCHEME / PROTOCOL   https - how to fetch it
                             (http , https , ftp , mailto , file)
      2  DOMAIN / HOST       www.example.com - which server
      3  PORT                443 - optional ; the default is 80 for
                             http and 443 for https
      4  PATH               /products/list.php - which resource on
                             that server
      5  QUERY STRING       ?id=25&sort=price - parameters, after a
                             ? and separated by &
      6  FRAGMENT           #top - a position WITHIN the page.
                             It is handled by the BROWSER and is
                             never sent to the server.
   ```

   Simple examples
   ```
      https://www.google.com
      https://www.bb.org.bd/en/index.php
      https://example.com/images/logo.png
      ftp://ftp.example.com/files/report.pdf
      mailto:info@example.com
   ```

   Absolute and relative URLs
   ```
      ABSOLUTE   the complete address, usable from anywhere
           https://example.com/images/logo.png

      RELATIVE   relative to the current page
           images/logo.png      a folder below the current one
           ../logo.png          one folder up
           /images/logo.png     from the site ROOT
   ```

   Related terms that are often confused
   ```
      URI  Uniform Resource IDENTIFIER - the general term. Every URL
           is a URI.
      URL  Uniform Resource LOCATOR - a URI that says WHERE the
           resource is and HOW to get it.
      URN  Uniform Resource NAME - names a resource WITHOUT saying
           where it is , e.g.  urn:isbn:0451450523

      So :  URL = URI that includes a LOCATION.
   ```
   - How a URL is resolved: the browser reads the `domain`, asks `DNS` for its IP address, opens a `TCP` connection to that IP on the given `port`, and sends an HTTP request for the `path` and `query string`. The `fragment` is applied locally after the page arrives.
   - One practical note: characters that are not allowed in a URL must be `percent-encoded` — a space becomes `%20`, and an `&` inside a value becomes `%26`. Failing to encode a query value is a common source of broken links and of `injection` vulnerabilities.

3. **(খ) নিচের টেবিলটি তৈরি করার জন্য HTML কোড লিখুন :** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 413 (ET: N/A)]*

| Std name | Compulsory | Optional |
|---|---|---|
| Hasan | Bangla | English | ICT | Math |
| Nafis | Bangla | English | ICT | Biology |

| Std name | Compulsory | Optional |
|---|---|---|
| Hasan | Bangla | English | ICT | Math |
| Nafis | Bangla | English | ICT | Biology |

   Answer: (Answered in English, as required for IT topics.) The table needs `5 columns`, and the two header cells `Compulsory` and `Optional` span more than one column, so `colspan` is used.

   The HTML code
   ```html
   <table border="1" cellpadding="5" cellspacing="0">
       <tr>
           <th>Std name</th>
           <th colspan="3">Compulsory</th>
           <th>Optional</th>
       </tr>
       <tr>
           <td>Hasan</td>
           <td>Bangla</td>
           <td>English</td>
           <td>ICT</td>
           <td>Math</td>
       </tr>
       <tr>
           <td>Nafis</td>
           <td>Bangla</td>
           <td>English</td>
           <td>ICT</td>
           <td>Biology</td>
       </tr>
   </table>
   ```

   How the output looks
   ```
      +----------+--------------------------------+----------+
      | Std name |          Compulsory            | Optional |
      +----------+----------+----------+----------+----------+
      | Hasan    | Bangla   | English  | ICT      | Math     |
      +----------+----------+----------+----------+----------+
      | Nafis    | Bangla   | English  | ICT      | Biology  |
      +----------+----------+----------+----------+----------+
   ```
   - The assumption made: `Bangla, English and ICT` are the compulsory subjects, so `Compulsory` spans `3` columns, and `Optional` spans one. If the intended split is two and two, change `colspan="3"` to `colspan="2"` on Compulsory and add `colspan="2"` to Optional — the total must still come to `5`.

   The tags used
   ```
      <table>   the whole table
      <tr>      a table ROW
      <th>      a HEADER cell - bold and centred by default
      <td>      a DATA cell
      colspan   how many COLUMNS the cell spans - across
      rowspan   how many ROWS the cell spans - down
   ```
   ```
      THE RULE FOR CHECKING A SPANNED TABLE

      Every row must account for the SAME number of columns :

           row 1 :  1 + 3 + 1 = 5      correct
           row 2 :  1 + 1 + 1 + 1 + 1 = 5   correct
           row 3 :  1 + 1 + 1 + 1 + 1 = 5   correct

      If the totals differ, the table renders with ragged or
      overlapping cells. This is the single commonest mistake with
      colspan and rowspan.
   ```

   The modern version, with CSS instead of the old attributes
   ```html
   <style>
       table { border-collapse: collapse; }
       th, td { border: 1px solid #333; padding: 6px 10px; }
       th { background: #eee; }
   </style>

   <table>
       <thead>
           <tr>
               <th>Std name</th>
               <th colspan="3">Compulsory</th>
               <th>Optional</th>
           </tr>
       </thead>
       <tbody>
           <tr><td>Hasan</td><td>Bangla</td><td>English</td>
               <td>ICT</td><td>Math</td></tr>
           <tr><td>Nafis</td><td>Bangla</td><td>English</td>
               <td>ICT</td><td>Biology</td></tr>
       </tbody>
   </table>
   ```
   - `border`, `cellpadding` and `cellspacing` are deprecated presentational attributes; the correct place for them is `CSS`. `<thead>` and `<tbody>` are also worth adding, because they let the header repeat when a long table is printed.

4. **একটি ওয়েবসাইটের (Website) কয়টি অংশ থাকে এবং কী কী?** *[সাধারণ জ্ঞান: বিজ্ঞান ও প্রযুক্তি, বিষয় কোড: ১০৪, মান: ৪০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

Answer: (Answered in English, as required for IT topics.) A website has `four` main parts, in the sense of the sections that appear on a page.
   ```
      +==========================================================+
      |                       HEADER                             |
      |   logo , site title , banner                             |
      +==========================================================+
      |                    NAVIGATION MENU                       |
      |   Home | About | Products | Services | Contact           |
      +==========================================================+
      |                                          |               |
      |            MAIN CONTENT / BODY           |    SIDEBAR    |
      |                                          |               |
      |   the actual text, images and forms      |  links , ads  |
      |                                          |  categories   |
      +==========================================================+
      |                       FOOTER                             |
      |   copyright , contact , privacy policy , social links    |
      +==========================================================+
   ```
   ```
      1. HEADER      the top of the page - logo, site name, banner.
                     It is the same on every page, so the visitor
                     always knows which site they are on.

      2. NAVIGATION  the menu that links to the other pages. Often
                     counted as part of the header.

      3. BODY / MAIN
         CONTENT     the actual content of that page - the only part
                     that changes from page to page. A SIDEBAR may
                     sit beside it for related links or
                     advertisements.

      4. FOOTER      the bottom - copyright, contact details,
                     privacy policy, sitemap, social media links.
   ```
   - Counted this way there are `four` parts: header, navigation, body and footer. Some books count `five` by listing the sidebar separately, or `three` by folding navigation into the header. All three answers are accepted; state which convention is being used.

   The HTML5 tags for these parts
   ```html
      <body>
          <header>   ... logo and site title ...   </header>
          <nav>      ... the menu ...              </nav>
          <main>
              <article> ... the page content ... </article>
              <aside>   ... the sidebar ...      </aside>
          </main>
          <footer>   ... copyright and links ...  </footer>
      </body>
   ```

   The other sense of "parts of a website"
   ```
      If the question means the COMPONENTS a website is BUILT from,
      the answer is three :

        DOMAIN NAME   the address - www.example.com , registered and
             renewed yearly
        WEB HOSTING   the server space where the files live
        WEBSITE FILES the HTML, CSS, JavaScript, images and, for a
             dynamic site, the server-side code and DATABASE
   ```
   ```
      And by PAGE :
           HOME PAGE      the entry point , index.html
           INNER PAGES    About , Products , Services , Contact
           LANDING PAGES  for a specific campaign
   ```
   - Which reading is intended can be told from the marks: a `4-mark` question wants the `page sections` — header, navigation, body, footer — with a labelled diagram. That is the answer given above.

5. **(ক) ওয়েব ডিজাইন কী? স্ট্যাটিক ও ডায়নামিক ওয়েবসাইটের পার্থক্য ব্যাখ্যা করুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

Answer: (Answered in English, as required for IT topics.) What web design is
   - `Web design` is the process of planning and creating the `look, layout and usability` of a website — what the visitor sees and how they interact with it. It covers the visual design and the front-end implementation.
   ```
      WHAT IT INVOLVES
        LAYOUT           the arrangement of header, navigation,
                         content and footer
        VISUAL DESIGN    colour scheme, typography, images, spacing
        NAVIGATION       how the visitor moves between pages
        RESPONSIVENESS   the page works on phone, tablet and desktop
        ACCESSIBILITY    usable with a screen reader and by keyboard
        USABILITY        can the visitor achieve their goal quickly

      THE TOOLS
        HTML   the structure and content
        CSS    the presentation - colours, fonts, layout
        JavaScript  behaviour on the client side
        Figma , Adobe XD for the mock-ups
   ```
   - The distinction from `web development`: web design decides `how it looks and feels`; web development `builds it`, including the server-side logic and the database.

   Difference between static and dynamic websites

   | Point | Static website | Dynamic website |
   |---|---|---|
   | Content | `Fixed` — the same for every visitor | `Generated` per request, may differ per user |
   | Built with | `HTML`, `CSS`, JavaScript only | Adds a `server-side language` — PHP, Python, Java, Node.js |
   | Database | `None` | `Required` — MySQL, PostgreSQL, MongoDB |
   | How a page is served | The stored `.html` file is sent as it is | The server `runs code` and builds the page |
   | To change content | Edit the `HTML file` and re-upload | Update the `database`, usually through an admin panel |
   | Speed | `Faster` — nothing to compute | Slower — code runs and the database is queried |
   | Hosting cost | `Cheap` | Higher — needs a server that can run code |
   | Development cost | `Low` | Higher |
   | Security | `Very secure` — no database, no server code to attack | More exposed — `SQL injection`, session attacks |
   | Interactivity | Very limited | `High` — login, search, cart, comments |
   | Scalability of content | Poor — 100 pages means 100 files | `Excellent` — one template serves thousands of pages |
   | Examples | A brochure site, a personal portfolio | Facebook, Amazon, a bank's internet banking, WordPress |

   How each one serves a page
   ```
      STATIC
           browser --request--> web server --sends the stored
                                             index.html
           No processing. The file that is stored is the file that
           is sent.

      DYNAMIC
           browser --request--> web server --> runs PHP / Java code
                                           --> QUERIES THE DATABASE
                                           --> builds the HTML
                                           --> sends it back
           The HTML never existed until the request arrived.
   ```
   ```mermaid
   flowchart LR
       A[Browser] -->|request| B[Web server]
       B -->|static: send the file| A
       B -->|dynamic| C[Server-side code]
       C --> D[(Database)]
       D --> C
       C -->|generated HTML| A
   ```

   - When each is the right choice: a `static` site is correct for a small brochure, a portfolio or documentation — it is fast, cheap and almost impossible to attack. A `dynamic` site is necessary the moment the content changes often, users must log in, or the same page must show different data to different people.
   - Two modern qualifications worth adding. A `static site generator` such as Jekyll or Hugo builds static HTML from templates and content files, giving the maintainability of a dynamic site with the speed and security of a static one. And a `single-page application` blurs the line further — the HTML file is static, but it fetches data from an `API` and rewrites the page in the browser.

6. **What is the popular way of linking many documents?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

Answer: The popular way of linking many documents is the `hyperlink`, created with the anchor tag `<a>` and its `href` attribute.
   ```html
      <a href="page2.html">Go to page 2</a>
   ```
   - This is what makes the web a `web`: documents linked to documents. The technology is called `hypertext`, and it is the `HT` in both `HTML` and `HTTP`.

   The forms a link can take
   ```html
      <!-- another page on the same site - a RELATIVE link -->
      <a href="about.html">About us</a>
      <a href="products/list.html">Products</a>
      <a href="../index.html">Home</a>

      <!-- another website - an ABSOLUTE link -->
      <a href="https://www.example.com">Example</a>

      <!-- a position WITHIN the same page - a FRAGMENT link -->
      <a href="#section3">Jump to section 3</a>
      ...
      <h2 id="section3">Section 3</h2>

      <!-- a position within ANOTHER page -->
      <a href="report.html#summary">Summary of the report</a>

      <!-- an email address -->
      <a href="mailto:info@example.com">Email us</a>

      <!-- a telephone number, useful on mobile -->
      <a href="tel:+8801700000000">Call us</a>

      <!-- a file to download -->
      <a href="form.pdf" download>Download the form</a>

      <!-- an image used as a link -->
      <a href="home.html"><img src="logo.png" alt="Home"></a>
   ```

   The attributes of `<a>`
   ```
      href      REQUIRED. The destination.
      target    where to open it :
                     _self   the same tab (the default)
                     _blank  a NEW tab
      rel       the relationship. With target="_blank" always add
                rel="noopener noreferrer" - without it the new page
                can reach back and control the original page, which
                is a real security hole.
      title     tooltip text
      download  save the file instead of opening it
   ```

   Navigation — many documents linked as a set
   ```html
      <nav>
          <ul>
              <li><a href="index.html">Home</a></li>
              <li><a href="about.html">About</a></li>
              <li><a href="products.html">Products</a></li>
              <li><a href="contact.html">Contact</a></li>
          </ul>
      </nav>
   ```
   ```
      The usual structures for linking many documents :

      LINEAR / SEQUENTIAL   page 1 -> page 2 -> page 3
           each page links only to the next and previous. Suits a
           tutorial or a form wizard.

      TREE / HIERARCHICAL              HOME
                                    /   |   \
                             Products About Contact
                             /     \
                        Laptops  Printers
           A menu at every level. The usual structure for a website.

      WEBBED / NETWORK      every page links to many others - as
           Wikipedia does.
   ```
   - The related mechanism, worth one line: a `sitemap.xml` lists every document on the site for search engines, and a `<link>` tag in the `<head>` links a document to a `stylesheet` or an icon. But for linking one document to another, `<a href="...">` is the answer.

7. **Which tag is used for creating button in html?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

Answer: The `<button>` tag is used to create a button in HTML.
   ```html
      <button type="button">Click Me</button>
   ```
   - The content between the tags is what appears on the button, and it may include text, an image or an icon.

   The three types of `<button>`
   ```html
      <form action="/save" method="post">
          <input type="text" name="name">

          <button type="submit">Submit</button>  <!-- submits the
                                                      form ; this is
                                                      the DEFAULT
                                                      inside a form -->
          <button type="reset">Clear</button>    <!-- clears all the
                                                      fields -->
          <button type="button">Calculate</button> <!-- does NOTHING
                                                        on its own ;
                                                        used with
                                                        JavaScript -->
      </form>
   ```
   ```
      THE COMMONEST MISTAKE : omitting  type  inside a form.
      The default is  type="submit" , so a button meant only to run
      some JavaScript will SUBMIT THE FORM and reload the page.
      Always write  type="button"  for a non-submitting button.
   ```

   The other ways to make a button
   ```html
      <!-- using the input tag - the older way -->
      <input type="button"  value="Click Me">
      <input type="submit"  value="Submit">
      <input type="reset"   value="Reset">
      <input type="image" src="go.png" alt="Submit">

      <!-- a link styled to look like a button -->
      <a href="page.html" class="btn">Go</a>
   ```

   `<button>` compared with `<input type="button">`

   | Point | `<button>` | `<input type="button">` |
   |---|---|---|
   | Tag type | Container — has a closing tag | `Empty` tag |
   | Label from | The `content` between the tags | The `value` attribute |
   | Can contain HTML | `Yes` — an image, an icon, bold text | `No` — plain text only |
   | Easier to style | `Yes` | Less flexible |
   | Default type in a form | `submit` | `button` — does nothing |

   - Which to use: `<button>` is preferred in modern HTML, because it can contain markup and is easier to style.
   ```html
      <button type="submit">
          <img src="search.png" alt=""> Search
      </button>
   ```

   With JavaScript
   ```html
      <button type="button" onclick="alert('Hello')">Say hello</button>

      <!-- better practice - keep the JavaScript out of the HTML -->
      <button type="button" id="calc">Calculate</button>
      <script>
          document.getElementById("calc").addEventListener("click",
              function () { /* ... */ });
      </script>
   ```
   - One accessibility point: a `<div>` styled to look like a button is not a button. A real `<button>` is reachable by the `Tab` key, activates on `Enter` and `Space`, and is announced as a button by a screen reader. A styled `<div>` does none of these unless every one of them is added by hand — which is why the correct tag matters.

8. **(ক) HTML Element কী? উদাহরণসহ বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 607 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) What an HTML element is
   - An `HTML element` is a complete unit of an HTML document. It normally consists of a `start tag`, the `content`, and an `end tag`.
   ```
      <p>This is a paragraph.</p>
      |_|                   |__|
      start tag             end tag
          |_________________|
               content

      ELEMENT = start tag + content + end tag
   ```
   - Note the distinction: a `tag` is just the marker `<p>`; the `element` is the whole thing including its content. An `attribute` is extra information written inside the start tag.

   Parts of an element
   ```
      <a href="page.html" title="Next">Click here</a>
      |_| |______________________|    |________| |__|
      tag       attributes             content   end
      name

      ATTRIBUTE = name="value"  ,  written only in the START tag
   ```

   Types of element
   ```
      1. NORMAL (container) elements - have a closing tag
           <p>text</p>
           <h1>Heading</h1>
           <div>...</div>
           <a href="x.html">link</a>
           <ul><li>item</li></ul>

      2. EMPTY (void) elements - NO content and NO closing tag
           <br>      a line break
           <hr>      a horizontal rule
           <img src="a.jpg" alt="A">
           <input type="text">
           <meta charset="UTF-8">
           <link rel="stylesheet" href="style.css">
   ```
   ```
      3. By DISPLAY behaviour

         BLOCK-LEVEL   starts on a NEW LINE and takes the full width
              <div> <p> <h1> to <h6> <ul> <ol> <li> <table>
              <form> <header> <footer> <section>

         INLINE        stays IN THE LINE and takes only the width it
                       needs
              <span> <a> <img> <b> <i> <strong> <em> <input>
              <label> <br>

         An INLINE element must not contain a BLOCK element.
         <span><div>...</div></span> is invalid.
   ```

   Nesting — and the rule that governs it
   ```html
      <div>
          <h2>Products</h2>
          <p>Our <strong>best</strong> items.</p>
      </div>
   ```
   ```
      Elements must be nested, never overlapped :

           CORRECT :  <p><strong>text</strong></p>
           WRONG   :  <p><strong>text</p></strong>

      The one opened LAST must be closed FIRST.
   ```

   A complete example
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <title>My Page</title>
   </head>
   <body>
       <h1>Welcome</h1>
       <p>This is a <strong>paragraph</strong> with a
          <a href="about.html">link</a>.</p>
       <img src="photo.jpg" alt="A photograph">
       <ul>
           <li>First item</li>
           <li>Second item</li>
       </ul>
   </body>
   </html>
   ```
   ```
      Here <html> is the ROOT element, containing <head> and <body>
      as CHILD elements ; <head> and <body> are SIBLINGS. This
      parent-child-sibling tree is exactly what the browser builds
      as the DOM.
   ```
   - The `<html>`, `<head>`, `<title>` and `<body>` elements are the minimum a valid page needs. Everything visible goes inside `<body>`; `<head>` holds information about the page — the character set, the title, and links to stylesheets.

9. **(খ) Static ও Dynamic ওয়েবসাইটের মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 607 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) Difference between static and dynamic websites

   | Point | Static website | Dynamic website |
   |---|---|---|
   | Content | `Fixed` — the same for every visitor | `Generated` per request; may differ per user |
   | Built with | `HTML`, `CSS`, JavaScript only | Adds a `server-side language` — PHP, Python, Java, Node.js |
   | Database | `None` | `Required` — MySQL, PostgreSQL, MongoDB |
   | How a page is served | The stored `.html` file is sent as it is | The server `runs code` and builds the page |
   | To change content | Edit the `HTML file` and re-upload it | Update the `database`, through an admin panel |
   | Speed | `Faster` — nothing to compute | Slower — code runs and the database is queried |
   | Hosting | `Cheap`, any web space | Needs a server that can run code |
   | Development cost and time | `Low` | Higher |
   | Security | `Very secure` — no database, no server code | Exposed to `SQL injection`, session attacks |
   | Interactivity | Very limited | `High` — login, search, cart, comments |
   | Content scalability | Poor — 100 pages means 100 files | `Excellent` — one template serves thousands of pages |
   | Maintenance | Needs someone who can edit HTML | Any trained user can update content |
   | Examples | Brochure site, portfolio, documentation | Facebook, Amazon, internet banking, WordPress |

   How each serves a page
   ```
      STATIC
           browser --request--> web server --sends the stored
                                             index.html
           NO processing. The file stored is the file sent.

      DYNAMIC
           browser --request--> web server --> runs PHP / Java code
                                           --> QUERIES THE DATABASE
                                           --> builds the HTML
                                           --> sends it back
           The HTML did not exist until the request arrived.
   ```
   ```mermaid
   flowchart LR
       A[Browser] -->|request| B[Web server]
       B -->|static: send the stored file| A
       B -->|dynamic| C[Server-side code]
       C --> D[(Database)]
       D --> C
       C -->|generated HTML| A
   ```

   Which to choose
   ```
      STATIC is right when :
           the content rarely changes
           there is no login and no user-specific data
           the budget is small
           speed and security matter most
           -> a brochure site , a portfolio , documentation

      DYNAMIC is necessary when :
           content changes often, and non-technical staff must
                update it
           users must LOG IN
           the same page must show DIFFERENT data to different users
           there is a search, a cart or a comment facility
           -> e-commerce , internet banking , a news site , any
              portal
   ```
   - Two modern qualifications. A `static site generator` such as Jekyll or Hugo builds plain HTML from templates and content files, giving a dynamic site's maintainability with a static site's speed and security. And a `single-page application` blurs the line completely — the HTML file itself is static, but it fetches data from an `API` and rewrites the page in the browser, so the page is dynamic while the file is not.

10. **অথবা, (ক) উদাহরণসহ HTML webpage এর গঠন ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 608 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) Structure of an HTML web page
    - Every HTML page has the same skeleton: a `doctype`, a root `<html>` element, and inside it exactly two children — `<head>` for information `about` the page, and `<body>` for the content that is `displayed`.
    ```
       +--------------------------------------------------+
       | <!DOCTYPE html>       declares HTML5             |
       +--------------------------------------------------+
       | <html>                the ROOT element           |
       |  +--------------------------------------------+  |
       |  | <head>   information ABOUT the page        |  |
       |  |   <meta charset>  , <title> , <link> ,     |  |
       |  |   <style> , <script>                       |  |
       |  |   NOT DISPLAYED on the page                |  |
       |  +--------------------------------------------+  |
       |  +--------------------------------------------+  |
       |  | <body>   everything the visitor SEES       |  |
       |  |   headings , paragraphs , images , links , |  |
       |  |   tables , forms                           |  |
       |  +--------------------------------------------+  |
       | </html>                                          |
       +--------------------------------------------------+
    ```

    The example
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport"
              content="width=device-width, initial-scale=1.0">
        <title>My First Page</title>
        <link rel="stylesheet" href="style.css">
    </head>
    <body>

        <header>
            <h1>Welcome to My Site</h1>
        </header>

        <nav>
            <a href="index.html">Home</a> |
            <a href="about.html">About</a> |
            <a href="contact.html">Contact</a>
        </nav>

        <main>
            <h2>About this page</h2>
            <p>This is a <strong>paragraph</strong> with a
               <a href="https://example.com">link</a>.</p>

            <img src="photo.jpg" alt="A photograph" width="300">

            <ul>
                <li>First item</li>
                <li>Second item</li>
            </ul>
        </main>

        <footer>
            <p>&copy; 2026 My Site</p>
        </footer>

    </body>
    </html>
    ```

    What each part does
    ```
       <!DOCTYPE html>
            Tells the browser this is HTML5. Without it the browser
            falls into QUIRKS MODE and renders the page by old,
            inconsistent rules.

       <html lang="en">
            The ROOT element. Everything else sits inside it. The
            lang attribute helps screen readers pronounce the text
            and helps search engines.

       <head>
            <meta charset="UTF-8">   the CHARACTER ENCODING. Without
                 it, Bangla and other non-ASCII text appears as
                 garbage. It must be the FIRST thing in the head.
            <meta name="viewport">   makes the page RESPONSIVE on a
                 phone. Without it a mobile browser renders a
                 desktop-width page and shrinks it.
            <title>                  the text in the browser TAB,
                 and the heading a search engine shows.
            <link rel="stylesheet">  attaches the CSS file.

       <body>
            Everything visible. The HTML5 SEMANTIC elements give it
            structure :
                 <header>  the top - logo and site title
                 <nav>     the navigation menu
                 <main>    the main content ; ONE per page
                 <footer>  copyright and links
    ```

    The minimum valid page
    ```html
    <!DOCTYPE html>
    <html>
    <head><title>Page</title></head>
    <body>Hello</body>
    </html>
    ```
    - The four required elements are `<html>`, `<head>`, `<title>` and `<body>`. `<title>` is the only one the HTML specification actually makes mandatory inside the head.
    - The tree structure this creates is exactly what the browser builds as the `DOM`: `<html>` is the root, `<head>` and `<body>` are its children and each other's siblings, and every nested element becomes a child node. JavaScript then manipulates that same tree.

11. **(খ) নিচের লিস্টটি তৈরি করার জন্য HTML কোড লিখুন :** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 609 (ET: N/A)]*
   1. Fruits
      (a) Mango
      (b) Orange
   2. Vagetables
      - Green Capsicum
      - Yellow Capsicum
      - Red Capsicum

1. Fruits
      (a) Mango
      (b) Orange
   2. Vagetables
      - Green Capsicum
      - Yellow Capsicum
      - Red Capsicum

    Answer: (Answered in English, as required for IT topics.) The list needs an `ordered list` at the outer level, with a `nested ordered list` using lower-case letters under "Fruits" and a `nested unordered list` under "Vegetables".

    The HTML code
    ```html
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
    ```

    The output
    ```
       1. Fruits
            a. Mango
            b. Orange
       2. Vegetables
            - Green Capsicum
            - Yellow Capsicum
            - Red Capsicum
    ```
    - The `(a)` and `(b)` with brackets cannot be produced by the `type` attribute alone, which gives `a.` and `b.`. To get the exact brackets, CSS counters are needed:
    ```html
    <style>
        ol.bracket { list-style: none; counter-reset: item; }
        ol.bracket li { counter-increment: item; }
        ol.bracket li::before { content: "(" counter(item, lower-alpha) ") "; }
    </style>

    <ol>
        <li>Fruits
            <ol class="bracket">
                <li>Mango</li>
                <li>Orange</li>
            </ol>
        </li>
        ...
    </ol>
    ```

    The list tags
    ```
       <ol>   ORDERED list - numbered
       <ul>   UNORDERED list - bulleted
       <li>   LIST ITEM - used inside both
       <dl>   DESCRIPTION list , with <dt> term and <dd> description
    ```
    ```
       THE type ATTRIBUTE OF <ol>

            type="1"   1 , 2 , 3      (the default)
            type="A"   A , B , C
            type="a"   a , b , c
            type="I"   I , II , III
            type="i"   i , ii , iii

       Other useful attributes :
            start="5"     begin numbering at 5
            reversed      count downwards
    ```
    ```
       THE list-style-type PROPERTY OF <ul>

            disc    a filled circle  (the default)
            circle  a hollow circle
            square  a filled square
            none    no marker at all
    ```

    The nesting rule — the point the question tests
    ```
       The nested list goes INSIDE the <li> of its parent, BEFORE
       that </li> :

            CORRECT
            <li>Fruits
                <ol><li>Mango</li></ol>
            </li>

            WRONG - the nested list is placed BETWEEN two <li>
            elements, outside any of them :
            <li>Fruits</li>
            <ol><li>Mango</li></ol>

       A list may only contain <li> elements as its direct children.
       Placing an <ol> or <ul> directly inside another <ol> or <ul>,
       rather than inside an <li>, is invalid HTML.
    ```
    - The modern practice: use `CSS` for the marker style — `list-style-type: lower-alpha` — rather than the `type` attribute, which is a presentational hold-over. The `type` attribute still works in every browser, so either answer is acceptable in an exam.

12. **অথবা, নিম্নোক্ত উপাদানগুলোসহ একটি HTML page লিখুন। Hyperlink, Ordered list, Unordered list, Form (Tent box, Check box, Option Button).** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) The page below contains a `hyperlink`, an `ordered list`, an `unordered list`, and a `form` with a text box, check boxes and radio (option) buttons.

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Student Registration</title>
    </head>
    <body>

        <h1>Student Registration Page</h1>

        <!-- 1. HYPERLINK -->
        <p>
            Visit our
            <a href="https://www.example.com" target="_blank"
               rel="noopener noreferrer">official website</a>
            for more information.
        </p>
        <p><a href="index.html">Back to Home</a></p>

        <!-- 2. ORDERED LIST -->
        <h2>Admission Steps</h2>
        <ol>
            <li>Collect the application form</li>
            <li>Fill in your personal details</li>
            <li>Attach the required documents</li>
            <li>Pay the admission fee</li>
            <li>Submit the form</li>
        </ol>

        <!-- 3. UNORDERED LIST -->
        <h2>Required Documents</h2>
        <ul>
            <li>SSC certificate</li>
            <li>HSC certificate</li>
            <li>National ID card copy</li>
            <li>Two passport-size photographs</li>
        </ul>

        <!-- 4. FORM -->
        <h2>Registration Form</h2>
        <form action="/register" method="post">

            <!-- TEXT BOX -->
            <p>
                <label for="name">Full Name :</label>
                <input type="text" id="name" name="name"
                       placeholder="Enter your full name" required>
            </p>

            <p>
                <label for="email">Email :</label>
                <input type="email" id="email" name="email" required>
            </p>

            <!-- CHECK BOX - many may be chosen -->
            <p>Subjects (choose any) :</p>
            <p>
                <input type="checkbox" id="bangla" name="subject[]"
                       value="Bangla">
                <label for="bangla">Bangla</label>

                <input type="checkbox" id="english" name="subject[]"
                       value="English">
                <label for="english">English</label>

                <input type="checkbox" id="ict" name="subject[]"
                       value="ICT" checked>
                <label for="ict">ICT</label>
            </p>

            <!-- RADIO / OPTION BUTTON - only ONE may be chosen -->
            <p>Gender :</p>
            <p>
                <input type="radio" id="male" name="gender"
                       value="Male" checked>
                <label for="male">Male</label>

                <input type="radio" id="female" name="gender"
                       value="Female">
                <label for="female">Female</label>
            </p>

            <p>
                <button type="submit">Submit</button>
                <button type="reset">Clear</button>
            </p>

        </form>

    </body>
    </html>
    ```

    The points the question is testing
    ```
       HYPERLINK
            <a href="...">text</a>
            With target="_blank" always add rel="noopener noreferrer" -
            without it the new page can reach back and control the
            original page.

       ORDERED LIST     <ol> - numbered ; use it when the ORDER
            matters, as it does for admission steps.
       UNORDERED LIST   <ul> - bulleted ; use it when the order does
            NOT matter.

       TEXT BOX         <input type="text">

       CHECK BOX        <input type="checkbox">
            MANY may be selected. Each needs its own value. To submit
            several under one name, use  name="subject[]".

       RADIO BUTTON     <input type="radio">
            Only ONE may be selected within a group, and the GROUP IS
            DEFINED BY A SHARED name ATTRIBUTE. This is the single
            most important detail :

                 SAME name  -> mutually exclusive , as intended
                 DIFFERENT name -> each becomes its own group and all
                      of them can be selected at once - the classic
                      bug.
    ```
    ```
       CHECKBOX vs RADIO , stated plainly

            CHECKBOX : many choices allowed , independent of each
                 other , and it can be UNCHECKED again.
            RADIO    : one choice only , grouped by name , and once
                 one is chosen the group CANNOT be cleared by
                 clicking - only by choosing another.
    ```
    - Two details that carry marks. Every input needs a `name`, because the `name` is what is sent to the server — an input without one submits nothing. And every input should have a `<label for="id">`: clicking the label then selects the control, and a screen reader reads the label with the field, which is what makes the form accessible.

13. **(ক) HTML এবং CSS কী? সংক্ষেপে ব্যাখ্যা করুন। শুধুমাত্র HTML এবং CSS ব্যবহার করে Web Site তৈরির ক্ষেত্রে সীমাবদ্ধতা আলোচনা করুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 705 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) What HTML is
    - `HTML` stands for `HyperText Markup Language`. It provides the `structure and content` of a web page — headings, paragraphs, images, links, tables and forms. It is a `markup` language, not a programming language: it has no variables, no conditions and no loops.
    ```html
       <h1>Welcome</h1>
       <p>This is a <strong>paragraph</strong>.</p>
       <img src="photo.jpg" alt="A photograph">
       <a href="about.html">About us</a>
    ```

    What CSS is
    - `CSS` stands for `Cascading Style Sheets`. It controls the `presentation` — colours, fonts, spacing, borders and layout. It separates how a page `looks` from what it `contains`.
    ```css
       h1     { color: navy; font-size: 32px; text-align: center; }
       p      { line-height: 1.6; margin-bottom: 15px; }
       .card  { border: 1px solid #ccc; padding: 20px;
                border-radius: 8px; }
    ```
    ```
       THE DIVISION OF LABOUR

            HTML  =  STRUCTURE and CONTENT   -> WHAT it is
            CSS   =  PRESENTATION            -> HOW it looks
            JavaScript = BEHAVIOUR           -> WHAT IT DOES
    ```
    - Why the separation matters: one CSS file restyles a thousand pages at once, the HTML stays readable, and the same content can be presented differently on a phone, a desktop and a printer.

    Limitations of building a website with HTML and CSS only

    1. No server-side processing
    - HTML and CSS run entirely in the `browser`. Nothing can be executed on the server, so nothing can be computed, stored or decided there.

    2. No database
    - Content cannot be stored or retrieved. Every page must be written as a separate file by hand, so a hundred product pages means a hundred files to create and maintain.

    3. The site can only be static
    - The page sent is the page stored. It is `the same for every visitor`, and it cannot show one user their own data.

    4. No user authentication
    - `Login, registration and sessions are impossible.` A password cannot be checked without server-side code, and there is no secure place to keep it.

    5. No form processing
    - A `<form>` can be `displayed`, but nothing can `receive` the submitted data. Without a server-side script the form has nowhere to send it, so a contact form cannot deliver a message.

    6. No search, no filtering, no sorting of real data
    - These need a database query. Client-side JavaScript can sort what is already on the page, but not search a catalogue that is not there.

    7. No content management
    - A non-technical person cannot update the site. Every change means editing HTML, so there is no admin panel and no `CMS`.

    8. No dynamic interactivity
    - CSS can produce hover effects, transitions and animations, and modern CSS can do a surprising amount. But `no logic` — no calculation, no validation of business rules, no reaction to data.

    9. No e-commerce
    - A cart, a payment gateway and an order record all need server-side code and a database.

    10. Poor content scalability and maintainability
    - A change to the navigation menu must be repeated in every single file, because there are no templates and no includes.

    What can still be built with HTML and CSS alone
    ```
       a personal PORTFOLIO
       a company BROCHURE site - a few pages that rarely change
       a landing page for a campaign
       DOCUMENTATION or a manual
       a resume or CV page
    ```

    What is needed to remove each limitation
    ```
       JAVASCRIPT              client-side interactivity, validation,
            fetching data from an API
       A SERVER-SIDE LANGUAGE  PHP , Python , Java , Node.js - logic,
            authentication, form handling
       A DATABASE              MySQL , PostgreSQL , MongoDB - storing
            and querying content
       A CMS or FRAMEWORK      WordPress , Laravel , Django - content
            management and templates
    ```
    - The qualification worth adding: a `static site generator` such as Jekyll or Hugo removes the maintainability problem without any server-side code — templates and content files are compiled into plain HTML. That gives a static site the maintainability of a dynamic one, and it is why static sites remain a genuine choice rather than merely a beginner's one.

14. **(খ) Static Web Page এবং Dynamic Web Page এর মধ্যে পার্থক্য আলোচনা করুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 705 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) Difference between a static web page and a dynamic web page

    | Point | Static web page | Dynamic web page |
    |---|---|---|
    | Content | `Fixed` — the same for every visitor | `Generated` at request time; may differ per user |
    | Built with | `HTML`, `CSS`, JavaScript only | Adds a `server-side language` — PHP, Python, Java, Node.js |
    | Database | `None` | `Required` — MySQL, PostgreSQL, MongoDB |
    | How it is served | The stored `.html` file is sent unchanged | The server `runs code` and builds the page |
    | File extension | `.html`, `.htm` | `.php`, `.jsp`, `.aspx` |
    | To change content | Edit the `HTML file` and re-upload | Update the `database`, via an admin panel |
    | Speed | `Faster` — nothing to compute | Slower — code runs, database is queried |
    | Hosting | `Cheap`, any web space | Needs a server able to run code |
    | Security | `Very secure` — no database, no server code | Exposed to `SQL injection`, session attacks |
    | Interactivity | Very limited | `High` — login, search, cart, comments |
    | Content scalability | Poor — 100 pages means 100 files | `Excellent` — one template serves thousands |
    | Who can update it | Someone who can edit HTML | `Any trained user` |
    | Examples | Portfolio, brochure site, documentation | Facebook, Amazon, internet banking, WordPress |

    How each is served
    ```
       STATIC
            browser --request--> web server --> sends the stored
                                                index.html
            NO processing. The file stored is the file sent.

       DYNAMIC
            browser --request--> web server --> runs PHP / JSP code
                                            --> QUERIES THE DATABASE
                                            --> builds the HTML
                                            --> sends it back
            The HTML did not exist until the request arrived.
    ```
    ```mermaid
    flowchart LR
        A[Browser] -->|request| B[Web server]
        B -->|static: send the stored file| A
        B -->|dynamic| C[Server-side code]
        C --> D[(Database)]
        D --> C
        C -->|generated HTML| A
    ```

    The two kinds of "dynamic", which are often confused
    ```
       SERVER-SIDE DYNAMIC
            The server builds different HTML for each request, from a
            database. This is what "dynamic web page" normally means.
            Technologies : PHP , JSP , ASP.NET , Node.js

       CLIENT-SIDE DYNAMIC
            The HTML file is fixed, but JAVASCRIPT changes the page
            in the browser after it loads - an image slider, a
            dropdown menu, a form validated as you type.
            The FILE is static ; the PAGE behaves dynamically.
    ```
    - Which to choose: a `static` page is right when the content rarely changes, there is no login, and speed and security matter most. A `dynamic` page becomes necessary the moment users must log in, content changes often, or the same page must show different data to different visitors.
    - Two modern qualifications: a `static site generator` such as Jekyll or Hugo compiles templates and content into plain HTML, giving a static page the maintainability of a dynamic one; and a `single-page application` serves one static HTML file that then fetches data from an `API` and rewrites itself — a static file producing a fully dynamic page.

15. **(ক) কোন প্রতিষ্ঠানের Web page development এ HTML এবং CSS এর ভূমিকা কি? শুধুমাত্র HTML এবং CSS ব্যবহার করে কোন ধরনের Web Page Development করা যেতে পারে?** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 771 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) The role of HTML and CSS in an organisation's web page development

    HTML — structure and content
    - `HTML (HyperText Markup Language)` provides the `skeleton` of every page. It defines what each piece of content `is` — a heading, a paragraph, a table, a form field, a link.
    ```
       ITS ROLE IN AN ORGANISATION'S SITE

         marks up the CONTENT the organisation wants to publish -
              notices, circulars, product details, contact
              information
         builds the FORMS through which visitors submit data
         builds the TABLES for price lists, tender notices, results
         creates the NAVIGATION linking every page
         supplies the SEMANTIC structure - <header> , <nav> ,
              <main> , <article> , <footer> - which is what search
              engines and screen readers rely on
         holds the META information : <title> , description ,
              charset. <meta charset="UTF-8"> is what makes BANGLA
              text display correctly
         embeds images, audio and video
    ```

    CSS — presentation and identity
    - `CSS (Cascading Style Sheets)` controls how the page `looks`. It is where the organisation's visual identity lives.
    ```
       ITS ROLE IN AN ORGANISATION'S SITE

         enforces the BRAND - the official colours, logo placement
              and typography, applied consistently across every page
         controls the LAYOUT - header, sidebar, content, footer -
              using Flexbox and Grid
         makes the site RESPONSIVE, so it works on the phone most
              visitors actually use
         provides a PRINT STYLESHEET, so a notice or a form prints
              cleanly without the navigation
         supports ACCESSIBILITY - adequate contrast, readable font
              sizes, visible focus outlines
         gives ONE-POINT MAINTENANCE : changing one CSS file
              restyles the entire site. Without it, a change of the
              official colour would mean editing every page.
    ```
    ```
       THE DIVISION

            HTML  =  STRUCTURE and CONTENT   -> WHAT it is
            CSS   =  PRESENTATION            -> HOW it looks
    ```

    What kind of web pages can be developed with HTML and CSS alone
    ```
       STATIC WEB PAGES - the content is fixed and the same for
       every visitor.

       SUITABLE FOR
         an INFORMATION or BROCHURE site - about us, mission,
              history, organogram, contact
         a NOTICE BOARD or circular page, updated occasionally by
              hand
         a DEPARTMENT or officer DIRECTORY
         a portfolio or product CATALOGUE with a fixed range
         DOCUMENTATION , a manual , a citizen's charter
         a LANDING PAGE for a campaign
         a printable FORM to download
         a tender notice list
       All of these can be built, styled, made responsive and made
       accessible with HTML and CSS only.
    ```

    What cannot be built, and why
    ```
       NOT POSSIBLE with HTML and CSS alone :

         LOGIN and user accounts - no server-side code to check a
              password, no session
         FORM PROCESSING - a form can be DISPLAYED but nothing can
              RECEIVE the submitted data
         DATABASE-driven content - no search, no filtering, no
              sorting of real data
         a CONTENT MANAGEMENT panel - every update needs an HTML
              editor
         e-COMMERCE - cart, payment, order records
         any CALCULATION or business logic

       WHAT IS NEEDED TO ADD THEM
         JAVASCRIPT              client-side interactivity and
              validation, fetching data from an API
         a SERVER-SIDE LANGUAGE  PHP , Python , Java , Node.js
         a DATABASE              MySQL , PostgreSQL
         a CMS                   WordPress , Drupal - so non-
              technical staff can publish notices themselves
    ```
    - The practical judgement for an organisation: `HTML and CSS are enough for a site that publishes information`, and such a site is fast, cheap, secure and easy to host. The moment the organisation needs `citizens to submit applications`, `staff to log in`, or `non-technical officers to publish notices themselves`, a server-side language, a database and usually a `CMS` become necessary.

16. **(ii) HTML ও CSS কী?** *[BPSC Assistant Network Engineer 2020 compact it 950-951 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) HTML
    - `HTML` stands for `HyperText Markup Language`. It is the standard language used to create the `structure and content` of a web page — headings, paragraphs, images, links, lists, tables and forms.
    ```html
       <h1>Welcome</h1>
       <p>This is a <strong>paragraph</strong>.</p>
       <img src="photo.jpg" alt="A photograph">
       <a href="about.html">About us</a>
    ```
    ```
       POINTS TO NOTE
         It is a MARKUP language, NOT a programming language - it
              has no variables, no conditions and no loops.
         "HYPERTEXT" means text containing LINKS to other documents ;
              that is what makes the web a web.
         It uses TAGS written in angle brackets. Most come in pairs :
              <p> ... </p>
         Some are EMPTY tags with no closing tag : <br> , <hr> ,
              <img> , <input>
         The current version is HTML5.
         A page has two parts : <head> for information ABOUT the
              page, and <body> for what is DISPLAYED.
    ```

    CSS
    - `CSS` stands for `Cascading Style Sheets`. It controls the `presentation` of an HTML document — colours, fonts, spacing, borders, backgrounds and layout.
    ```css
       h1    { color: navy; font-size: 32px; text-align: center; }
       p     { line-height: 1.6; margin-bottom: 15px; }
       .card { border: 1px solid #ccc; padding: 20px;
               border-radius: 8px; }
    ```
    ```
       THE SYNTAX

            selector  {  property : value ;  }
              h1      {  color    : navy ;  }

       THREE WAYS TO APPLY IT
         INLINE     inside the tag :
                    <p style="color:red">text</p>
         INTERNAL   in a <style> block in the <head>
         EXTERNAL   in a separate .css file, linked with
                    <link rel="stylesheet" href="style.css">
                    THE BEST METHOD - one file styles the whole site.

       "CASCADING" means the rules are applied in a defined ORDER OF
       PRIORITY when several rules target the same element :

            inline style  >  ID (#id)  >  class (.class)  >
            element (p)

       The more SPECIFIC rule wins ; between rules of equal
       specificity, the LAST one written wins.
    ```

    The relationship between them
    ```
            HTML  =  STRUCTURE and CONTENT   ->  WHAT it is
            CSS   =  PRESENTATION            ->  HOW it looks
            JavaScript = BEHAVIOUR           ->  WHAT IT DOES

       The analogy usually given, a house :
            HTML  =  the walls and rooms
            CSS   =  the paint, tiles and furniture
            JS    =  the electricity and plumbing
    ```
    - Why the separation matters: one external CSS file restyles a thousand pages at once; the HTML stays readable; the same content can be presented differently on a phone, a desktop and a printer; and the stylesheet is `cached` by the browser, so pages after the first load faster.

17. **একটি Image ও একটি Web site URL HTML প্রদর্শন করার জন্য প্রয়োজনীয় code লিখুন?** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1022 (ET: N/A)]*

Answer: The code needed to display an image and a website URL (a hyperlink).
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Image and Link</title>
    </head>
    <body>

        <!-- 1. DISPLAY AN IMAGE -->
        <img src="photo.jpg" alt="A photograph" width="300"
             height="200">

        <!-- 2. DISPLAY A WEBSITE URL as a clickable link -->
        <a href="https://www.example.com">Visit Example.com</a>

    </body>
    </html>
    ```

    The image tag
    ```html
       <img src="photo.jpg" alt="A photograph" width="300">
    ```
    ```
       <img> is an EMPTY tag - there is NO closing </img>.

       src     REQUIRED - the path or URL of the image
            relative :  src="images/photo.jpg"
            absolute :  src="https://example.com/photo.jpg"
       alt     the alternative text. Shown if the image fails to
            load, and READ ALOUD by a screen reader. Never omit it.
       width , height   the size in pixels. Setting both stops the
            page jumping about while the image loads.
    ```

    The hyperlink tag
    ```html
       <a href="https://www.example.com">Visit Example.com</a>
    ```
    ```
       <a> is the ANCHOR tag , and href is the destination.

       The TEXT BETWEEN THE TAGS is what the visitor clicks.
       To show the URL itself as the visible text :

            <a href="https://www.example.com">https://www.example.com</a>

       target="_blank"  opens it in a NEW TAB. With it, always add
            rel="noopener noreferrer" - otherwise the new page can
            reach back and control the original page.
    ```

    An image used as a link — both together
    ```html
       <a href="https://www.example.com" target="_blank"
          rel="noopener noreferrer">
           <img src="logo.png" alt="Visit Example.com" width="150">
       </a>
    ```
    - Here the `<img>` sits `inside` the `<a>`, so clicking the picture follows the link. The `alt` text should then describe the `destination`, not the picture, because that is what a screen reader announces.

    A fuller version, with a caption
    ```html
       <figure>
           <img src="photo.jpg" alt="Head office building"
                width="300">
           <figcaption>
               Our head office -
               <a href="https://www.example.com/contact">see
               directions</a>
           </figcaption>
       </figure>
    ```
    - Note the difference between the two tags: `<img>` is an `empty` element with no closing tag, while `<a>` is a `container` element whose content is the clickable text or image. Both are `inline` elements, so they sit within a line of text rather than starting a new one.

18. **Write down the description of `<header>`, `<footer>`, `<section>` and `<article>` tag of new HTML5.** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1057 (ET: AUST)]*

Answer: These are four of the `semantic` elements introduced in HTML5. They replace anonymous `<div>` containers with tags that state `what the content is`.

    `<header>`
    - Introductory content for the page or for a section — typically a logo, a site title, a heading, and often the navigation.
    ```html
       <header>
           <img src="logo.png" alt="Company logo">
           <h1>My Company</h1>
           <nav>
               <a href="index.html">Home</a>
               <a href="about.html">About</a>
           </nav>
       </header>
    ```
    ```
       A page may contain MORE THAN ONE <header> - one for the page
       and one inside each <article> or <section>.
       It must NOT be placed inside a <footer> or another <header>.
    ```

    `<footer>`
    - Closing content for the page or a section — copyright, contact details, author information, related links, a privacy policy.
    ```html
       <footer>
           <p>&copy; 2026 My Company. All rights reserved.</p>
           <p>Contact : info@example.com</p>
           <nav><a href="privacy.html">Privacy policy</a></nav>
       </footer>
    ```
    ```
       As with <header>, a page may have SEVERAL <footer> elements -
       the page footer plus one inside each article, giving the
       author and date of that article.
    ```

    `<section>`
    - A `thematic grouping` of content — a distinct part of a document that would normally carry a heading. It is used to divide a page into logical chapters.
    ```html
       <section>
           <h2>Our Services</h2>
           <p>We provide web development and hosting.</p>
       </section>

       <section>
           <h2>Our Clients</h2>
           <p>We work with banks and government agencies.</p>
       </section>
    ```
    ```
       RULE OF THUMB : a <section> should have a HEADING. If it does
       not, it is probably a plain <div>.
       <section> is NOT a styling container - use <div> for that.
    ```

    `<article>`
    - Content that is `self-contained` and would make sense on its own if taken out of the page and republished elsewhere.
    ```html
       <article>
           <header>
               <h2>Understanding HTML5</h2>
               <p>By Rahim, 12 March 2026</p>
           </header>
           <p>HTML5 introduced semantic elements ...</p>
           <footer><p>Filed under : Web Development</p></footer>
       </article>
    ```
    ```
       Examples of an <article> : a blog post , a news story , a
       forum post , a product card , a user comment.

       THE TEST : could this content be taken out and published in
       an RSS feed on its own and still make sense ? If yes, it is an
       <article> ; if no, it is a <section>.
    ```

    `<section>` against `<article>` — the distinction examiners test
    ```
       <ARTICLE>  is SELF-CONTAINED and independently distributable.
       <SECTION>  is a THEMATIC PART of a larger whole and depends on
                  its surroundings.

       They can be nested EITHER WAY :

            an ARTICLE divided into SECTIONS
                 <article>
                     <section><h3>Introduction</h3>...</section>
                     <section><h3>Method</h3>...</section>
                 </article>

            a SECTION containing several ARTICLES
                 <section>
                     <h2>Latest News</h2>
                     <article>...</article>
                     <article>...</article>
                 </section>
    ```

    How they fit together
    ```html
    <body>
        <header>  ... site logo and title ...  </header>
        <nav>     ... the menu ...             </nav>
        <main>
            <section>
                <h2>Blog</h2>
                <article> ... first post ...  </article>
                <article> ... second post ... </article>
            </section>
            <aside>   ... sidebar ...          </aside>
        </main>
        <footer>  ... copyright ...            </footer>
    </body>
    ```
    ```
       THE OTHER HTML5 SEMANTIC ELEMENTS
            <nav>      navigation links
            <main>     the main content ; ONE per page
            <aside>    tangentially related content - a sidebar
            <figure> , <figcaption>   an image with a caption
            <time>     a machine-readable date
            <mark>     highlighted text
            <details> , <summary>     a collapsible block
    ```
    - Why semantic tags matter rather than plain `<div>`s: a `screen reader` can jump straight to `<main>` or list the page's sections, which a page of anonymous divs cannot offer; `search engines` use the structure to understand what the page is about; and the markup is far easier for a person to read and maintain. Visually, `<header>` and `<div>` render identically — the whole benefit is in the `meaning`.

19. **(ক) Web portal ও Web hosting কী? Web hosting এর প্রয়োজনীয়তা ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1089-1090 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) What a web portal is
    - A `web portal` is a website that acts as a `single gateway` to many different services, applications and sources of information, usually personalised for the logged-in user.
    ```
       A WEBSITE presents information ; a PORTAL gives ACCESS to
       SERVICES, usually after a LOGIN, and shows each user their own
       data.

       +----------------------------------------------------+
       |                    WEB PORTAL                      |
       |   single login  ->  personalised dashboard         |
       +----------------------------------------------------+
          |          |           |          |           |
       +------+  +-------+  +--------+  +-------+  +--------+
       | Mail |  | News  |  | Search |  | Forms |  | Reports|
       +------+  +-------+  +--------+  +-------+  +--------+

       EXAMPLES
         GOVERNMENT : bangladesh.gov.bd , the National Portal ,
              a university student portal, a tax e-filing portal
         BANKING    : an internet banking portal - accounts, cards,
              transfers, statements in one place
         CORPORATE  : an employee self-service portal - payslip,
              leave, attendance
    ```
    ```
       FEATURES OF A PORTAL
         single sign-on for many services
         a PERSONALISED dashboard - each user sees their own data
         ROLE-BASED access - a student, a teacher and an
              administrator see different things
         integration with several back-end systems
         search across all the content
         notifications and messaging
    ```

    What web hosting is
    - `Web hosting` is the service of `storing a website's files on a server that is permanently connected to the internet`, so that anyone can reach them at any time.
    ```
       Website files  --uploaded-->  HOSTING SERVER  --served-->
                                     (always on)          visitors

       The hosting provider supplies : disk space , bandwidth , a web
       server (Apache or Nginx) , a database , email accounts , an
       SSL certificate , and backups.
    ```

    Why web hosting is necessary
    ```
       1. THE SITE MUST BE AVAILABLE 24 HOURS A DAY
            A personal computer would have to stay switched on, on a
            fixed IP, with an uninterrupted connection, forever. A
            hosting provider has redundant power, generators and
            multiple internet links - which in Bangladesh matters
            very directly.

       2. A PUBLIC, STATIC ADDRESS IS NEEDED
            A home connection gets a CHANGING private IP address, so
            the site could not be found. Hosting gives a fixed public
            IP that the DOMAIN NAME can point to.

       3. BANDWIDTH AND SPEED
            A data centre has far more upload bandwidth than any
            home or office line, so many visitors can be served at
            once.

       4. THE SERVER SOFTWARE IS PROVIDED AND MAINTAINED
            Apache or Nginx, PHP, MySQL, mail - installed, patched
            and configured by the provider.

       5. SECURITY
            Firewall, DDoS protection, SSL certificates, malware
            scanning, and prompt patching - beyond what most
            organisations can do themselves.

       6. BACKUP AND RECOVERY
            Automated daily backups, and the ability to restore after
            a failure or an attack.

       7. SCALABILITY
            More disk, more bandwidth or a bigger plan can be added
            as traffic grows, without buying hardware.

       8. COST
            Buying, housing, powering, cooling and administering a
            server is far more expensive than renting space, for all
            but the largest organisations.

       9. TECHNICAL SUPPORT
            Someone is responsible when it stops working - which is
            the real value of a support contract.
    ```

    Types of hosting
    ```
       SHARED         many sites on one server. Cheapest ; limited
            resources ; a busy neighbour slows you down.
       VPS            a virtual private server - a guaranteed slice
            of a machine, with root access.
       DEDICATED      a whole physical server. Expensive, maximum
            control.
       CLOUD          resources scale on demand and are billed by
            use - AWS , Azure , Google Cloud.
       MANAGED        the provider handles updates, security and
            backups - e.g. managed WordPress hosting.
       COLOCATION     you own the server ; the provider supplies the
            rack, power and connectivity.
    ```
    - The two things that must go together: `hosting` provides the space, and a `domain name` provides the address. Hosting without a domain is reachable only by IP address; a domain without hosting points at nothing. Both are rented, and both must be `renewed` — a site that vanishes is very often a domain nobody renewed.

20. **(ক) Web site কি? Linear/Sequential structure and Tree/Hierarchical structure সচিত্র বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1091 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) What a website is
    - A `website` is a collection of `related web pages`, stored on a web server under one `domain name`, and reachable over the internet. The entry page is called the `home page`.
    ```
       A website is made of three things :
            DOMAIN NAME   the address - www.example.com
            WEB HOSTING   the server space where the files live
            THE FILES     HTML , CSS , JavaScript , images , and for
                          a dynamic site the server-side code and a
                          DATABASE
    ```
    - Kinds of website: `static` (fixed content, HTML and CSS only) and `dynamic` (generated per request from a database). By purpose they may be informational, e-commerce, portal, blog, educational or government.

    Linear / sequential structure
    ```
       The pages are arranged in ONE FIXED ORDER. Each page links
       only to the NEXT and the PREVIOUS one, so the visitor is led
       through the content step by step.

       +--------+     +--------+     +--------+     +--------+
       | Page 1 |---->| Page 2 |---->| Page 3 |---->| Page 4 |
       |  Intro |<----| Step 1 |<----| Step 2 |<----| Finish |
       +--------+     +--------+     +--------+     +--------+
    ```
    ```mermaid
    flowchart LR
        A[Page 1: Intro] --> B[Page 2: Step 1]
        B --> C[Page 3: Step 2]
        C --> D[Page 4: Finish]
        D --> C
        C --> B
        B --> A
    ```
    ```
       USED FOR
         a TUTORIAL or lesson that must be read in order
         a multi-step FORM or registration WIZARD
         an online test taken question by question
         a slide presentation or e-book

       ADVANTAGES     simple ; the visitor cannot get lost ; the
            order of the content is guaranteed.
       DISADVANTAGES  RIGID - to reach page 4 the visitor must pass
            through 2 and 3. Useless for a site whose pages are
            independent.
    ```

    Tree / hierarchical structure
    ```
       The pages are arranged in LEVELS, branching out from the home
       page. This is the usual structure for a website.

                            +-----------+
                            | HOME PAGE |
                            +-----------+
                           /      |      \
                  +--------+  +--------+  +---------+
                  |Products|  | About  |  | Contact |
                  +--------+  +--------+  +---------+
                   /      \        |
           +---------+ +---------+ +---------+
           | Laptops | | Printers| | History |
           +---------+ +---------+ +---------+
              /    \
       +--------+ +--------+
       | HP     | | Dell   |
       +--------+ +--------+
    ```
    ```mermaid
    flowchart TD
        H[Home Page] --> P[Products]
        H --> A[About]
        H --> C[Contact]
        P --> L[Laptops]
        P --> Pr[Printers]
        L --> HP[HP]
        L --> D[Dell]
        A --> Hi[History]
    ```
    ```
       USED FOR
         almost every ordinary website - company, government,
         educational, e-commerce

       ADVANTAGES     ORGANISED and easy to navigate ; the visitor
            always knows where they are ; it SCALES to thousands of
            pages ; a menu can be built directly from the tree.
       DISADVANTAGES  a DEEP tree means many clicks to reach a page.
            The usual rule is a MAXIMUM OF THREE LEVELS, and the
            "three-click rule" - any page reachable within three
            clicks of the home page.
    ```

    Comparison
    ```
       +----------------+---------------------+---------------------+
       | Point          | LINEAR              | TREE                |
       +----------------+---------------------+---------------------+
       | Order          | FIXED               | free                |
       | Navigation     | next / previous     | menu , breadcrumb   |
       | Visitor choice | none                | full                |
       | Scales to many | NO                  | YES                 |
       |   pages        |                     |                     |
       | Best for       | tutorial , wizard   | ordinary website    |
       +----------------+---------------------+---------------------+
    ```
    - The two other structures worth naming in one line: the `webbed` or `network` structure, where every page links to many others, as Wikipedia does — flexible, but the visitor can easily get lost; and the `hybrid`, which most real sites actually use — a tree for the overall site with a linear sequence inside a checkout or registration flow.

21. **(খ) নিচের টেবিলটি তৈরি করার জন্য HTML কোড লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1091 (ET: N/A)]*

| Customer Name | Product Name |  |  | Product Manufacturer |
|---|---|---|---|---|
| Mr. Jhon | Computer | Printer | Modem | HP |
|  |  |  |  | HP |
|  |  |  |  | ASUS |

| Customer Name | Product Name |  |  | Product Manufacturer |
|---|---|---|---|---|
| Mr. Jhon | Computer | Printer | Modem | HP |
|  |  |  |  | HP |
|  |  |  |  | ASUS |

    Answer: (Answered in English, as required for IT topics.) The table has `5 columns`. `Product Name` spans three of them in the header, and in the body the customer name and the three product cells span all three data rows, while the manufacturer column has a separate value in each row. So both `colspan` and `rowspan` are needed.

    The HTML code
    ```html
    <table border="1" cellpadding="5" cellspacing="0">
        <tr>
            <th rowspan="2">Customer Name</th>
            <th colspan="3">Product Name</th>
            <th rowspan="2">Product Manufacturer</th>
        </tr>
        <tr>
            <th>1</th>
            <th>2</th>
            <th>3</th>
        </tr>
        <tr>
            <td rowspan="3">Mr. Jhon</td>
            <td rowspan="3">Computer</td>
            <td rowspan="3">Printer</td>
            <td rowspan="3">Modem</td>
            <td>HP</td>
        </tr>
        <tr>
            <td>HP</td>
        </tr>
        <tr>
            <td>ASUS</td>
        </tr>
    </table>
    ```

    The output
    ```
       +---------------+----------------------------+--------------+
       | Customer Name |        Product Name        | Product      |
       |               +----------+--------+--------+ Manufacturer |
       |               |    1     |   2    |   3    |              |
       +---------------+----------+--------+--------+--------------+
       |               |          |        |        |     HP       |
       |               |          |        |        +--------------+
       |   Mr. Jhon    | Computer | Printer| Modem  |     HP       |
       |               |          |        |        +--------------+
       |               |          |        |        |    ASUS      |
       +---------------+----------+--------+--------+--------------+
    ```
    - The simpler version, if the sub-header row of `1 2 3` is not wanted:
    ```html
    <table border="1" cellpadding="5" cellspacing="0">
        <tr>
            <th>Customer Name</th>
            <th colspan="3">Product Name</th>
            <th>Product Manufacturer</th>
        </tr>
        <tr>
            <td rowspan="3">Mr. Jhon</td>
            <td rowspan="3">Computer</td>
            <td rowspan="3">Printer</td>
            <td rowspan="3">Modem</td>
            <td>HP</td>
        </tr>
        <tr><td>HP</td></tr>
        <tr><td>ASUS</td></tr>
    </table>
    ```

    The more natural layout for the same data
    ```html
    <!-- each product paired with its own manufacturer -->
    <table border="1" cellpadding="5" cellspacing="0">
        <tr>
            <th>Customer Name</th>
            <th>Product Name</th>
            <th>Product Manufacturer</th>
        </tr>
        <tr>
            <td rowspan="3">Mr. Jhon</td>
            <td>Computer</td><td>HP</td>
        </tr>
        <tr><td>Printer</td><td>HP</td></tr>
        <tr><td>Modem</td><td>ASUS</td></tr>
    </table>
    ```
    ```
       +---------------+--------------+----------------------+
       | Customer Name | Product Name | Product Manufacturer |
       +---------------+--------------+----------------------+
       |               | Computer     |         HP           |
       |               +--------------+----------------------+
       |   Mr. Jhon    | Printer      |         HP           |
       |               +--------------+----------------------+
       |               | Modem        |        ASUS          |
       +---------------+--------------+----------------------+
    ```

    The rule for checking any spanned table
    ```
       colspan   how many COLUMNS the cell spans - ACROSS
       rowspan   how many ROWS the cell spans - DOWN

       A cell covered by a span from above must be OMITTED from that
       row's HTML - it is NOT written as an empty <td>.

       COUNT THE COLUMNS IN EVERY ROW, including cells spanned in
       from above :

            row 1 :  1 + 3 + 1                        = 5
            row 2 :  (2 spanned in) + 1 + 1 + 1       = 5
            row 3 :  1 + 1 + 1 + 1 + 1                = 5
            row 4 :  (4 spanned in) + 1               = 5
            row 5 :  (4 spanned in) + 1               = 5

       If the totals differ, the table renders ragged. Writing an
       extra empty <td> in a row that already has a cell spanned into
       it is the single commonest mistake with rowspan.
    ```

22. **(b) Explain `<div>`.............`</div>` tag of HTML with an example.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1143-1144 (ET: N/A)]*

Answer: What `<div>` is
    - `<div>` is a `block-level container` with no meaning of its own. It groups other elements so they can be styled or positioned together, or manipulated as a unit by JavaScript. The name is short for `division`.
    ```
       It has NO visual effect by itself - it adds no border, no
       colour, no spacing. It is a plain box.

       Being BLOCK-LEVEL, it :
            starts on a NEW LINE
            takes the FULL WIDTH available
            can contain both block and inline elements
    ```

    Example
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>div example</title>
        <style>
            .card {
                border: 1px solid #ccc;
                border-radius: 8px;
                padding: 20px;
                margin-bottom: 15px;
                background-color: #f9f9f9;
                width: 300px;
            }
            .card h3 { color: navy; margin-top: 0; }
            #main    { max-width: 900px; margin: 0 auto; }
        </style>
    </head>
    <body>

        <div id="main">

            <div class="card">
                <h3>Laptop</h3>
                <p>Price : 60,000 Tk</p>
                <p>Manufacturer : HP</p>
            </div>

            <div class="card">
                <h3>Printer</h3>
                <p>Price : 12,000 Tk</p>
                <p>Manufacturer : Canon</p>
            </div>

        </div>

    </body>
    </html>
    ```
    ```
       WHAT THIS SHOWS

       1. GROUPING - each product's heading and paragraphs are
          wrapped in ONE div, so they move and style together.
       2. class="card"  applies the SAME style to MANY divs.
       3. id="main"     identifies ONE div - an id must be UNIQUE on
          the page.
       4. Nesting - divs inside divs is normal and is how page
          layout is built.
    ```

    Using `<div>` for layout
    ```html
       <div id="wrapper">
           <div id="header">   ... logo ...     </div>
           <div id="nav">      ... menu ...     </div>
           <div id="content">  ... main text ... </div>
           <div id="sidebar">  ... links ...    </div>
           <div id="footer">   ... copyright ... </div>
       </div>
    ```
    ```
       This was the standard way to build a page before HTML5. It
       still works, but the SEMANTIC elements are now preferred :

            <div id="header">  ->  <header>
            <div id="nav">     ->  <nav>
            <div id="content"> ->  <main>
            <div id="sidebar"> ->  <aside>
            <div id="footer">  ->  <footer>

       They render IDENTICALLY - the benefit is MEANING. A screen
       reader can jump to <main> ; it cannot know what
       <div id="content"> is for.
    ```

    `<div>` against `<span>`

    | Point | `<div>` | `<span>` |
    |---|---|---|
    | Display | `Block-level` | `Inline` |
    | New line | `Yes` | `No` |
    | Width | Full width available | Only what the content needs |
    | May contain | Block and inline elements | `Inline` elements only |
    | Used for | Grouping `sections` | Styling `part of a line` |
    ```html
       <div>This starts on a new line.</div>
       <p>This word is <span style="color:red">red</span> only.</p>
    ```
    - When `<div>` is still the right choice: purely for `styling or layout`, where no semantic element fits — a flexbox wrapper, a grid cell, a modal container. When it is the wrong choice: where a semantic element exists. Using `<div>` for a page header, a navigation menu or a button is worse markup for no benefit.
    - One accessibility warning: a `<div>` styled to look like a button is `not` a button. A real `<button>` is reachable by `Tab`, activates on `Enter` and `Space`, and is announced as a button. A styled `<div>` does none of those unless each is added by hand.

23. **Write HTML5 media tags name.** *[Probashi Kallyan Bank Programmer 2019 compact it 1158 (ET: AUST)]*

Answer: The HTML5 media tags are:
    ```
       <audio>    plays sound - music, a recording
       <video>    plays video
       <source>   specifies ALTERNATIVE media files, so the browser
                  can pick a format it supports
       <track>    adds subtitles, captions or chapters to a video
       <embed>    embeds external content or a plug-in
       <object>   embeds an external resource - PDF, Flash, applet
       <param>    passes parameters to an <object>
    ```
    - Of these, `<audio>` and `<video>` are the two genuinely new in HTML5, and they are the answer if only the main ones are asked for. Before HTML5, playing media needed a plug-in such as Flash; these tags made it native to the browser.

    `<audio>`
    ```html
       <audio controls>
           <source src="song.mp3" type="audio/mpeg">
           <source src="song.ogg" type="audio/ogg">
           Your browser does not support the audio element.
       </audio>
    ```
    ```
       ATTRIBUTES
            controls   show the play, pause and volume controls -
                 without it the player is INVISIBLE
            autoplay   start automatically (most browsers now BLOCK
                 this unless muted)
            loop       repeat when it ends
            muted      start silent
            preload    none | metadata | auto
            src        the file, if only one format is used

       FORMATS : MP3 , OGG , WAV
    ```

    `<video>`
    ```html
       <video width="640" height="360" controls poster="thumb.jpg">
           <source src="movie.mp4" type="video/mp4">
           <source src="movie.webm" type="video/webm">
           <track src="subtitles_en.vtt" kind="subtitles"
                  srclang="en" label="English">
           Your browser does not support the video tag.
       </video>
    ```
    ```
       ATTRIBUTES
            controls , autoplay , loop , muted , preload
            width , height   the display size
            poster           the still image shown before playing

       FORMATS : MP4 (H.264) , WebM , Ogg
            MP4 is the most widely supported - if only one format is
            provided, use MP4.
    ```

    Why `<source>` is used rather than a single `src`
    ```
       No single format is supported by every browser. Listing
       several <source> elements lets the browser take the FIRST one
       it can play :

            <video controls>
                <source src="movie.mp4"  type="video/mp4">
                <source src="movie.webm" type="video/webm">
                Fallback text for a very old browser.
            </video>

       The TEXT between the tags is the FALLBACK, shown only by a
       browser that supports neither the tag nor any source.
    ```

    `<track>` — subtitles and captions
    ```html
       <track src="captions_bn.vtt" kind="captions" srclang="bn"
              label="Bangla" default>
    ```
    ```
       kind can be : subtitles , captions , descriptions , chapters ,
       metadata.
       The file is in WebVTT format. Captions are what make video
       content ACCESSIBLE to deaf users, and they also let search
       engines index what is said.
    ```
    - Two practical points. `autoplay` with sound is blocked by every modern browser, so an autoplaying video must also be `muted`. And the media tags come with a full `JavaScript API` — `play()`, `pause()`, `currentTime`, `volume`, and events such as `ended` and `timeupdate` — which is what allows a custom player to be built without any plug-in.

24. **Write down the proper use of these semantics in HTML-`<header>`, `<footer>`, `<article>` and `<section>`.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1162 (ET: N/A)]*, *[Agrani Bank Ltd. Officer (ICT) 2017 compact it 1224 (ET: N/A)]*

Answer: These four `semantic` elements from HTML5 replace anonymous `<div>` containers with tags that state what the content `is`.

    `<header>`
    ```
       PROPER USE : introductory content for the page OR for a
       section - a logo, a site title, a heading, and often the
       navigation.
    ```
    ```html
       <header>
           <img src="logo.png" alt="Company logo">
           <h1>My Company</h1>
           <nav>
               <a href="index.html">Home</a>
               <a href="about.html">About</a>
           </nav>
       </header>
    ```
    ```
       A page may have SEVERAL <header> elements - one for the page,
       and one inside each <article> or <section>.
       It must NOT be nested inside a <footer> or another <header>.
    ```

    `<section>`
    ```
       PROPER USE : a THEMATIC GROUPING of content - a distinct part
       of a document that would normally carry a heading.
    ```
    ```html
       <section>
           <h2>Our Services</h2>
           <p>We provide web development and hosting.</p>
       </section>
    ```
    ```
       RULE OF THUMB : a <section> should HAVE A HEADING. If it does
       not, it is probably a plain <div>.
       <section> is NOT a styling wrapper - use <div> for that.
    ```

    `<article>`
    ```
       PROPER USE : content that is SELF-CONTAINED and would still
       make sense if taken out of the page and republished
       elsewhere.
    ```
    ```html
       <article>
           <header>
               <h2>Understanding HTML5</h2>
               <p>By Rahim, 12 March 2026</p>
           </header>
           <p>HTML5 introduced semantic elements ...</p>
           <footer><p>Filed under : Web Development</p></footer>
       </article>
    ```
    ```
       Examples : a blog post , a news story , a forum post , a
       product card , a user comment.

       THE TEST : could it appear in an RSS feed on its own and still
       make sense ? If yes, it is an <article>.
    ```

    `<footer>`
    ```
       PROPER USE : closing content for the page or a section -
       copyright, contact details, author information, related
       links, a privacy policy.
    ```
    ```html
       <footer>
           <p>&copy; 2026 My Company. All rights reserved.</p>
           <nav><a href="privacy.html">Privacy policy</a></nav>
       </footer>
    ```

    `<section>` against `<article>` — the point examiners test
    ```
       <ARTICLE>  SELF-CONTAINED , independently distributable.
       <SECTION>  a THEMATIC PART of a larger whole ; it depends on
                  its surroundings.

       They nest EITHER WAY :

            an ARTICLE divided into SECTIONS
                 <article>
                     <section><h3>Introduction</h3>...</section>
                     <section><h3>Method</h3>...</section>
                 </article>

            a SECTION containing several ARTICLES
                 <section>
                     <h2>Latest News</h2>
                     <article>...</article>
                     <article>...</article>
                 </section>
    ```

    The whole page together
    ```html
    <body>
        <header>  ... logo and site title ...  </header>
        <nav>     ... the menu ...             </nav>
        <main>
            <section>
                <h2>Blog</h2>
                <article> ... first post ...  </article>
                <article> ... second post ... </article>
            </section>
            <aside>   ... sidebar ...          </aside>
        </main>
        <footer>  ... copyright ...            </footer>
    </body>
    ```
    - Common misuses to avoid: using `<section>` merely to wrap something for styling, when a `<div>` is meant; using `<article>` for a page fragment that could not stand alone; and putting a page's only `<h1>` inside an `<article>` rather than in the page `<header>`.
    - Why the semantic tags matter at all: they render `identically` to a `<div>`. The benefit is entirely in the `meaning` — a screen reader can jump straight to `<main>` or list the page's sections, and a search engine can tell an article's content from the navigation around it. Neither is possible with a page of anonymous divs.

25. **Write down the name of some HTML5 media tag.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1162 (ET: N/A)]*

Answer: The HTML5 media tags are:
    ```
       <audio>    plays sound - music, a recording
       <video>    plays video
       <source>   lists ALTERNATIVE media files, so the browser can
                  choose a format it supports
       <track>    adds subtitles, captions or chapters to a video
       <embed>    embeds external content or a plug-in
       <object>   embeds an external resource - PDF, applet
       <param>    passes parameters to an <object>
    ```
    - `<audio>` and `<video>` are the two genuinely new in HTML5, and they are the answer if only the main ones are wanted. Before HTML5, playing media in a browser required a plug-in such as Flash.

    `<audio>`
    ```html
       <audio controls>
           <source src="song.mp3" type="audio/mpeg">
           <source src="song.ogg" type="audio/ogg">
           Your browser does not support the audio element.
       </audio>
    ```
    ```
       Attributes : controls , autoplay , loop , muted , preload , src
       Formats    : MP3 , OGG , WAV

       Without  controls  the player is INVISIBLE - the commonest
       mistake.
    ```

    `<video>`
    ```html
       <video width="640" height="360" controls poster="thumb.jpg">
           <source src="movie.mp4" type="video/mp4">
           <source src="movie.webm" type="video/webm">
           <track src="subtitles_en.vtt" kind="subtitles"
                  srclang="en" label="English">
           Your browser does not support the video tag.
       </video>
    ```
    ```
       Attributes : controls , autoplay , loop , muted , preload ,
                    width , height , poster
       Formats    : MP4 (H.264) , WebM , Ogg

       MP4 is the most widely supported ; if only one format is
       provided, use MP4.
    ```

    Why `<source>` and the fallback text are used
    ```
       No single format plays in every browser, so several <source>
       elements are listed and the browser takes the FIRST it can
       play.

       The TEXT between the tags is the FALLBACK - shown only by a
       browser that supports neither the tag nor any of the sources.
    ```
    - Two practical points: `autoplay` with sound is blocked by every modern browser, so an autoplaying video must also be `muted`; and both tags come with a full `JavaScript API` — `play()`, `pause()`, `currentTime`, `volume`, and events such as `ended` and `timeupdate` — which is how a custom player is built with no plug-in at all.

26. **What is canvas HTML? What is difference between HTML canvas and SVG?** *[Investment Corporation Bangladesh Assistant Programmer 2017 compact it 1216 (ET: N/A)]*

Answer: What HTML canvas is
    - `<canvas>` is an HTML5 element that provides a `blank rectangular drawing area` on which graphics are drawn `with JavaScript`. The tag itself draws nothing — it only reserves the space.
    ```html
       <canvas id="myCanvas" width="400" height="200"
               style="border:1px solid #000">
           Your browser does not support canvas.
       </canvas>

       <script>
           const c   = document.getElementById("myCanvas");
           const ctx = c.getContext("2d");

           ctx.fillStyle = "blue";
           ctx.fillRect(20, 20, 150, 80);        // a filled rectangle

           ctx.beginPath();
           ctx.arc(280, 60, 40, 0, 2 * Math.PI); // a circle
           ctx.strokeStyle = "red";
           ctx.stroke();

           ctx.font = "16px Arial";
           ctx.fillText("Hello Canvas", 20, 140);
       </script>
    ```
    ```
       POINTS TO NOTE
         width and height must be set as ATTRIBUTES, not only in
              CSS. Setting them in CSS STRETCHES the bitmap and
              blurs the drawing - a very common mistake.
         getContext("2d") gives the drawing context ; "webgl" gives
              3D.
         Canvas is PIXEL-BASED. Once a shape is drawn, the canvas
              "forgets" it - only the pixels remain.
    ```

    Difference between canvas and SVG

    | Point | Canvas | SVG |
    |---|---|---|
    | Graphics type | `Raster` — pixel-based | `Vector` — shape-based |
    | Resolution | `Dependent` — pixelates when scaled | `Independent` — sharp at any zoom |
    | DOM | `No` — shapes are not objects | `Yes` — every shape is a DOM node |
    | Drawn with | `JavaScript` only | `Markup`, plus optional CSS and JS |
    | Event handling | On the whole canvas; the shape must be worked out by hand | `Per shape` — attach a click to a circle directly |
    | Styling with CSS | `No` | `Yes` |
    | Best with | `Many` objects on a `small` area | `Few` objects on a `large` area |
    | Performance | Fast with thousands of objects | Degrades beyond a few thousand elements |
    | Animation | Redraw the whole frame | Change an attribute; CSS or SMIL animation |
    | Text | Rendered as pixels — `not selectable or searchable` | Real text — `selectable, searchable, indexed` |
    | Accessibility | `Poor` — a screen reader sees one image | `Good` — shapes carry markup and titles |
    | Saving | `.png` via `toDataURL()` | `.svg` — an editable text file |
    | Typical use | Games, charts with huge data, image editing, video filters | Logos, icons, maps, diagrams, ordinary charts |

    The same circle in each
    ```html
       <!-- CANVAS - drawn by script, no DOM node for the circle -->
       <canvas id="c" width="200" height="200"></canvas>
       <script>
           const ctx = document.getElementById("c").getContext("2d");
           ctx.beginPath();
           ctx.arc(100, 100, 50, 0, 2 * Math.PI);
           ctx.fillStyle = "green";
           ctx.fill();
       </script>

       <!-- SVG - the circle IS an element in the DOM -->
       <svg width="200" height="200">
           <circle cx="100" cy="100" r="50" fill="green"
                   onclick="alert('clicked')" />
       </svg>
    ```
    ```
       THE FUNDAMENTAL DIFFERENCE

       SVG   remembers every shape as an OBJECT. It can be selected,
             styled with CSS, given an event handler, and changed
             later. The cost is memory and slowdown once there are
             thousands of shapes.

       CANVAS  draws pixels and FORGETS them. There is nothing to
             remember, so it stays fast with a hundred thousand
             particles - but to make one shape clickable you must
             track its coordinates yourself and test the mouse
             position against them.
    ```
    - How to choose: `SVG` for anything that must scale, be styled, be clicked, be searched or be printed — logos, icons, maps, dashboards and ordinary charts. `Canvas` for games, real-time visualisation of very large data sets, image manipulation and video processing.
    - The related third option worth naming: `WebGL`, obtained with `getContext("webgl")`, which uses the GPU for hardware-accelerated 3D on the same `<canvas>` element.

27. **What are the uses of `<header>`, `<article>`, `<section>` and `<footer>` in html?** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1217 (ET: N/A)]*

Answer: These are four `semantic` elements from HTML5. They render exactly like a `<div>` — their value is that they state `what the content is`.

    `<header>` — introductory content
    ```
       USE : the top of the page or of a section - logo, site title,
       heading, and often the navigation.
    ```
    ```html
       <header>
           <img src="logo.png" alt="Company logo">
           <h1>My Company</h1>
           <nav><a href="index.html">Home</a></nav>
       </header>
    ```
    - A page may have `several` headers — one for the page and one inside each article or section. It must not be nested inside a `<footer>` or another `<header>`.

    `<article>` — self-contained content
    ```
       USE : content that would still make sense if taken out of the
       page and republished on its own.
    ```
    ```html
       <article>
           <header>
               <h2>Understanding HTML5</h2>
               <p>By Rahim, 12 March 2026</p>
           </header>
           <p>HTML5 introduced semantic elements ...</p>
           <footer><p>Filed under : Web Development</p></footer>
       </article>
    ```
    - Examples: a blog post, a news story, a forum post, a product card, a user comment. The test is whether it could appear in an `RSS feed` alone and still make sense.

    `<section>` — a thematic grouping
    ```
       USE : a distinct part of a document that would normally carry
       a heading.
    ```
    ```html
       <section>
           <h2>Our Services</h2>
           <p>We provide web development and hosting.</p>
       </section>
    ```
    - Rule of thumb: a `<section>` should `have a heading`. If it does not, a `<div>` is what is wanted. `<section>` is not a styling wrapper.

    `<footer>` — closing content
    ```
       USE : the bottom of the page or of a section - copyright,
       contact details, author information, related links, privacy
       policy.
    ```
    ```html
       <footer>
           <p>&copy; 2026 My Company. All rights reserved.</p>
           <p>Contact : info@example.com</p>
       </footer>
    ```

    `<article>` against `<section>` — what the question is really testing
    ```
       <ARTICLE>  SELF-CONTAINED and independently distributable.
       <SECTION>  a THEMATIC PART of a larger whole ; it depends on
                  its surroundings.

       Either may contain the other :

            an ARTICLE split into SECTIONS
                 <article>
                     <section><h3>Introduction</h3>...</section>
                     <section><h3>Method</h3>...</section>
                 </article>

            a SECTION holding several ARTICLES
                 <section>
                     <h2>Latest News</h2>
                     <article>...</article>
                     <article>...</article>
                 </section>
    ```

    The whole page
    ```html
    <body>
        <header>  ... logo and site title ...  </header>
        <nav>     ... the menu ...             </nav>
        <main>
            <section>
                <h2>Blog</h2>
                <article> ... first post ...  </article>
                <article> ... second post ... </article>
            </section>
            <aside>   ... sidebar ...          </aside>
        </main>
        <footer>  ... copyright ...            </footer>
    </body>
    ```
    - Why they are used instead of `<div>`: a `screen reader` can jump straight to `<main>` or list the page's sections, which anonymous divs cannot offer; `search engines` use the structure to tell an article's content from the navigation around it; and the markup is far easier for a person to read. Visually nothing changes — the entire benefit is `meaning`.

28. **What is HTML Canvas? Differentiate between canvas and SVG.** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1219 (ET: N/A)]*

Answer: What HTML Canvas is
    - `<canvas>` is an HTML5 element that provides a `blank rectangular drawing area` on which graphics are drawn `with JavaScript`. The tag itself draws nothing — it only reserves the space.
    ```html
       <canvas id="myCanvas" width="400" height="200"
               style="border:1px solid #000">
           Your browser does not support canvas.
       </canvas>

       <script>
           const c   = document.getElementById("myCanvas");
           const ctx = c.getContext("2d");

           ctx.fillStyle = "blue";
           ctx.fillRect(20, 20, 150, 80);         // rectangle

           ctx.beginPath();
           ctx.arc(280, 60, 40, 0, 2 * Math.PI);  // circle
           ctx.strokeStyle = "red";
           ctx.stroke();

           ctx.font = "16px Arial";
           ctx.fillText("Hello Canvas", 20, 140); // text
       </script>
    ```
    ```
       POINTS TO NOTE
         width and height must be set as ATTRIBUTES, not only in
              CSS. Setting them in CSS STRETCHES the bitmap and
              blurs the drawing.
         getContext("2d") gives the 2D drawing context ;
              getContext("webgl") gives hardware-accelerated 3D.
         Canvas is PIXEL-BASED. Once a shape is drawn the canvas
              keeps only the pixels - the shape itself is forgotten.
    ```

    Difference between canvas and SVG

    | Point | Canvas | SVG |
    |---|---|---|
    | Graphics type | `Raster` — pixel-based | `Vector` — shape-based |
    | Resolution | `Dependent` — pixelates when scaled | `Independent` — sharp at any zoom |
    | DOM | `No` — shapes are not objects | `Yes` — every shape is a DOM node |
    | Created with | `JavaScript` only | `Markup`, plus optional CSS and JS |
    | Events | Only on the whole canvas | `Per shape` |
    | CSS styling | `No` | `Yes` |
    | Best with | `Many` objects, `small` area | `Few` objects, `large` area |
    | Performance | Fast with thousands of objects | Degrades past a few thousand elements |
    | Animation | Redraw the whole frame | Change an attribute; CSS animation |
    | Text | Pixels — `not selectable or searchable` | Real text — `selectable, searchable` |
    | Accessibility | `Poor` — one opaque image | `Good` — markup with titles |
    | Saving | `.png` via `toDataURL()` | `.svg` — an editable text file |
    | Typical use | Games, huge-data charts, image editing | Logos, icons, maps, diagrams, charts |

    The same circle in each
    ```html
       <!-- CANVAS - drawn by script ; no DOM node for the circle -->
       <canvas id="c" width="200" height="200"></canvas>
       <script>
           const ctx = document.getElementById("c").getContext("2d");
           ctx.beginPath();
           ctx.arc(100, 100, 50, 0, 2 * Math.PI);
           ctx.fillStyle = "green";
           ctx.fill();
       </script>

       <!-- SVG - the circle IS an element in the DOM -->
       <svg width="200" height="200">
           <circle cx="100" cy="100" r="50" fill="green"
                   onclick="alert('clicked')" />
       </svg>
    ```
    ```
       THE FUNDAMENTAL DIFFERENCE

       SVG   REMEMBERS each shape as an object. It can be selected,
             styled with CSS, given an event handler and changed
             later. The cost is memory, and slowdown once there are
             thousands of shapes.

       CANVAS  draws pixels and FORGETS them. Nothing is remembered,
             so it stays fast with a hundred thousand particles -
             but to make one shape clickable you must track its
             coordinates yourself and test the mouse position
             against them.
    ```
    - How to choose: `SVG` for anything that must scale, be styled, be clicked, be searched or be printed — logos, icons, maps, dashboards and ordinary charts. `Canvas` for games, real-time visualisation of very large data sets, image manipulation and video processing.
    - One point worth adding: they can be `combined`. A common pattern is a canvas for the heavy pixel work with an SVG or HTML layer above it for the labels, buttons and tooltips — which gives canvas's speed together with SVG's interactivity and accessibility.

29. **What is local Storage and session Storage in HTML5?** *[Agrani Bank Ltd. Officer (ICT) 2017 compact it 1224 (ET: N/A)]*

Answer: `localStorage` and `sessionStorage` are the two parts of the HTML5 `Web Storage API`. Both store data as `key–value pairs` in the browser, on the client side, with no server involvement.

    localStorage
    - Stores data with `no expiry`. It survives closing the tab, closing the browser and restarting the computer, and it is `shared across all tabs` of the same origin.
    ```javascript
       localStorage.setItem("theme", "dark");        // save
       let t = localStorage.getItem("theme");        // read -> "dark"
       localStorage.removeItem("theme");             // delete one
       localStorage.clear();                         // delete all
       localStorage.length                           // how many keys

       // objects must be converted - only STRINGS can be stored
       localStorage.setItem("user",
           JSON.stringify({ name: "Rahim", id: 5 }));
       let u = JSON.parse(localStorage.getItem("user"));
    ```
    - Used for: a remembered theme or language, user preferences, a saved draft, a cached list, an offline shopping cart.

    sessionStorage
    - Stores data only for the `current tab's session`. It is cleared when that tab or window is closed, and it is `not shared with other tabs` — each tab has its own isolated copy.
    ```javascript
       sessionStorage.setItem("step", "3");
       let s = sessionStorage.getItem("step");
       sessionStorage.removeItem("step");
       sessionStorage.clear();
    ```
    - Used for: the current position in a multi-step form, a one-time token, temporary state that must not leak between tabs — such as two tabs each filling in a different application form.

    The difference

    | Point | localStorage | sessionStorage |
    |---|---|---|
    | Lifetime | `Permanent` until deleted by code or the user | Until the `tab is closed` |
    | Survives browser restart | `Yes` | `No` |
    | Shared between tabs | `Yes`, same origin | `No` — each tab is isolated |
    | Capacity | About `5–10 MB` per origin | About `5–10 MB` per origin |
    | Sent to the server | `No` | `No` |
    | API | Identical | Identical |

    Both compared with cookies

    | Point | Web Storage | Cookies |
    |---|---|---|
    | Capacity | `5–10 MB` | About `4 KB` |
    | Sent with every HTTP request | `No` | `Yes` — added to every request |
    | Expiry | localStorage never; sessionStorage on tab close | A `set expiry date` |
    | Read by the server | `No` — client only | `Yes` |
    | Accessible to JavaScript | Yes | Yes, unless `HttpOnly` |
    | Intended for | Client-side data and preferences | `Session management`, server-read state |
    - Why cookies still exist: only a cookie is `sent to the server automatically`, which is what session authentication needs, and only a cookie can be marked `HttpOnly` so JavaScript cannot read it.

    The important warnings
    ```
       1. NEVER STORE SENSITIVE DATA
            Web Storage is readable by ANY JavaScript on the page. A
            single XSS flaw exposes everything in it. So no
            passwords, no card numbers, and preferably no
            authentication tokens - a token belongs in an HttpOnly
            cookie.

       2. ONLY STRINGS CAN BE STORED
            Everything else must go through JSON.stringify() and
            JSON.parse(). Storing an object directly saves the text
            "[object Object]".

       3. IT IS SYNCHRONOUS
            A large read or write BLOCKS the page. It is unsuitable
            for large data - use IndexedDB for that.

       4. IT IS PER ORIGIN
            Scheme, host and port together. http and https on the
            same domain are DIFFERENT origins with separate storage.

       5. IT MAY THROW
            In private browsing mode, or when the quota is exceeded,
            setItem() raises an exception - so it should be wrapped
            in try/catch.
    ```
    - The third member of the family, worth naming: `IndexedDB`, a full asynchronous client-side database for large structured data, used where Web Storage's 5 MB and synchronous API are inadequate.

30. **What are the minimum HTML Tags is used web pages? How can your comments at web pages so that browser not read this?** *[Bangladesh Bank Assistant Programmer 2016 compact it 1266 (ET: N/A)]*

Answer: The minimum HTML tags used in a web page
    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>My Page</title>
    </head>
    <body>
        Hello
    </body>
    </html>
    ```
    ```
       THE FOUR ESSENTIAL TAGS

       <html>    the ROOT element. Everything else goes inside it.
       <head>    information ABOUT the page - not displayed.
       <title>   the text in the browser TAB. This is the ONLY
                 element the HTML specification makes MANDATORY
                 inside the head.
       <body>    everything the visitor SEES.

       Plus <!DOCTYPE html> - not a tag but a DECLARATION. It tells
       the browser to use HTML5 rules. Without it the browser falls
       into QUIRKS MODE and renders by old, inconsistent rules.
    ```

    The practical minimum, which should also include
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport"
              content="width=device-width, initial-scale=1.0">
        <title>My Page</title>
    </head>
    <body>
        <h1>Hello</h1>
    </body>
    </html>
    ```
    ```
       <meta charset="UTF-8">
            The CHARACTER ENCODING. Without it, Bangla and other
            non-ASCII text appears as garbage. It must be the FIRST
            thing in the head.

       <meta name="viewport" ...>
            Makes the page RESPONSIVE. Without it a mobile browser
            renders a desktop-width page and shrinks it.

       lang="en"
            Helps screen readers pronounce the text correctly, and
            helps search engines.
    ```

    How to write comments that the browser does not display
    ```html
       <!-- This is an HTML comment. The browser IGNORES it. -->

       <!--
            A comment may span
            several lines.
       -->

       <p>Visible text</p>
       <!-- <p>This paragraph is commented out and will not
            appear.</p> -->
    ```
    ```
       SYNTAX :   <!--   the comment   -->

       Opening marker : <!--        (exclamation , two hyphens)
       Closing marker : -->         (two hyphens , greater-than)
    ```

    What comments are used for
    ```
       - to explain the markup to another developer
       - to label the start and end of a large block
            <!-- START of the navigation menu -->
            ...
            <!-- END of the navigation menu -->
       - to disable code temporarily during debugging
       - to record the author, date or version
    ```

    The rules and warnings
    ```
       1. COMMENTS MUST NOT BE NESTED.
            <!-- outer <!-- inner --> still outer -->
            This BREAKS - the first --> closes the comment, and the
            rest becomes visible text.

       2. DO NOT PUT TWO HYPHENS INSIDE A COMMENT.
            <!-- a -- b -->  is invalid.

       3. THE COMMENT IS NOT DISPLAYED, BUT IT IS SENT TO THE
          BROWSER.
            Anyone can read it with "View Source". So NEVER put a
            password, an internal URL, an API key or a note about a
            security weakness in an HTML comment. This is a real and
            common source of information leakage.

       4. COMMENTS IN OTHER LANGUAGES ARE DIFFERENT.
            CSS         : /* comment */
            JavaScript  : // line   or   /* block */
            PHP         : // or #  or  /* */    - and a PHP comment
                 is removed on the SERVER, so it never reaches the
                 browser at all.
    ```
    - The point worth stating at the end: an HTML comment hides text from the `display`, not from the `visitor`. Anything that must genuinely be hidden has to be kept on the server — in a server-side comment or outside the delivered file entirely.

31. **What are SOAP and RESTful APIs? Discuss the differences between them in terms of architecture, format, and usage.** *[Senior Officer (IT) Date: 17 October 2015 Full Marks: 200 Time: 2 hours [bitbox it book 223]]*

Answer:
    - **SOAP (Simple Object Access Protocol)**: A standardized, contract-based XML communication protocol that strictly relies on WSDL (Web Services Description Language) definitions and WS-Security specifications.
    - **RESTful API (Representational State Transfer)**: An architectural design style that utilizes standard stateless HTTP methods (GET, POST, PUT, DELETE) to manipulate resources identified by URIs.

    Comparison between SOAP and REST:

    | Feature | SOAP API | RESTful API |
    |---|---|---|
    | Underlying Nature | Formal Protocol with strict specifications and standards | Architectural Style with flexible design principles |
    | Data Format | Strictly XML only | Supports JSON (standard), XML, HTML, and Plain Text |
    | Transport Protocols | Protocol independent (HTTP, HTTPS, SMTP, TCP, JMS) | Strictly bound to HTTP and HTTPS |
    | Bandwidth & Speed | Heavier payload; slower parsing due to verbose XML envelopes | Lightweight; faster execution and minimal bandwidth consumption |
    | State Management | Can be configured as stateful or stateless | Strictly Stateless (every request carries complete context) |
    | Security Standard | Built-in WS-Security, ACID transaction compliance | Relies on transport-layer TLS/HTTPS, OAuth 2.0, and JWT tokens |
    | Best Suited For | Enterprise banking, payment gateways, legacy telecommunications | Modern web apps, mobile backends, cloud microservices |

32. **Translation [Bangla to English]** *[compact it 522]*
Capacity development in banking is crucial as the industry faces evolving challenges and opportunities in a rapidly changing landscape. It encompasses enhancing the knowledge, skills, and capabilities of banking professionals to effectively navigate complex financial environments. This includes training in areas such as financial literacy, risk management, regulatory compliance, and technological proficiency. As banks integrate advanced technologies, and digital banking solutions, there is a growing need for specialized expertise to harness these tools for operational efficiency and customer service enhancement. Capacity development initiatives also focus on leadership development, fostering strategic thinking and decision-making abilities among senior executives to steer banks through economic uncertainties and competitive pressures.

Answer:
    অনুবাদ (বঙ্গানুবাদ):
    ব্যাংকিং খাতে সক্ষমতা উন্নয়ন অত্যন্ত গুরুত্বপূর্ণ, কারণ দ্রুত পরিবর্তনশীল প্রেক্ষাপটে এ শিল্প প্রতিনিয়ত নতুন নতুন চ্যালেঞ্জ ও সম্ভাবনার মুখোমুখি হচ্ছে। জটিল আর্থিক পরিবেশকে কার্যকরভাবে পরিচালনার লক্ষ্যে ব্যাংকিং পেশাজীবীদের জ্ঞান, দক্ষতা ও সামর্থ্য বৃদ্ধি করাই এর মূল লক্ষ্য। এর অন্তর্ভুক্ত রয়েছে আর্থিক সাক্ষরতা, ঝুঁকি ব্যবস্থাপনা, আইনি ও নীতিগত বাধ্যবাধকতা পরিপালন এবং প্রযুক্তিগত দক্ষতার মতো ক্ষেত্রসমূহে প্রশিক্ষণ প্রদান। ব্যাংকসমূহ যখন উন্নত প্রযুক্তি ও ডিজিটাল ব্যাংকিং সলিউশন সমন্বিত করছে, তখন পরিচালনগত দক্ষতা বৃদ্ধি এবং গ্রাহকসেবার মানোন্নয়নে এসব প্রযুক্তি ব্যবহারের জন্য বিশেষায়িত দক্ষতার প্রয়োজনীয়তা ক্রমাগত বাড়ছে। সক্ষমতা উন্নয়নমূলক উদ্যোগসমূহ নেতৃত্ব বিকাশের ওপরও গুরুত্বারোপ করে, যা অর্থনৈতিক অনিশ্চয়তা ও প্রতিযোগিতামূলক চাপের মধ্য দিয়ে ব্যাংকগুলোকে পরিচালিত করতে ঊর্ধ্বতন নির্বাহীদের কৌশলগত চিন্তাভাবনা ও সিদ্ধান্ত গ্রহণের সক্ষমতা বৃদ্ধি করে।

## JavaScript & jQuery (DOM & Validation) (16)

1. **Jquery for email validation** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

Answer: jQuery email validation
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="UTF-8">
       <title>Email Validation</title>
       <script src="https://code.jquery.com/jquery-3.7.1.min.js">
       </script>
       <style>
           .error { color: red;   font-size: 13px; }
           .ok    { color: green; font-size: 13px; }
       </style>
   </head>
   <body>

   <form id="myForm">
       <label for="email">Email :</label>
       <input type="text" id="email" name="email">
       <span id="msg"></span>
       <br><br>
       <button type="submit">Submit</button>
   </form>

   <script>
   $(document).ready(function () {

       // the validation function
       function isValidEmail(email) {
           var pattern = /^[^\s@]+@[^\s@]+\.[^\s@]{2,}$/;
           return pattern.test(email);
       }

       // validate as the user types
       $("#email").on("keyup blur", function () {
           var email = $(this).val().trim();

           if (email === "") {
               $("#msg").text("Email is required")
                        .attr("class", "error");
           } else if (!isValidEmail(email)) {
               $("#msg").text("Invalid email address")
                        .attr("class", "error");
           } else {
               $("#msg").text("Valid email")
                        .attr("class", "ok");
           }
       });

       // validate again on submit
       $("#myForm").on("submit", function (e) {
           var email = $("#email").val().trim();

           if (!isValidEmail(email)) {
               e.preventDefault();          // STOP the submission
               $("#msg").text("Please enter a valid email")
                        .attr("class", "error");
               $("#email").focus();
           }
       });

   });
   </script>

   </body>
   </html>
   ```

   Tested results
   ```
      a@b.com                    -> VALID
      rahim.ali@example.co.uk    -> VALID
      bad@                       -> INVALID  (no domain)
      @bad.com                   -> INVALID  (no local part)
      no at.com                  -> INVALID  (no @ , and a space)
      x@y.z                      -> INVALID  (top-level domain must
                                               be at least 2 letters)
   ```

   The regular expression, part by part
   ```
      /^[^\s@]+@[^\s@]+\.[^\s@]{2,}$/

      ^          start of the string
      [^\s@]+    one or more characters that are NOT a space and
                 NOT an @   -> the local part
      @          exactly one @
      [^\s@]+    the domain name
      \.         a literal dot  (escaped, because a bare . means
                 "any character")
      [^\s@]{2,} at least TWO characters - the top-level domain
      $          end of the string
   ```

   Alternatives worth knowing
   ```html
      <!-- 1. HTML5 does most of this with no code at all -->
      <input type="email" required>
      <!-- the browser validates it and shows its own message -->

      <!-- 2. the jQuery Validate plugin -->
      <script src="jquery.validate.min.js"></script>
      <script>
      $("#myForm").validate({
          rules:    { email: { required: true, email: true } },
          messages: { email: { required: "Email is required",
                               email: "Enter a valid email" } }
      });
      </script>
   ```
   - The point that must be stated: `client-side validation is for the user's convenience, never for security`. Anyone can disable JavaScript or send the request directly, so the `email must be validated again on the server`. Client-side checks catch typing mistakes; server-side checks are what actually protect the application.
   - And no regular expression can prove an address `exists`. The only real test is to `send a confirmation email` and require the user to click the link — which is why every registration system does exactly that.

2. **Write Javascript code to check NID validity?** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1359 (ET: BUET)]*

Answer: A Bangladeshi `NID` (National ID) number is `10`, `13` or `17` digits long. The 17-digit form begins with a 4-digit year of birth, and the older forms are 13 and 10 digits.
   ```javascript
   function isValidNID(nid) {

       // 1. remove spaces and dashes the user may have typed
       nid = String(nid).replace(/[\s-]/g, "").trim();

       // 2. it must be empty of everything except digits
       if (!/^\d+$/.test(nid)) {
           return { valid: false, message: "NID must contain digits only" };
       }

       // 3. the length must be 10 , 13 or 17
       if (nid.length !== 10 && nid.length !== 13 && nid.length !== 17) {
           return { valid: false,
                    message: "NID must be 10, 13 or 17 digits" };
       }

       // 4. for the 17-digit form, check the birth year is sensible
       if (nid.length === 17) {
           var year = parseInt(nid.substring(0, 4), 10);
           var now  = new Date().getFullYear();
           if (year < 1900 || year > now) {
               return { valid: false,
                        message: "Invalid birth year in NID" };
           }
       }

       return { valid: true, message: "Valid NID" };
   }
   ```

   Tested results
   ```
      1234567890            ->  VALID   (10 digits)
      1234567890123         ->  VALID   (13 digits)
      19851234567890123     ->  VALID   (17 digits , year 1985)
      12345678901234567     ->  VALID by length , but the year
                                 1234 is rejected by the year check
      12345                 ->  INVALID (wrong length)
      12a4567890            ->  INVALID (contains a letter)
   ```

   The complete form
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="UTF-8">
       <title>NID Validation</title>
       <style>
           .error { color: red;   font-size: 13px; }
           .ok    { color: green; font-size: 13px; }
       </style>
   </head>
   <body>

   <form id="nidForm">
       <label for="nid">NID Number :</label>
       <input type="text" id="nid" maxlength="17">
       <span id="msg"></span>
       <br><br>
       <button type="submit">Submit</button>
   </form>

   <script>
   function isValidNID(nid) {
       nid = String(nid).replace(/[\s-]/g, "").trim();
       if (!/^\d+$/.test(nid))
           return { valid: false, message: "Digits only" };
       if ([10, 13, 17].indexOf(nid.length) === -1)
           return { valid: false, message: "Must be 10, 13 or 17 digits" };
       if (nid.length === 17) {
           var y = parseInt(nid.substring(0, 4), 10);
           if (y < 1900 || y > new Date().getFullYear())
               return { valid: false, message: "Invalid birth year" };
       }
       return { valid: true, message: "Valid NID" };
   }

   var input = document.getElementById("nid");
   var msg   = document.getElementById("msg");

   input.addEventListener("keyup", function () {
       var r = isValidNID(input.value);
       msg.textContent = input.value === "" ? "" : r.message;
       msg.className   = r.valid ? "ok" : "error";
   });

   document.getElementById("nidForm").addEventListener("submit",
       function (e) {
           var r = isValidNID(input.value);
           if (!r.valid) {
               e.preventDefault();
               msg.textContent = r.message;
               msg.className   = "error";
               input.focus();
           }
       });
   </script>

   </body>
   </html>
   ```

   The regular expression version, if a one-line answer is wanted
   ```javascript
      function isValidNID(nid) {
          return /^(\d{10}|\d{13}|\d{17})$/.test(String(nid).trim());
      }
   ```
   ```
      ^          start
      \d{10}     exactly 10 digits
      |          OR
      \d{13}     exactly 13 digits
      |          OR
      \d{17}     exactly 17 digits
      $          end

      The anchors ^ and $ are essential. Without them the pattern
      would match 10 digits ANYWHERE inside a longer string.
   ```
   - What this validation can and cannot do: it checks the `format` only. Whether the number actually belongs to a real person can be confirmed only by querying the `Election Commission NID verification service`, which is what banks do during account opening.
   - And as always: `client-side validation is for the user's convenience, not for security`. The NID must be validated again on the `server`, because anyone can disable JavaScript or post the request directly.

3. **Which tag is used to write JavaScript in html?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

Answer: The `<script>` tag is used to write JavaScript in HTML.
   ```html
      <script>
          alert("Hello World");
      </script>
   ```

   The two ways of using it
   ```html
      <!-- 1. INTERNAL - the code is written inside the tag -->
      <script>
          document.getElementById("demo").innerHTML = "Hello";
      </script>

      <!-- 2. EXTERNAL - the code is in a separate .js file -->
      <script src="script.js"></script>
   ```
   ```
      With  src  the tag must still be CLOSED, and it must be
      EMPTY - anything written between the tags is IGNORED when
      src is present.

           CORRECT :  <script src="app.js"></script>
           WRONG   :  <script src="app.js" />
   ```

   Where to place it
   ```
      IN THE <head>
           The script is loaded before the page is drawn, so it
           BLOCKS rendering. And an element the script refers to
           does not exist yet, so getElementById returns null.

      AT THE END OF <body> - the usual recommendation
           The HTML is drawn first, so the page appears quickly and
           every element already exists when the script runs.

      IN THE <head> WITH defer  - the modern best practice
           <script src="app.js" defer></script>
           The file is fetched in parallel with parsing and then
           executed after the HTML is complete.
   ```
   ```
      THE THREE LOADING MODES

      <script src="a.js">          fetch and execute IMMEDIATELY -
           parsing STOPS while it downloads and runs
      <script src="a.js" async>    fetch in parallel , execute AS
           SOON AS IT ARRIVES - order NOT guaranteed
      <script src="a.js" defer>    fetch in parallel , execute
           after parsing , IN ORDER
   ```

   The `type` attribute
   ```html
      <script>                    <!-- HTML5 : JavaScript is the
                                       default, no type needed -->
      <script type="text/javascript">   <!-- older, still valid -->
      <script type="module">      <!-- an ES6 module ; import and
                                       export may be used -->
   ```

   Related tags and attributes, for completeness
   ```html
      <!-- inline event handler - works, but not recommended -->
      <button onclick="alert('Hi')">Click</button>

      <!-- shown only when JavaScript is DISABLED -->
      <noscript>
          This site requires JavaScript to be enabled.
      </noscript>
   ```
   - The practice worth stating: keep JavaScript in an `external file` rather than inline. The browser then `caches` it, one file serves every page, the HTML stays readable, and behaviour is separated from structure — the same argument that puts CSS in its own file.

4. **Write Javascript function to validate a customer number where the customer number in 3 uppercase letter and district code followed by 8 digits.** *[BICIC Assistant Programmer 2022 compact it 630 (ET: BUET)]*

Answer: The customer number is `3 uppercase letters` — the district code — followed by `8 digits`, giving a total length of 11 characters.
   ```javascript
   function validateCustomerNumber(custNo) {

       custNo = String(custNo).trim();

       // 3 uppercase letters followed by exactly 8 digits
       var pattern = /^[A-Z]{3}\d{8}$/;

       return pattern.test(custNo);
   }
   ```

   Tested results
   ```
      DHA12345678     ->  VALID
      ABC12345678     ->  VALID
      dha12345678     ->  INVALID  (lower case letters)
      DHAK12345678    ->  INVALID  (4 letters)
      DHA1234567      ->  INVALID  (only 7 digits)
      DHA123456789    ->  INVALID  (9 digits)
      DH112345678     ->  INVALID  (a digit among the letters)
   ```

   The regular expression, part by part
   ```
      /^[A-Z]{3}\d{8}$/

      ^         start of the string
      [A-Z]     one UPPERCASE letter , A to Z
      {3}       exactly three of them
      \d        one digit , 0 to 9   (same as [0-9])
      {8}       exactly eight of them
      $         end of the string

      The anchors ^ and $ are ESSENTIAL. Without them the pattern
      would match a valid number buried inside a longer string, so
      "XXDHA12345678YY" would pass.
   ```

   The version with specific error messages
   ```javascript
   function validateCustomerNumber(custNo) {

       custNo = String(custNo).trim();

       if (custNo === "")
           return { valid: false, message: "Customer number is required" };

       if (custNo.length !== 11)
           return { valid: false,
                    message: "Must be exactly 11 characters" };

       if (!/^[A-Z]{3}/.test(custNo))
           return { valid: false,
                    message: "First 3 characters must be uppercase letters" };

       if (!/^[A-Z]{3}\d{8}$/.test(custNo))
           return { valid: false,
                    message: "Last 8 characters must be digits" };

       return { valid: true,
                district: custNo.substring(0, 3),
                serial:   custNo.substring(3),
                message:  "Valid customer number" };
   }
   ```

   The complete form
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="UTF-8">
       <title>Customer Number Validation</title>
       <style>
           .error { color: red;   font-size: 13px; }
           .ok    { color: green; font-size: 13px; }
       </style>
   </head>
   <body>

   <form id="custForm">
       <label for="cust">Customer Number :</label>
       <input type="text" id="cust" maxlength="11"
              placeholder="DHA12345678"
              style="text-transform:uppercase">
       <span id="msg"></span>
       <br><br>
       <button type="submit">Submit</button>
   </form>

   <script>
   function validateCustomerNumber(c) {
       return /^[A-Z]{3}\d{8}$/.test(String(c).trim());
   }

   var input = document.getElementById("cust");
   var msg   = document.getElementById("msg");

   input.addEventListener("keyup", function () {
       input.value = input.value.toUpperCase();   // help the user
       if (input.value === "") { msg.textContent = ""; return; }

       if (validateCustomerNumber(input.value)) {
           msg.textContent = "Valid";  msg.className = "ok";
       } else {
           msg.textContent = "Format must be AAA12345678";
           msg.className   = "error";
       }
   });

   document.getElementById("custForm").addEventListener("submit",
       function (e) {
           if (!validateCustomerNumber(input.value)) {
               e.preventDefault();
               msg.textContent = "Invalid customer number";
               msg.className   = "error";
               input.focus();
           }
       });
   </script>

   </body>
   </html>
   ```
   - Two useful touches in the form: `text-transform:uppercase` in CSS displays the input in capitals, and `input.value.toUpperCase()` actually converts it — the CSS alone changes only the appearance, so the value sent would still be lower case. And `maxlength="11"` stops over-typing before validation is even needed.
   - If the letters must be one of a fixed list of district codes, the pattern is extended: `/^(DHA|CTG|SYL|KHU|RAJ|BAR|RAN|MYM)\d{8}$/`. And as always, the same check must be repeated on the `server` — client-side validation is for the user's convenience, not for security.

5. **Write HTML and Javascript code of following box.** *[EGCB Assistant Engineer (CSE) 2022 compact it 716 (ET: BUET)]*

Answer: The question is `incomplete` — the figure of the box was not captured with it, so the exact layout cannot be reproduced. The two forms such a question normally asks for are given below, and either can be adapted to whatever box the figure shows.

   Version 1 — a dialogue box (alert, confirm, prompt)
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="UTF-8">
       <title>Dialogue Boxes</title>
   </head>
   <body>

       <button onclick="showAlert()">Alert Box</button>
       <button onclick="showConfirm()">Confirm Box</button>
       <button onclick="showPrompt()">Prompt Box</button>
       <p id="result"></p>

   <script>
       function showAlert() {
           alert("This is an alert box");
       }

       function showConfirm() {
           var ok = confirm("Do you want to continue ?");
           document.getElementById("result").innerHTML =
               ok ? "You pressed OK" : "You pressed Cancel";
       }

       function showPrompt() {
           var name = prompt("Please enter your name", "Rahim");
           document.getElementById("result").innerHTML =
               (name === null) ? "You cancelled"
                               : "Hello " + name;
       }
   </script>

   </body>
   </html>
   ```
   ```
      THE THREE BUILT-IN BOXES

      alert(message)
           One message and an OK button. Returns nothing.

      confirm(message)
           OK and Cancel. Returns TRUE for OK, FALSE for Cancel.

      prompt(message, default)
           A text box with OK and Cancel. Returns the STRING typed,
           or NULL if Cancel is pressed.

      NOTE : prompt returns a STRING even for a number, so
      parseInt() or Number() is needed before arithmetic. And
      Cancel returns null, NOT an empty string - the two must be
      distinguished.
   ```

   Version 2 — an input box with a calculation
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="UTF-8">
       <title>Input Box</title>
       <style>
           .box {
               border: 2px solid #333;
               border-radius: 8px;
               padding: 20px;
               width: 300px;
               font-family: Arial, sans-serif;
           }
           .box h3    { margin-top: 0; }
           .box input { width: 100%; padding: 6px;
                        margin-bottom: 10px; }
           .box button{ padding: 6px 14px; }
           #out       { font-weight: bold; color: navy; }
       </style>
   </head>
   <body>

   <div class="box">
       <h3>Simple Calculator</h3>

       <label for="n1">First number :</label>
       <input type="number" id="n1">

       <label for="n2">Second number :</label>
       <input type="number" id="n2">

       <button onclick="calculate()">Add</button>

       <p>Result : <span id="out">-</span></p>
   </div>

   <script>
       function calculate() {
           var a = document.getElementById("n1").value;
           var b = document.getElementById("n2").value;

           if (a === "" || b === "") {
               document.getElementById("out").innerHTML =
                   "Please fill in both fields";
               return;
           }

           // the values are STRINGS, so they must be converted -
           // "2" + "3" would give "23", not 5
           var sum = Number(a) + Number(b);

           document.getElementById("out").innerHTML = sum;
       }
   </script>

   </body>
   </html>
   ```
   ```
      +---------------------------------+
      |  Simple Calculator              |
      |                                 |
      |  First number :                 |
      |  +---------------------------+  |
      |  |                           |  |
      |  +---------------------------+  |
      |  Second number :                |
      |  +---------------------------+  |
      |  |                           |  |
      |  +---------------------------+  |
      |  [ Add ]                        |
      |                                 |
      |  Result : 25                    |
      +---------------------------------+
   ```
   - The mistake this example is designed to show: `input.value is always a string`. Without `Number()` or `parseInt()`, `"2" + "3"` produces `"23"` rather than `5`. Subtraction, multiplication and division convert automatically; only `+` does not, because `+` also means string concatenation.
   - If the figure showed a `modal` dialogue rather than a plain box, the same HTML is used inside a fixed-position overlay `<div>`, shown and hidden by setting `style.display` — or, in modern HTML, with the `<dialog>` element and its `showModal()` method.

6. **Explain hoisting in JavaScript?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 761 (ET: N/A)]*

Answer: What hoisting is
   - `Hoisting` is JavaScript's behaviour of moving `declarations` to the top of their scope before the code runs. The `declaration` is hoisted; the `assignment` is not.
   ```javascript
      console.log(x);      // undefined  - NOT an error
      var x = 5;
      console.log(x);      // 5
   ```
   ```
      The engine treats it as :

           var x;               // declaration HOISTED to the top
           console.log(x);      // undefined - declared but not yet
                                // assigned
           x = 5;               // the assignment stays where it was
           console.log(x);      // 5
   ```
   - Why it happens: JavaScript runs in `two phases`. In the `compilation` phase it scans the scope and registers every declaration; in the `execution` phase it runs the statements. So a variable exists before the line that declares it is reached.

   `var` — hoisted and initialised to `undefined`
   ```javascript
      function test() {
          console.log(a);      // undefined
          var a = 10;
          console.log(a);      // 10
      }
   ```

   `let` and `const` — hoisted, but NOT initialised
   ```javascript
      console.log(b);      // ReferenceError : Cannot access 'b'
                           // before initialization
      let b = 5;
   ```
   ```
      let and const ARE hoisted, but they are placed in the
      TEMPORAL DEAD ZONE (TDZ) - the region from the start of the
      scope to the line of the declaration. Touching the variable
      inside the TDZ throws a ReferenceError.

      THIS IS THE POINT MOST OFTEN GOT WRONG. People say "let is
      not hoisted". It IS hoisted ; it is simply not INITIALISED,
      which is why the error is "cannot access before
      initialization" rather than "b is not defined".
   ```

   Function declarations — hoisted completely
   ```javascript
      greet();                     // "Hello" - it WORKS

      function greet() {
          console.log("Hello");
      }
   ```
   - A `function declaration` is hoisted with its whole body, so it can be called before it appears in the file.

   Function expressions — NOT hoisted
   ```javascript
      greet();                     // TypeError : greet is not a
                                   // function
      var greet = function () {
          console.log("Hello");
      };
   ```
   ```
      Here only  var greet  is hoisted, as undefined. Calling
      undefined() gives a TypeError - a DIFFERENT error from the
      ReferenceError above, and the distinction is often examined.

      An ARROW FUNCTION behaves the same way :
           greet();                 // ReferenceError (with let)
           let greet = () => {};
   ```

   Summary
   ```
      +---------------------+-----------+------------------------+
      | Declaration         | Hoisted ? | Value before the line  |
      +---------------------+-----------+------------------------+
      | var                 | YES       | undefined              |
      | let                 | yes       | TDZ -> ReferenceError  |
      | const               | yes       | TDZ -> ReferenceError  |
      | function declaration| YES       | the whole function     |
      | function expression | as var    | undefined -> TypeError |
      | class               | yes       | TDZ -> ReferenceError  |
      +---------------------+-----------+------------------------+
   ```

   A classic trap
   ```javascript
      var x = 1;
      function f() {
          console.log(x);      // undefined , NOT 1
          var x = 2;
      }
      f();
   ```
   ```
      The inner  var x  is hoisted to the top of f(), so it SHADOWS
      the outer x for the whole function. At the console.log the
      local x exists but has not been assigned, so it is undefined.
   ```
   - The practical conclusion: use `let` and `const` rather than `var`. Their `temporal dead zone` turns a silent `undefined` into a loud `ReferenceError`, so a variable used before its declaration becomes an error the developer sees instead of a bug the user finds. Declaring variables at the top of the scope makes hoisting irrelevant, which is the real remedy.

7. **Display element by id in JavaScript?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 762 (ET: N/A)]*

Answer: An element is fetched by its `id` with `document.getElementById()`, and its content is displayed or changed through `innerHTML` or `textContent`.
   ```html
   <!DOCTYPE html>
   <html>
   <head><meta charset="UTF-8"><title>getElementById</title></head>
   <body>

       <p id="demo">Original text</p>
       <button onclick="show()">Show</button>

   <script>
       function show() {
           // 1. GET the element by its id
           var el = document.getElementById("demo");

           // 2. READ its content
           console.log(el.innerHTML);        // "Original text"

           // 3. CHANGE its content
           el.innerHTML = "Text changed by JavaScript";
       }
   </script>

   </body>
   </html>
   ```

   Reading and writing content
   ```javascript
      var el = document.getElementById("demo");

      el.innerHTML   = "<b>Bold text</b>";   // HTML is PARSED
      el.textContent = "<b>Bold text</b>";   // shown as plain TEXT
      el.innerText   = "Visible text only";  // ignores hidden text

      // for a form field, use .value , NOT .innerHTML
      var name = document.getElementById("nameBox").value;
   ```
   ```
      innerHTML vs textContent - the point that matters

      innerHTML    parses the string as HTML. If the string came
           from a USER, this creates an XSS vulnerability :
                el.innerHTML = userInput;   // DANGEROUS
           A user could submit <img src=x onerror="...">.

      textContent  inserts the string as plain text. Tags are
           displayed, not executed. ALWAYS use textContent for
           untrusted data.
   ```

   Changing an attribute and the style
   ```javascript
      var img = document.getElementById("pic");

      img.src = "new.jpg";                   // a direct property
      img.setAttribute("alt", "New image");  // any attribute
      img.getAttribute("src");               // read it back

      img.style.border  = "2px solid red";   // one style
      img.classList.add("highlight");        // better - use a class
   ```

   The other ways to select elements
   ```javascript
      document.getElementById("demo")            // ONE element ,
                                                 // or null
      document.getElementsByClassName("card")    // a LIVE
                                                 // HTMLCollection
      document.getElementsByTagName("p")         // a live collection
      document.querySelector(".card")            // the FIRST match ,
                                                 // any CSS selector
      document.querySelectorAll(".card")         // a STATIC NodeList
                                                 // of all matches
   ```
   ```
      getElementById is the FASTEST, because an id is unique and the
      browser keeps an index of ids.

      querySelector is the most FLEXIBLE - it accepts any CSS
      selector :
           document.querySelector("#main .card > p:first-child")
   ```

   The two mistakes that account for most failures
   ```
      1. THE SCRIPT RUNS BEFORE THE ELEMENT EXISTS

           <head>
               <script>
                   document.getElementById("demo").innerHTML = "Hi";
                   // TypeError : Cannot set property of null
               </script>
           </head>
           <body><p id="demo"></p></body>

         The <p> has not been parsed yet, so getElementById returns
         NULL.

         THE FIX - any one of :
           put the <script> at the END of <body>
           use  <script src="app.js" defer></script>
           wrap the code in
                document.addEventListener("DOMContentLoaded",
                    function () { ... });

      2. USING innerHTML ON A FORM FIELD
           An <input> has no inner HTML. Its content is in .value :
                document.getElementById("box").value
   ```
   - One further note: `id` must be `unique` in a document. If two elements share an id the HTML is invalid, and `getElementById` returns only the first — a bug that is very hard to see, because nothing reports an error.

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

   Answer: The code as given is already complete and correct in its logic. The only defect is the `missing space` before "is", which makes the output read `1is an odd value.` instead of `1 is an odd value.`

   The corrected code
   ```html
   <!DOCTYPE html>
   <html>
   <body>
   <script>
       for (var x = 1; x <= 9; x++) {
           if (x % 2 == 0) {
               console.log(x + " is an even value.");
           } else {
               console.log(x + " is an odd value.");
           }
       }
   </script>
   </body>
   </html>
   ```

   The output
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

   How it works
   ```
      for (var x = 1; x <= 9; x++)

           initialisation : x = 1
           condition      : x <= 9   - checked BEFORE each pass
           increment      : x++      - run AFTER each pass

      x % 2 == 0

           The MODULUS operator gives the REMAINDER of x divided
           by 2.
                even number -> remainder 0  -> the if is TRUE
                odd  number -> remainder 1  -> the else runs

           x=1 : 1 % 2 = 1  -> odd
           x=2 : 2 % 2 = 0  -> even
           x=3 : 3 % 2 = 1  -> odd     and so on to 9
   ```

   If the output must appear on the page rather than in the console
   ```html
   <!DOCTYPE html>
   <html>
   <body>

   <div id="output"></div>

   <script>
       var result = "";
       for (var x = 1; x <= 9; x++) {
           if (x % 2 == 0) {
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
   - `console.log` writes to the browser's `developer console` (F12), which the visitor never sees. To show the result on the page, `innerHTML` or `document.write` is needed. Building the whole string first and assigning `innerHTML` once is better than assigning inside the loop, because each assignment forces the browser to re-parse and re-render.

   The shorter forms worth knowing
   ```javascript
      // the ternary operator, in place of if-else
      for (var x = 1; x <= 9; x++) {
          console.log(x + (x % 2 === 0 ? " is an even value."
                                       : " is an odd value."));
      }

      // a template literal , ES6
      for (let x = 1; x <= 9; x++) {
          const type = x % 2 === 0 ? "even" : "odd";
          console.log(`${x} is an ${type} value.`);
      }
   ```
   - Two details worth stating. `let` should be preferred to `var` for the loop counter: `var` is function-scoped, so `x` still exists after the loop and equals 10, whereas `let` is block-scoped and confined to the loop. And `===` should be preferred to `==`: `==` performs type coercion, so `"0" == 0` is true, while `===` compares type as well and avoids a whole class of silent bugs.

9. **Differentiate among $.ajax(), $.get() and $.load() function of jQuery with necessary example.** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1058 (ET: AUST)]*, *[Probashi Kallyan Bank Programmer 2019 compact it 1158 (ET: AUST)]*

Answer: All three are jQuery AJAX methods, but they differ in `flexibility` and in `what they do with the response`.

   | Point | `$.ajax()` | `$.get()` | `$.load()` |
   |---|---|---|---|
   | Type | The `low-level` general method | A `shorthand` for GET | A `method on a selected element` |
   | HTTP method | `Any` — GET, POST, PUT, DELETE | `GET` only | `GET`, or `POST` if data is passed |
   | Called on | `$` (jQuery itself) | `$` | `$("#selector")` — an element |
   | What it does with the reply | Hands it to your `callback` | Hands it to your `callback` | `Inserts it into the element` automatically |
   | Options available | `All` of them | Few | Few |
   | Error handling | `Full` — error, complete, statusCode | Limited — chain `.fail()` | A callback that reports the status |
   | Can load part of a page | No | No | `Yes` — with a selector fragment |
   | Use when | Anything non-trivial | A quick GET of data | Dropping HTML into a container |

   `$.ajax()` — the full form
   ```javascript
      $.ajax({
          url:      "getUser.php",
          type:     "POST",
          data:     { id: 5, name: "Rahim" },
          dataType: "json",
          timeout:  5000,
          beforeSend: function () {
              $("#loader").show();
          },
          success: function (response) {
              $("#result").html(response.name);
          },
          error: function (xhr, status, err) {
              console.log("Failed : " + status + " " + err);
          },
          complete: function () {
              $("#loader").hide();      // runs on success AND error
          }
      });
   ```
   - Every other AJAX method in jQuery is a wrapper around this one. It is the only one that gives access to `type`, `timeout`, `headers`, `beforeSend`, `contentType` and `async`.

   `$.get()` — shorthand for a GET request
   ```javascript
      $.get("getUser.php", { id: 5 }, function (data) {
          $("#result").html(data);
      });

      // it returns a promise, so it can be chained
      $.get("data.json")
       .done(function (d) { console.log(d); })
       .fail(function ()  { console.log("error"); })
       .always(function () { console.log("finished"); });
   ```
   ```
      It is exactly equivalent to :

           $.ajax({ url: "getUser.php", type: "GET",
                    data: { id: 5 }, success: function (data) {...} });

      The companion methods are :
           $.post()      the same, with type POST
           $.getJSON()   a GET that parses the reply as JSON
           $.getScript() a GET that executes the reply as JavaScript
   ```

   `$.load()` — load HTML straight into an element
   ```javascript
      // load a whole page fragment into a div
      $("#content").load("page.html");

      // load ONLY PART of another page - the distinctive feature
      $("#content").load("page.html #section2");

      // with a callback
      $("#content").load("page.html", function (response, status) {
          if (status === "error") {
              $("#content").html("Could not load the content.");
          }
      });

      // passing data makes it a POST
      $("#content").load("search.php", { q: "laptop" });
   ```
   ```
      THE TWO THINGS THAT MAKE $.load() DIFFERENT

      1. It is called on an ELEMENT, not on $ , and it INSERTS the
         response into that element automatically. No success
         callback is needed just to display the result.

      2. It can fetch a FRAGMENT :
                $("#content").load("page.html #section2");
         jQuery fetches the whole page, then keeps only the part
         matching #section2. Convenient, but note that the WHOLE
         page still travels over the network.
   ```

   The relationship
   ```
      $.ajax()   -  the engine
         |
         +--- $.get()      GET , callback
         +--- $.post()     POST , callback
         +--- $.getJSON()  GET , parsed as JSON
         +--- .load()      GET , inserted into the element

      All of them ultimately call $.ajax().
   ```

   Which to use
   ```
      NEED a POST, custom headers, a timeout, or proper error
           handling            ->  $.ajax()
      NEED to fetch some data quickly with a GET
                               ->  $.get()  or  $.getJSON()
      NEED to drop a block of HTML into a container
                               ->  .load()
   ```
   - The modern alternative worth naming: the browser's own `fetch()` API with `async/await` does everything `$.ajax()` does, with no library at all.
   ```javascript
      const res  = await fetch("getUser.php");
      const data = await res.json();
   ```
   - One caution about `fetch()`: unlike `$.ajax()`, it does `not` treat an HTTP `404` or `500` as an error — the promise resolves, and `res.ok` must be checked explicitly. That difference catches out developers moving from jQuery.

10. **How do you change the value of a HTML element using HTML DOM?** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1058 (ET: AUST)]*

Answer: The value of an HTML element is changed through the DOM by selecting the element and then assigning to the appropriate property. `Which` property depends on the kind of element.
    ```javascript
       // 1. the CONTENT of an ordinary element
       document.getElementById("demo").innerHTML = "New text";

       // 2. the VALUE of a form field
       document.getElementById("nameBox").value = "Rahim";

       // 3. an ATTRIBUTE
       document.getElementById("pic").src = "new.jpg";
    ```

    The three properties for content
    ```javascript
       var el = document.getElementById("demo");

       el.innerHTML   = "<b>Bold</b>";   // parsed as HTML - shows
                                         // BOLD text
       el.textContent = "<b>Bold</b>";   // plain text - shows the
                                         // TAGS literally
       el.innerText   = "Visible only";  // like textContent, but
                                         // respects CSS visibility
    ```
    ```
       innerHTML vs textContent - the security point

       innerHTML PARSES the string as HTML. Assigning user input to
       it creates an XSS vulnerability :

            el.innerHTML = userInput;    // DANGEROUS
            // a user could submit  <img src=x onerror="steal()">

       ALWAYS use textContent for data that came from a user.
       Use innerHTML only for markup you generated yourself.
    ```

    Form elements use `.value`, not `.innerHTML`
    ```javascript
       document.getElementById("txt").value    = "Rahim";   // text box
       document.getElementById("chk").checked  = true;      // checkbox
       document.getElementById("sel").value    = "Dhaka";   // dropdown
       document.getElementById("area").value   = "Notes";   // textarea
    ```
    ```
       An <input> has NO inner HTML - it is an empty element. Setting
       innerHTML on it does nothing at all, and this is the
       commonest DOM mistake.
    ```

    A complete example
    ```html
    <!DOCTYPE html>
    <html>
    <head><meta charset="UTF-8"><title>Change value</title></head>
    <body>

        <p id="demo">Original text</p>
        <input type="text" id="nameBox" value="old name">
        <img id="pic" src="old.jpg" alt="Picture" width="150">
        <br><br>
        <button onclick="changeAll()">Change everything</button>

    <script>
        function changeAll() {
            // content of a paragraph
            document.getElementById("demo").textContent =
                "The text has been changed";

            // value of an input
            document.getElementById("nameBox").value = "Rahim";

            // attribute of an image
            document.getElementById("pic").src = "new.jpg";
            document.getElementById("pic").alt = "New picture";

            // a style
            document.getElementById("demo").style.color = "green";

            // a class - the better way to change appearance
            document.getElementById("demo").classList.add("highlight");
        }
    </script>

    </body>
    </html>
    ```

    Selecting the element
    ```javascript
       document.getElementById("demo")          // ONE element or null
       document.querySelector(".card")          // FIRST CSS match
       document.querySelectorAll(".card")       // ALL matches
       document.getElementsByClassName("card")  // a LIVE collection
       document.getElementsByTagName("p")       // a live collection
    ```
    ```
       To change MANY elements, loop over the collection :

            document.querySelectorAll(".price").forEach(function (el) {
                el.textContent = "100 Tk";
            });
    ```

    The mistake that breaks most scripts
    ```
       THE SCRIPT RUNS BEFORE THE ELEMENT EXISTS

            <head>
                <script>
                    document.getElementById("demo").innerHTML = "Hi";
                    // TypeError : Cannot set property of null
                </script>
            </head>
            <body><p id="demo"></p></body>

       THE FIX - any one of :
            put the <script> at the END of <body>
            use  <script src="app.js" defer></script>
            wrap the code in
                 document.addEventListener("DOMContentLoaded",
                     function () { ... });
    ```
    - The jQuery equivalents, for comparison: `$("#demo").html("New text")`, `$("#demo").text("New text")` and `$("#nameBox").val("Rahim")`. The distinction between `.html()` and `.text()` is exactly the `innerHTML` and `textContent` distinction, with the same security implication.

11. **Difference among $.ajax(), $.load() and $.get().** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1162 (ET: N/A)]*

Answer: The three are all jQuery AJAX methods, differing in `flexibility` and in `what they do with the response`.

    | Point | `$.ajax()` | `$.get()` | `$.load()` |
    |---|---|---|---|
    | Type | The `low-level` general method | `Shorthand` for GET | A method on a `selected element` |
    | HTTP method | `Any` — GET, POST, PUT, DELETE | `GET` only | GET, or POST if data is passed |
    | Called on | `$` | `$` | `$("#selector")` |
    | Response handling | Given to `your callback` | Given to `your callback` | `Inserted into the element` automatically |
    | Options | `All` | Few | Few |
    | Error handling | `Full` — error, complete, statusCode | Chain `.fail()` | A status argument in the callback |
    | Loads part of a page | No | No | `Yes` — with a fragment selector |

    `$.ajax()`
    ```javascript
       $.ajax({
           url:      "getUser.php",
           type:     "POST",
           data:     { id: 5 },
           dataType: "json",
           timeout:  5000,
           beforeSend: function () { $("#loader").show(); },
           success:  function (r)  { $("#result").html(r.name); },
           error:    function (xhr, status, err) {
                         console.log("Failed : " + err);
                     },
           complete: function ()   { $("#loader").hide(); }
       });
    ```
    - The only method giving access to `type`, `timeout`, `headers`, `beforeSend` and `contentType`. Every other jQuery AJAX method is a wrapper around it.

    `$.get()`
    ```javascript
       $.get("getUser.php", { id: 5 }, function (data) {
           $("#result").html(data);
       });

       // it returns a promise
       $.get("data.json")
        .done(function (d) { console.log(d); })
        .fail(function ()  { console.log("error"); });
    ```
    ```
       Equivalent to :
            $.ajax({ url: "getUser.php", type: "GET",
                     data: { id: 5 }, success: function (d) {...} });

       Companions : $.post() , $.getJSON() , $.getScript()
    ```

    `$.load()`
    ```javascript
       // load a page fragment into a div
       $("#content").load("page.html");

       // load ONLY PART of another page
       $("#content").load("page.html #section2");

       // with a callback
       $("#content").load("page.html", function (resp, status) {
           if (status === "error")
               $("#content").html("Could not load the content.");
       });
    ```
    ```
       THE TWO DISTINCTIVE FEATURES

       1. It is called on an ELEMENT and INSERTS the response into
          that element automatically - no success callback is needed
          simply to display the result.

       2. It can fetch a FRAGMENT of another page. jQuery downloads
          the WHOLE page and then keeps only the part matching the
          selector - convenient, but the entire page still crosses
          the network.
    ```

    The relationship
    ```
       $.ajax()   -  the engine
          |
          +--- $.get()      GET , callback
          +--- $.post()     POST , callback
          +--- $.getJSON()  GET , parsed as JSON
          +--- .load()      GET , inserted into the element

       All of them ultimately call $.ajax().
    ```
    - Which to use: `$.ajax()` when a POST, a timeout, custom headers or real error handling is needed; `$.get()` or `$.getJSON()` for a quick data fetch; `.load()` to drop a block of HTML into a container.
    - The modern alternative: the browser's own `fetch()` with `async/await` needs no library at all. One difference to remember — `fetch()` does `not` treat a `404` or `500` as an error, so `res.ok` must be checked explicitly, whereas `$.ajax()` calls its `error` handler automatically.

12. **How to change html attribute through html DOM?** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1163 (ET: N/A)]*, *[Investment Corporation Bangladesh Assistant Programmer 2017 compact it 1216 (ET: N/A)]*

Answer: An attribute is changed through the DOM either by assigning to the matching `property` or by calling `setAttribute()`.
    ```javascript
       var img = document.getElementById("pic");

       // 1. as a PROPERTY - shorter, and works for standard
       //    attributes
       img.src = "new.jpg";
       img.alt = "New picture";

       // 2. with setAttribute() - works for ANY attribute
       img.setAttribute("src", "new.jpg");
       img.setAttribute("data-id", "42");
    ```

    The methods
    ```javascript
       el.setAttribute("name", "value")   // set or replace
       el.getAttribute("name")            // read - returns a STRING
                                          // or null
       el.removeAttribute("name")         // delete
       el.hasAttribute("name")            // true / false
    ```

    A complete example
    ```html
    <!DOCTYPE html>
    <html>
    <head><meta charset="UTF-8"><title>Change attribute</title></head>
    <body>

        <img id="pic" src="old.jpg" alt="Old picture" width="150">
        <a  id="link" href="old.html">Click here</a>
        <input id="box" type="text" value="text">
        <br><br>
        <button onclick="changeAttributes()">Change</button>

    <script>
        function changeAttributes() {

            // an image
            var img = document.getElementById("pic");
            img.src = "new.jpg";
            img.setAttribute("alt", "New picture");
            img.setAttribute("width", "300");

            // a link
            var link = document.getElementById("link");
            link.href   = "https://example.com";
            link.target = "_blank";
            link.setAttribute("rel", "noopener noreferrer");

            // a form field
            var box = document.getElementById("box");
            box.setAttribute("placeholder", "Enter your name");
            box.disabled = true;             // a BOOLEAN attribute

            // remove one
            img.removeAttribute("width");
        }
    </script>

    </body>
    </html>
    ```

    Property against `setAttribute()` — where they differ
    ```
       For most attributes they are interchangeable. Three cases
       where they are NOT :

       1. BOOLEAN ATTRIBUTES - checked , disabled , selected ,
          readonly

            el.checked = true;                    // CORRECT
            el.setAttribute("checked", "false");  // WRONG - the
                 attribute's PRESENCE is what counts, so this
                 actually CHECKS the box.
            To uncheck : el.removeAttribute("checked") , or better
                 el.checked = false;

       2. value ON AN INPUT

            el.value                  the CURRENT value, including
                                      whatever the user typed
            el.getAttribute("value")  the value written in the HTML -
                                      the DEFAULT, which does not
                                      change as the user types

       3. class - the attribute is "class" but the property is
          "className"

            el.className = "card active";
            el.setAttribute("class", "card active");
            el.classList.add("active");        // the BEST way
            el.classList.remove("active");
            el.classList.toggle("active");
    ```
    ```
       AND href :
            link.href                  returns the ABSOLUTE URL,
                                       e.g. "https://site.com/a.html"
            link.getAttribute("href")  returns exactly what was
                                       written, e.g. "a.html"
    ```

    Changing style — attribute or class
    ```javascript
       // one style at a time
       el.style.color           = "red";
       el.style.backgroundColor = "yellow";   // camelCase , NOT
                                              // background-color

       // BETTER - change a class and keep the styling in CSS
       el.classList.add("highlight");
    ```
    - Why the class approach is preferred: styling stays in the `stylesheet` where it belongs, one class can carry a dozen properties, and the change is easy to reverse with `classList.remove()`.

    Custom data attributes
    ```html
       <div id="prod" data-id="42" data-price="1500"></div>
    ```
    ```javascript
       var d = document.getElementById("prod");

       d.dataset.id     // "42"    - the dataset API
       d.dataset.price  // "1500"
       d.dataset.stock = "10";     // adds data-stock="10"
    ```
    - Note that every attribute value is a `string`. `d.dataset.price` gives `"1500"`, so `Number()` or `parseInt()` is needed before arithmetic — otherwise `d.dataset.price + 1` produces `"15001"`.
    - The jQuery equivalents: `$("#pic").attr("src", "new.jpg")`, `$("#pic").removeAttr("width")`, `$("#box").prop("disabled", true)` and `$("#prod").data("id")`. jQuery draws the same distinction — `attr()` for attributes, `prop()` for boolean properties.

13. **Suppose you've a javaScript code name as “bankScript” write the code for loading in HTML using JS.** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1173 (ET: N/A)]*

Answer: An external JavaScript file named `bankScript` is loaded with the `<script>` tag and its `src` attribute.
    ```html
       <script src="bankScript.js"></script>
    ```

    The complete page
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Bank Application</title>

        <!-- external CSS -->
        <link rel="stylesheet" href="style.css">

        <!-- external JavaScript , loaded with defer -->
        <script src="bankScript.js" defer></script>
    </head>
    <body>

        <h1>Bank Application</h1>
        <input type="text" id="amount" placeholder="Enter amount">
        <button id="btn">Calculate Interest</button>
        <p id="result"></p>

    </body>
    </html>
    ```

    `bankScript.js`
    ```javascript
       function calculateInterest(principal, rate, years) {
           return (principal * rate * years) / 100;
       }

       document.addEventListener("DOMContentLoaded", function () {

           document.getElementById("btn").addEventListener("click",
               function () {
                   var p = Number(document.getElementById("amount").value);

                   if (!p || p <= 0) {
                       document.getElementById("result").textContent =
                           "Please enter a valid amount";
                       return;
                   }

                   var interest = calculateInterest(p, 8, 1);
                   document.getElementById("result").textContent =
                       "Interest for 1 year : " + interest + " Tk";
               });
       });
    ```

    Where the tag may be placed
    ```
       1. AT THE END OF <body>  - the traditional recommendation
            <body>
                ... all the HTML ...
                <script src="bankScript.js"></script>
            </body>
          The HTML is parsed first, so every element already exists.

       2. IN <head> WITH defer  - the modern best practice
            <script src="bankScript.js" defer></script>
          The file downloads in PARALLEL with parsing and runs after
          the HTML is complete. Fastest, and the DOM is ready.

       3. IN <head> WITHOUT defer  - AVOID
            Parsing STOPS while the file downloads and runs, so the
            page appears later ; and getElementById returns NULL,
            because the elements do not exist yet.
    ```
    ```
       THE THREE LOADING MODES

       <script src="a.js">          fetch and run IMMEDIATELY ;
            parsing BLOCKS
       <script src="a.js" async>    fetch in parallel , run AS SOON
            AS IT ARRIVES - order between files NOT guaranteed
       <script src="a.js" defer>    fetch in parallel , run after
            parsing , IN ORDER

       Use  defer  for your own scripts that depend on the DOM ; use
       async only for independent scripts such as analytics.
    ```

    Loading several files, and the order rule
    ```html
       <!-- a LIBRARY must come BEFORE the code that uses it -->
       <script src="jquery-3.7.1.min.js"></script>
       <script src="bankScript.js"></script>
    ```
    - With plain `src` or with `defer`, files execute in the order written. With `async` they do not, so a library and the code that depends on it must never both use `async`.

    Loading a script dynamically, from JavaScript
    ```javascript
       var s = document.createElement("script");
       s.src = "bankScript.js";
       s.onload  = function () { console.log("loaded"); };
       s.onerror = function () { console.log("failed to load"); };
       document.head.appendChild(s);
    ```

    As an ES6 module
    ```html
       <script type="module" src="bankScript.js"></script>
    ```
    ```javascript
       // bankScript.js
       export function calculateInterest(p, r, y) {
           return (p * r * y) / 100;
       }

       // another file
       import { calculateInterest } from "./bankScript.js";
    ```
    - Modules are `deferred by default` and have their own scope, so nothing leaks into the global namespace. They must be served over `http` or `https`, not opened as a `file://` page.
    - Why external files are preferred to inline script: the browser `caches` the file, so it is downloaded once and reused on every page; one file serves the whole site; the HTML stays readable; and behaviour is separated from structure — the same argument that puts CSS in its own file.

14. **What is closure in JavaScript? Explain with an example?** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1217 (ET: N/A)]*

Answer: What a closure is
    - A `closure` is a function that `remembers the variables of the scope in which it was created`, and can still use them even after that outer function has finished executing.
    ```
       A closure is formed whenever a function is defined INSIDE
       another function and then used OUTSIDE it. The inner function
       keeps a live reference to the outer function's variables -
       they are NOT copied, and they are NOT destroyed when the
       outer function returns.
    ```

    Example — a counter
    ```javascript
       function makeCounter() {
           let count = 0;                    // a LOCAL variable

           return function () {              // the inner function
               count++;                      // it USES count
               return count;
           };
       }

       const c1 = makeCounter();
       const c2 = makeCounter();

       console.log(c1());     // 1
       console.log(c1());     // 2
       console.log(c1());     // 3
       console.log(c2());     // 1   - a SEPARATE closure
    ```
    ```
       TESTED OUTPUT :  1  2  3  1

       Two things this proves :

       1. count SURVIVES after makeCounter() has returned. Normally
          a local variable is destroyed when its function ends -
          here it is kept alive because the returned function still
          refers to it.

       2. c1 and c2 have THEIR OWN count. Each call to makeCounter()
          creates a NEW scope and therefore a NEW closure. This is
          why c2() returns 1 and not 4.
    ```

    Example — data privacy, the main practical use
    ```javascript
       function createAccount(initialBalance) {
           let balance = initialBalance;     // PRIVATE - unreachable
                                             // from outside

           return {
               deposit: function (amount) {
                   balance += amount;
                   return balance;
               },
               withdraw: function (amount) {
                   if (amount > balance) return "Insufficient balance";
                   balance -= amount;
                   return balance;
               },
               getBalance: function () {
                   return balance;
               }
           };
       }

       const acc = createAccount(1000);

       console.log(acc.deposit(500));    // 1500
       console.log(acc.withdraw(200));   // 1300
       console.log(acc.getBalance());    // 1300
       console.log(acc.withdraw(5000));  // "Insufficient balance"
       console.log(acc.balance);         // undefined  <- PRIVATE
    ```
    ```
       TESTED OUTPUT : 1500 , 1300 , 1300 , "Insufficient balance" ,
                       undefined

       The last line is the point. balance CANNOT be read or written
       directly - only the three returned functions can touch it.
       JavaScript had no  private  keyword, and closures are how
       ENCAPSULATION was achieved.
    ```

    The classic interview trap
    ```javascript
       // WITH var - the wrong output
       for (var i = 1; i <= 3; i++) {
           setTimeout(function () { console.log(i); }, 0);
       }
       // prints  4  4  4

       // WITH let - correct
       for (let j = 1; j <= 3; j++) {
           setTimeout(function () { console.log(j); }, 0);
       }
       // prints  1  2  3
    ```
    ```
       TESTED : var gives "4 4 4" , let gives "1 2 3"

       WHY :  var is FUNCTION-scoped, so all three callbacks close
       over the SAME i. By the time they run, the loop has finished
       and i is 4.

       let is BLOCK-scoped, so each iteration creates a NEW binding
       of j - three separate closures, holding 1, 2 and 3.

       The pre-ES6 fix was an IIFE, which created a new scope by
       hand :
            for (var i = 1; i <= 3; i++) {
                (function (n) {
                    setTimeout(function () { console.log(n); }, 0);
                })(i);
            }
    ```

    Where closures are used in real code
    ```
       PRIVATE DATA         as in createAccount above
       FUNCTION FACTORIES   function multiplier(n) {
                                return x => x * n;
                            }
                            const double = multiplier(2);
       CALLBACKS and EVENT HANDLERS - they close over the variables
            they need
       THE MODULE PATTERN   an IIFE returning only a public API
       MEMOISATION and CACHING - the cache lives in the closure
       setTimeout , setInterval , and every asynchronous callback
       PARTIAL APPLICATION and currying
    ```

    The caution
    ```
       A closure keeps its outer variables ALIVE, so they cannot be
       garbage collected while the closure exists. Holding a
       closure over a large object - a big array, a DOM node - keeps
       that object in memory, which is a real source of MEMORY LEAKS
       in long-running pages.
    ```
    - The definition to give in one sentence: `a closure is the combination of a function and the lexical environment in which it was declared`. Every JavaScript function is technically a closure; the term is used when the surrounding variables actually outlive the call that created them.

15. **Difference among $.ajax(), $.load(), $.get().** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1217 (ET: N/A)]*

Answer: The three are jQuery AJAX methods, differing in `flexibility` and in `what they do with the response`.

    | Point | `$.ajax()` | `$.get()` | `$.load()` |
    |---|---|---|---|
    | Type | The `low-level` general method | `Shorthand` for GET | A method on a `selected element` |
    | HTTP method | `Any` — GET, POST, PUT, DELETE | `GET` only | GET, or POST if data is passed |
    | Called on | `$` | `$` | `$("#selector")` |
    | Response | Given to `your callback` | Given to `your callback` | `Inserted into the element` automatically |
    | Options | `All` | Few | Few |
    | Error handling | `Full` — error, complete, statusCode | Chain `.fail()` | A status argument in the callback |
    | Loads part of a page | No | No | `Yes` — with a fragment selector |
    | Returns | A jqXHR promise | A jqXHR promise | The `jQuery object`, for chaining |

    `$.ajax()` — the general method
    ```javascript
       $.ajax({
           url:      "getUser.php",
           type:     "POST",
           data:     { id: 5 },
           dataType: "json",
           timeout:  5000,
           beforeSend: function () { $("#loader").show(); },
           success:  function (r) { $("#result").html(r.name); },
           error:    function (xhr, status, err) {
                         console.log("Failed : " + err);
                     },
           complete: function () { $("#loader").hide(); }
       });
    ```
    - The only one of the three that exposes `type`, `timeout`, `headers`, `contentType`, `beforeSend` and `async`. Every other jQuery AJAX method is a wrapper around it.

    `$.get()` — a GET request
    ```javascript
       $.get("getUser.php", { id: 5 }, function (data) {
           $("#result").html(data);
       });

       // it returns a promise
       $.get("data.json")
        .done(function (d) { console.log(d); })
        .fail(function ()  { console.log("error"); })
        .always(function () { console.log("finished"); });
    ```
    ```
       Exactly equivalent to :
            $.ajax({ url: "getUser.php", type: "GET",
                     data: { id: 5 }, success: function (d) {...} });

       Its companions : $.post() , $.getJSON() , $.getScript()
    ```

    `$.load()` — load HTML into an element
    ```javascript
       $("#content").load("page.html");

       // load ONLY PART of another page
       $("#content").load("page.html #section2");

       // with a callback
       $("#content").load("page.html", function (resp, status) {
           if (status === "error")
               $("#content").html("Could not load the content.");
       });

       // passing data makes it a POST
       $("#content").load("search.php", { q: "laptop" });
    ```
    ```
       THE TWO THINGS THAT SET IT APART

       1. It is called on an ELEMENT and INSERTS the response into
          that element automatically. No callback is needed simply
          to display the result.

       2. It can fetch a FRAGMENT. jQuery downloads the WHOLE page
          and then keeps only the part matching the selector -
          convenient, but the entire page still crosses the network.
    ```

    The relationship
    ```
       $.ajax()   -  the engine
          |
          +--- $.get()      GET , callback
          +--- $.post()     POST , callback
          +--- $.getJSON()  GET , parsed as JSON
          +--- .load()      GET , inserted into the element

       All three ultimately call $.ajax().
    ```
    - Which to use: `$.ajax()` for a POST, a timeout, custom headers or real error handling; `$.get()` or `$.getJSON()` for a quick data fetch; `.load()` to drop a block of HTML into a container.
    - The modern replacement: the browser's own `fetch()` with `async/await` needs no library. One difference to note — `fetch()` does `not` treat a `404` or `500` as an error, so `res.ok` must be checked by hand, whereas `$.ajax()` calls its `error` handler automatically.

16. **What is the working procedure of AJAX?** *[Agrani Bank Ltd. Senior Officer (IT) 2017 compact it 1221-1222 (ET: N/A)]*

Answer: What AJAX is
    - `AJAX` stands for `Asynchronous JavaScript and XML`. It is a technique that lets a web page `exchange data with the server and update part of itself, without reloading the whole page`.
    ```
       WITHOUT AJAX
            click -> the whole page is requested -> the whole page
            reloads -> the screen flickers and scroll position is
            lost

       WITH AJAX
            click -> JavaScript sends a background request -> only
            the reply data comes back -> only the relevant part of
            the page is updated
    ```
    - Despite the name, `XML` is rarely used now — `JSON` replaced it — and AJAX requests need not be asynchronous, though they almost always are.

    The working procedure
    ```mermaid
    sequenceDiagram
        participant U as User
        participant B as Browser (JS)
        participant X as XMLHttpRequest
        participant S as Server
        participant D as Database
        U->>B: clicks or types
        B->>X: create the request object
        X->>S: HTTP request (in the background)
        S->>D: query
        D-->>S: data
        S-->>X: response (JSON / HTML / XML)
        X->>B: onreadystatechange fires
        B->>U: update part of the page (DOM)
    ```
    ```
       STEP BY STEP

       1. An EVENT occurs - a click, a keystroke, a page load.

       2. JavaScript creates an XMLHttpRequest object (or calls
          fetch()).
                 var xhr = new XMLHttpRequest();

       3. It CONFIGURES the request - the method, the URL, and
          whether it is asynchronous.
                 xhr.open("GET", "getData.php?id=5", true);

       4. It registers a CALLBACK to run when the state changes.
                 xhr.onreadystatechange = function () { ... };

       5. It SENDS the request. Control returns IMMEDIATELY - this
          is what "asynchronous" means. The page stays responsive
          and the user can carry on.
                 xhr.send();

       6. The SERVER receives the request, runs its code, queries
          the database, and sends back only the DATA - as JSON,
          HTML, XML or plain text. It does NOT send a whole page.

       7. When the response arrives the CALLBACK fires. It checks
          readyState === 4 (done) and status === 200 (OK).

       8. JavaScript UPDATES THE DOM with the data - only the part
          of the page that changed.
    ```

    The code — plain XMLHttpRequest
    ```javascript
       function loadData() {
           var xhr = new XMLHttpRequest();

           xhr.onreadystatechange = function () {
               if (xhr.readyState === 4) {          // 4 = DONE
                   if (xhr.status === 200) {        // 200 = OK
                       var data = JSON.parse(xhr.responseText);
                       document.getElementById("result").textContent =
                           data.name;
                   } else {
                       document.getElementById("result").textContent =
                           "Error : " + xhr.status;
                   }
               }
           };

           xhr.open("GET", "getUser.php?id=5", true);
           xhr.send();
       }
    ```
    ```
       THE FIVE readyState VALUES

            0  UNSENT           open() not yet called
            1  OPENED           open() called
            2  HEADERS_RECEIVED
            3  LOADING          the response is arriving
            4  DONE             the response is complete

       Only state 4 matters in practice, and status must ALSO be
       checked - state 4 with status 404 means the request finished
       and FAILED.
    ```

    The same thing with `fetch()` — the modern way
    ```javascript
       async function loadData() {
           try {
               const res = await fetch("getUser.php?id=5");

               if (!res.ok)                      // MUST be checked
                   throw new Error("HTTP " + res.status);

               const data = await res.json();
               document.getElementById("result").textContent = data.name;

           } catch (err) {
               document.getElementById("result").textContent =
                   "Error : " + err.message;
           }
       }
    ```
    - The trap in `fetch()`: it does `not` reject on a `404` or `500`. The promise resolves normally, so `res.ok` must be tested explicitly — otherwise an error page is parsed as if it were data.

    Where AJAX is used
    ```
       live SEARCH SUGGESTIONS as the user types
       FORM VALIDATION against the server - "is this username taken ?"
       INFINITE SCROLL and "load more"
       a chat application
       auto-saving a draft
       updating a cart total without leaving the page
       dependent DROPDOWNS - choosing a district fills the thana list
    ```

    Advantages and limitations
    ```
       ADVANTAGES
         FASTER and smoother - only data crosses the network, not a
              whole page
         LESS BANDWIDTH and less server load
         the page does not FLICKER and the scroll position is kept
         a desktop-like experience

       LIMITATIONS
         it needs JAVASCRIPT ENABLED
         the BACK BUTTON and BOOKMARKING break unless the History
              API is used
         SEARCH ENGINES may not see content loaded by AJAX
         SAME-ORIGIN POLICY blocks requests to another domain unless
              the server sends CORS headers
         debugging is harder, because the request is invisible in
              the address bar
    ```
    - The security point that must be stated: an AJAX endpoint is a `public URL`. Anyone can call it directly with `curl`, without the page. So `authentication, authorisation and input validation must all be enforced on the server` — the fact that the only caller is your own JavaScript proves nothing.

## HTTP Protocol (10)

1. **What do the following specific HTTP status codes mean? Write down the exact standard text phrase for each: (a) 200 (b) 403 (c) 503** [SO IT 25-07-2026]

Answer: The three status codes, with their exact standard reason phrases.
   ```
      (a) 200  ->  OK
      (b) 403  ->  Forbidden
      (c) 503  ->  Service Unavailable
   ```

   What each one means

   (a) `200 OK`
   - The request `succeeded`. This is the normal response for a successful `GET`, `POST` or `HEAD`. For a `GET` the requested resource is in the body of the response.
   ```
      Class 2xx = SUCCESS.
      Other members : 201 Created , 202 Accepted , 204 No Content
   ```

   (b) `403 Forbidden`
   - The server `understood` the request and `refuses to fulfil it`. The client is `identified` but does `not have permission`. Repeating the request will not help, and authenticating again will not help either.
   ```
      Causes : file or directory permissions are wrong ; directory
           listing is disabled ; the user's role does not allow the
           action ; access blocked by IP.

      403 vs 401 - the distinction that is examined :

           401 Unauthorized  "I do not know WHO you are."
                Authentication is MISSING or INVALID. Log in and
                try again. The server sends a WWW-Authenticate
                header.

           403 Forbidden     "I know who you are, and you are NOT
                ALLOWED." Authentication succeeded ; AUTHORISATION
                failed. Logging in again changes nothing.

      Class 4xx = CLIENT ERROR - the fault is at the client's end.
   ```

   (c) `503 Service Unavailable`
   - The server is `temporarily unable` to handle the request — it is overloaded, or it is down for maintenance. The condition is `temporary`, and the server may send a `Retry-After` header saying when to try again.
   ```
      Causes : the server is overloaded ; scheduled maintenance ;
           the application pool has stopped ; a backend service is
           unreachable.

      503 vs 500 :
           500 Internal Server Error  the code CRASHED - a bug, an
                unhandled exception. The problem is in the
                application.
           503 Service Unavailable    the server is UP but cannot
                serve right now. Nothing is broken ; it is
                temporarily unavailable.

      Class 5xx = SERVER ERROR - the fault is at the server's end.
   ```

   The five classes of status code
   ```
      1xx  INFORMATIONAL   the request was received, processing
           100 Continue , 101 Switching Protocols

      2xx  SUCCESS
           200 OK , 201 Created , 204 No Content

      3xx  REDIRECTION     further action is needed
           301 Moved Permanently , 302 Found ,
           304 Not Modified

      4xx  CLIENT ERROR
           400 Bad Request , 401 Unauthorized , 403 Forbidden ,
           404 Not Found , 405 Method Not Allowed ,
           429 Too Many Requests

      5xx  SERVER ERROR
           500 Internal Server Error , 502 Bad Gateway ,
           503 Service Unavailable , 504 Gateway Timeout
   ```
   - The first digit is what carries the meaning, and it is worth remembering as a rule: `2 = it worked`, `3 = look elsewhere`, `4 = your mistake`, `5 = our mistake`.

2. **Describe any two key differences between the HTTP GET and HTTP POST methods used for communication between a web browser and a web server.** *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

Answer: Two key differences between `GET` and `POST`.

   1. Where the data is carried
   ```
      GET   sends the data in the URL, as a QUERY STRING :

           GET /search?name=rahim&city=dhaka HTTP/1.1

           - the data is VISIBLE in the address bar
           - it is stored in the browser HISTORY and in server LOGS
           - it can be BOOKMARKED and shared as a link
           - it is limited in length - about 2,000 characters in
             practice

      POST  sends the data in the REQUEST BODY :

           POST /login HTTP/1.1
           Content-Type: application/x-www-form-urlencoded

           username=rahim&password=secret

           - the data is NOT in the URL
           - not in the address bar, not in history, not bookmarkable
           - NO practical size limit
           - it can carry a FILE UPLOAD, which GET cannot
   ```

   2. Effect on the server — safe against unsafe
   ```
      GET is meant to be SAFE and IDEMPOTENT.
           It should only READ data and change nothing. Repeating a
           GET has the same effect as making it once, so the browser
           may CACHE it, PREFETCH it, or repeat it on a refresh
           without warning.

      POST is NOT safe and NOT idempotent.
           It is meant to CHANGE something - create a record, make
           a payment, submit a form. The browser will NOT repeat it
           silently ; it asks "Confirm form resubmission ?" on a
           refresh, precisely because repeating it might charge the
           customer twice.
   ```
   ```
      THE PRACTICAL CONSEQUENCE

      Using GET for an action that changes data is a real
      vulnerability :

           <a href="/deleteUser?id=5">Delete</a>

      A search engine crawler following that link deletes the user.
      And a page on another site can trigger it with a hidden
      image :
           <img src="https://bank.com/transfer?to=attacker&amt=5000">
      This is CSRF, and it works because a GET is fired
      automatically with the victim's cookies.

      Any action that CHANGES STATE must use POST, PUT or DELETE,
      with a CSRF token.
   ```

   The full comparison

   | Point | GET | POST |
   |---|---|---|
   | Data location | In the `URL` (query string) | In the request `body` |
   | Visible in address bar | `Yes` | `No` |
   | Size limit | About `2,000` characters | Practically `unlimited` |
   | Bookmarkable | `Yes` | No |
   | In browser history | `Yes` | No |
   | Cached by the browser | `Yes` | No |
   | Safe on refresh | Yes | Asks to `resubmit` |
   | Idempotent | `Yes` | `No` |
   | File upload | No | `Yes` |
   | Default for `<form>` | `Yes` | Must be specified |
   | Use for | `Reading` — search, filter, view | `Changing` — login, submit, pay |

   When to use each
   ```
      USE GET when
           the request only READS data
           the URL should be shareable or bookmarkable
           the parameters are not sensitive
           -> search results , a filtered product list , a report
              by date range

      USE POST when
           the request CHANGES something
           the data is SENSITIVE - a password
           the data is LARGE, or is a FILE
           -> login , registration , payment , file upload ,
              deleting a record
   ```
   - One point that must be stated plainly: `POST is not encryption`. The data is hidden from the address bar but travels as plain text on the wire exactly as a GET does. Only `HTTPS` protects it. A password sent by POST over plain HTTP is just as readable to anyone on the network.

3. **6.7 What do the following specific HTTP status codes mean? Write down the exact standard text phrase for each: (a) 200 (b) 403 (c) 503** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

Answer: The three codes with their exact standard reason phrases.
   ```
      (a) 200  ->  OK
      (b) 403  ->  Forbidden
      (c) 503  ->  Service Unavailable
   ```

   (a) `200 OK`
   - The request `succeeded`. This is the normal reply to a successful `GET`, `POST` or `HEAD`; for a `GET` the requested resource is in the response body.
   ```
      Class 2xx = SUCCESS
      Also : 201 Created , 202 Accepted , 204 No Content
   ```

   (b) `403 Forbidden`
   - The server `understood` the request and `refuses to fulfil it`. The client is identified but does `not have permission`. Re-authenticating will not help.
   ```
      Causes : wrong file or directory permissions ; directory
           listing disabled ; the user's role does not allow the
           action ; blocked by IP address.

      401 vs 403 - the distinction that is examined :

           401 Unauthorized   "I do not know WHO you are."
                Authentication is MISSING or INVALID. The server
                sends a WWW-Authenticate header. Logging in fixes
                it.
           403 Forbidden      "I know who you are, and you are NOT
                ALLOWED." Authentication succeeded ; AUTHORISATION
                failed. Logging in again changes nothing.

      Class 4xx = CLIENT ERROR
   ```

   (c) `503 Service Unavailable`
   - The server is `temporarily unable` to handle the request — overloaded, or down for maintenance. The condition is temporary, and a `Retry-After` header may say when to try again.
   ```
      Causes : overload ; scheduled maintenance ; the application
           pool has stopped ; a backend service is unreachable.

      500 vs 503 :
           500 Internal Server Error  the code CRASHED - a bug or an
                unhandled exception. The application is broken.
           503 Service Unavailable    the server is UP but cannot
                serve right now. Nothing is broken.

      Class 5xx = SERVER ERROR
   ```

   The five classes
   ```
      1xx  INFORMATIONAL  100 Continue , 101 Switching Protocols
      2xx  SUCCESS        200 OK , 201 Created , 204 No Content
      3xx  REDIRECTION    301 Moved Permanently , 302 Found ,
                          304 Not Modified
      4xx  CLIENT ERROR   400 Bad Request , 401 Unauthorized ,
                          403 Forbidden , 404 Not Found ,
                          405 Method Not Allowed ,
                          429 Too Many Requests
      5xx  SERVER ERROR   500 Internal Server Error ,
                          502 Bad Gateway ,
                          503 Service Unavailable ,
                          504 Gateway Timeout
   ```
   - The first digit carries the meaning, and the rule is worth remembering directly: `2 = it worked`, `3 = look elsewhere`, `4 = your mistake`, `5 = our mistake`.
   - One practical note: `403` is sometimes returned deliberately in place of `404` so that an attacker cannot tell whether a resource exists. Conversely, some sites return `404` where `403` would be correct, for the same reason — hiding the existence of a resource is itself a security measure.

4. **(ক) ফর্ম জমা দেয়ার পদ্ধতি GET এবং POST এর মধ্যে পার্থক্য কী, কখন কোন পদ্ধতি ব্যবহার করতে হয় উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) Difference between the GET and POST form submission methods

   | Point | GET | POST |
   |---|---|---|
   | Data location | In the `URL` as a query string | In the request `body` |
   | Visible in address bar | `Yes` | `No` |
   | Size limit | About `2,000` characters | Practically `unlimited` |
   | Bookmarkable | `Yes` | No |
   | Stored in browser history | `Yes` | No |
   | Cached by the browser | `Yes` | No |
   | Behaviour on refresh | Repeats silently | Asks "`resubmit` the form?" |
   | Idempotent | `Yes` — repeating changes nothing | `No` |
   | File upload | Not possible | `Possible` |
   | Default for `<form>` | `Yes` | Must be specified |
   | Intended for | `Reading` data | `Changing` data |

   What each request looks like
   ```
      GET
           GET /search?name=rahim&city=dhaka HTTP/1.1
           Host: example.com

           The data is IN THE URL, after the ? , with pairs
           separated by & .

      POST
           POST /login HTTP/1.1
           Host: example.com
           Content-Type: application/x-www-form-urlencoded

           username=rahim&password=secret

           The data is in the BODY, after the headers.
   ```

   The HTML
   ```html
      <!-- GET - a search form -->
      <form action="search.php" method="get">
          <input type="text" name="q">
          <button type="submit">Search</button>
      </form>
      <!-- submits to :  search.php?q=laptop  -->

      <!-- POST - a login form -->
      <form action="login.php" method="post">
          <input type="text"     name="username">
          <input type="password" name="password">
          <button type="submit">Login</button>
      </form>

      <!-- POST with a file upload - enctype is REQUIRED -->
      <form action="upload.php" method="post"
            enctype="multipart/form-data">
          <input type="file" name="photo">
          <button type="submit">Upload</button>
      </form>
   ```

   When to use GET
   ```
      The request only READS data and changes nothing, and the URL
      should be shareable.

      EXAMPLES
        a SEARCH form            search.php?q=laptop
        a FILTERED product list  products.php?category=phone&max=20000
        a report by date range   report.php?from=2026-01-01
        pagination               list.php?page=3

      WHY GET IS RIGHT HERE : the result can be BOOKMARKED, sent as
      a link, and CACHED. A search result page that cannot be shared
      as a URL is a worse product.
   ```

   When to use POST
   ```
      The request CHANGES something, or the data is sensitive,
      large, or a file.

      EXAMPLES
        LOGIN                    the password must not be in the URL
        REGISTRATION
        PAYMENT and fund transfer
        FILE UPLOAD              GET cannot carry a file at all
        DELETING or updating a record
        a long comment or article
   ```

   The rule that must be stated
   ```
      NEVER USE GET FOR AN ACTION THAT CHANGES DATA.

           <a href="/deleteUser?id=5">Delete</a>

      A search-engine crawler following that link DELETES THE USER.
      And another site can fire it from a hidden image :
           <img src="https://bank.com/transfer?to=attacker&amt=5000">
      which sends it automatically with the victim's cookies. This
      is CSRF.

      Any state-changing action must use POST (or PUT / DELETE),
      with a CSRF TOKEN.
   ```
   - One point candidates often get wrong: `POST is not encryption`. It merely keeps the data out of the address bar; on the wire it travels as plain text exactly as a GET does. Only `HTTPS` protects it, so a password sent by POST over plain HTTP is just as readable to anyone on the network.

5. **What is cookie? What is its purpose?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*

Answer: What a cookie is
   - A `cookie` is a small piece of data — a name and a value, usually under `4 KB` — that a web server sends to the browser, and that the browser then `stores and sends back with every subsequent request` to that site.
   ```
      HOW IT WORKS

      1. The server sends it in a response header :
           Set-Cookie: sessionId=abc123; Path=/; HttpOnly; Secure

      2. The browser STORES it.

      3. On every later request to that site the browser sends it
         back AUTOMATICALLY :
           Cookie: sessionId=abc123

      The programmer does nothing at step 3 - the browser attaches
      it by itself. That automatic behaviour is the whole point of
      a cookie, and it is also the reason CSRF attacks are
      possible.
   ```

   Its purpose
   ```
      1. SESSION MANAGEMENT - the main purpose
           HTTP is STATELESS : each request is independent and the
           server remembers nothing. A cookie carrying a SESSION ID
           is what lets the server recognise the same user across
           requests - so a login persists from page to page.
           Without cookies, a user would be logged out on every
           click.

      2. PERSONALISATION
           Language , theme , currency , font size , "last viewed"
           items - remembered between visits.

      3. TRACKING AND ANALYTICS
           Counting visitors, measuring how long they stay, and
           which pages they read. THIRD-PARTY cookies follow a user
           across different sites for advertising - which is why
           consent banners exist and why browsers now block them.

      4. SHOPPING CART
           Keeping items in the cart for a visitor who has not
           logged in.

      5. "REMEMBER ME"
           A long-lived cookie so the user need not log in again.
   ```

   Types of cookie
   ```
      BY LIFETIME
        SESSION cookie     no Expires attribute. Deleted when the
             browser closes. Used for the login session.
        PERSISTENT cookie  has Expires or Max-Age. Survives a
             restart. Used for preferences and "remember me".

      BY ORIGIN
        FIRST-PARTY   set by the site being visited.
        THIRD-PARTY   set by another domain whose content the page
             includes - an advertiser. Now blocked by default in
             most browsers.
   ```

   The security attributes — the part that matters
   ```
      Set-Cookie: sessionId=abc123; HttpOnly; Secure;
                  SameSite=Strict; Path=/; Max-Age=3600

      HttpOnly     JAVASCRIPT CANNOT READ IT. This is what limits
           the damage of an XSS flaw - a stolen script cannot read
           document.cookie and take the session.

      Secure       sent ONLY over HTTPS, never over plain HTTP.

      SameSite     Strict | Lax | None. Controls whether the cookie
           is sent on a request coming from ANOTHER SITE, which is
           the main defence against CSRF.

      Path , Domain   limit which URLs and hosts receive it.
      Max-Age / Expires   when it should be deleted.
   ```

   Reading and writing a cookie
   ```javascript
      // JavaScript
      document.cookie = "theme=dark; max-age=86400; path=/";
      console.log(document.cookie);   // all readable cookies
   ```
   ```php
      // PHP
      setcookie("theme", "dark", time() + 86400, "/");
      echo $_COOKIE["theme"];
   ```

   The limits and cautions
   ```
      SIZE      about 4 KB per cookie , and roughly 20 to 50
           cookies per domain
      OVERHEAD  every cookie is sent with EVERY request to that
           domain, including requests for images and stylesheets -
           so large cookies slow the site down
      NOT SECURE STORAGE  a cookie is stored in plain text on the
           user's machine and can be read and edited by the user.
           NEVER store a password, a card number or an amount in a
           cookie, and never trust its value without verifying it
           on the server
      PRIVACY   the user may delete or block cookies at any time,
           so the application must cope with their absence
   ```
   - The distinction from `Web Storage`: `localStorage` and `sessionStorage` hold far more (5–10 MB) and are `never sent to the server`. That makes them better for client-side preferences, but useless for session authentication — only a `cookie` is transmitted automatically, and only a cookie can be marked `HttpOnly`, which is exactly why sessions still use cookies.

6. **What is the difference between http and https?** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 648 (ET: BUET)], [BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 796 (ET: N/A)]*

Answer: Difference between HTTP and HTTPS

   | Point | HTTP | HTTPS |
   |---|---|---|
   | Full form | `HyperText Transfer Protocol` | `HTTP Secure` |
   | Encryption | `None` — plain text | `Encrypted` with TLS |
   | Default port | `80` | `443` |
   | URL prefix | `http://` | `https://` |
   | Certificate | Not needed | `SSL/TLS certificate` required |
   | Browser indication | "Not secure" warning | `Padlock` icon |
   | Data interception | Readable by anyone on the path | `Unreadable` |
   | Server identity | `Not verified` | `Verified` by a Certificate Authority |
   | Speed | Marginally faster | Slightly slower — negligible with HTTP/2 |
   | Search ranking | Penalised | `Preferred` by Google |
   | Required for | — | Payments, logins, HTTP/2, service workers |

   What HTTPS adds
   ```
      HTTPS is HTTP running inside a TLS tunnel. It provides three
      things :

      1. CONFIDENTIALITY - ENCRYPTION
           Nobody between the browser and the server can read the
           traffic. Over plain HTTP, anyone on the same Wi-Fi, the
           ISP, or an attacker at any router can read passwords,
           card numbers and cookies in plain text.

      2. INTEGRITY
           The data cannot be MODIFIED in transit without
           detection. Over HTTP an intermediary can inject
           advertisements, or alter a downloaded file.

      3. AUTHENTICATION
           The CERTIFICATE proves the server really is the site it
           claims to be, because a Certificate Authority has
           verified it. This is what prevents a fake bank site
           from impersonating the real one.
   ```

   How the TLS handshake works
   ```mermaid
   sequenceDiagram
       participant B as Browser
       participant S as Server
       B->>S: ClientHello (TLS versions, cipher suites)
       S->>B: ServerHello + certificate (public key)
       B->>B: verify the certificate with the CA
       B->>S: key exchange, encrypted with the public key
       B->>S: Finished (switch to encrypted)
       S->>B: Finished (switch to encrypted)
       B->>S: encrypted HTTP request
       S->>B: encrypted HTTP response
   ```
   ```
      1. The browser asks for a secure connection and lists the
         TLS versions and ciphers it supports.
      2. The server replies with its CERTIFICATE, which contains
         its PUBLIC KEY.
      3. The browser VERIFIES the certificate - is it signed by a
         trusted CA, is it for this domain, has it expired ?
      4. A SESSION KEY is agreed, protected by the server's public
         key.
      5. Everything after that is encrypted with the SYMMETRIC
         session key, which is far faster than public-key
         encryption.

      So HTTPS uses ASYMMETRIC encryption to agree a key, and then
      SYMMETRIC encryption for the data. This is the point most
      often asked.
   ```

   What HTTPS does and does not protect
   ```
      ENCRYPTED
           the URL PATH and query string
           the request and response BODIES
           all HEADERS, including cookies

      NOT HIDDEN
           the DOMAIN NAME - visible through DNS and SNI, so an
                observer knows you visited bank.com, but not which
                page
           the IP ADDRESS
           the SIZE and TIMING of the traffic
   ```
   - Two points that are widely misunderstood. First, `HTTPS does not mean the site is trustworthy` — it means the connection is private and the domain is verified. A phishing site can obtain a free certificate and show a padlock, so the padlock proves `who you are talking to`, not `that they are honest`. Second, `HTTPS is now effectively mandatory`: browsers mark HTTP pages "Not secure", `HTTP/2`, geolocation and service workers refuse to work without it, and free certificates from `Let's Encrypt` remove the old cost objection entirely.
   - The related mechanism worth naming: `HSTS` (HTTP Strict Transport Security), a response header that tells the browser to use HTTPS for that domain in future and refuse to fall back — closing the window in which a first plain-HTTP request could be intercepted.

7. **(গ) URL কী? একটি URL ক্লিক করার পর Web Page Show করার পূর্ব পর্যন্ত যে কয়টি Step হয় সেগুলির নাম লিখুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 705 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) What a URL is
   - `URL` stands for `Uniform Resource Locator`. It is the complete address saying `where a resource is and how to fetch it`.
   ```
      https://www.example.com:443/products/list.php?id=25#top
      |____|   |_____________| |_| |______________| |_____| |_|
      scheme      domain      port      path         query  frag

      SCHEME    https  - the protocol to use
      DOMAIN    www.example.com - which server
      PORT      443 - optional ; 80 for http , 443 for https
      PATH      /products/list.php - which resource
      QUERY     ?id=25 - parameters
      FRAGMENT  #top - a position within the page ; handled by the
                BROWSER and never sent to the server
   ```

   The steps from clicking a URL to seeing the page
   ```mermaid
   flowchart TD
       A[1. URL parsed] --> B[2. Browser cache checked]
       B --> C[3. DNS lookup: domain to IP]
       C --> D[4. TCP three-way handshake]
       D --> E[5. TLS handshake, if HTTPS]
       E --> F[6. HTTP request sent]
       F --> G[7. Server processes it]
       G --> H[8. HTTP response returned]
       H --> I[9. HTML parsed, DOM built]
       I --> J[10. CSS, JS, images fetched]
       J --> K[11. Render tree, layout, paint]
   ```
   ```
      1. URL PARSING
           The browser splits the URL into scheme, host, port,
           path, query and fragment, and normalises it.

      2. CACHE CHECK
           Browser cache -> OS cache -> router cache -> ISP cache.
           If a valid cached copy exists, the page can be shown
           with no network request at all.

      3. DNS RESOLUTION
           The DOMAIN NAME must be turned into an IP ADDRESS.
           browser cache -> OS hosts file -> local DNS resolver ->
           root server -> TLD server (.com) -> authoritative
           server -> returns 93.184.216.34

      4. TCP CONNECTION - the THREE-WAY HANDSHAKE
                browser --SYN-----> server
                browser <--SYN-ACK- server
                browser --ACK-----> server
           A reliable connection now exists on port 80 or 443.

      5. TLS HANDSHAKE - only for HTTPS
           The server sends its CERTIFICATE ; the browser verifies
           it against a trusted CA ; a symmetric SESSION KEY is
           agreed. Everything afterwards is encrypted.

      6. HTTP REQUEST SENT
                GET /products/list.php?id=25 HTTP/1.1
                Host: www.example.com
                User-Agent: ...
                Cookie: sessionId=abc123
                Accept: text/html

      7. THE SERVER PROCESSES IT
           The web server routes the path ; for a dynamic page it
           runs PHP or Java code, which QUERIES THE DATABASE and
           builds the HTML.

      8. HTTP RESPONSE RETURNED
                HTTP/1.1 200 OK
                Content-Type: text/html; charset=UTF-8
                Content-Length: 4823

                <!DOCTYPE html> ...

      9. HTML PARSED, DOM BUILT
           The browser reads the HTML and builds the DOM TREE.

     10. SUB-RESOURCES FETCHED
           Every <link>, <script>, <img> triggers a FURTHER request
           - repeating steps 3 to 8 for each, though the connection
           is reused. CSS becomes the CSSOM. A blocking <script>
           stops parsing until it has run.

     11. RENDER : the DOM and CSSOM are combined into the RENDER
           TREE ; LAYOUT computes the position and size of every
           box ; PAINT draws the pixels ; COMPOSITE puts the layers
           together on screen.

     12. THE FRAGMENT is applied - the browser scrolls to #top.
           JavaScript's DOMContentLoaded and then load events fire.
   ```

   The short answer, if only the names of the steps are wanted
   ```
      1. Parse the URL
      2. Check the cache
      3. DNS lookup - domain to IP
      4. TCP three-way handshake
      5. TLS handshake (HTTPS only)
      6. Send the HTTP request
      7. Server processes and queries the database
      8. Receive the HTTP response
      9. Parse the HTML, build the DOM
     10. Fetch CSS, JavaScript and images
     11. Build the render tree, lay out, paint
     12. Page displayed ; events fire
   ```
   - Where the time actually goes: `DNS` and the `TCP/TLS handshakes` cost a full network round trip each, which is why `keep-alive`, `HTTP/2` connection reuse and a `CDN` — which shortens the distance — make a far larger difference than optimising the server code. And step 10 is usually the slowest of all: a page requesting eighty images is limited by the number of parallel connections, not by the server.

8. **(c) Explain the difference between Stateless and Stateful protocols. Which type of protocol http is?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 885-886 (ET: N/A)]*

Answer: Stateless and stateful protocols

   | Point | Stateless protocol | Stateful protocol |
   |---|---|---|
   | Server memory | Remembers `nothing` between requests | `Remembers` the client's state |
   | Each request | `Independent` and self-contained | Depends on `earlier` requests |
   | Server resources | `Low` — nothing stored per client | `High` — a session is held per client |
   | Scalability | `Excellent` — any server can serve any request | `Poor` — the client is tied to one server |
   | Crash recovery | `Easy` — nothing was lost | Hard — the session state is lost |
   | Complexity | `Simple` | Complex |
   | Examples | `HTTP`, HTTPS, UDP, DNS, IP | `FTP`, Telnet, SSH, TCP, SMTP |

   Stateless
   ```
      Every request must carry EVERYTHING the server needs. The
      server answers it and FORGETS the client completely.

      Request 1 : "give me page A"     -> served , forgotten
      Request 2 : "give me page B"     -> served , forgotten
                                          (the server does not know
                                           this is the same client)

      ADVANTAGES
        any server in a cluster can answer any request - so a LOAD
             BALANCER can send requests anywhere, and servers can
             be added freely
        no memory is consumed per client
        a server crash loses nothing
        requests can be CACHED

      DISADVANTAGE
        the client must resend its identity every time, so more
        data travels with each request
   ```

   Stateful
   ```
      The server keeps a RECORD of the conversation, so a request
      can depend on what came before.

      FTP example :
           USER rahim          -> the server remembers the user
           PASS secret         -> now authenticated
           CWD /reports        -> the server remembers the CURRENT
                                  DIRECTORY
           GET data.csv        -> fetched FROM that directory

      The GET only makes sense because the server remembered the
      earlier commands. That memory IS the state.
   ```

   Which type is HTTP?
   ```
      HTTP IS A STATELESS PROTOCOL.

      Each HTTP request is independent and complete in itself. The
      server does not, by the protocol, remember anything about a
      previous request from the same browser.
   ```
   - Why HTTP was designed that way: the web had to serve an unbounded number of clients from a limited number of servers. Statelessness is what makes that possible — any server can answer any request, load balancing is trivial, and no memory is consumed for a visitor who has gone away.

   How state is added on top of a stateless HTTP
   ```
      Since login and shopping carts obviously DO need state, it is
      layered ON TOP of the protocol rather than built into it :

      COOKIES         a small value the browser returns with every
           request. The commonest mechanism.
      SESSIONS        the server stores the data and gives the
           browser only a SESSION ID in a cookie.
      TOKENS          a JWT held by the client and sent in an
           Authorization header - stateless on the SERVER, because
           the token itself carries the identity.
      HIDDEN FORM FIELDS and URL PARAMETERS
      localStorage / sessionStorage
      HTTP KEEP-ALIVE reuses the TCP CONNECTION, but this is
           transport efficiency, NOT application state.
   ```
   ```
      THE DISTINCTION THAT MATTERS

           THE PROTOCOL is stateless.
           THE APPLICATION built on it can be stateful.

      Saying "HTTP is stateful because of cookies" is wrong.
      Cookies are a WORKAROUND that adds state at the application
      layer ; the protocol itself still treats each request as
      independent.
   ```
   - The modern design preference follows the same logic: `REST` deliberately requires each request to be `self-contained`, because that is what allows a service to be scaled by simply adding servers. `Stateful` protocols such as `FTP` and `SSH` are used where a genuine ongoing session is needed — a file transfer or an interactive shell — and they pay for it in scalability.

9. **What is the difference between http session and http cookies?** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 911 (ET: BUET)]*

Answer: Difference between an HTTP session and HTTP cookies

   | Point | Cookie | Session |
   |---|---|---|
   | Stored on | The `client` — the browser | The `server` |
   | What the client holds | The `actual data` | Only a `session ID` |
   | Size limit | About `4 KB` | Limited only by server memory or disk |
   | Lifetime | Until its `Expires` date, or browser close | Until `timeout` or logout — typically 20–30 min |
   | Security | `Weaker` — the user can read and edit it | `Stronger` — the data never leaves the server |
   | Readable by the user | `Yes` | `No` |
   | Survives browser close | Yes, if persistent | `No` — the session cookie is lost |
   | Server load | `None` | `Consumes` memory per user |
   | Scalability | Easy | Harder — needs shared session storage |
   | Data type | `Strings` only | Any object the language supports |
   | Depends on the other? | No | `Yes` — a session normally needs a cookie for its ID |

   How they work together — the point of the question
   ```
      1. The user logs in.
      2. The SERVER creates a SESSION and stores the data in it :
                session["user_id"]  = 5
                session["username"] = "rahim"
                session["role"]     = "admin"
      3. The server generates a random SESSION ID :  abc123xyz
      4. That ID - and ONLY that ID - is sent to the browser IN A
         COOKIE :
                Set-Cookie: PHPSESSID=abc123xyz; HttpOnly; Secure
      5. On every later request the browser returns the cookie :
                Cookie: PHPSESSID=abc123xyz
      6. The server looks up abc123xyz and recovers the user's data.
   ```
   ```mermaid
   sequenceDiagram
       participant B as Browser
       participant S as Server
       B->>S: POST /login (username, password)
       S->>S: verify, create session, store user data
       S-->>B: Set-Cookie: SESSIONID=abc123
       B->>S: GET /dashboard  (Cookie: SESSIONID=abc123)
       S->>S: look up session abc123, recover the user
       S-->>B: personalised page
   ```
   ```
      SO THEY ARE NOT ALTERNATIVES.

      The COOKIE is the TRANSPORT - it carries the session ID
           between browser and server on every request.
      The SESSION is the STORAGE - the actual data kept on the
           server.

      A session without a cookie has no way to identify the client ;
      a cookie without a session can hold only small, non-sensitive
      values.
   ```

   Why sensitive data goes in the session, not the cookie
   ```
      IN A COOKIE (bad)
           Set-Cookie: user_id=5; role=admin

           The user can OPEN THE BROWSER'S DEVELOPER TOOLS and
           change role=admin to anything they like. The next
           request arrives claiming to be an administrator.

      IN A SESSION (correct)
           Set-Cookie: PHPSESSID=abc123xyz

           The ID is a random string that means nothing on its own.
           The role is held on the SERVER, where the user cannot
           reach it. Changing the cookie only produces an invalid
           session ID.
   ```

   The code
   ```php
      // SESSION - PHP
      session_start();
      $_SESSION["user_id"] = 5;         // stored on the SERVER
      echo $_SESSION["user_id"];
      session_destroy();                // logout

      // COOKIE - PHP
      setcookie("theme", "dark", time() + 86400, "/");
      echo $_COOKIE["theme"];           // stored in the BROWSER
   ```

   Which to use for what
   ```
      USE A COOKIE for
           small, non-sensitive preferences - theme, language,
           "remember me", "do not show this banner again"
           anything that must survive the browser closing

      USE A SESSION for
           the logged-in user's identity and role
           anything SENSITIVE
           anything larger than 4 KB
           a shopping cart for a logged-in user
   ```
   - Two security attributes the session cookie must carry: `HttpOnly`, so JavaScript cannot read it — this is what limits the damage of an XSS flaw — and `Secure`, so it is sent only over HTTPS. Adding `SameSite=Strict` is the main defence against `CSRF`.
   - The scalability problem worth naming: because the session lives on `one` server, a load balancer must send that user's requests back to the same machine (`sticky sessions`), or the sessions must be held in shared storage such as `Redis`. The alternative modern approach is a `JWT` — a signed token the client holds, which carries the identity itself, so the server keeps no session at all.

10. **It is a small price of data stored on a user's computer by the web browser while browsing a website. What we are talking about?** *[Sadharan Bima Corporation Programmer/ AP/AME 2020 compact it 1002 (ET: DU)], [BSEC Assistant Director (MIS) 2021 compact it 938 (ET: IBA)]*

Answer: The answer is a `cookie` — more precisely an `HTTP cookie`, also called a web cookie or browser cookie.
    ```
       DEFINITION
       A cookie is a small piece of data - typically under 4 KB -
       that a website sends to the browser, and that the browser
       STORES ON THE USER'S COMPUTER and sends back with every
       subsequent request to that site.
    ```

    How it works
    ```
       1. The server sends it in a response header :
            Set-Cookie: sessionId=abc123; Path=/; HttpOnly; Secure

       2. The BROWSER STORES IT on the user's machine.

       3. On every later request to that site the browser returns it
          AUTOMATICALLY :
            Cookie: sessionId=abc123

       Step 3 needs no code at all - the browser attaches it by
       itself. That automatic behaviour is the point of a cookie,
       and it is also why CSRF attacks are possible.
    ```

    What cookies are used for
    ```
       SESSION MANAGEMENT   the main purpose. HTTP is STATELESS, so
            a cookie carrying a SESSION ID is what lets the server
            recognise the same user across requests - which is what
            keeps a login alive from page to page.
       PERSONALISATION      language , theme , currency , font size
       TRACKING and ANALYTICS   visitor counts , time on site ;
            THIRD-PARTY cookies follow a user across different sites
            for advertising
       SHOPPING CART        for a visitor who has not logged in
       "REMEMBER ME"        a long-lived cookie so the user need not
            log in again
    ```

    Types
    ```
       BY LIFETIME
         SESSION cookie     no expiry date ; deleted when the
              browser closes
         PERSISTENT cookie  has Expires or Max-Age ; survives a
              restart

       BY ORIGIN
         FIRST-PARTY   set by the site being visited
         THIRD-PARTY   set by another domain included in the page -
              an advertiser. Now blocked by default in most browsers
    ```

    The security attributes
    ```
       Set-Cookie: sessionId=abc123; HttpOnly; Secure;
                   SameSite=Strict; Max-Age=3600

       HttpOnly   JavaScript CANNOT read it - this limits the damage
            of an XSS flaw
       Secure     sent only over HTTPS
       SameSite   controls whether it is sent on a request from
            another site - the main CSRF defence
    ```

    The related terms, so the answer is not confused with them
    ```
       COOKIE          up to ~4 KB , SENT TO THE SERVER with every
            request , has an expiry date
       localStorage    5-10 MB , NEVER sent to the server ,
            no expiry
       sessionStorage  5-10 MB , never sent , cleared when the TAB
            closes
       CACHE           stored copies of FILES - images, CSS - not
            key-value data
       SESSION         the data itself, stored ON THE SERVER ; the
            cookie only carries its ID
    ```
    - If the question's wording — "stored on a user's computer by the web browser while browsing a website" — is matched term by term: `stored on the user's computer` and `by the browser` rule out a session, which lives on the server; `small piece of data` rules out the cache, which holds whole files. The answer is a `cookie`.

## Web Services & APIs (SOAP vs REST) (8)

1. **What are SOAP and RESTful APIs in web services? State one main difference between SOAP and REST in terms of how they exchange data.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1426 (ET: E-Zone)]*

Answer: What SOAP is
   - `SOAP (Simple Object Access Protocol)` is a `protocol` for exchanging structured messages between applications. Every message is an `XML envelope` with a strictly defined format, and the service is described by a `WSDL` file.
   ```xml
      <?xml version="1.0"?>
      <soap:Envelope
          xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
          <soap:Header>
              <auth:Credentials>...</auth:Credentials>
          </soap:Header>
          <soap:Body>
              <getBalance>
                  <accountNo>1234567890</accountNo>
              </getBalance>
          </soap:Body>
      </soap:Envelope>
   ```

   What a RESTful API is
   - `REST (Representational State Transfer)` is an `architectural style`, not a protocol. Resources are identified by `URLs`, and the standard `HTTP methods` operate on them. The data is usually `JSON`.
   ```
      GET    /api/accounts/1234567890            read it
      POST   /api/accounts                       create one
      PUT    /api/accounts/1234567890            replace it
      PATCH  /api/accounts/1234567890            update part of it
      DELETE /api/accounts/1234567890            delete it

      Response :
           { "accountNo": "1234567890",
             "balance": 45000,
             "currency": "BDT" }
   ```

   The one main difference in how they exchange data
   ```
      SOAP  must use XML, wrapped in a mandatory SOAP ENVELOPE with
            a Header and a Body, and the format is fixed by the
            WSDL contract.

      REST  can use ANY format - JSON , XML , plain text , HTML -
            and JSON is normal in practice. There is no envelope :
            the data is sent as the plain HTTP body.
   ```
   - Stated in one sentence: `SOAP is XML-only inside a rigid envelope; REST sends plain data — usually JSON — in the HTTP body with no envelope at all`. That is why a REST response is a fraction of the size of the equivalent SOAP response, and why REST is the choice for mobile applications and public web APIs.

   The fuller comparison

   | Point | SOAP | REST |
   |---|---|---|
   | Nature | A `protocol`, with strict rules | An architectural `style` |
   | Data format | `XML` only | `JSON`, XML, text — usually JSON |
   | Envelope | `Required` | None |
   | Message size | `Large` — verbose | `Small` |
   | Transport | HTTP, SMTP, TCP, JMS | `HTTP only` |
   | Contract | `WSDL` — formal and machine-readable | OpenAPI / Swagger, optional |
   | Operations | Named methods — `getBalance()` | `HTTP verbs` on URLs |
   | Caching | Not cacheable | `GET is cacheable` |
   | Security | `WS-Security` — message-level, end to end | HTTPS/TLS, OAuth 2.0 — transport-level |
   | Transactions | `Built in` — WS-AtomicTransaction | Not built in |
   | Error reporting | A `SOAP Fault` element | `HTTP status codes` |
   | Learning curve | `Steep` | Gentle |

   Where each is used
   ```
      SOAP is still used where the requirements are formal :
           BANKING and payment systems - ISO 20022 messaging
           telecom provisioning
           government and enterprise integration
           anywhere ACID TRANSACTIONS, message-level security or a
                guaranteed contract is required

      REST is used almost everywhere else :
           public web APIs , mobile application back ends ,
           microservices , cloud services
   ```
   - The reason banks still run SOAP: `WS-Security` signs and encrypts the `message` rather than the connection, so it stays protected as it passes through intermediaries, and `WS-AtomicTransaction` gives a distributed two-phase commit. REST has no equivalent of either, and for a funds transfer crossing several systems those guarantees are what matter.

2. **What is API?** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*

Answer: What an API is
   - `API` stands for `Application Programming Interface`. It is a defined set of rules through which `one piece of software communicates with another` — stating what requests may be made, in what format, and what will be returned, while `hiding how the work is done`.
   ```
      An API is a CONTRACT. The caller needs to know only WHAT to
      send and WHAT comes back, never HOW it is produced. The
      provider may rewrite the internals completely, and as long as
      the contract holds, nothing breaks.
   ```

   The analogy
   ```
      You (client)  ->  the WAITER (API)  ->  the KITCHEN (server)

      You order from the MENU in the expected form. You never enter
      the kitchen. Change the chef or the recipe - the menu still
      works.
   ```

   Example
   ```
      REQUEST
           GET https://api.weather.com/v1/current?city=Dhaka
           Authorization: Bearer <api-key>

      RESPONSE
           { "city": "Dhaka", "temperature": 32, "humidity": 78 }

      The application shows 32 degrees, knowing nothing about how
      the figure was obtained.
   ```

   Types
   ```
      WEB API      over HTTP , between systems : REST , SOAP ,
                   GraphQL
      LIBRARY API  the functions a library exposes : printf() ,
                   ArrayList
      OS API       system calls : open() , read() , Win32
      DATABASE API JDBC , ODBC
      HARDWARE API a device driver interface
   ```

   Why APIs are used
   ```
      REUSE          use a service someone else built
      ABSTRACTION    the internals may change without breaking the
           caller
      INTEGRATION    systems in different languages, written by
           different companies, work together
      SECURITY       only what the API exposes is reachable ; the
           database is never touched directly
      PARALLEL WORK  front-end and back-end teams agree the
           interface first, then work at the same time
   ```

   Everyday examples
   ```
      Google Maps API      a map inside another application
      bKash / SSLCOMMERZ   taking a payment without handling card
           data
      NID verification     a bank checking an applicant's NID
      SMS gateway          sending an OTP
      Facebook Login       signing in without storing a password
   ```
   - The security point worth stating: an API endpoint is a `public URL`. Anyone can call it directly with `curl`, without your application, so `authentication` (an API key or `OAuth 2.0`), `authorisation`, `input validation` and `rate limiting` all have to be enforced on the `server`.

3. **What is an API?** *[BBA Assistant Programmer 12.07.2025 compact it 1432 (ET: BUET)]*

Answer: What an API is
   - `API` stands for `Application Programming Interface`. It is a defined set of rules through which `one piece of software communicates with another` — stating what requests may be made, in what format, and what will be returned, while `hiding how the work is done`.
   ```
      An API is a CONTRACT. The caller needs to know only WHAT to
      send and WHAT comes back, never HOW it is computed. The
      provider may rewrite the internals entirely and, as long as
      the contract holds, nothing breaks.
   ```

   The restaurant analogy
   ```
      You (the client)  ->  the WAITER (the API)  ->  the KITCHEN
                                                      (the server)

      You order from the MENU in the expected form. You never enter
      the kitchen or learn the recipes. Change the chef or the
      stove - the menu still works.
   ```

   Example
   ```
      REQUEST
           GET https://api.exchangerate.com/v1/latest?base=USD
           Authorization: Bearer <api-key>

      RESPONSE
           {
             "base": "USD",
             "date": "2026-09-04",
             "rates": { "BDT": 121.50, "EUR": 0.92 }
           }

      The application displays the rate. It has no idea which
      markets were consulted or how the figure was derived.
   ```

   Types of API
   ```
      WEB API      over HTTP , between systems : REST , SOAP ,
                   GraphQL
      LIBRARY API  the functions a library exposes : printf() ,
                   ArrayList
      OS API       system calls : open() , read() , Win32
      DATABASE API JDBC , ODBC
      HARDWARE API a device driver interface
   ```
   ```
      BY ACCESS
        PUBLIC / OPEN    anyone may use it - Google Maps
        PARTNER          only for approved business partners
        PRIVATE          internal to one organisation
        COMPOSITE        one call that combines several services
   ```

   Why APIs are used
   ```
      REUSE          use a service someone else built
      ABSTRACTION    the internals can change without breaking the
           caller
      INTEGRATION    systems in different languages, by different
           companies, can work together
      SECURITY       only what the API exposes is reachable ; the
           database is never touched directly
      PARALLEL WORK  front-end and back-end teams agree the
           interface first, then work simultaneously
   ```

   Everyday examples
   ```
      Google Maps API        a map inside another application
      bKash / SSLCOMMERZ     taking a payment without handling card
           data
      NID verification API   a bank checking an applicant's NID
      SMS gateway API        sending an OTP
      Facebook Login         signing in without storing a password
   ```
   - The security point that must be stated: an API endpoint is a `public URL`. Anyone can call it directly with `curl`, without your application. So `authentication` (an API key or `OAuth 2.0`), `authorisation`, `input validation` and `rate limiting` all have to be enforced `on the server` — the fact that only your own app is meant to call it proves nothing.

4. **Write difference between REST API and SOAP API.** *[BKSP Assistant Programmer 13.07.2024 compact it 1460 (ET: N/A)]*

Answer: Difference between a REST API and a SOAP API

   | Point | SOAP API | REST API |
   |---|---|---|
   | Full form | `Simple Object Access Protocol` | `Representational State Transfer` |
   | Nature | A `protocol` with strict rules | An architectural `style` |
   | Data format | `XML` only | `JSON`, XML, text — usually JSON |
   | Envelope | `Required` — Header and Body | `None` |
   | Message size | `Large` — verbose | `Small` |
   | Transport | HTTP, SMTP, TCP, JMS | `HTTP only` |
   | Contract | `WSDL` — formal, machine-readable | OpenAPI / Swagger, optional |
   | Operations | Named methods — `getBalance()` | `HTTP verbs` on resource URLs |
   | Caching | `Not cacheable` | `GET is cacheable` |
   | Security | `WS-Security` — message-level, end to end | HTTPS/TLS, OAuth 2.0 — transport-level |
   | Transactions | `Built in` — WS-AtomicTransaction | Not built in |
   | Errors reported by | A `SOAP Fault` element | `HTTP status codes` |
   | Statelessness | Can be stateful | `Stateless` by design |
   | Performance | Slower — XML parsing | `Faster` |
   | Learning curve | `Steep` | Gentle |
   | Browser-friendly | No | `Yes` — callable from JavaScript |

   SOAP — a request
   ```xml
      POST /BankService HTTP/1.1
      Content-Type: text/xml

      <?xml version="1.0"?>
      <soap:Envelope
          xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
          <soap:Header>
              <auth:Credentials>...</auth:Credentials>
          </soap:Header>
          <soap:Body>
              <getBalance>
                  <accountNo>1234567890</accountNo>
              </getBalance>
          </soap:Body>
      </soap:Envelope>
   ```

   REST — the same operation
   ```
      GET /api/accounts/1234567890 HTTP/1.1
      Authorization: Bearer <token>

      RESPONSE
      { "accountNo": "1234567890", "balance": 45000,
        "currency": "BDT" }
   ```
   ```
      THE FULL SET OF REST OPERATIONS

      GET    /api/accounts          list them
      GET    /api/accounts/123      read one
      POST   /api/accounts          create one
      PUT    /api/accounts/123      replace it
      PATCH  /api/accounts/123      update part of it
      DELETE /api/accounts/123      delete it

      The URL names the RESOURCE ; the HTTP VERB names the action.
      A URL such as /api/getAccount?id=123 is a common mistake -
      it puts the verb in the URL, which is not REST.
   ```

   Where each is used
   ```
      SOAP is still used where the requirements are formal :
           BANKING and payment systems - ISO 20022 messaging
           telecom provisioning
           government and enterprise integration
           anywhere ACID TRANSACTIONS, message-level security or a
                guaranteed machine-readable contract is required

      REST is used almost everywhere else :
           public web APIs , mobile back ends , microservices ,
           cloud services , anything called from a browser
   ```
   - Why banks still run SOAP: `WS-Security` signs and encrypts the `message` itself rather than the connection, so it remains protected while passing through intermediaries; and `WS-AtomicTransaction` provides a distributed two-phase commit. REST has no equivalent of either, and for a funds transfer crossing several systems those guarantees are the whole point.
   - The third option worth naming: `GraphQL`, where the client specifies exactly which fields it wants in a single request. It removes REST's problems of `over-fetching` (receiving fields you do not need) and `under-fetching` (having to make several calls), at the cost of losing simple HTTP caching.

5. **What is API? Explain with example.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*

Answer: What an API is
   - `API` stands for `Application Programming Interface`. It is a defined set of rules through which `one piece of software talks to another` — stating what requests may be made, in what format, and what will be returned, while `hiding how the work is done`.
   ```
      An API is a CONTRACT. The caller needs to know only WHAT to
      send and WHAT comes back, never HOW it is produced. The
      provider may rewrite the internals completely and, as long as
      the contract holds, nothing breaks.
   ```

   The analogy
   ```
      A RESTAURANT

           You (client) -> the WAITER (API) -> the KITCHEN (server)

      You order from the MENU in the expected form. You never enter
      the kitchen or learn the recipes. Change the chef, the stove
      or the recipe - the menu still works.
   ```

   Example 1 — a payment gateway API, the case a bank exam wants
   ```
      An e-commerce site must take payment by bKash. It does NOT
      build a payment system ; it CALLS the bKash API.

      REQUEST
           POST https://api.bkash.com/v1/payment/create
           Authorization: Bearer <token>
           Content-Type: application/json

           {
             "amount": 1500,
             "currency": "BDT",
             "merchantInvoiceNumber": "INV-2026-0912"
           }

      RESPONSE
           {
             "paymentID": "TR0011abc456",
             "bkashURL": "https://pay.bkash.com/TR0011abc456",
             "status": "Initiated"
           }

      The site redirects the customer to bkashURL. The customer
      enters their PIN ON BKASH'S OWN PAGE, so the shop never sees
      it. When payment completes, bKash calls the shop back.

      WHAT THE API GAVE
        the shop handles NO PIN and NO card data - so it needs no
             PCI-DSS certification for them
        bKash can change its internal system freely
        the shop wrote no payment logic at all
   ```

   Example 2 — a library API
   ```java
      // Java Collections API
      List<String> names = new ArrayList<>();
      names.add("Rahim");            // an API method
      names.sort(null);              // another
      int n = names.size();

      You call add() without knowing whether an ArrayList uses an
      array, how it grows, or how the sort is implemented. The
      METHOD SIGNATURES are the API.
   ```

   Example 3 — a weather API
   ```
      REQUEST   GET https://api.weather.com/v1/current?city=Dhaka

      RESPONSE  { "city": "Dhaka", "temperature": 32,
                  "humidity": 78 }

      The application shows 32 degrees. It has no idea where the
      satellites are or how the forecast is computed.
   ```

   Types of API
   ```
      WEB API      over HTTP : REST , SOAP , GraphQL
      LIBRARY API  the functions a library exposes
      OS API       system calls : open() , read() , Win32
      DATABASE API JDBC , ODBC
      HARDWARE API a device driver interface
   ```

   Why APIs are used
   ```
      REUSE          use a service someone else built
      ABSTRACTION    the internals may change without breaking the
           caller
      INTEGRATION    different languages, different companies, one
           working system
      SECURITY       only what the API exposes is reachable
      PARALLEL WORK  front-end and back-end teams agree the
           interface, then work simultaneously
   ```
   - The security point: an API endpoint is a `public URL`. Anyone can call it directly with `curl`, without your application, so `authentication` (an API key or `OAuth 2.0`), `authorisation`, `input validation` and `rate limiting` must all be enforced on the `server`.

6. **What is the two prime advantages of RESTful API?** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 756 (ET: N/A)]*

Answer: The two prime advantages of a RESTful API are `statelessness`, which gives scalability, and its `uniform interface over standard HTTP`, which gives simplicity and interoperability.

   1. Statelessness — and therefore scalability
   ```
      Every request carries EVERYTHING the server needs. The server
      stores NO session for the client and forgets it immediately
      after answering.

      WHY THIS IS THE PRIME ADVANTAGE

           Request 1 -> may be answered by SERVER A
           Request 2 -> may be answered by SERVER B
           Request 3 -> may be answered by SERVER C

           None of them needs to know what the others did.

      CONSEQUENCES
        a LOAD BALANCER may send any request to any server -
             no sticky sessions, no shared session store
        capacity is increased by simply ADDING SERVERS -
             HORIZONTAL SCALING
        a server crash loses NOTHING, because it held nothing
        responses to GET are CACHEABLE, so a CDN or a proxy can
             answer without touching the server at all
        no memory is consumed for a client who has gone away

      This is why REST underpins large-scale services. A stateful
      design ties each user to one machine, and that is what limits
      how far it can grow.
   ```

   2. A uniform interface over standard HTTP — simplicity and interoperability
   ```
      REST uses what the web already has : URLs to name resources,
      and the standard HTTP VERBS to act on them.

           GET    /api/accounts/123     read
           POST   /api/accounts         create
           PUT    /api/accounts/123     replace
           PATCH  /api/accounts/123     update part
           DELETE /api/accounts/123     delete

      Plus standard HTTP STATUS CODES for the outcome :
           200 OK , 201 Created , 400 Bad Request ,
           401 Unauthorized , 404 Not Found , 500 Server Error

      CONSEQUENCES
        ANY client in ANY language can call it - a browser, a
             mobile app, a Python script, curl
        no special library and no WSDL contract is needed
        it is testable from a browser address bar
        JSON keeps the payload SMALL, which matters on a mobile
             network
        it uses HTTP CACHING, PROXIES and COMPRESSION for free,
             because it is ordinary HTTP
        a new developer can learn the whole API from a few example
             URLs
   ```

   The other advantages, in brief
   ```
      LIGHTWEIGHT      JSON instead of a verbose XML envelope, so
           a REST response is a fraction of the SOAP equivalent
      LANGUAGE and PLATFORM INDEPENDENT
      SEPARATION of CLIENT and SERVER - either may be rewritten
           independently
      LAYERED - a gateway, a cache or a load balancer may sit
           between client and server without either knowing
      EASY TO EVOLVE - a new resource is a new URL
   ```

   What REST does not provide, and should be mentioned
   ```
      NO BUILT-IN TRANSACTIONS   there is no equivalent of
           WS-AtomicTransaction, so a multi-step operation
           spanning services must be handled by the application
      TRANSPORT-LEVEL SECURITY ONLY   HTTPS protects the
           CONNECTION ; SOAP's WS-Security protects the MESSAGE,
           so it stays protected through intermediaries
      NO FORMAL CONTRACT by default - OpenAPI or Swagger has to be
           added
      OVER-FETCHING and UNDER-FETCHING - a fixed response may
           return more fields than needed, or force several calls.
           GraphQL exists to solve exactly this
   ```
   - If only `two` are to be named, `statelessness` and the `uniform HTTP interface` are the right answer, because every other benefit follows from them: caching, horizontal scaling and crash resilience all come from statelessness, and language independence, testability and small payloads all come from using plain HTTP and JSON.

7. **What is API?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 865 (ET: BUET)]*

Answer: What an API is
   - `API` stands for `Application Programming Interface`. It is a defined set of rules through which `one piece of software communicates with another` — stating what requests may be made, in what format, and what will be returned, while `hiding how the work is done`.
   ```
      An API is a CONTRACT. The caller needs to know only WHAT to
      send and WHAT comes back, never HOW it is produced. The
      provider may rewrite the internals completely, and as long as
      the contract holds, nothing breaks.
   ```

   The analogy
   ```
      You (client)  ->  the WAITER (API)  ->  the KITCHEN (server)

      You order from the MENU in the expected form. You never enter
      the kitchen. Change the chef or the recipe - the menu still
      works.
   ```

   Example
   ```
      REQUEST
           GET https://api.weather.com/v1/current?city=Dhaka
           Authorization: Bearer <api-key>

      RESPONSE
           { "city": "Dhaka", "temperature": 32, "humidity": 78 }

      The application shows 32 degrees, knowing nothing about how
      the figure was obtained.
   ```

   Types
   ```
      WEB API      over HTTP , between systems : REST , SOAP ,
                   GraphQL
      LIBRARY API  the functions a library exposes : printf() ,
                   ArrayList
      OS API       system calls : open() , read() , Win32
      DATABASE API JDBC , ODBC
      HARDWARE API a device driver interface
   ```

   Why APIs are used
   ```
      REUSE          use a service someone else built
      ABSTRACTION    the internals may change without breaking the
           caller
      INTEGRATION    systems in different languages, written by
           different companies, work together
      SECURITY       only what the API exposes is reachable ; the
           database is never touched directly
      PARALLEL WORK  front-end and back-end teams agree the
           interface first, then work at the same time
   ```

   Everyday examples
   ```
      Google Maps API      a map inside another application
      bKash / SSLCOMMERZ   taking a payment without handling card
           data
      NID verification     a bank checking an applicant's NID
      SMS gateway          sending an OTP
      Facebook Login       signing in without storing a password
   ```
   - The security point worth stating: an API endpoint is a `public URL`. Anyone can call it directly with `curl`, without your application, so `authentication` (an API key or `OAuth 2.0`), `authorisation`, `input validation` and `rate limiting` all have to be enforced on the `server`.

8. **What is SOAP?** *[Bangladesh Bank Assistant Programmer 2019 compact it 1157 (ET: DU)]*

Answer: What SOAP is
   - `SOAP` stands for `Simple Object Access Protocol`. It is a `W3C standard protocol` for exchanging structured information between applications. Every message is an `XML document` wrapped in a mandatory `envelope`, and the service is described by a `WSDL` file.
   ```
      SOAP is a PROTOCOL, not a style. Its message format, error
      format and processing rules are all fixed by the standard -
      which is exactly why it is used where a formal, verifiable
      contract is required.
   ```

   The message structure
   ```xml
      <?xml version="1.0"?>
      <soap:Envelope
          xmlns:soap="http://www.w3.org/2003/05/soap-envelope">

          <soap:Header>
              <auth:Credentials>
                  <auth:Username>bankuser</auth:Username>
                  <auth:Token>xyz789</auth:Token>
              </auth:Credentials>
          </soap:Header>

          <soap:Body>
              <getBalance xmlns="http://bank.example.com/">
                  <accountNo>1234567890</accountNo>
              </getBalance>
          </soap:Body>

      </soap:Envelope>
   ```
   ```
      THE FOUR PARTS

      ENVELOPE   REQUIRED. The root element. It identifies the
           document as a SOAP message.
      HEADER     OPTIONAL. Metadata - authentication credentials,
           transaction IDs, routing information. This is where
           WS-Security places its signatures.
      BODY       REQUIRED. The actual request or response data.
      FAULT      OPTIONAL, inside the Body. The standard error
           format :
                <soap:Fault>
                    <faultcode>soap:Client</faultcode>
                    <faultstring>Invalid account number</faultstring>
                </soap:Fault>
   ```

   The supporting standards
   ```
      WSDL  Web Services Description Language
           An XML file describing every operation, its parameters
           and its return types. A client STUB can be GENERATED
           automatically from it, in any language. This is SOAP's
           real strength - a machine-readable contract.

      UDDI  Universal Description, Discovery and Integration -
           a directory of services. Largely unused now.

      WS-* the extension family :
           WS-Security          message-level signing and
                encryption
           WS-AtomicTransaction distributed two-phase commit
           WS-ReliableMessaging guaranteed delivery
           WS-Addressing        routing information
   ```

   Features
   ```
      PLATFORM and LANGUAGE INDEPENDENT - everything is XML
      TRANSPORT INDEPENDENT - it can run over HTTP, SMTP, TCP or
           JMS, unlike REST which is HTTP only
      EXTENSIBLE through the WS-* standards
      STRONGLY TYPED - the WSDL fixes every type
      BUILT-IN ERROR HANDLING through SOAP Fault
      MESSAGE-LEVEL SECURITY, not merely transport-level
   ```

   Advantages and disadvantages
   ```
      ADVANTAGES
        a FORMAL, machine-readable CONTRACT (WSDL) , so client code
             can be generated
        WS-SECURITY signs and encrypts the MESSAGE itself, so it
             stays protected through intermediaries - HTTPS only
             protects the connection
        BUILT-IN TRANSACTIONS - a genuine two-phase commit across
             services
        RELIABLE MESSAGING with guaranteed delivery
        works over transports other than HTTP

      DISADVANTAGES
        VERBOSE - the XML envelope makes messages several times
             larger than the equivalent JSON
        SLOWER - XML must be parsed
        COMPLEX - a steep learning curve
        NOT CACHEABLE
        awkward to call from a browser or a mobile app
   ```

   Where it is still used
   ```
      BANKING and payment systems - ISO 20022 messaging
      telecom provisioning
      government and large enterprise integration
      anywhere ACID TRANSACTIONS, message-level security or a
           guaranteed contract is mandatory
   ```
   - Why SOAP survives despite REST: for a funds transfer crossing several institutions, `WS-Security` and `WS-AtomicTransaction` provide guarantees REST has no equivalent of. Where those guarantees are not needed — a public web API, a mobile back end, a microservice — `REST` with JSON is smaller, faster and far simpler, which is why it has taken over everywhere else.

## Full Stack & Backend Web Development (7)

1. **Write appropriate program client and database using any language and a login page using ID and password. [Approximate Web page login code]** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 320 (ET: N/A)]*

Answer: A login page with a client side, a server side and a database. `PHP` and `MySQL` are used, and the same structure applies in any language.

   1. The database
   ```sql
      CREATE DATABASE bankdb;
      USE bankdb;

      CREATE TABLE users (
          id            INT AUTO_INCREMENT PRIMARY KEY,
          username      VARCHAR(50)  NOT NULL UNIQUE,
          password_hash VARCHAR(255) NOT NULL,
          full_name     VARCHAR(100),
          is_active     TINYINT(1) DEFAULT 1,
          failed_count  INT DEFAULT 0,
          created_at    TIMESTAMP DEFAULT CURRENT_TIMESTAMP
      );

      -- the password is stored as a HASH, never in plain text
      INSERT INTO users (username, password_hash, full_name)
      VALUES ('rahim',
              '$2y$10$abcdefghijklmnopqrstuv...',   -- password_hash()
              'Rahim Uddin');
   ```
   ```
      THE COLUMN IS password_hash , NOT password.
      A plain-text password column is the single worst defect a
      login system can have - one database leak exposes every
      user's password, including the ones they reuse elsewhere.
   ```

   2. The client — `login.html`
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <title>Login</title>
       <style>
           body  { font-family: Arial, sans-serif; }
           .box  { width: 300px; margin: 80px auto;
                   border: 1px solid #ccc; border-radius: 8px;
                   padding: 25px; }
           input { width: 100%; padding: 8px; margin-bottom: 12px; }
           button{ width: 100%; padding: 9px; }
           .error{ color: red; font-size: 13px; }
       </style>
   </head>
   <body>

   <div class="box">
       <h3>Bank Login</h3>

       <form id="loginForm" action="login.php" method="post">
           <label for="username">Username</label>
           <input type="text" id="username" name="username" required>

           <label for="password">Password</label>
           <input type="password" id="password" name="password"
                  required>

           <button type="submit">Login</button>
           <p id="msg" class="error"></p>
       </form>
   </div>

   <script>
       document.getElementById("loginForm")
           .addEventListener("submit", function (e) {

           var u = document.getElementById("username").value.trim();
           var p = document.getElementById("password").value;

           if (u === "" || p === "") {
               e.preventDefault();
               document.getElementById("msg").textContent =
                   "Both fields are required";
               return;
           }
           if (p.length < 8) {
               e.preventDefault();
               document.getElementById("msg").textContent =
                   "Password must be at least 8 characters";
           }
       });
   </script>

   </body>
   </html>
   ```
   - Note `method="post"`: with `get` the password would appear in the address bar, in the browser history and in the server log.

   3. The server — `login.php`
   ```php
   <?php
   session_start();

   $host = "localhost"; $db = "bankdb";
   $user = "dbuser";    $pass = "dbpass";

   // PDO with exceptions turned on
   try {
       $pdo = new PDO("mysql:host=$host;dbname=$db;charset=utf8mb4",
                      $user, $pass,
                      [PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
                       PDO::ATTR_EMULATE_PREPARES => false]);
   } catch (PDOException $e) {
       die("Database connection failed");   // never echo $e here
   }

   $username = trim($_POST["username"] ?? "");
   $password = $_POST["password"] ?? "";

   if ($username === "" || $password === "") {
       header("Location: login.html?error=empty");
       exit;
   }

   // PREPARED STATEMENT - this is what stops SQL injection
   $stmt = $pdo->prepare(
       "SELECT id, username, password_hash, full_name, is_active
        FROM users WHERE username = :u LIMIT 1");
   $stmt->execute([":u" => $username]);
   $row = $stmt->fetch(PDO::FETCH_ASSOC);

   // ONE generic message for BOTH a wrong username and a wrong
   // password - saying which would reveal who has an account
   if (!$row || !password_verify($password, $row["password_hash"])) {
       if ($row) {
           $pdo->prepare("UPDATE users SET failed_count =
                          failed_count + 1 WHERE id = ?")
               ->execute([$row["id"]]);
       }
       header("Location: login.html?error=invalid");
       exit;
   }

   if (!$row["is_active"]) {
       header("Location: login.html?error=inactive");
       exit;
   }

   // SUCCESS
   session_regenerate_id(true);        // prevents session fixation
   $_SESSION["user_id"]  = $row["id"];
   $_SESSION["username"] = $row["username"];
   $_SESSION["name"]     = $row["full_name"];

   $pdo->prepare("UPDATE users SET failed_count = 0 WHERE id = ?")
       ->execute([$row["id"]]);

   header("Location: dashboard.php");   // POST-redirect-GET
   exit;
   ?>
   ```

   4. The protected page — `dashboard.php`
   ```php
   <?php
   session_start();

   // EVERY protected page must check this
   if (!isset($_SESSION["user_id"])) {
       header("Location: login.html");
       exit;
   }
   ?>
   <!DOCTYPE html>
   <html><head><meta charset="UTF-8"><title>Dashboard</title></head>
   <body>
       <h2>Welcome,
           <?= htmlspecialchars($_SESSION["name"]) ?>
       </h2>
       <a href="logout.php">Logout</a>
   </body>
   </html>
   ```

   5. Logout — `logout.php`
   ```php
   <?php
   session_start();
   $_SESSION = [];
   session_destroy();
   header("Location: login.html");
   exit;
   ?>
   ```

   The security points, which is what this question really tests
   ```
      1. HASH THE PASSWORD, never store it
           password_hash($p, PASSWORD_DEFAULT)   to store
           password_verify($p, $hash)            to check
         bcrypt is DELIBERATELY SLOW, which is what makes brute
         force impractical. MD5 and SHA1 are UNSUITABLE - they are
         fast, which helps the attacker.

      2. PREPARED STATEMENTS, never string concatenation
           WRONG : "SELECT * FROM users WHERE username = '$u'"
                   username  ' OR '1'='1  logs in as anyone
           RIGHT : prepare(... WHERE username = :u)

      3. ONE GENERIC ERROR MESSAGE
           "Invalid username or password" for BOTH cases.
           "No such user" reveals which accounts exist - USER
           ENUMERATION.

      4. session_regenerate_id(true) on login
           Without it, a session ID an attacker planted before the
           login remains valid afterwards - SESSION FIXATION.

      5. htmlspecialchars() on ALL output
           Prevents XSS if a username contains <script>.

      6. HTTPS ONLY
           POST hides the password from the address bar but NOT
           from the network. Only TLS encrypts it.

      7. LOCK THE ACCOUNT after repeated failures, and RATE LIMIT
         by IP address.

      8. NEVER echo the database error to the user - it reveals the
         schema.

      9. VALIDATE ON THE SERVER. The JavaScript check is for the
         user's convenience only ; anyone can disable it.
   ```
   - The complete flow: `login.html` → POST → `login.php` verifies against the database → creates a `session` → redirects to `dashboard.php`, which checks the session on every request. The `POST-redirect-GET` pattern in step 3 is what stops the browser re-submitting the login when the user presses refresh.

2. **(খ) Client-side scripting এর তুলনায় Server-side scripting এর সুবিধাগুলো কী কী?** *[Software Assistant Programmer 13.10.2022 compact it 709 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) The distinction
   ```
      CLIENT-SIDE SCRIPTING   runs in the BROWSER , on the user's
           machine.  JavaScript.
      SERVER-SIDE SCRIPTING   runs on the SERVER , before the page
           is sent.  PHP , Python , Java , Node.js , ASP.NET.
   ```

   Advantages of server-side scripting over client-side

   1. Security — the decisive advantage
   ```
      The CODE IS NEVER SENT to the browser. The user receives only
      the OUTPUT - the finished HTML.

           CLIENT-SIDE : press Ctrl+U and the entire script is
                visible. Any logic, any constant, any threshold is
                open to inspection - and to modification.
           SERVER-SIDE : the source stays on the server. The user
                sees the result and nothing else.

      THE CONSEQUENCE : all BUSINESS RULES, PASSWORD CHECKING,
      PRICE CALCULATION and AUTHORISATION must be on the server.
      A discount rule enforced only in JavaScript can be edited by
      the user in the developer console.
   ```

   2. Database access
   - Only server-side code can connect to the database. Credentials placed in client-side code would be visible to everyone. Every query, insert and update therefore happens on the server.

   3. It cannot be disabled or bypassed
   ```
      A user can disable JavaScript, edit it in the browser
      console, or send an HTTP request directly with curl -
      skipping the page entirely.

      SERVER-SIDE CODE ALWAYS RUNS. This is why VALIDATION MUST BE
      REPEATED ON THE SERVER : the client-side check is for the
      user's convenience, and the server-side check is the one
      that actually protects the application.
   ```

   4. Browser independence
   - The server produces plain HTML, so the result is identical in every browser. Client-side scripts must contend with differences between browsers and versions, and with users who have scripting turned off.

   5. It can access server resources
   - The file system, other servers, internal APIs, email and SMS gateways, and payment gateways. A browser is confined by the `same-origin policy` and the sandbox.

   6. Session management and authentication
   - Sessions are stored on the server, where the user cannot read or alter them. A role held in client-side storage could simply be changed to `admin`.

   7. Heavy processing
   - Report generation, image processing and large calculations run on server hardware rather than on whatever device the visitor happens to hold. It also does not matter whether that device is a slow phone.

   8. Search engine visibility
   - Content generated on the server is present in the HTML the crawler receives. Content inserted later by JavaScript may not be indexed.

   9. Centralised change
   - Fixing the code on the server fixes it for every user at once. Client-side code is already cached in thousands of browsers.

   Where client-side scripting is better
   ```
      IMMEDIATE RESPONSE     no network round trip, so validation
           and interaction feel instant
      LESS SERVER LOAD       the work is done on the user's machine
      LESS BANDWIDTH         no request needed for every small
           interaction
      RICH INTERACTIVITY     animation, drag and drop, canvas,
           instant filtering
      WORKS OFFLINE          with service workers and localStorage
   ```

   The correct division
   ```
      +---------------------------+---------------------------+
      | CLIENT-SIDE (JavaScript)  | SERVER-SIDE (PHP / Java)  |
      +---------------------------+---------------------------+
      | quick input validation    | AUTHENTICATION            |
      |   for convenience         | AUTHORISATION             |
      | UI interaction, animation | ALL business rules        |
      | showing and hiding fields | DATABASE access           |
      | sorting a visible table   | PRICE and total           |
      | fetching data by AJAX     |   calculation             |
      | instant feedback          | SESSION management       |
      |                           | FINAL validation          |
      +---------------------------+---------------------------+

      THE RULE : validate on the client for SPEED, and on the
      server for CORRECTNESS AND SECURITY. Never only on the
      client.
   ```
   - The one-line summary: `server-side scripting is authoritative, client-side scripting is advisory`. A real application uses both — the client for responsiveness, the server for every decision that matters.

3. **(খ) PHP কি? Web Development এ Java Script এর প্রয়োজনীয়তা সম্পর্কে বিবরণ দিন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 771 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) What PHP is
   - `PHP` stands for `PHP: Hypertext Preprocessor` — a recursive acronym; the original name was Personal Home Page. It is a `server-side scripting language` designed for web development. The code runs on the `server`, and only its `output` — plain HTML — is sent to the browser.
   ```php
      <!DOCTYPE html>
      <html>
      <body>
          <h1>Welcome</h1>
          <?php
              $name = "Rahim";
              echo "<p>Hello, " . htmlspecialchars($name) . "</p>";
          ?>
      </body>
      </html>
   ```
   ```
      FEATURES
        SERVER-SIDE - the source is never sent to the browser
        OPEN SOURCE and free
        CROSS-PLATFORM - Windows, Linux, macOS
        EMBEDDED IN HTML , between <?php and ?>
        supports MySQL, PostgreSQL, Oracle and more
        handles forms, sessions, cookies, file uploads and email
        runs about 75 per cent of websites, including WordPress,
             Facebook's original codebase, and Wikipedia
        files carry the .php extension

      THE LAMP / LEMP STACK
           Linux + Apache (or Nginx) + MySQL + PHP
   ```

   The necessity of JavaScript in web development

   1. It is the only language the browser runs
   - Every browser has a JavaScript engine and no other. Whatever the server is written in — PHP, Java, Python — anything happening `in the browser` must be JavaScript. That alone makes it unavoidable.

   2. Immediate interaction with no round trip
   ```
      Form validation, a dropdown menu, a tab switch, a modal
      dialogue, an image slider - all instant, because nothing
      crosses the network.

      Without JavaScript, checking whether an email field is
      valid would need a full page reload.
   ```

   3. DOM manipulation — changing the page after it loads
   ```javascript
      document.getElementById("total").textContent = "1500 Tk";
      document.querySelector(".card").classList.add("selected");
   ```
   - PHP produces the page `once`; after that only JavaScript can change it. Every cart total that updates without a reload works this way.

   4. AJAX — talking to the server without reloading
   ```javascript
      const res  = await fetch("getPrice.php?id=5");
      const data = await res.json();
   ```
   - This is what makes live search suggestions, infinite scroll, auto-save, chat and dependent dropdowns possible. It is `PHP and JavaScript together`: JavaScript asks, PHP answers with data.

   5. Client-side validation, for the user's convenience
   - Mistakes are caught before the form is submitted, which saves the user a round trip and saves the server a request. The same checks must still be repeated in PHP, because JavaScript can be disabled.

   6. Modern front-end applications
   - `React`, `Angular` and `Vue` are all JavaScript, and single-page applications exist only because of it.

   7. It now runs on the server too
   - `Node.js` allows JavaScript on the server, so one language can serve both ends of the application.

   8. Facilities PHP cannot reach
   - Geolocation, the camera and microphone, `localStorage`, `canvas` for graphics, drag and drop, notifications, `WebSocket` for real-time updates, and offline working through service workers. All of these are browser capabilities, and only JavaScript can use them.

   How the two work together
   ```
      PHP  (server)                 JavaScript (browser)
      ---------------------------   ---------------------------
      database access               DOM manipulation
      authentication, sessions      instant validation
      business rules                animation and interaction
      generating the HTML           AJAX requests
      file handling, email          browser APIs - camera, GPS,
      payment gateway calls              storage
      FINAL validation              first-line validation
   ```
   ```mermaid
   flowchart LR
       A[Browser: JavaScript] -->|AJAX request| B[Server: PHP]
       B --> C[(MySQL)]
       C --> B
       B -->|JSON| A
       A -->|update the DOM| A
   ```
   - The division to state clearly: `PHP is authoritative, JavaScript is advisory`. Every decision that matters — who is logged in, what price is charged, what may be deleted — is made in PHP, because the user can edit or disable JavaScript at will. JavaScript's job is to make the application `responsive`, not to make it `correct`.

4. **(b) What are the resources you need to access a web enabled application?** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 796 (ET: N/A)]*

Answer: The resources needed to access a web-enabled application, grouped by layer.

   1. Client-side resources
   ```
      A DEVICE          a computer, laptop, tablet or smartphone
      A WEB BROWSER     Chrome , Firefox , Edge , Safari - the
           CLIENT SOFTWARE. It must support the HTML, CSS and
           JavaScript the application uses.
      AN OPERATING SYSTEM to run the browser
      AN INTERNET CONNECTION with adequate bandwidth
      INPUT and DISPLAY hardware - keyboard, mouse or touch screen
      Sometimes a PLUG-IN or a specific browser version, and for a
           banking application a supported TLS version
   ```

   2. Network resources
   ```
      AN INTERNET SERVICE PROVIDER (ISP)
      A DNS SERVICE       to turn www.example.com into an IP
           address. Without DNS the site is reachable only by IP.
      TCP/IP              the protocol stack the whole exchange
           rests on
      BANDWIDTH           enough for the page and its images
      ROUTERS , SWITCHES , a FIREWALL along the path
      An SSL/TLS certificate for HTTPS, so the connection is
           encrypted
   ```

   3. Server-side resources
   ```
      A WEB SERVER        Apache , Nginx , IIS - receives the HTTP
           request and returns the response
      AN APPLICATION SERVER or RUNTIME  PHP , Tomcat for Java ,
           Node.js , .NET - runs the business logic for a DYNAMIC
           application
      A DATABASE SERVER   MySQL , PostgreSQL , Oracle , SQL Server
      AN OPERATING SYSTEM Linux or Windows Server
      HARDWARE            CPU, RAM, storage - or a cloud instance
      A DOMAIN NAME       registered and renewed
      HOSTING             shared, VPS, dedicated or cloud
      POWER and COOLING   UPS and generator ; in Bangladesh this is
           not optional
   ```

   4. Application resources
   ```
      THE APPLICATION CODE itself
      USER CREDENTIALS     a username and password, and for a bank
           an OTP or a hardware token
      AUTHORISATION        the account must have the ROLE
           permitting the action
      THE URL              the address of the application
      Any required LICENCE for the software
   ```

   5. Supporting resources
   ```
      BACKUP and DISASTER RECOVERY - and a TESTED restore
      MONITORING and LOGGING
      TECHNICAL SUPPORT and an SLA
      SECURITY - firewall, intrusion detection, patch management
      DOCUMENTATION and user TRAINING
   ```

   The path a request actually takes, showing where each resource is used
   ```mermaid
   flowchart LR
       A[Device + browser] -->|internet| B[DNS]
       B --> C[Web server: Apache/Nginx]
       C --> D[Application runtime: PHP/Java]
       D --> E[(Database server)]
       E --> D
       D --> C
       C -->|HTTP response| A
   ```
   ```
      1. The USER has a device, a browser and a connection.
      2. DNS resolves the domain to an IP address.
      3. TCP - and TLS for HTTPS - opens the connection.
      4. The WEB SERVER receives the HTTP request.
      5. The APPLICATION RUNTIME executes the business logic.
      6. The DATABASE SERVER supplies the data.
      7. The response returns as HTML, which the browser renders.

      REMOVE ANY ONE of these and the application is unreachable -
      which is the point the question is testing.
   ```

   The minimum, if a short answer is wanted
   ```
      1. a DEVICE with a WEB BROWSER
      2. an INTERNET CONNECTION
      3. the URL or domain name  (and DNS to resolve it)
      4. valid USER CREDENTIALS , if the application requires login
      5. on the other side : a WEB SERVER , an APPLICATION SERVER
         and a DATABASE SERVER, all running
   ```
   - The single point that distinguishes a web-enabled application from a desktop one: `nothing is installed on the client`. The browser is the only client software required, which is why the same application serves Windows, Linux, macOS, Android and iOS without any per-platform work — and it is why the `browser` and the `connection` are the only resources the user has to supply.

5. **Apache কোন ধরনের Server এক কথায় লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 866 (ET: BUET)]*

Answer: `Apache` is a `web server`.
   ```
      Its full name is the APACHE HTTP SERVER, often written as
      "Apache httpd".
   ```

   What that means
   ```
      A WEB SERVER receives an HTTP request and returns an HTTP
      response - a web page, an image, a stylesheet, or the output
      of a script.

           browser --HTTP request--> APACHE --HTTP response-->
                                         |
                                         +--> passes .php files to
                                              the PHP interpreter
   ```

   Key facts
   ```
      TYPE          Web server (HTTP server)
      DEVELOPED BY  the Apache Software Foundation
      RELEASED      1995
      LICENCE       Open source and free - Apache License 2.0
      PLATFORM      Cross-platform : Linux , Windows , macOS
      DEFAULT PORT  80 for HTTP , 443 for HTTPS
      ARCHITECTURE  PROCESS or THREAD based - one worker per
                    connection
      CONFIGURATION httpd.conf , and per-directory .htaccess files
      MODULES       mod_rewrite for URL rewriting , mod_ssl for
                    HTTPS , mod_php , mod_security
      PART OF       the LAMP stack :
                    Linux + APACHE + MySQL + PHP
   ```
   - It was for many years the most widely used web server in the world, and it remains one of the two dominant ones.

   Apache compared with Nginx — the usual follow-up
   ```
      +----------------+--------------------+--------------------+
      | Point          | APACHE             | NGINX              |
      +----------------+--------------------+--------------------+
      | Architecture   | process / thread   | EVENT-DRIVEN ,     |
      |                | per connection     | asynchronous       |
      | Static files   | slower             | FASTER             |
      | Many concurrent| more memory per    | handles thousands  |
      |   connections  | connection         | efficiently        |
      | .htaccess      | SUPPORTED - per-   | not supported      |
      |                | directory config   |                    |
      | Dynamic content| built-in modules   | passes to PHP-FPM  |
      | Configuration  | more flexible      | simpler, central   |
      | Common role    | application server | REVERSE PROXY and  |
      |                |                    | load balancer      |
      +----------------+--------------------+--------------------+

      They are frequently used TOGETHER : Nginx in front as a
      reverse proxy serving static files, with Apache behind it
      handling the application.
   ```

   Other server types, so the answer is not confused
   ```
      WEB SERVER          Apache , Nginx , IIS , LiteSpeed
      APPLICATION SERVER  Tomcat , JBoss , WebLogic , WebSphere
      DATABASE SERVER     MySQL , PostgreSQL , Oracle
      MAIL SERVER         Postfix , Sendmail , Exchange
      FILE SERVER         Samba , NFS
      DNS SERVER          BIND
      PROXY SERVER        Squid , HAProxy
   ```
   - The distinction worth adding in one line: a `web server` serves HTTP content and hands dynamic requests to an interpreter; an `application server` such as Tomcat runs the application code itself and provides services like transactions and connection pooling. Apache is the former — though with `mod_php` loaded it performs part of the latter's job, which is why the two terms are often blurred in practice.

6. **Discuss the necessary of using application framework in web application development.** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1053 (ET: BUET)]*

Answer: What an application framework is
   - An `application framework` is a ready-made skeleton for an application. It provides the routing, request handling, database layer, templating and security, so the developer writes only the parts specific to the application.
   ```
      EXAMPLES
        PHP      Laravel , Symfony , CodeIgniter
        Java     Spring Boot , Struts
        Python   Django , Flask
        .NET     ASP.NET MVC / Core
        Ruby     Rails
        JS       Express (server) , React / Angular / Vue (client)
   ```

   Why a framework is necessary

   1. It removes repetitive work
   ```
      Every web application needs the same machinery :
           routing a URL to some code
           reading form input and validating it
           connecting to the database
           managing sessions and logins
           rendering templates
           handling and logging errors
           sending email

      Written by hand, this is weeks of work BEFORE the first
      business feature. A framework supplies all of it on the
      first day.
   ```

   2. Security by default — the strongest argument
   ```
      A framework already defends against the standard attacks :

        SQL INJECTION   the ORM and query builder use PREPARED
             STATEMENTS automatically
        XSS             the template engine ESCAPES output by
             default, so {{ $name }} is safe even if $name
             contains <script>
        CSRF            a token is inserted into every form and
             verified on every POST
        PASSWORD HASHING with bcrypt, not MD5
        SESSION FIXATION the session ID is regenerated on login

      Hand-written code gets these wrong, and the mistakes are not
      visible until they are exploited. This is the single most
      important reason to use a framework rather than start from
      nothing.
   ```

   3. It enforces a structure — usually MVC
   ```
      MODEL       data and business rules
      VIEW        presentation
      CONTROLLER  request handling

      The framework's CONVENTIONS decide where each kind of code
      belongs, so a new developer knows where to look, and code
      review has a standard to measure against. Without one, every
      project invents its own arrangement.
   ```

   4. Faster development, and a shorter time to market
   - Scaffolding, migrations, an admin panel and a command-line generator mean a working prototype in days rather than weeks.

   5. Maintainability
   - Standard structure, standard naming and a large body of documentation. When a developer leaves, the replacement already knows the framework — which is not true of a bespoke architecture.

   6. Testability
   - Frameworks ship with a testing setup, dependency injection and factories for test data, so unit and integration tests are practical rather than aspirational.

   7. Database abstraction
   ```
      An ORM - Eloquent, Hibernate, Django ORM - lets the code work
      with objects instead of SQL, and MIGRATIONS keep the schema
      under version control :

           php artisan migrate

      Changing from MySQL to PostgreSQL becomes a configuration
      change rather than a rewrite.
   ```

   8. A community, and third-party packages
   - Bugs are found and fixed by thousands of users; a package exists for payment gateways, PDF generation, image handling, queues and reporting; and answers to problems are already written down.

   9. Scalability features built in
   - Caching, queues, background jobs, session drivers and API rate limiting are configuration rather than code.

   10. Modern practices come with it
   - Routing, middleware, dependency injection, API versioning, validation rules and a `CI/CD`-friendly project layout.

   The costs, which a complete answer should state
   ```
      LEARNING CURVE       the framework's conventions must be
           learnt before anything can be built
      PERFORMANCE OVERHEAD a framework does more work per request
           than hand-written code
      LESS CONTROL         you work the framework's way ; fighting
           it is worse than following it
      DEPENDENCY           the project is tied to the framework's
           upgrade cycle and its continued maintenance
      OVERKILL for a very small site - a three-page brochure needs
           no framework at all
      SECURITY OF THE FRAMEWORK ITSELF - a vulnerability in a
           popular framework affects every site using it, so it
           must be kept PATCHED
   ```
   - The judgement to state: for anything with a `login and a database`, a framework is the right choice, and the deciding reason is `security` rather than speed. Hand-written authentication, escaping and CSRF protection are where real applications fail, and a framework gets all three right by default. For a static brochure site, a framework adds cost with no benefit.

7. **(b) Draw three tier architecture of web technology.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1142 (ET: N/A)]*

Answer: Three-tier architecture of web technology
   ```mermaid
   flowchart TD
       A["TIER 1 - PRESENTATION<br/>Browser: HTML, CSS, JavaScript"] -->|HTTP request| B["TIER 2 - APPLICATION / LOGIC<br/>Web server + PHP, Java, .NET"]
       B -->|HTTP response| A
       B -->|SQL query| C["TIER 3 - DATA<br/>MySQL, Oracle, SQL Server"]
       C -->|result set| B
   ```
   ```
      +==============================================================+
      |            TIER 1  -  PRESENTATION TIER                      |
      |                     (CLIENT TIER)                            |
      |                                                              |
      |     +----------------------------------------------+         |
      |     |   WEB BROWSER                                |         |
      |     |   HTML  -  structure                         |         |
      |     |   CSS   -  presentation                      |         |
      |     |   JavaScript - client-side behaviour         |         |
      |     +----------------------------------------------+         |
      |     Runs on the USER'S MACHINE                               |
      +==============================================================+
                 |   HTTP / HTTPS request       ^   HTML response
                 v                              |
      +==============================================================+
      |         TIER 2  -  APPLICATION TIER                          |
      |              (BUSINESS LOGIC / MIDDLE TIER)                  |
      |                                                              |
      |     +----------------------------------------------+         |
      |     |   WEB SERVER      Apache , Nginx , IIS       |         |
      |     +----------------------------------------------+         |
      |     +----------------------------------------------+         |
      |     |   APPLICATION SERVER / RUNTIME               |         |
      |     |   PHP , Java (Tomcat) , .NET , Node.js       |         |
      |     |                                              |         |
      |     |   - authentication and authorisation         |         |
      |     |   - ALL business rules                       |         |
      |     |   - input validation                        |         |
      |     |   - session management                       |         |
      |     |   - builds the HTML response                 |         |
      |     +----------------------------------------------+         |
      +==============================================================+
                 |   SQL query                  ^   result set
                 v                              |
      +==============================================================+
      |             TIER 3  -  DATA TIER                             |
      |                   (DATABASE TIER)                            |
      |                                                              |
      |     +----------------------------------------------+         |
      |     |   DATABASE SERVER                            |         |
      |     |   MySQL , PostgreSQL , Oracle , SQL Server   |         |
      |     |                                              |         |
      |     |   - stores and retrieves the data            |         |
      |     |   - enforces integrity constraints           |         |
      |     |   - transactions , indexes , backup          |         |
      |     +----------------------------------------------+         |
      +==============================================================+
   ```

   What each tier does
   ```
      TIER 1 - PRESENTATION
           Everything the user sees and interacts with. It contains
           NO business rules and NO database access. Runs in the
           BROWSER, on the user's own device.

      TIER 2 - APPLICATION
           The only tier that makes DECISIONS. It receives the
           request, authenticates the user, applies the business
           rules, queries the database, and builds the response.
           It is the ONLY tier that talks to the database.

      TIER 3 - DATA
           Stores the data and guarantees its integrity. It never
           talks to the browser directly.
   ```

   The rule the architecture depends on
   ```
      EACH TIER TALKS ONLY TO THE ONE NEXT TO IT.

           Tier 1  <->  Tier 2  <->  Tier 3

      The BROWSER MUST NEVER REACH THE DATABASE DIRECTLY. If it
      could, the database credentials would have to be in the
      client code, where every user can read them. This single
      rule is what makes the design secure.
   ```

   Advantages
   - `Security` — the database is not exposed to the client, and every rule is enforced in tier 2 where the user cannot alter it.
   - `Scalability` — each tier is scaled independently: more application servers behind a load balancer, or a database replica.
   - `Maintainability` — a change to the interface touches tier 1 only; a change to a business rule touches tier 2 only.
   - `Reusability` — the same tier 2 serves a web page, a mobile application and an API.
   - `Parallel development` — front-end, back-end and database teams work simultaneously against agreed interfaces.
   - `Flexibility` — the database can be replaced without touching the browser code.

   Comparison with the other tier counts
   ```
      1-TIER   everything on one machine - a desktop application
           with a local database.

      2-TIER   CLIENT-SERVER. A thick client talks DIRECTLY to the
           database. Simple, but the database credentials live in
           the client, business logic is duplicated in every
           client, and it does not scale.

      3-TIER   as above - the standard for web applications.

      N-TIER   tier 2 is subdivided further : a web tier, a
           service tier, a caching tier, a message queue, a
           reporting service. Microservices are the extreme case.
   ```
   - Where the tiers physically run in practice: tier 1 on the user's device, tier 2 and tier 3 on `separate servers` — which is what allows the database to sit behind its own firewall, reachable only from the application servers. Putting tiers 2 and 3 on one machine still counts as three-tier logically, but it forfeits that protection.

## CSS & Styling (Inline, Internal, External) (4)

1. **(ক) CSS কী? CSS এর প্রকারভেদসমূহ উদাহরণসহ আলোচনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 411 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) What CSS is
   - `CSS` stands for `Cascading Style Sheets`. It controls the `presentation` of an HTML document — colours, fonts, spacing, borders, backgrounds and layout. It separates how a page `looks` from what it `contains`.
   ```css
      selector  {  property : value ;  }

      h1        {  color: navy; font-size: 32px;
                   text-align: center;  }
   ```
   ```
      "CASCADING" refers to the ORDER OF PRIORITY applied when
      several rules target the same element :

           inline style  >  #id  >  .class  >  element

      The more SPECIFIC rule wins ; between rules of equal
      specificity, the LAST one written wins. !important overrides
      all of them, and should be avoided.
   ```

   The three types of CSS

   1. Inline CSS
   - Written directly in the element's `style` attribute.
   ```html
      <p style="color:red; font-size:18px;">This is red text.</p>
      <h1 style="text-align:center; color:navy;">Heading</h1>
   ```
   ```
      ADVANTAGE     highest priority ; useful for one quick
           exception, and for HTML EMAIL, where external CSS is
           stripped
      DISADVANTAGE  it must be repeated on every element ; it
           mixes presentation with content ; it cannot be cached ;
           it cannot use HOVER or MEDIA QUERIES
           -> the WORST method for a real site
   ```

   2. Internal CSS — embedded
   - Written inside a `<style>` block in the `<head>` of the page.
   ```html
      <!DOCTYPE html>
      <html>
      <head>
          <style>
              body { font-family: Arial, sans-serif; }
              h1   { color: navy; text-align: center; }
              p    { line-height: 1.6; }
              .card{ border: 1px solid #ccc; padding: 20px; }
          </style>
      </head>
      <body>
          <h1>Welcome</h1>
          <p>Some text.</p>
      </body>
      </html>
   ```
   ```
      ADVANTAGE     styles the WHOLE PAGE from one place ; no extra
           HTTP request
      DISADVANTAGE  applies to ONE PAGE ONLY, so it must be
           repeated in every file ; not cached separately ;
           increases the size of every page
           -> acceptable for a single-page document
   ```

   3. External CSS
   - Written in a separate `.css` file and attached with `<link>`.
   ```css
      /* style.css */
      body  { font-family: Arial, sans-serif; margin: 0; }
      h1    { color: navy; text-align: center; }
      .card { border: 1px solid #ccc; padding: 20px;
              border-radius: 8px; }
   ```
   ```html
      <head>
          <link rel="stylesheet" href="style.css">
      </head>
   ```
   ```
      ADVANTAGE     ONE FILE STYLES THE WHOLE SITE - change the
           colour once and a thousand pages change ; the browser
           CACHES it, so pages after the first load faster ; the
           HTML stays clean
      DISADVANTAGE  one extra HTTP request on the first load ; the
           page may flash unstyled if the file is slow

      -> THE BEST METHOD, and the one to name if only one is asked
         for.
   ```

   Priority when all three are present
   ```
      INLINE  >  INTERNAL  >  EXTERNAL

      ...but internal against external actually depends on the
      ORDER in the <head>. The one appearing LAST wins :

           <link rel="stylesheet" href="style.css">
           <style> h1 { color: red; } </style>
           -> the internal rule wins, being later

           <style> h1 { color: red; } </style>
           <link rel="stylesheet" href="style.css">
           -> the EXTERNAL file wins, being later

      This surprises people, and it is a common exam trap. Only
      INLINE has a genuinely higher specificity ; the other two
      simply cascade by position.
   ```

   The fourth method, worth one line
   ```html
      <!-- @import , inside a stylesheet or a <style> block -->
      <style>
          @import url("style.css");
      </style>
   ```
   - `@import` works, but it is `slower` than `<link>`: the browser cannot start downloading the imported file until it has parsed the file that imports it, so the requests are serialised rather than parallel. `<link>` is preferred.

2. **What is CSS? What is CSS framework? Write down 3 CSS framework name?** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*

Answer: What CSS is
   - `CSS` stands for `Cascading Style Sheets`. It controls the `presentation` of an HTML document — colours, fonts, spacing, borders, backgrounds and layout — keeping how a page `looks` separate from what it `contains`.
   ```css
      selector { property : value ; }

      h1       { color: navy; font-size: 32px; }
      .card    { border: 1px solid #ccc; padding: 20px; }
   ```
   ```
      Applied in three ways :
           INLINE     style="..." in the tag
           INTERNAL   a <style> block in the <head>
           EXTERNAL   a separate .css file, linked with <link> -
                      THE BEST METHOD
   ```

   What a CSS framework is
   - A `CSS framework` is a ready-made collection of stylesheets — and often a little JavaScript — providing a `grid system`, pre-styled components and utility classes, so a developer builds a responsive interface without writing CSS from nothing.
   ```
      WHAT A FRAMEWORK PROVIDES

        a RESPONSIVE GRID SYSTEM - columns that rearrange
             themselves on a phone
        PRE-STYLED COMPONENTS - buttons, forms, navigation bars,
             cards, modals, tables, alerts
        a TYPOGRAPHY and SPACING scale, so the design is consistent
        UTILITY CLASSES - text-center , mt-3 , d-flex
        BROWSER NORMALISATION - the same appearance in every
             browser
        ACCESSIBILITY defaults built into the components
   ```

   Three CSS framework names
   ```
      1. BOOTSTRAP     the most widely used. A 12-column grid,
           a large component library, and Sass variables for
           theming. Originally from Twitter.

      2. TAILWIND CSS  a UTILITY-FIRST framework. Instead of a
           pre-made .btn class, small single-purpose classes are
           composed in the HTML :
                <button class="px-4 py-2 bg-blue-600 text-white
                               rounded hover:bg-blue-700">

      3. FOUNDATION    by ZURB. A mobile-first grid, strong
           accessibility support, and a highly customisable build.
   ```
   ```
      OTHERS worth naming :
           Bulma        modern, pure CSS, no JavaScript
           Materialize  implements Google's Material Design
           Semantic UI  class names that read like English
           Skeleton     very small and minimal
   ```

   Advantages of using a framework
   - `Faster development` — a responsive layout in hours rather than days.
   - `Responsive by default` — the grid and the breakpoints are already designed and tested.
   - `Cross-browser consistency` — the framework has absorbed the browser differences.
   - `Consistent design` — one spacing and typography scale across the whole application.
   - `Well documented`, with a large community and many examples.
   - `Accessibility` defaults in the components.

   Disadvantages
   - `File size` — the full framework is far larger than the CSS an application actually uses, though a build step can strip the unused parts.
   - `Generic appearance` — sites built on the default Bootstrap theme look alike.
   - `Learning curve` — the framework's own class names must be learnt.
   - `Class clutter` in the HTML, which is the standing criticism of the utility-first approach.
   - `Dependency` on the framework's upgrade cycle, and `overkill` for a small static page.

   - Which to choose: `Bootstrap` where speed and a familiar component set matter, and where the team is not primarily front-end; `Tailwind` where a distinctive design is wanted and the team is comfortable composing utilities; and `no framework at all` for a small site, since modern `Flexbox` and `CSS Grid` do natively what frameworks were originally invented to work around.

3. **(খ) CSS Box Model এ ‘Padding’ এবং ‘Margin’ এরিয়ার মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) The CSS box model
   - Every element is a rectangular box built of `four` areas, from the inside out.
   ```
      +==================================================+
      |                    MARGIN                        |
      |   +------------------------------------------+   |
      |   |                 BORDER                   |   |
      |   |   +----------------------------------+   |   |
      |   |   |             PADDING              |   |   |
      |   |   |   +--------------------------+   |   |   |
      |   |   |   |                          |   |   |   |
      |   |   |   |        CONTENT           |   |   |   |
      |   |   |   |    (text or image)       |   |   |   |
      |   |   |   |                          |   |   |   |
      |   |   |   +--------------------------+   |   |   |
      |   |   |                                  |   |   |
      |   |   +----------------------------------+   |   |
      |   |                                          |   |
      |   +------------------------------------------+   |
      |                                                  |
      +==================================================+

      CONTENT  the text or image itself
      PADDING  space INSIDE the border - between content and border
      BORDER   the line around the padding
      MARGIN   space OUTSIDE the border - between this element and
               its neighbours
   ```

   Difference between padding and margin

   | Point | Padding | Margin |
   |---|---|---|
   | Position | `Inside` the border | `Outside` the border |
   | Separates | Content from the `border` | This element from `other elements` |
   | Background colour | `Included` — takes the element's background | `Transparent` — shows what is behind |
   | Clickable | `Yes` — part of the element | `No` |
   | Negative value | `Not allowed` | `Allowed` — `margin: -10px` |
   | Collapsing | `Never` collapses | Vertical margins `collapse` |
   | `auto` value | Not meaningful | `margin: 0 auto` centres the element |
   | Affects element size | `Increases` it (in the default box model) | Does not — it pushes neighbours away |

   The syntax is identical
   ```css
      padding: 10px;                  /* all four sides */
      padding: 10px 20px;             /* top-bottom , left-right */
      padding: 10px 20px 15px 5px;    /* top right bottom left -
                                         CLOCKWISE */
      padding-top: 10px;              /* one side */

      margin: 10px;                   /* the same forms */
      margin: 0 auto;                 /* centre horizontally */
   ```

   The two differences that actually cause bugs

   1. Background colour
   ```css
      .box { background: yellow; padding: 20px; margin: 20px; }
   ```
   ```
      The PADDING is YELLOW - it belongs to the element.
      The MARGIN is TRANSPARENT - the page background shows through.

      This is the quickest way to tell them apart on screen.
   ```

   2. Margin collapsing
   ```css
      .a { margin-bottom: 30px; }
      .b { margin-top:    20px; }
   ```
   ```
      The gap between .a and .b is 30px , NOT 50px.

      VERTICAL margins between adjacent elements COLLAPSE to the
      LARGER of the two. Horizontal margins never collapse, and
      PADDING NEVER COLLAPSES - 30px of padding plus 20px of
      padding always gives 50px.

      This surprises everyone once, and it is a favourite exam
      question.
   ```

   The size calculation — the other classic trap
   ```css
      .box { width: 300px; padding: 20px; border: 5px solid; }
   ```
   ```
      DEFAULT  box-sizing: content-box

           total width = 300 + 20 + 20 + 5 + 5
                       = 350px          <- NOT 300

           width applies to the CONTENT only. Padding and border
           are ADDED on top, which is why layouts overflow.

      THE FIX  box-sizing: border-box

           * { box-sizing: border-box; }

           total width = 300px , with padding and border INSIDE it.
           Content width becomes 300 - 50 = 250px.

      Almost every modern stylesheet begins with that rule,
      precisely to avoid the arithmetic above.
   ```

   When to use which
   ```
      USE PADDING when
           the content needs breathing space INSIDE a bordered box
           or a coloured background
           a button needs to be larger and more clickable
           a table cell needs internal spacing

      USE MARGIN when
           two elements need SEPARATING
           a block needs CENTRING - margin: 0 auto
           a heading needs space above it, away from the paragraph
           before
   ```
   - One further asymmetry worth stating: a `click` inside the padding counts as clicking the element, but a click in the margin does not. So a button made larger with `padding` gains a bigger clickable target, while the same button made larger with `margin` gains only empty space around it.

4. **(খ) CSS কী? কতভাবে একজন Website develop কারী তার page-এ CSS ব্যবহার করতে পারে।** *[Software Assistant Programmer 13.10.2022 compact it 708 (ET: N/A)]*

Answer: (Answered in English, as required for IT topics.) What CSS is
   - `CSS` stands for `Cascading Style Sheets`. It controls the `presentation` of an HTML document — colours, fonts, spacing, borders, backgrounds and layout — keeping how a page `looks` separate from what it `contains`.
   ```css
      selector { property : value ; }

      h1       { color: navy; font-size: 32px;
                 text-align: center; }
   ```
   ```
      "CASCADING" refers to the priority applied when several rules
      target the same element :

           inline style  >  #id  >  .class  >  element

      The more SPECIFIC rule wins ; between rules of equal
      specificity, the LAST one written wins.
   ```

   The ways a developer can use CSS on a page

   1. Inline CSS
   ```html
      <p style="color:red; font-size:18px;">This is red text.</p>
   ```
   ```
      Written in the element's own style attribute.

      USE IT FOR    one quick exception ; HTML EMAIL, where
           external CSS is stripped by mail clients
      AVOID IT FOR  a real site : it must be repeated on every
           element, it mixes presentation with content, it cannot
           be cached, and it CANNOT use :hover or MEDIA QUERIES
   ```

   2. Internal CSS — embedded
   ```html
      <head>
          <style>
              body { font-family: Arial, sans-serif; }
              h1   { color: navy; text-align: center; }
              .card{ border: 1px solid #ccc; padding: 20px; }
          </style>
      </head>
   ```
   ```
      USE IT FOR    a SINGLE-PAGE document, or a page-specific
           override
      AVOID IT FOR  a multi-page site : the block must be copied
           into every file, and it is not cached separately
   ```

   3. External CSS
   ```html
      <head>
          <link rel="stylesheet" href="style.css">
      </head>
   ```
   ```css
      /* style.css */
      body  { font-family: Arial, sans-serif; margin: 0; }
      h1    { color: navy; text-align: center; }
      .card { border: 1px solid #ccc; padding: 20px; }
   ```
   ```
      THE BEST METHOD, and the one to recommend.

      ONE FILE STYLES THE WHOLE SITE - change the colour once and
           a thousand pages change
      the browser CACHES it, so every page after the first loads
           faster
      the HTML stays clean and readable
      several files may be linked : reset.css , layout.css ,
           theme.css
      a print-only stylesheet can be attached :
           <link rel="stylesheet" href="print.css" media="print">
   ```

   4. `@import`
   ```html
      <style>
          @import url("style.css");
      </style>
   ```
   - It works, but it is `slower` than `<link>`: the browser cannot begin downloading the imported file until it has parsed the file that imports it, so requests are serialised instead of parallel.

   Priority when more than one method is used
   ```
      INLINE  >  INTERNAL  >  EXTERNAL

      ...but internal against external actually depends on ORDER in
      the <head> - the one appearing LAST wins :

           <link href="style.css">           then  <style>...</style>
           -> the INTERNAL rule wins

           <style>...</style>                then  <link href="...">
           -> the EXTERNAL file wins

      Only INLINE has a genuinely higher specificity. The other two
      simply cascade by position, and this is a common exam trap.
   ```
   - Which a developer should actually choose: `external` for everything, with `internal` only for a page-specific override and `inline` only where nothing else is possible, such as an HTML email. The reason is not style but engineering — one cached file, one place to change, and HTML that a person can read.

## Web Security & Browser Same-Origin Policy (Iframe) (2)

1. **A & B two frames in a browser loaded from different origins. Why is it a reasonable security policy to allow A to navigate B to another origin base only on whether the display area of A contains dis-pare of B and A has the control over area.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 494 (ET: N/A)]*

Answer: The question, restated
   - Two frames `A` and `B` are loaded from `different origins`. The browser permits `A` to navigate `B` to another URL, and the stated justification is that `A's display area contains B's display area, and A controls that area`. The question asks why that is a reasonable security policy.

   The rule the browser actually applies
   ```
      The SAME-ORIGIN POLICY normally forbids a frame from one
      origin to READ or WRITE another origin's content :

           A cannot read B's DOM
           A cannot read B's cookies
           A cannot call B's JavaScript
           A cannot read text a user typed into B

      But there is a DELIBERATE EXCEPTION :

           A frame MAY NAVIGATE a frame it is the ANCESTOR of -
           that is, one it embedded - to any URL, even
           cross-origin.
   ```

   Why the exception is reasonable — the argument

   1. A already controls that region of the screen
   ```
      A EMBEDDED B in the first place. A chose B's URL, its
      position and its size :

           <iframe src="https://b.example.com" width="600"
                   height="400"></iframe>

      A COULD SIMPLY REMOVE THE IFRAME ALTOGETHER, or point it
      somewhere else at creation time, or cover it with an opaque
      div.

      So navigating B GRANTS A NO POWER IT DID NOT ALREADY HAVE.
      The policy denies A nothing it could not achieve by other
      means, which is the test of whether a restriction is
      worthwhile.
   ```

   2. Navigation is not access
   ```
      Navigating B DESTROYS B's document and loads a new one. It
      does NOT let A read the old one.

           A can say  "B, go to that URL"
           A CANNOT   read what was in B , read B's cookies, or
                      read what the user typed into B

      The confidentiality of B's data is never breached, because
      the old document is gone rather than exposed.
   ```

   3. The screen region is A's responsibility
   ```
      The user sees ONE page - A's page. Every pixel inside A's
      area is, from the user's point of view, part of A's content.
      B occupies that area only because A allowed it to.

      Giving A control over its own screen region is therefore
      consistent with what the user already believes, and A is
      already accountable for what appears there.
   ```

   4. It is necessary in practice
   ```
      Real applications depend on it :

        an OAUTH or PAYMENT flow inside an iframe must be able to
             redirect after the step completes
        a page with a navigation pane and a content pane needs the
             pane to change
        a CAPTCHA or a widget must be replaceable

      Forbidding it would break a great deal without protecting
      anything.
   ```

   Where the boundary is drawn — what is still forbidden
   ```
      ALLOWED
           A frame may navigate itself, its own DESCENDANTS, and
           the TOP frame if it is the only frame on the page.

      FORBIDDEN
           A frame may NOT navigate an UNRELATED frame - a sibling
           it did not embed, or a frame in another tab or window it
           did not open.

      WHY : an unrelated frame's screen area is NOT A's
      responsibility, and A has no existing power over it. Allowing
      that would let any embedded advertisement redirect the whole
      page, which is exactly the abuse the restriction prevents.
   ```

   The attacks the policy still leaves open, and their defences
   ```
      CLICKJACKING
           A embeds B invisibly and tricks the user into clicking
           B's "Transfer" button while believing they are clicking
           A's page.
           DEFENCE : B refuses to be framed -
                X-Frame-Options: DENY  or  SAMEORIGIN
                Content-Security-Policy: frame-ancestors 'self'
           A site handling money must send one of these.

      FRAME PHISHING
           A navigates B to a look-alike login page.
           DEFENCE : the same headers, plus HTTPS and a visible
                address bar the user can check.

      TABNABBING
           A page opened with target="_blank" navigates its opener
           to a phishing site.
           DEFENCE : rel="noopener noreferrer" on every such link.
   ```
   - The principle underlying the whole policy, stated plainly: `the same-origin policy protects data, not layout`. Reading another origin's content is forbidden because it leaks `information`; navigating a frame you embedded is permitted because it changes only `what is displayed in your own area` — and the site being framed retains the power to refuse framing entirely through `X-Frame-Options` or `frame-ancestors`.

2. **What is CORS in web development?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 761 (ET: N/A)]*

Answer: What CORS is
   - `CORS` stands for `Cross-Origin Resource Sharing`. It is a browser mechanism that lets a server `explicitly permit` a web page from one origin to make requests to a different origin — relaxing the `same-origin policy` in a controlled way.
   ```
      AN ORIGIN = SCHEME + HOST + PORT , all three.

           https://example.com          the origin
           http://example.com           DIFFERENT - scheme differs
           https://api.example.com      DIFFERENT - host differs
           https://example.com:8080     DIFFERENT - port differs
   ```

   The problem it solves
   ```
      THE SAME-ORIGIN POLICY blocks JavaScript on one origin from
      READING a response from another origin :

           page on   https://myapp.com
           calls     https://api.other.com/data
           -> the browser BLOCKS the JavaScript from reading it :
              "No 'Access-Control-Allow-Origin' header is present
               on the requested resource."

      WHY THE POLICY EXISTS : without it, any malicious page you
      visited could call https://yourbank.com/api/balance with
      YOUR COOKIES ATTACHED and read your balance. The same-origin
      policy is what makes cookie-based sessions safe at all.
   ```

   How CORS works — the server decides
   ```
      The SERVER adds response headers granting permission :

           Access-Control-Allow-Origin: https://myapp.com
           Access-Control-Allow-Methods: GET, POST, PUT, DELETE
           Access-Control-Allow-Headers: Content-Type, Authorization
           Access-Control-Allow-Credentials: true
           Access-Control-Max-Age: 86400

      The BROWSER then permits the JavaScript to read the response.
   ```
   ```
      THE KEY POINT, and the one most often misunderstood :

      CORS IS ENFORCED BY THE BROWSER, AND GRANTED BY THE SERVER.

      It is NOT a server-side protection. curl , Postman and a
      Python script IGNORE CORS COMPLETELY, because they are not
      browsers. CORS protects the USER from a malicious page ; it
      does NOT protect the API from an attacker.
   ```

   Simple requests and preflighted requests
   ```
      A SIMPLE REQUEST goes straight through :
           method is GET , HEAD or POST
           and only safe headers are used
           and Content-Type is one of :
                text/plain
                application/x-www-form-urlencoded
                multipart/form-data

      ANYTHING ELSE IS PREFLIGHTED. The browser first sends an
      OPTIONS request to ask permission :

           OPTIONS /api/data HTTP/1.1
           Origin: https://myapp.com
           Access-Control-Request-Method: PUT
           Access-Control-Request-Headers: Content-Type

           HTTP/1.1 204 No Content
           Access-Control-Allow-Origin: https://myapp.com
           Access-Control-Allow-Methods: GET, POST, PUT, DELETE
           Access-Control-Allow-Headers: Content-Type
           Access-Control-Max-Age: 86400

      Only if that succeeds does the real PUT follow.
      Note that Content-Type: application/json - which every REST
      API uses - TRIGGERS A PREFLIGHT. This is why "it works in
      Postman but not in the browser" is such a common complaint.
   ```
   ```mermaid
   sequenceDiagram
       participant B as Browser (myapp.com)
       participant S as API (api.other.com)
       B->>S: OPTIONS /api/data (preflight)
       S-->>B: 204 + Access-Control-Allow-* headers
       B->>S: PUT /api/data (the real request)
       S-->>B: 200 + Access-Control-Allow-Origin
       B->>B: JavaScript may now read the response
   ```

   Enabling it on the server
   ```javascript
      // Node.js / Express
      const cors = require("cors");
      app.use(cors({ origin: "https://myapp.com",
                     credentials: true }));
   ```
   ```php
      // PHP
      header("Access-Control-Allow-Origin: https://myapp.com");
      header("Access-Control-Allow-Methods: GET, POST, PUT, DELETE");
      header("Access-Control-Allow-Headers: Content-Type,
              Authorization");
   ```

   The security mistakes to avoid
   ```
      1. Access-Control-Allow-Origin: *
           Allows ANY site to call the API. Acceptable for a
           PUBLIC, read-only API with no authentication. NEVER
           acceptable for an authenticated one.

      2. "*" TOGETHER WITH credentials
           Access-Control-Allow-Origin: *
           Access-Control-Allow-Credentials: true
           The browser REJECTS this combination outright - and
           rightly, because it would let any site read an
           authenticated response. An explicit origin must be
           named.

      3. REFLECTING THE Origin HEADER BACK
           header("Access-Control-Allow-Origin: " . $_SERVER["HTTP_ORIGIN"]);
           This accepts EVERY origin while appearing specific. It
           is a real vulnerability, and a common one.

      4. TREATING CORS AS SECURITY
           It is not. AUTHENTICATION, AUTHORISATION, INPUT
           VALIDATION and RATE LIMITING must all be enforced on the
           server regardless of CORS, because a non-browser client
           ignores CORS entirely.
   ```
   - The related mechanism worth naming: `JSONP` was the pre-CORS workaround, exploiting the fact that `<script>` tags are not subject to the same-origin policy. It works only for `GET`, hands the remote server the ability to run arbitrary code in your page, and is `obsolete` — CORS replaced it and should always be used instead.
