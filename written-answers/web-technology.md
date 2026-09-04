<!-- TOC START -->
**Table of Contents** — 7 subtopics · 77 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [HTML & Web Fundamentals](#html--web-fundamentals-30) | 30 |
| 2 | [JavaScript & jQuery (DOM & Validation)](#javascript--jquery-dom--validation-16) | 16 |
| 3 | [HTTP Protocol](#http-protocol-10) | 10 |
| 4 | [Web Services & APIs (SOAP vs REST)](#web-services--apis-soap-vs-rest-8) | 8 |
| 5 | [Full Stack & Backend Web Development](#full-stack--backend-web-development-7) | 7 |
| 6 | [CSS & Styling (Inline, Internal, External)](#css--styling-inline-internal-external-4) | 4 |
| 7 | [Web Security & Browser Same-Origin Policy (Iframe)](#web-security--browser-same-origin-policy-iframe-2) | 2 |

<!-- TOC END -->

---

## HTML & Web Fundamentals (30)

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

## JavaScript & jQuery (DOM & Validation) (16)

1. **Jquery for email validation** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

2. **Write Javascript code to check NID validity?** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1359 (ET: BUET)]*

3. **Which tag is used to write JavaScript in html?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

4. **Write Javascript function to validate a customer number where the customer number in 3 uppercase letter and district code followed by 8 digits.** *[BICIC Assistant Programmer 2022 compact it 630 (ET: BUET)]*

5. **Write HTML and Javascript code of following box.** *[EGCB Assistant Engineer (CSE) 2022 compact it 716 (ET: BUET)]*

6. **Explain hoisting in JavaScript?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 761 (ET: N/A)]*

7. **Display element by id in JavaScript?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 762 (ET: N/A)]*

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

9. **Differentiate among $.ajax(), $.get() and $.load() function of jQuery with necessary example.** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1058 (ET: AUST)]*, *[Probashi Kallyan Bank Programmer 2019 compact it 1158 (ET: AUST)]*

10. **How do you change the value of a HTML element using HTML DOM?** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1058 (ET: AUST)]*

11. **Difference among $.ajax(), $.load() and $.get().** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1162 (ET: N/A)]*

12. **How to change html attribute through html DOM?** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1163 (ET: N/A)]*, *[Investment Corporation Bangladesh Assistant Programmer 2017 compact it 1216 (ET: N/A)]*

13. **Suppose you've a javaScript code name as “bankScript” write the code for loading in HTML using JS.** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1173 (ET: N/A)]*

14. **What is closure in JavaScript? Explain with an example?** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1217 (ET: N/A)]*

15. **Difference among $.ajax(), $.load(), $.get().** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1217 (ET: N/A)]*

16. **What is the working procedure of AJAX?** *[Agrani Bank Ltd. Senior Officer (IT) 2017 compact it 1221-1222 (ET: N/A)]*

## HTTP Protocol (10)

1. What do the following specific HTTP status codes mean? Write down the exact standard text phrase for each: (a) 200 (b) 403 (c) 503 [SO IT 25-07-2026]

2. Describe any two key differences between the HTTP GET and HTTP POST methods used for communication between a web browser and a web server. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

3. **6.7 What do the following specific HTTP status codes mean? Write down the exact standard text phrase for each: (a) 200 (b) 403 (c) 503** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

4. **(ক) ফর্ম জমা দেয়ার পদ্ধতি GET এবং POST এর মধ্যে পার্থক্য কী, কখন কোন পদ্ধতি ব্যবহার করতে হয় উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

5. **What is cookie? What is its purpose?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*

6. **What is the difference between http and https?** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 648 (ET: BUET)], [BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 796 (ET: N/A)]*

7. **(গ) URL কী? একটি URL ক্লিক করার পর Web Page Show করার পূর্ব পর্যন্ত যে কয়টি Step হয় সেগুলির নাম লিখুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 705 (ET: N/A)]*

8. **(c) Explain the difference between Stateless and Stateful protocols. Which type of protocol http is?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 885-886 (ET: N/A)]*

9. **What is the difference between http session and http cookies?** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 911 (ET: BUET)]*

10. **It is a small price of data stored on a user's computer by the web browser while browsing a website. What we are talking about?** *[Sadharan Bima Corporation Programmer/ AP/AME 2020 compact it 1002 (ET: DU)], [BSEC Assistant Director (MIS) 2021 compact it 938 (ET: IBA)]*

## Web Services & APIs (SOAP vs REST) (8)

1. **What are SOAP and RESTful APIs in web services? State one main difference between SOAP and REST in terms of how they exchange data.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1426 (ET: E-Zone)]*

2. **What is API?** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*

3. **What is an API?** *[BBA Assistant Programmer 12.07.2025 compact it 1432 (ET: BUET)]*

4. **Write difference between REST API and SOAP API.** *[BKSP Assistant Programmer 13.07.2024 compact it 1460 (ET: N/A)]*

5. **What is API? Explain with example.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*

6. **What is the two prime advantages of RESTful API?** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 756 (ET: N/A)]*

7. **What is API?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 865 (ET: BUET)]*

8. **What is SOAP?** *[Bangladesh Bank Assistant Programmer 2019 compact it 1157 (ET: DU)]*

## Full Stack & Backend Web Development (7)

1. **Write appropriate program client and database using any language and a login page using ID and password. [Approximate Web page login code]** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 320 (ET: N/A)]*

2. **(খ) Client-side scripting এর তুলনায় Server-side scripting এর সুবিধাগুলো কী কী?** *[Software Assistant Programmer 13.10.2022 compact it 709 (ET: N/A)]*

3. **(খ) PHP কি? Web Development এ Java Script এর প্রয়োজনীয়তা সম্পর্কে বিবরণ দিন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 771 (ET: N/A)]*

4. **(b) What are the resources you need to access a web enabled application?** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 796 (ET: N/A)]*

5. **Apache কোন ধরনের Server এক কথায় লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 866 (ET: BUET)]*

6. **Discuss the necessary of using application framework in web application development.** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1053 (ET: BUET)]*

7. **(b) Draw three tier architecture of web technology.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1142 (ET: N/A)]*

## CSS & Styling (Inline, Internal, External) (4)

1. **(ক) CSS কী? CSS এর প্রকারভেদসমূহ উদাহরণসহ আলোচনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 411 (ET: N/A)]*

2. **What is CSS? What is CSS framework? Write down 3 CSS framework name?** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*

3. **(খ) CSS Box Model এ ‘Padding’ এবং ‘Margin’ এরিয়ার মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

4. **(খ) CSS কী? কতভাবে একজন Website develop কারী তার page-এ CSS ব্যবহার করতে পারে।** *[Software Assistant Programmer 13.10.2022 compact it 708 (ET: N/A)]*

## Web Security & Browser Same-Origin Policy (Iframe) (2)

1. **A & B two frames in a browser loaded from different origins. Why is it a reasonable security policy to allow A to navigate B to another origin base only on whether the display area of A contains dis-pare of B and A has the control over area.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 494 (ET: N/A)]*

2. **What is CORS in web development?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 761 (ET: N/A)]*
