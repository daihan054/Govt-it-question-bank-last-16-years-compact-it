# Coaching Class Lecture Analysis & Question Search Prompt

## ১. ব্যবহারকারীর রেডি প্রম্পট (User Copy-Paste Prompt)
নতুন কোনো ক্লাসের নোট বা ছবি দেওয়ার সময় নিচের প্রম্পটটি ব্যবহার করুন:

```text
Class notes / images pore prothome chat box-e details-e bolbe sir ki ki poraise (Topic and Subtopic breakdown).
Tarpor ei porar shathe "all-questions" folder-er written ebong mcq file-gular kon kon subtopic common sheta question count shoho chat box-ei list kore dekhabe.
Eigula chat box-e dekhanor por tumi amar permission / OK-er wait korbe.
Ami permission dile tumi "Nipu bhai important topics" folder-er written.md ebong mcq.md update korbe (ekhane 2-column table akare boshbe ebong subtopic question count descending order-e sort thakbe) ebong update seshe nij thekei Git commit ebong push kore dibe.
```

---

## ২. এআই অ্যাসিস্ট্যান্টের কার্যপ্রণালী (Step-by-Step AI Execution Workflow)

### ধাপ ১: লেকচার বিশ্লেষণ ও চ্যাটবক্সে বিস্তারিত উপস্থাপন
- ব্যবহারকারীর দেওয়া ইমেজ বা নোট থেকে টেক্সট ও কনসেপ্ট উদ্ধার করা।
- চ্যাটবক্সে প্রতিটি টপিক ও সাবটপিক পরিষ্কার ও বিস্তারিতভাবে তুলে ধরা:
  - `Topic: <টপিকের নাম>`
  - `Subtopic: <স্যার ক্লাসে কী পড়িয়েছেন এবং মূল টেকনিক্যাল পয়েন্টের সারসংক্ষেপ>`

### ধাপ ২: কমন সাবটপিক নির্ধারণ ও চ্যাটবক্সে প্রদর্শন
- `all-questions/written/` এবং `all-questions/mcq/` থেকে স্যারের পড়ানো বিষয়ের সাথে হুবহু মিল থাকা সাবটপিকগুলো খুঁজে বের করা।
- অপ্রাসঙ্গিক বা ক্লাসে না পড়ানো কোনো সাবটপিক (যেমন: জটিল ম্যাথ বা অপঠিত অংশ) বাদ রাখা।
- চ্যাটবক্সেই লিখিত ও এমসিকিউ সাবটপিকগুলোর তালিকা প্রশ্নসংখ্যার ভিত্তিতে বড় থেকে ছোট (Descending) সাজিয়ে উপস্থাপন করা:
  - **Written Subtopics (Count Descending)**
  - **MCQ Subtopics (Count Descending)**

### ধাপ ৩: ব্যবহারকারীর অনুমতির অপেক্ষা (Crucial Step)
- চ্যাটবক্সে সম্পূর্ণ বিশ্লেষণ দেওয়ার পর **ফাইলে কোনো কিছু না লিখে ব্যবহারকারীর মতামতের জন্য অপেক্ষা করা**।
- প্রম্পট: *"এই সাবটপিকগুলো কি চূড়ান্ত করবো? আপনার অনুমতি পেলে 'Nipu bhai important topics' ফোল্ডারের ফাইলগুলো আপডেট করবো।"*

### ধাপ ৪: অনুমতি পাওয়ার পর ফাইল আপডেট
- ব্যবহারকারী "OK", "হাঁ", "করো" বা অনুমতি দিলে তবেই ফাইল আপডেট করা:
  1. `Nipu bhai important topics/written.md`
  2. `Nipu bhai important topics/mcq.md`
- **টেবিল ফরম্যাট নিয়ম:**
  - ২ কলামের টেবিল হবে: `| File Name | Subtopic |`
  - কোনো ফাইলের প্রথম সারিতে ফাইলের নাম থাকবে, পরবর্তী সারিগুলোতে ফাইলের ঘরের অংশ ফাঁকা থাকবে।
  - সাবটপিকগুলো ব্র্যাকেটের ভেতরের প্রশ্নসংখ্যা অনুযায়ী বড় থেকে ছোট (Descending) ক্রমানুসারে সাজানো থাকতে হবে।

### ধাপ ৫: স্বয়ংক্রিয় গিট কমিট ও পুশ (Automatic Git Commit & Push)
- ফাইল আপডেট সম্পন্ন হওয়ামাত্রই ব্যবহারকারীকে আলাদাভাবে না বলতে বলে অ্যাসিস্ট্যান্ট স্বয়ংক্রিয়ভাবে Git commit ও push করবে:
  1. পরিবর্তিত ফাইল স্টেজ করা: `git add "Nipu bhai important topics/written.md" "Nipu bhai important topics/mcq.md"`
  2. প্রাসঙ্গিক ও অর্থপূর্ণ কমিট মেসেজ দেওয়া: `git commit -m "Add <Topic/Class Name> subtopics to Nipu bhai important topics"`
  3. রিমোট রিপোজিটরিতে পুশ করা: `git push origin main`
- পুশ সফল হলে কমিট হ্যাশ ও স্ট্যাটাস ব্যবহারকারীকে চ্যাটবক্সে জানিয়ে দেওয়া।
