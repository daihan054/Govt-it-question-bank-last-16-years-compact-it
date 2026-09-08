<!-- TOC START -->
**Table of Contents** — 7 subtopics · 49 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [HTML, XML & Web Fundamentals](#html-xml--web-fundamentals-15) | 15 |
| 2 | [PHP & Server-Side](#php--server-side-9) | 9 |
| 3 | [Scripting & JavaScript](#scripting--javascript-8) | 8 |
| 4 | [Web Services & APIs](#web-services--apis-6) | 6 |
| 5 | [Full Stack & Web Servers](#full-stack--web-servers-5) | 5 |
| 6 | [HTTP & Status Codes](#http--status-codes-5) | 5 |
| 7 | [CSS & Styling](#css--styling-1) | 1 |

<!-- TOC END -->

---

## HTML, XML & Web Fundamentals (15)

1. **Which of the following is the root tag of the HTML document?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 6 (ET: BIBM)]*  
   a) <body>  
   b) <head>  
   c) <title>  
   d) <html>

   answer: d — <html>  
   explanation: Everything in the document sits inside the <html> element, which is the root of the tree.

2. **How to create an unordered list (a list with the list items in bullets) in HTML?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 6 (ET: BIBM)]*  
   a) <ul>  
   b) <ol>  
   c) <li>  
   d) <i>

   answer: a — <ul>  
   explanation: <ul> creates an unordered (bulleted) list, with each item in an <li>.

3. **What is the popular way to linking many documents?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*  
   **Ans:** hyperlink

   answer: Hyperlink  
   explanation: A hyperlink, written with the anchor tag <a href="...">, connects one document to another so users can jump between them.

4. **URL stands for–** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 130 (ET: N/A)]*  
   a) Universal Resource Locator  
   b) Uniform Resource Locator  
   c) Unique Resource Locator  
   d) None

   answer: b — Uniform Resource Locator  
   explanation: A URL gives the uniform address of a resource — its scheme, host and path.

5. **XSLT processors evaluate each statement in the context of the match that has been made. That is, XSLT processors are:** *[Sonali and Janata Bank Assistant Database Administrator 25-09-2021 compact it 113 (ET: N/A)]*  
   a) Context oriented  
   b) Procedural oriented  
   c) Object oriented  
   d) Relational oriented

   answer: a — Context oriented  
   explanation: XSLT evaluates each instruction relative to the current node it has matched, so the context node determines the result.

6. **Suppose you are using an HTML browser at a client machine C to access a static HTML webpage hosted in a HTTP server S. The page contains exactly one static embedded image which also resides at S. Assuming no web caching which of the following is correct when you load the webpage along with the embedded image?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 85 (ET: N/A)], [Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 183 (ET: N/A)]*  
   a. C need to send at least 2 HTTP requests to S using two different TCP connection.  
   b. C need to send at least 2 HTTP requests to S but a single TCP connection is sufficient.  
   c. A single HTTP request is sufficient without using any TCP connection from C to S.  
   d. A single HTTP request is sufficient using a single TCP connection from C to S.

   answer: b — C need to send at least 2 HTTP requests to S but a single TCP connection is sufficient  
   explanation: The page and the image are separate resources needing separate GETs, but HTTP/1.1 keeps the connection alive so one TCP connection carries both.

7. **Which one is the first search engine?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 160 (ET: N/A)]*  
   A) Google  
   B) Archie  
   C) Alta vista  
   D) WAIS

   answer: B — Archie  
   explanation: Archie, built in 1990, indexed FTP file listings and is regarded as the first internet search engine.

8. **The newest version of HTML is:** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 161 (ET: N/A)]*  
   A) WML  
   B) HTML5  
   C) XSL  
   D) HTML3

   answer: B — HTML5  
   explanation: HTML5 is the current standard, adding native audio, video, canvas and semantic elements.

9. **When a web browser interacts with a web server, the following actions take place?** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 183 (ET: N/A)]*  
   A1: The web browser requests a webpage using HTTP.  
   A2: The web browser establishes a TCP connection with the web server.  
   A3: The web server sends the requested webpage using HTTP.  
   A4: The web browser resolves the domain name using DNS.  
   Which is the correct order of execution of the above actions?  
   a) A4, A2, A1, A3  
   b) A1, A2, A3, A4  
   c) A4, A1, A2, A3  
   d) A2, A4, A1, A3

   answer: a — A4, A2, A1, A3  
   explanation: The browser first resolves the name through DNS, then opens a TCP connection, sends the HTTP request and finally receives the response.

10. **Which HTML attribute is used to hide characters of an input password?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 156 (ET: DU)]*  
   a) href  
   b) type  
   c) tyle  
   d) src

   answer: b — type  
   explanation: Setting type="password" on an input makes the browser mask the characters as they are typed.

11. **Which of the followings is not a built-in HTML tag?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 157 (ET: DU)]*  
   a) <script>  
   b) <form>  
   c) <html>  
   d) All of these are valid built-in HTML tags

   answer: d — All of these are valid built-in HTML tags  
   explanation: <script>, <form> and <html> are all standard HTML elements.

12. **Which of the following converts the documents written by HTML?** *[BTRC Sub-Assistant Director (Technical) 2019 compact it 201 (ET: IBA)]*  
   A. Browser  
   B. FTP  
   C. HTPP  
   D. Web

   answer: A. Browser  
   explanation: The browser parses the HTML and renders it as the formatted page the user sees.

13. **A nonstandard HTML extension that causes scrolling text to appear as pan of a Web page is-** *[Combined Bank Senior Officer (IT) 2018 compact it 221 (ET: DU)]*  
   A) DHCP  
   B) mask off  
   C) Dhrystone  
   D) marquee

   answer: D — marquee  
   explanation: <marquee> was a non-standard tag that scrolled text across the page; it is deprecated and CSS animation replaces it.

14. **Which of the following tags is used to create a paragraph in HTML?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 250 (ET: N/A)]*  
   A) <para>content</para>  
   B) <cont>para</cont>  
   C) <p> content</p>  
   D) <body>content</body>

   answer: C — <p> content</p>  
   explanation: The <p> element marks a paragraph of text.

15. **One advantage of XML compared to HTML is ________** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*  
   a. XML works on more platforms  
   b. XML is suited to using webpage as frontend to database  
   c. XML was designed for portable phone  
   d. XML is simpler to learn than html

   answer: b — XML is suited to using webpage as frontend to database  
   explanation: XML separates data from presentation and carries self-describing structured content, which makes it good for exchanging database records.

## PHP & Server-Side (9)

1. **Which is not a valid variable name in PHP?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 6 (ET: BIBM)]*  
   a) age  
   b) _age  
   c) PersonAge  
   d) 1age

   answer: d — 1age  
   explanation: A PHP variable name must start with a letter or underscore after the $, never with a digit.

2. **Which of the followings is a Web Framework built with PHP?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 153 (ET: DU)]*  
   a) Laravel  
   b) Django  
   c) MVC  
   d) Spring

   answer: a — Laravel  
   explanation: Laravel is a PHP MVC framework; Django is Python and Spring is Java.

3. **What will be the output of the following PHP code? <?php "Hello World" ?>** *[Probashi Kallyan Bank Programmer: 2019 compact it 211 (ET: AUST)]*  
   A) Error  
   B) Hello World  
   C) Nothing  
   D) None of this  
   16. What is the output of the code shown?  
   %(qty)d more %(food)s'%{'qty':1,'food':'spam'} *[Probashi Kallyan Bank Programmer: 2019 compact it 211 (ET: AUST)]*  
   A) Error  
   B) 1 more spam  
   C) No output  
   D) 1 more foods

   answer: C — Nothing  
   explanation: The string is just an expression that is never echoed or printed, so the page stays blank. The stray Python item pasted here answers (B) 1 more spam, since the dictionary fills the named format fields.

4. **Which is correct for concatenation in PHP?** *[Bangladesh Bank Assistant Programmer 2016 compact it 244 (ET: N/A)]*  
   A) $add = Sadd+1  
   B) $add = $add +1  
   C) $add = $add + Sadd  
   D) $add. = +1;

   answer: D — $add. = +1;  
   explanation: PHP joins strings with the dot, and the concatenating assignment is written .= — the option is the garbled form of $add .= 1. <!-- verify -->

5. **Which is used for adding two or more string in PHP?** *[Bangladesh Bank Assistant Programmer 2016 compact it 244 (ET: N/A)]*  
   A) +  
   B) *  
   C) . (dot)  
   D) |

   answer: C — . (dot)  
   explanation: PHP concatenates strings with the . operator; + is arithmetic addition.

6. **Which of the following function returns the number of characters in a string variable?** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*  
   a. count($variable)  
   b. len($variable)  
   c. strlen($variable)  
   d. strcount($variable)

   answer: c — strlen($variable)  
   explanation: strlen() returns the number of bytes (characters) in a string.

7. **PHP is widely used ________ scripting language that is especially suited for web development and can be embedded into html.** *[Bangladesh Bank Assistant Programmer 2011 compact it 273 (ET: N/A)]*  
   a. Open source general purpose  
   b. Proprietary general purpose  
   c. Open source special purpose  
   c. Proprietary special purpose

   answer: a — Open source general purpose  
   explanation: PHP is free and open source, is general purpose, and its code can be written directly inside HTML.

8. **Which of the following is not true?** *[Bangladesh Bank Assistant Programmer 2011 compact it 273 (ET: N/A)]*  
   a. PHP can be used develop applications  
   b. PHP makes a website dynamic  
   c. PHP applications cannot be compiled  
   d. PHP cannot be embedded into html

   answer: d — PHP cannot be embedded into html  
   explanation: PHP is designed to be embedded in HTML using <?php ... ?>, so this statement is false.

9. **How do you write a conditional statement for executing some statements only if "1" is not equal to 5?** *[Bangladesh Bank Assistant Programmer 2011 compact it 273 (ET: N/A)]*  
   a. if(1<>5)  
   b. if(1!=5)  
   c. if(1=!5)  
   d. if<>5

   answer: b — if(1!=5)  
   explanation: PHP uses != for "not equal"; <> also works but != is the standard form, and =! is not an operator.

## Scripting & JavaScript (8)

1. **Where can JavaScript code be placed in an html page?** *[Combined Bank Maintenance Engineer 2018 compact it 228 (ET: N/A)]*  
   A) <head>  
   B) <body>  
   C) both A and B  
   D) none

   answer: C — both A and B  
   explanation: A <script> block is valid in the head or the body, and can also be loaded from an external file.

2. **What is the value of variable x after the following statement is executed in JavaScript var x2= "3" + "4" ?** *[Combined Bank Maintenance Engineer 2018 compact it 228 (ET: N/A)]*  
   A) 34  
   B) 7  
   C) 0  
   D) undefine

   answer: A — 34  
   explanation: The + operator on two strings concatenates them, giving the string "34" rather than the number 7.

3. **Which is correct to open new window/tab of browser?** *[Bangladesh Bank Assistant Programmer 2016 compact it 244 (ET: N/A)]*  
   A) <a href=[http://www.example.com](http://www.example.com) target= "_blank"> new window/tab</a>  
   B) <a href=[http://www.example.com](http://www.example.com) target= "blank"> new window/tab</a>  
   C) <a href=[http://www.example.com](http://www.example.com) target= "_blank“new window”> new window</a>  
   D) None

   answer: A — <a href=http://www.example.com target= "_blank"> new window/tab</a>  
   explanation: target="_blank" tells the browser to open the link in a new tab or window; the underscore is required.

4. **Which is the correct variable declaration in JavaScript?** *[Bangladesh Bank Assistant Programmer 2016 compact it 244 (ET: N/A)]*  
   A) var a= {'a', 'b', 'c'};  
   B) var a= {'a' 'b' 'c'}  
   C) var a= {“a” “b” “c”}  
   D) None

   answer: D — None  
   explanation: Braces build an object of key:value pairs, so a list of bare values is invalid — an array needs square brackets, as in var a = ['a','b','c'].

5. **Which one does run on client side?** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 258 (ET: N/A)]*  
   A) PHP  
   B) JavaScript  
   C) ASP.NET  
   D) None of these

   answer: B — JavaScript  
   explanation: JavaScript runs inside the browser; PHP and ASP.NET execute on the server.

6. **A script is a ________** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*  
   a. Program of sequence of instructions that is interpreted or carried out by processes directly  
   b. Program or sequence of instructions that is interpreted or carried out by another program  
   c. Program or sequence of instructions that is interpreted or carried out by web services only  
   d. None of these

   answer: b — Program or sequence of instructions that is interpreted or carried out by another program  
   explanation: A script is not compiled to machine code — an interpreter or host program reads and executes it.

7. **What is the correct JavaScript syntax to view "Hello World"?** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*  
   a. respone.write("Hellow World");  
   b. document.write("Hello World")  
   c. "Hello World"  
   d. echo("Hello World")

   answer: b — document.write("Hello World")  
   explanation: document.write outputs text into the page; echo is PHP and response.write is ASP.

8. **Inside which HTML element do we put the JavaScript?** *[Bangladesh Bank Assistant Programmer 2011 compact it 273 (ET: N/A)]*  
   a. <scripting>  
   b. <javascript>  
   c. <script>  
   d. <js>

   answer: c — <script>  
   explanation: JavaScript is placed inside a <script> element.

## Web Services & APIs (6)

1. **Between a client and a web server, which of the following used for inspecting the data that is sent from the client to the web server and blocking attacks such as SQL injection?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 100 (ET: N/A)]*  
   (a) Cluster configuration  
   (b) Load balancing function  
   (c) SSL-VPN function  
   (d) WAF

   answer: d — WAF  
   explanation: A Web Application Firewall inspects HTTP traffic at the application layer and blocks SQL injection, XSS and similar attacks.

2. **Which one of the following statements with respect to REST API is false?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 102 (ET: N/A)]*  
   (a) A REST API would use a GET request to retrieve a record  
   (b) A REST API would use a DELETE request to delete a record  
   (c) The operations in a REST API can be called from any HTTP client  
   (d) None of the above statements is false

   answer: d — None of the above statements is false  
   explanation: REST uses GET to read, DELETE to remove, and works over plain HTTP so any HTTP client can call it — all three statements are true.

3. **Which is the lightweight message format?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 168 (ET: N/A)]*  
   a) XML  
   b) JSON  
   c) SQL  
   d) HTML

   answer: b — JSON  
   explanation: JSON carries data as simple key-value text with far less markup overhead than XML.

4. **Which one is modern light weight message exchange format?** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 215 (ET: AUST)]*  
   A) JSON  
   B) XML  
   C) MX  
   D) HTML

   answer: A — JSON  
   explanation: JSON is the compact, human-readable format used for modern data exchange.

5. **Which one is modern lightweight message exchange format?** *[Combined Bank Maintenance Engineer 2018 compact it 224 (ET: N/A)]*  
   A) JSON  
   B) MX  
   C) HTML  
   D) XML

   answer: A — JSON  
   explanation: JavaScript Object Notation is lightweight, easy to parse and widely used by web APIs.

6. **Which one is modern lightweight message exchange format?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 246 (ET: N/A)]*  
   A) XM  
   B) MX  
   C) HTML  
   D) JSON (JavaScript Object Notation)

   answer: D — JSON (JavaScript Object Notation)  
   explanation: JSON is the modern lightweight data interchange format.

## Full Stack & Web Servers (5)

1. **Which of the following is not a web server?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xix (ET: DU)]*  
   (a) Apache tomcat  
   (b) PHP  
   (c) Jetty  
   (d) Tornado

   answer: b — PHP  
   explanation: PHP is a server-side scripting language that runs inside a web server; Tomcat, Jetty and Tornado are servers themselves.

2. **What is invoked via HTTP on the Web server computer when it responds to requests from a user's Web browser?** *[Sonali and Janata Bank Assistant Database Administrator 25-09-2021 compact it 116 (ET: N/A)]*  
   a) A Java application  
   b) A Java applet  
   c) A Java servlet  
   d) None of the above is correct

   answer: c — A Java servlet  
   explanation: A servlet runs inside the server's container and generates the HTTP response; an applet would run in the browser.

3. **Word Press can be called as ________** *[BREB Assistant General Manager (IT) 2016 compact it 256 (ET: N/A)]*  
   A) Static website  
   B) Dynamic website  
   C) Content Managed website  
   D) E-Commerce website

   answer: C — Content Managed website  
   explanation: WordPress is a content management system, so pages are created and edited through its admin interface.

4. **What type of system is Cisco mail platform?** *[Pubali Bank Limited Officer (IT) 2012 compact it 267 (ET: N/A)]*  
   a. Linux  
   b. MAC  
   c. Windows  
   d. Atari

   answer: a — Linux  
   explanation: Cisco's mail and messaging platforms run on a hardened Linux-based appliance operating system.

5. **Where the application server is installed for the web server?** *[Pubali Bank Limited Officer (IT) 2012 compact it 269 (ET: N/A)]*  
   a. Cisco MCS with cisco-based Windows operating system  
   b. Cisco MCS with cisco-based Unix operating system  
   c. Cisco MCS with cisco-based Linux operating system  
   d. Cisco MCS with cisco-based MAC operating system

   answer: c — Cisco MCS with cisco-based Linux operating system  
   explanation: The Cisco Media Convergence Server runs Cisco's own Linux-based appliance OS for its application servers.

## HTTP & Status Codes (5)

1. **What does HTTP Status Code 500 indicate?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xx (ET: DU)]*  
   (a) Bad Request  
   (b) Unauthorized Access  
   (c) Internal Server Error  
   (d) Not Found

   answer: c — Internal Server Error  
   explanation: 5xx codes mean the server failed; 500 is the generic internal server error, while 400 is Bad Request, 401 Unauthorized and 404 Not Found.

2. **When we browse internet, browser store some data in the computer. We are talking about-** *[DESCO Assistant Engineer (CSE) 2016 compact it 257 (ET: N/A)]*  
   a. Session  
   b. File  
   c. Memory  
   d. Cookie

   answer: d — Cookie  
   explanation: A cookie is a small text file the site stores on the client so it can recognise the user on later visits.

3. **While browsing, internet browser stores some data in the computer. Which is called by?** *[BREB Assistant General Manager (IT) 2016 compact it 255 (ET: N/A)]*  
   A) Session  
   B) File  
   C) Memory  
   D) Cookie

   answer: D — Cookie  
   explanation: Cookies hold session and preference data on the visitor's own machine.

4. **Programs that is automatically loaded and operates as a part of browser ----** *[BREB Assistant General Manager (IT) 2016 compact it 256 (ET: N/A)]*  
   A) Plug in  
   B) Add ones  
   C) Widgets  
   D) Utilities

   answer: A — Plug in  
   explanation: A plug-in loads with the browser and extends it to handle content the browser cannot render on its own.

5. **Which of the following statements is true regarding Cookies?** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 258 (ET: N/A)]*  
   A) It is stored in web-client  
   B) It is stored in server  
   C) Each browsing time cookies become reset  
   D) It is client-side program

   answer: A — It is stored in web-client  
   explanation: Cookies are saved on the user's own machine by the browser and sent back to the server with each request; they are data, not programs.

## CSS & Styling (1)

1. **Which CSS property is used to set the thickness or boldness of the text?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 7 (ET: BIBM)]*  
   a) font-size  
   b) font-style  
   c) font-weight  
   d) font-family

   answer: c — font-weight  
   explanation: font-weight sets how bold the text is, taking values such as normal, bold or 100 to 900.
