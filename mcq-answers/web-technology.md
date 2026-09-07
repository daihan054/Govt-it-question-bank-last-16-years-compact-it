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
answer: D
explanation: `<html>` হলো যেকোনো HTML ডকুমেন্টের রুট বা শীর্ষস্থানীয় কন্টেইনার ট্যাগ, যার ভেতর `<head>` ও `<body>` সহ অন্যান্য সমস্ত ট্যাগ অন্তর্ভুক্ত থাকে।

2. **How to create an unordered list (a list with the list items in bullets) in HTML?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 6 (ET: BIBM)]*
   a) <ul>
   b) <ol>
   c) <li>
   d) <i>
answer: A
explanation: HTML-এ বুলেট পয়েন্টযুক্ত আনঅর্ডারড লিস্ট তৈরি করতে `<ul>` (Unordered List) ট্যাগ ব্যবহৃত হয় (এবং প্রতিটি আইটেমের জন্য `<li>` ব্যবহৃত হয়)।

3. **What is the popular way to linking many documents?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*
   **Ans:** hyperlink
answer: Hyperlink
explanation: ওয়েবে একাধিক ডকুমেন্ট বা ওয়েব পেজকে পরস্পরের সাথে সংযুক্ত করার প্রধান এবং সর্বজনীন মাধ্যম হলো হাইপারলিংক (`<a>` ট্যাগ)।

4. **URL stands for–** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 130 (ET: N/A)]*
   a) Universal Resource Locator
   b) Uniform Resource Locator
   c) Unique Resource Locator
   d) None
answer: B
explanation: URL-এর পূর্ণরূপ হলো Uniform Resource Locator, যা ওয়ার্ল্ড ওয়াইড ওয়েবে কোনো সুনির্দিষ্ট রিসোর্সের গ্লোবাল ঠিকানা নির্দেশ করে।

5. **XSLT processors evaluate each statement in the context of the match that has been made. That is, XSLT processors are:** *[Sonali and Janata Bank Assistant Database Administrator 25-09-2021 compact it 113 (ET: N/A)]*
   a) Context oriented
   b) Procedural oriented
   c) Object oriented
   d) Relational oriented
answer: A
explanation: XSLT প্রসেসরগুলো কনটেক্সট-ওরিয়েন্টেড (Context oriented), কারণ প্রতিটি টেমপ্লেট রুল XML ট্রি কাঠামোর বর্তমান ম্যাচকৃত নোড বা কনটেক্সট (context node)-এর ওপর ভিত্তি করে মূল্যায়িত হয়।

6. **Suppose you are using an HTML browser at a client machine C to access a static HTML webpage hosted in a HTTP server S. The page contains exactly one static embedded image which also resides at S. Assuming no web caching which of the following is correct when you load the webpage along with the embedded image?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 85 (ET: N/A)], [Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 183 (ET: N/A)]*
   a. C need to send at least 2 HTTP requests to S using two different TCP connection.
   b. C need to send at least 2 HTTP requests to S but a single TCP connection is sufficient.
   c. A single HTTP request is sufficient without using any TCP connection from C to S.
   d. A single HTTP request is sufficient using a single TCP connection from C to S.
answer: B
explanation: HTTP/1.1 স্ট্যান্ডার্ডে পারসিস্টেন্ট কানেকশন (Persistent Connection) ব্যবহৃত হওয়ায় একটি একক TCP কানেকশন বজায় রেখেই ক্লায়েন্ট পরপর ২টি আলাদা HTTP GET রিকোয়েস্ট (HTML পেজ ও ছবির জন্য) পাঠাতে পারে।

7. **Which one is the first search engine?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 160 (ET: N/A)]*
   A) Google
   B) Archie
   C) Alta vista
   D) WAIS
answer: B
explanation: ১৯৯০ সালে অ্যালান এমটেজ (Alan Emtage) কর্তৃক উদ্ভাবিত 'Archie' হলো ইন্টারনেটের সর্বপ্রথম সার্চ ইঞ্জিন।

8. **The newest version of HTML is:** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 161 (ET: N/A)]*
   A) WML
   B) HTML5
   C) XSL
   D) HTML3
answer: B
explanation: HTML-এর সর্বাধুনিক ও পঞ্চম সংস্করণ হলো HTML5, যাতে সমৃদ্ধ মাল্টিমিডিয়া, সিম্যান্টিক ট্যাগ এবং আধুনিক ওয়েব এপিআই সমর্থন অন্তর্ভুক্ত রয়েছে।

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
answer: A
explanation: ওয়েব ব্রাউজারের কার্যপ্রণালীর সঠিক ক্রম হলো: ১. DNS রেজোলিউশন (A4) -> ২. সার্ভারের সাথে TCP হ্যান্ডশেক ও সংযোগ (A2) -> ৩. HTTP রিকোয়েস্ট প্রেরণ (A1) -> ৪. সার্ভার থেকে HTTP পেজ রেসপন্স গ্রহণ (A3)।

10. **Which HTML attribute is used to hide characters of an input password?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 156 (ET: DU)]*
   a) href
   b) type
   c) tyle
   d) src
answer: B
explanation: `<input>` ট্যাগে `type="password"` অ্যাট্রিবিউট ব্যবহারের মাধ্যমে ইনপুটকৃত পাসওয়ার্ডের অক্ষরগুলো মাস্ক (ডট বা অ্যাস্টেরিস্ক) করে গোপন রাখা হয়।

11. **Which of the followings is not a built-in HTML tag?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 157 (ET: DU)]*
   a) <script>
   b) <form>
   c) <html>
   d) All of these are valid built-in HTML tags
answer: D
explanation: `<script>`, `<form>` এবং `<html>`—এর প্রতিটিই স্ট্যান্ডার্ড ও বিল্ট-ইন HTML ট্যাগ।

12. **Which of the following converts the documents written by HTML?** *[BTRC Sub-Assistant Director (Technical) 2019 compact it 201 (ET: IBA)]*
   A. Browser
   B. FTP
   C. HTPP
   D. Web
answer: A
explanation: ওয়েব ব্রাউজার (Browser) HTML ডকুমেন্টের ট্যাগ ও কোড অনুবাদ (রেন্ডার) করে মানুষের পাঠযোগ্য ইন্টারফেসে প্রদর্শন করে।

13. **A nonstandard HTML extension that causes scrolling text to appear as pan of a Web page is-** *[Combined Bank Senior Officer (IT) 2018 compact it 221 (ET: DU)]*
   A) DHCP
   B) mask off
   C) Dhrystone
   D) marquee
answer: D
explanation: `<marquee>` ট্যাগ ব্যবহারের মাধ্যমে ওয়েব পেজে অনুভূমিক বা উল্লম্বভাবে টেক্সট/ইমেজ স্ক্রোল করানো হয়।

14. **Which of the following tags is used to create a paragraph in HTML?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 250 (ET: N/A)]*
   A) <para>content</para>
   B) <cont>para</cont>
   C) <p> content</p>
   D) <body>content</body>
answer: C
explanation: HTML-এ অনুচ্ছেদ বা প্যারাগ্রাফ তৈরি করতে `<p>` ট্যাগ ব্যবহার করা হয়।

15. **One advantage of XML compared to HTML is ________** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*
   a. XML works on more platforms
   b. XML is suited to using webpage as frontend to database
   c. XML was designed for portable phone
   d. XML is simpler to learn than html
answer: B
explanation: XML ডেটা উপস্থাপন ও পরিবহনের জন্য ডেটা-সেন্ট্রিক কাঠামোগত ফরম্যাট প্রদান করে, যা ডেটাবেজের ব্যাকএন্ড ও ওয়েব ফ্রন্টএন্ডের মধ্যে ডেটা আদান-প্রদানে চমৎকার সহায়তা করে।

## PHP & Server-Side (9)

1. **Which is not a valid variable name in PHP?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 6 (ET: BIBM)]*
   a) age
   b) _age
   c) PersonAge
   d) 1age
answer: D
explanation: PHP-তে ভেরিয়েবলের নাম অবশ্যই ডলার চিহ্নের (`$`) পর কোনো বর্ণ (letter) বা আন্ডারস্কোর (`_`) দিয়ে শুরু হতে হয়; কোনো সংখ্যা (digit) দিয়ে শুরু হতে পারে না (`$1age` অবৈধ)।

2. **Which of the followings is a Web Framework built with PHP?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 153 (ET: DU)]*
   a) Laravel
   b) Django
   c) MVC
   d) Spring
answer: A
explanation: Laravel হলো PHP-তে নির্মিত একটি ওপেন সোর্স ওয়েব অ্যাপ্লিকেশন ফ্রেমওয়ার্ক (Django হলো Python এবং Spring হলো Java ফ্রেমওয়ার্ক)।

3. **What will be the output of the following PHP code? <?php "Hello World" ?>** *[Probashi Kallyan Bank Programmer: 2019 compact it 211 (ET: AUST)]*
   A) Error
   B) Hello World
   C) Nothing
   D) None of this
answer: C
explanation: কোডটিতে কোনো `echo` বা `print` স্টেটমেন্ট না থাকায় ব্রাউজারে কোনো আউটপুট প্রদর্শিত হবে না (Nothing)।

   **What is the output of the code shown?**
   `%(qty)d more %(food)s'%{'qty':1,'food':'spam'}` *[Probashi Kallyan Bank Programmer: 2019 compact it 211 (ET: AUST)]*
   A) Error
   B) 1 more spam
   C) No output
   D) 1 more foods
answer: B
explanation: পাইথনের স্ট্রিং ইন্টারপোলেশনে ডিকশনারির কী 'qty' এর মান 1 এবং 'food' এর মান 'spam' প্রতিস্থাপিত হয়ে আউটপুট হবে "1 more spam"।

4. **Which is correct for concatenation in PHP?** *[Bangladesh Bank Assistant Programmer 2016 compact it 244 (ET: N/A)]*
   A) $add = Sadd+1
   B) $add = $add +1
   C) $add = $add + Sadd
   D) $add. = +1;
answer: D
explanation: PHP-তে স্ট্রিং কনক্যাটেনেশন অ্যাসাইনমেন্ট অপারেটর হিসেবে `.=` ব্যবহৃত হয় (ডট `.` হলো মৌলিক কনক্যাটেনেশন অপারেটর)।

5. **Which is used for adding two or more string in PHP?** *[Bangladesh Bank Assistant Programmer 2016 compact it 244 (ET: N/A)]*
   A) +
   B) *
   C) . (dot)
   D) |
answer: C
explanation: PHP-তে একাধিক স্ট্রিং জোড়া লাগানোর জন্য ডট (`.`) অপারেটর ব্যবহার করা হয় (`+` অপারেটর গাণিতিক যোগের জন্য সংরক্ষিত)।

6. **Which of the following function returns the number of characters in a string variable?** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*
   a. count($variable)
   b. len($variable)
   c. strlen($variable)
   d. strcount($variable)
answer: C
explanation: PHP-তে কোনো স্ট্রিং ভেরিয়েবলের মোট ক্যারেক্টার সংখ্যা (দৈর্ঘ্য) জানার জন্য `strlen()` ফাংশন ব্যবহৃত হয়।

7. **PHP is widely used ________ scripting language that is especially suited for web development and can be embedded into html.** *[Bangladesh Bank Assistant Programmer 2011 compact it 273 (ET: N/A)]*
   a. Open source general purpose
   b. Proprietary general purpose
   c. Open source special purpose
   c. Proprietary special purpose
answer: A
explanation: PHP-এর প্রমিত সংজ্ঞা অনুযায়ী এটি একটি বহুল ব্যবহৃত "Open source general purpose" সার্ভার-সাইড স্ক্রিপ্টিং ভাষা যা সহজে HTML-এর সাথে সংযুক্ত করা যায়।

8. **Which of the following is not true?** *[Bangladesh Bank Assistant Programmer 2011 compact it 273 (ET: N/A)]*
   a. PHP can be used develop applications
   b. PHP makes a website dynamic
   c. PHP applications cannot be compiled
   d. PHP cannot be embedded into html
answer: D
explanation: PHP সরাসরি HTML ট্যাগের ভেতর `<?php ... ?>` কোড ব্লকের মাধ্যমে এমবেড করা যায়; অতএব "PHP cannot be embedded into html" বক্তব্যটি অসত্য।

9. **How do you write a conditional statement for executing some statements only if "1" is not equal to 5?** *[Bangladesh Bank Assistant Programmer 2011 compact it 273 (ET: N/A)]*
   a. if(1<>5)
   b. if(1!=5)
   c. if(1=!5)
   d. if<>5
answer: B
explanation: PHP-তে নট-ইকুয়াল বা অসমান শর্ত যাচাই করার স্ট্যান্ডার্ড সিনট্যাক্স হলো `if (1 != 5)`।

## Scripting & JavaScript (8)

1. **Where can JavaScript code be placed in an html page?** *[Combined Bank Maintenance Engineer 2018 compact it 228 (ET: N/A)]*
   A) <head>
   B) <body>
   C) both A and B
   D) none
answer: C
explanation: জাভাস্ক্রিপ্ট কোড HTML ফাইলের `<head>` সেকশন অথবা `<body>` সেকশন (বা উভয় স্থানেই) `<script>` ট্যাগের মাধ্যমে স্থাপন করা যায়।

2. **What is the value of variable x after the following statement is executed in JavaScript var x2= "3" + "4" ?** *[Combined Bank Maintenance Engineer 2018 compact it 228 (ET: N/A)]*
   A) 34
   B) 7
   C) 0
   D) undefine
answer: A
explanation: জাভাস্ক্রিপ্টে দুটি স্ট্রিংয়ের মাঝে `+` অপারেটর ব্যবহার করলে স্ট্রিং কনক্যাটেনেশন (string concatenation) ঘটে, ফলে `"3" + "4"` এর মান হবে `"34"`।

3. **Which is correct to open new window/tab of browser?** *[Bangladesh Bank Assistant Programmer 2016 compact it 244 (ET: N/A)]*
   A) <a href=[http://www.example.com](http://www.example.com) target= "_blank"> new window/tab</a>
   B) <a href=[http://www.example.com](http://www.example.com) target= "blank"> new window/tab</a>
   C) <a href=[http://www.example.com](http://www.example.com) target= "_blank“new window”> new window</a>
   D) None
answer: A
explanation: ব্রাউজারের নতুন উইন্ডো বা ট্যাবে হাইপারলিংক খোলার জন্য HTML-এ `target="_blank"` অ্যাট্রিবিউট ব্যবহার করা হয়।

4. **Which is the correct variable declaration in JavaScript?** *[Bangladesh Bank Assistant Programmer 2016 compact it 244 (ET: N/A)]*
   A) var a= {'a', 'b', 'c'};
   B) var a= {'a' 'b' 'c'}
   C) var a= {“a” “b” “c”}
   D) None
answer: D
explanation: জাভাস্ক্রিপ্টে অ্যারে ঘোষণার জন্য স্কয়ার ব্র্যাকেট `['a', 'b', 'c']` এবং অবজেক্টের জন্য কী-ভ্যালু পেয়ার `{key: value}` প্রয়োজন; সেকেন্ড ব্র্যাকেটে কমা দিয়ে উপাদানের তালিকা কোনো বৈধ সিনট্যাক্স নয়, তাই সঠিক উত্তর None।

5. **Which one does run on client side?** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 258 (ET: N/A)]*
   A) PHP
   B) JavaScript
   C) ASP.NET
   D) None of these
answer: B
explanation: জাভাস্ক্রিপ্ট (JavaScript) ক্লায়েন্ট-সাইড প্রযুক্তি হিসেবে সরাসরি ব্যবহারকারীর ওয়েব ব্রাউজারে রান হয় (PHP এবং ASP.NET হলো সার্ভার-সাইড প্রযুক্তি)।

6. **A script is a ________** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*
   a. Program of sequence of instructions that is interpreted or carried out by processes directly
   b. Program or sequence of instructions that is interpreted or carried out by another program
   c. Program or sequence of instructions that is interpreted or carried out by web services only
   d. None of these
answer: B
explanation: স্ক্রিপ্ট হলো এমন নির্দেশাবলীর ধারা যা কম্পিউটার প্রসেসর কর্তৃক সরাসরি এক্সিকিউট না হয়ে অন্য কোনো প্রোগ্রাম বা ইন্টারপ্রেটার (যেমন জাভাস্ক্রিপ্ট ইঞ্জিন) দ্বারা মূল্যায়িত ও কার্যকর হয়।

7. **What is the correct JavaScript syntax to view "Hello World"?** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*
   a. respone.write("Hellow World");
   b. document.write("Hello World")
   c. "Hello World"
   d. echo("Hello World")
answer: B
explanation: ওয়েব ডকুমেন্টে কোনো টেক্সট সরাসরি রাইট বা প্রদর্শন করতে ক্লাসিক জাভাস্ক্রিপ্টে `document.write("Hello World")` ব্যবহৃত হয়।

8. **Inside which HTML element do we put the JavaScript?** *[Bangladesh Bank Assistant Programmer 2011 compact it 273 (ET: N/A)]*
   a. <scripting>
   b. <javascript>
   c. <script>
   d. <js>
answer: C
explanation: HTML ডকুমেন্টের অভ্যন্তরে জাভাস্ক্রিপ্ট কোড লিখতে `<script>` এলিমেন্ট/ট্যাগ ব্যবহার করা হয়।

## Web Services & APIs (6)

1. **Between a client and a web server, which of the following used for inspecting the data that is sent from the client to the web server and blocking attacks such as SQL injection?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 100 (ET: N/A)]*
   (a) Cluster configuration
   (b) Load balancing function
   (c) SSL-VPN function
   (d) WAF
answer: D
explanation: WAF (Web Application Firewall) হলো একটি বিশেষায়িত সিকিউরিটি মেকানিজম যা ক্লায়েন্ট ও ওয়েব সার্ভারের মধ্যবর্তী অ্যাপ্লিকেশন লেয়ার (Layer 7) ট্রাফিক পর্যবেক্ষণ করে এবং SQL ইনজেকশন, XSS সহ অন্যান্য ক্ষতিকর আক্রমণ প্রতিহত করে।

2. **Which one of the following statements with respect to REST API is false?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 102 (ET: N/A)]*
   (a) A REST API would use a GET request to retrieve a record
   (b) A REST API would use a DELETE request to delete a record
   (c) The operations in a REST API can be called from any HTTP client
   (d) None of the above statements is false
answer: D
explanation: RESTful স্থাপত্যে ডেটা পড়তে GET, মুছতে DELETE ব্যবহৃত হয় এবং যেকোনো প্রমিত HTTP ক্লায়েন্ট থেকে কল করা যায়; ফলে প্রদত্ত সবগুলো বক্তব্যই সত্য (অর্থাৎ কোনোটিই মিথ্যা নয়)।

3. **Which is the lightweight message format?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 168 (ET: N/A)]*
   a) XML
   b) JSON
   c) SQL
   d) HTML
answer: B
explanation: JSON (JavaScript Object Notation) হলো একটি সুসংগঠিত, টেক্সট-ভিত্তিক এবং লাইটওয়েট (হালকা ও দ্রুত পার্সযোগ্য) ডেটা ইন্টারচেঞ্জ ফরম্যাট।

4. **Which one is modern light weight message exchange format?** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 215 (ET: AUST)]*
   A) JSON
   B) XML
   C) MX
   D) HTML
answer: A
explanation: আধুনিক ওয়েব সার্ভিস ও মোবাইল অ্যাপ্লিকেশন যোগাযোগে এক্সএমএল-এর তুলনায় কম ওভারহেড ও দ্রুত পার্সিংয়ের কারণে JSON সবচেয়ে জনপ্রিয় লাইটওয়েট ফরম্যাট।

5. **Which one is modern lightweight message exchange format?** *[Combined Bank Maintenance Engineer 2018 compact it 224 (ET: N/A)]*
   A) JSON
   B) MX
   C) HTML
   D) XML
answer: A
explanation: আধুনিক ওয়েব প্রযুক্তি ও মাইক্রোসার্ভিসে দ্রুত ও কম ব্যান্ডউইথ খরচে মেসেজ বিনিময়ের প্রমিত ফরম্যাট হলো JSON।

6. **Which one is modern lightweight message exchange format?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 246 (ET: N/A)]*
   A) XM
   B) MX
   C) HTML
   D) JSON (JavaScript Object Notation)
answer: D
explanation: আধুনিক ওয়েব ডেভেলপমেন্ট ও API কমিউনিকেশনে JSON (JavaScript Object Notation) হলো সবচেয়ে জনপ্রিয় ও কার্যকর লাইটওয়েট মেসেজ ফরম্যাট।

## Full Stack & Web Servers (5)

1. **Which of the following is not a web server?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xix (ET: DU)]*
   (a) Apache tomcat
   (b) PHP
   (c) Jetty
   (d) Tornado
answer: B
explanation: PHP হলো একটি সার্ভার-সাইড প্রোগ্রামিং/স্ক্রিপ্টিং ভাষা, কোনো ওয়েব সার্ভার নয় (Apache Tomcat, Jetty ও Tornado হলো ওয়েব ও অ্যাপ্লিকেশন সার্ভার)।

2. **What is invoked via HTTP on the Web server computer when it responds to requests from a user's Web browser?** *[Sonali and Janata Bank Assistant Database Administrator 25-09-2021 compact it 116 (ET: N/A)]*
   a) A Java application
   b) A Java applet
   c) A Java servlet
   d) None of the above is correct
answer: C
explanation: ব্রাউজারের HTTP রিকোয়েস্ট প্রসেস করে ডায়নামিক রেসপন্স তৈরি করতে ওয়েব সার্ভার বা সার্ভলেট কন্টেইনারে জাভা সার্ভলেট (Java servlet) ইনভোক বা কার্যকর হয় (অ্যাপলেট ক্লায়েন্ট ব্রাউজারে চলত)।

3. **Word Press can be called as ________** *[BREB Assistant General Manager (IT) 2016 compact it 256 (ET: N/A)]*
   A) Static website
   B) Dynamic website
   C) Content Managed website
   D) E-Commerce website
answer: C
explanation: ওয়ার্ডপ্রেস (WordPress) মূলত একটি অত্যন্ত জনপ্রিয় কনটেন্ট ম্যানেজমেন্ট সিস্টেম (CMS), যা দিয়ে পরিচালিত ওয়েবসাইটগুলোকে Content Managed website বলা হয়।

4. **What type of system is Cisco mail platform?** *[Pubali Bank Limited Officer (IT) 2012 compact it 267 (ET: N/A)]*
   a. Linux
   b. MAC
   c. Windows
   d. Atari
answer: A
explanation: সিসকো মেইল প্ল্যাটফর্ম বা সিকিউর ইমেইল গেটওয়ে লিনাক্স/ইউনিক্স কার্নেল-ভিত্তিক বিশেষায়িত প্ল্যাটফর্মের ওপর পরিচালিত হয়।

5. **Where the application server is installed for the web server?** *[Pubali Bank Limited Officer (IT) 2012 compact it 269 (ET: N/A)]*
   a. Cisco MCS with cisco-based Windows operating system
   b. Cisco MCS with cisco-based Unix operating system
   c. Cisco MCS with cisco-based Linux operating system
   d. Cisco MCS with cisco-based MAC operating system
answer: C
explanation: সিসকো মিডিয়া কনভারজেন্স সার্ভারে (Cisco MCS) ওয়েব ও অ্যাপ্লিকেশন পরিষেবাগুলো সিসকো-বেসড লিনাক্স অপারেটিং সিস্টেমের (Cisco-based Linux OS) ওপর ইনস্টল ও কনফিগার করা হয়।

## HTTP & Status Codes (5)

1. **What does HTTP Status Code 500 indicate?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xx (ET: DU)]*
   (a) Bad Request
   (b) Unauthorized Access
   (c) Internal Server Error
   (d) Not Found

2. **When we browse internet, browser store some data in the computer. We are talking about-** *[DESCO Assistant Engineer (CSE) 2016 compact it 257 (ET: N/A)]*
   a. Session
   b. File
   c. Memory
   d. Cookie

3. **While browsing, internet browser stores some data in the computer. Which is called by?** *[BREB Assistant General Manager (IT) 2016 compact it 255 (ET: N/A)]*
   A) Session
   B) File
   C) Memory
   D) Cookie

4. **Programs that is automatically loaded and operates as a part of browser ----** *[BREB Assistant General Manager (IT) 2016 compact it 256 (ET: N/A)]*
   A) Plug in
   B) Add ones
   C) Widgets
   D) Utilities

5. **Which of the following statements is true regarding Cookies?** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 258 (ET: N/A)]*
   A) It is stored in web-client
   B) It is stored in server
   C) Each browsing time cookies become reset
   D) It is client-side program

## CSS & Styling (1)

1. **Which CSS property is used to set the thickness or boldness of the text?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 7 (ET: BIBM)]*
   a) font-size
   b) font-style
   c) font-weight
   d) font-family
