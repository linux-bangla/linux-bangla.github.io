---
author: ["Sharafat Karim"]
title: "কিভাবে পোস্ট পাবলিশ করতে হয়?"
date: "2024-12-21"
description: "লিনাক্স বাংলা ব্লগে পোষ্ট পাবলিশ করার সহজ উপায়"
summary: "লিনাক্স বাংলা ব্লগে পোষ্ট পাবলিশ করার সহজ উপায়। নতুন ব্যবহারকারীদের মূলত কথা চিন্তা করেই লেখা হয়েছে নিবন্ধ।"
tags: ["markdown", "syntax", "code", "guide"]
categories: ["github", "guide"]
series: ["Themes Guide"]
cover:
ShowToc: true
TocOpen: true
---

# ভুমিকা

আসসালামু আলাইকুম!

**লিনাক্স বাংলা ব্লগে** আপনাকে স্বাগত' জানাচ্ছি। এই নিবন্ধতে আমাদের এই ব্লগে কিভাবে পোস্ট পাবলিশ করতে হয় সেই আলোচনা টি কিছুটা সহজ করে তুলে ধরার চেষ্টা করা হলো।
আর যারা এর আগেও `hugo` বা কোনো একটি *static site generator* প্ল্যাটফর্ম ব্যবহার করেছেন বা, গিটহাব নিয়ে বেশ ভালো ধারণা রাখেন, তারা ফাইল structure টি একটু
ভালো করে লক্ষ্য করলেই সহজে অনুসরণ করতে পারবেন কোনো গাইডলাইন অনুসরণ ছাড়া।

তাহলে শুরু করা যাক।

সবার বোধগম্যতার জন্য আমি বাংলায় যেসকল শব্দ ব্যবহার করেছি, তার মূল, পারিভাষিক ও সমার্থক শব্দ গুলো কয়েকটি নিচে দেয়া হলো,

| মূল শব্দ | পারিভাষিক বা, বিকল্প শব্দ |
| --- | --- |
| পোস্ট | নিবন্ধ |
| ডাইরেক্টরি | ফোল্ডার |
| অনুলিপি | কপি |
| ঐচ্ছিক | অপশনাল |

# যা যা প্রয়োজন

আপনার সিস্টেমে নিম্নলিখিত টুলগুলো ইন্সটল করা থাকতে হবে,

- git
- hugo (বাধ্যতামূলক নয়)
- পছন্দের যেকোনো একটা টেক্সট এডিটর

> এক্ষেত্রে `hugo` যদি ইন্সটল করা না থাকে, তাহলে আপনি সরাসরি আপনার পোস্ট ওয়েবসাইটে পাবলিশ করার পর দেখতে কেমন হবে সেটা ধরতে পারবেন না, পাবলিশ করা ব্যতীত।

# পরিবেশ তৈরি

শূরুতেই, কাজের জন্য একটা পরিবেশ তৈরি করা যাক,

## ফোর্ক করা

আমাদের মূল গিটহাব রিপোজিটরি থেকে একটা ফোর্ক করতে হবে। আমাদের মূল গিটহাব রিপোজিটরি এখানে পাবেন,

- [লিনাক্স বাংলা ব্লগ](https://github.com/linux-bangla/linux-bangla.github.io)

এখান থেকে একটা ফোর্ক (fork) করে নিবো আমাদের নিজেদের অধীনে (***আপনার_নাম/লিনাক্স-বাংলা-ব্লগ***)।

## ক্লোন করা

আমরা আমাদের ফোর্ক করা রিপোজিটরি থেকে একটা ক্লোন তৈরি করবো। এতে আমাদের পরিবেশে একটা অনুলিপি তৈরি হবে।
আমাদের রিপোজিটরিতে একটা সাব-মোডিউল আছে, তাই ক্লোনের সময় আমরা সাব-মোডিউলটি নিয়ে ক্লোন করবো,

```bash
git clone --recurse-submodules আপনার_নাম/লিনাক্স-বাংলা-ব্লগ
```

# পর্যবেক্ষণ

এবার আমরা একটা নতুন ফোল্ডার পাবো, নিজেদের সিস্টেমে, যেখানে ক্লোন করেছি। যদি আমরা ফোল্ডারটি চালু করি, বেশ কিছু ফাইল ও ফোল্ডার দেখতে পাবো।

```
├── archetypes
├── assets
├── content
├── data
├── .git
├── .gitmodules (ফাইল)
├── .hugo_build.lock (ফাইল)
├── hugo.yaml (ফাইল)
├── i18n
├── layouts
├── public
├── resources
├── static
└── themes
```

> এখানে ফাইল বা ফোল্ডারের সংখ্যা আপনার সিস্টেমে কম বা বেশি হতে পারে। এতে চিন্তার কিছূ নেই।

এখন যদি আপনার সিস্টেমে `hugo` ইন্সটল করা থাকে, তাহলে আপনি এই পরিবেশে একটা লোকাল সার্ভার চালু করতে পারবেন।
একই ফোল্ডারে টার্মিনাল ওপেন করে নিচের কমান্ড টি দিলেই হবে,

```bash
hugo server serve -D
```

> আপনার terminal এর দিকে একটু লক্ষ করুন, যদি না কোনো এরর দেখা যায়।
> তাহলে আপনি আপনার ব্রাউজারে `http://localhost:1313` এ গিয়ে দেখতে পারবেন আপনার সাইট। <br>
> (টার্মিনালের আউটপুটেই দেখতে পারবেন উক্ত লিংক, ক্ষেত্রবিশেষে ভিন্ন হতে পারে)

## যদি কাজ না হয়?

প্রথমত নিশ্চিত করুন, আপনার `themes` ফোল্ডারে আপনার ব্যবহৃত থিমটি আছে কিনা। এটা খুবই গুরুত্বপূর্ণ। তাও কাজ না হলে, আমাদের কমিউনিটির সাথে যোগাযোগ করুন।

# আপনার নিজের একটা ফোল্ডার

## contents ফোল্ডার

চলুন এবার আমরা `content` ফোল্ডারে প্রবেশ করি। এখানে এরকম কিছূ একটা structure লক্ষ করবেন,

```
├── admin
│   ├── code_syntax copy.md
│   ├── emoji-support.md
│   ├── how-to-guide.md
│   ├── _index.md
│   ├── markdown-syntax.md
│   ├── math-typesetting.md
│   └── rich-content.md
├── archives.md
└── search.md
```
> হয়তো আপনি দুটো ফাইল পাবেন, `archives.md` এবং `search.md` এই দুটো ফাইল নিয়ে আমরা কাজ করবো না। আরো কয়েকটি ফোল্ডার দেখতে পারবেন।

> এখানে উপরের স্টাকচারে কেবল একটা ফোল্ডার `admin` দেখতে পাচ্ছি আমরা। আদতে আপনি হয়তো আরো ফোল্ডার দেখতে পারবেন। এখানে প্রতিটি ফোল্ডার হলো এক একটি পরিচিতি।

## নিজেকে যুক্ত করি

এখন আমরা নিজেকে যুক্ত করতে চাই এই সিস্টেমে। তাহলে আমরা মূলত এই `content` এর অধীনে নিজেদের নামে একটা ফোল্ডার তৈরি করে নিবো। তারপর আমাদের যা যা কাজ সব আমরা আমাদের নিজেদের
নামের ফোল্ডারেই করবো, এতে করে আমাদের একজনের কাজের সাথে আরেকজনের কাজের কোনো conflict থাকবে না।

> এই কাজ কেবল একবারই করতে হবে আমাদের। চিন্তার কিছূ নেই।

যেমন, আমার নাম হলো `sharafat`, তাহলে আমি একটা ফোল্ডার তৈরি করবো `sharafat` নামে।

## নিজের একটা প্রোফাইল পেজ (ঐচ্ছিক)

এবার আমাদের তৈরিকৃত এই ফোল্ডারে `_index.md` নামে একটা text file যুক্ত করবো। তারপর আপাতত,
সেই ফাইলে আমরা এইটুকু যুক্ত করবো,

```markdown
---
title: আপনার নাম
summary: আপনার সম্পর্কে সার-সংক্ষেপ
description: একটি ছোট বিবরণ
---
```

> কিন্তু কেনো করলাম এইটুকু? <br>
> সহজ উত্তর, এই ঠিকানায় প্রবেশ করুন <http://localhost:1313/আপনার_নাম/> <br>
> যেমন, আমার ক্ষেত্রে, <http://localhost:1313/sharafat/> এই ঠিকানায় প্রবেশ করলে আমি আমার প্রোফাইল পেজটি দেখতে পাবো।

> যদি আমরা এভাবে `_index.md` তৈরি না করি, কোনো সমস্যা হবে? <br>
> অবশ্যই না! তবে এক্ষেত্রে আপনি আপনার প্রোফাইল পেজ পাবেন না। এটা কেবল একটা ঐচ্ছিক একটা ব্যাপার।

# নিজের প্রথম পোস্ট

পোষ্ট করার ক্ষেত্রে আমরা প্রতিটি নিবন্ধের জন্য আলাদা আলাদা করে ফাইল তৈরি করবো।

উদাহারণস্বরূপ, আমি যদি একটা নতুন নিবন্ধ তৈরি করতে চাই, যেটার শিরোনাম হবে, My First Post, তাহলে `my-first-post.md` নামে একটা ফাইল তৈরি করবো আমাদের নিজেদের নামের ফোল্ডারে।
তাহলে আমাদের ফাইলের structure হবে,

```markdown
├── admin
│   ├── code_syntax copy.md
│   ├── emoji-support.md
│   ├── how-to-guide.md
│   ├── _index.md
│   ├── markdown-syntax.md
│   ├── math-typesetting.md
│   └── rich-content.md
├── archives.md
├── search.md
└── sharafat
    ├── _index.md
    └── my-first-post.md
```

## ফাইলের ভেতর কি কি থাকবে?

### হেডার বা মেটাডাটা

ফাইলের structure এমন হবে, যে, শূরুতে একটা হেডার থাকবে। এই হেডারে আমরা কিছু মেটাডাটা যুক্ত করবো। এই মেটাডাটা হলো আমাদের নিবন্ধের বিষয়ের কিছু মূল তথ্য।

```markdown
---
author: ["আপনার নাম"]
title: "আপনার টপিক"
date: "2024-12-21"
description: "লিনাক্স বাংলা ব্লগে পোষ্ট পাবলিশ করার সহজ উপায়"
summary: "লিনাক্স বাংলা ব্লগে পোষ্ট পাবলিশ করার সহজ উপায়। নতুন ব্যবহারকারীদের মূলত কথা চিন্তা করেই লেখা হয়েছে নিবন্ধ।"
tags: ["markdown", "syntax", "code", "guide"]
categories: ["github", "guide"]
series: ["Themes Guide"]
cover:
ShowToc: true
TocOpen: true
---
```

এখানে `tags` এবং `categories` চয়নের ক্ষেত্রে চাইলে আপনি আমাদের ব্লগের যেসব ট্যাগ ইতিমধ্যে ব্যবহুত হয়েছে সেসব ব্যবহার করলে সব পোস্ট একসাথে সর্ট করা যাবে। আর আপনি ধারাবাহিকভাবে
একাধিক পোস্ট করতে চাইলে `series` এর ক্ষেত্রে আপনি একটা সাধারণ (common) নাম দিতে পারবেন।

> cover এর ক্ষেত্রে আপনি আপনার পোস্টের জন্য একটা ছবি যুক্ত করতে পারবেন thumbnail হিসেবে। এটা একটা অপশনাল ব্যাপার।

> **showToc = true** হলে আপনার পোস্টে একটা টেবিল অফ কন্টেন্ট দেখা যাবে।

> আর **TocOpen = true** হলে টেবিল অফ কন্টেন্ট সব সময় খোলা থাকবে।

### নিবন্ধের মুল অংশ

এখন আমরা আমাদের কাঙ্খিত নিবন্ধ লিখতে পারবো। নিবন্ধে আমরা সাজসজ্জার জন্য মার্কডাউন সিন্টেক্স ব্যবহার করতে পারবো। মার্কডাউন সিন্টেক্স হলো একটা সাধারণ টেক্সট ফরম্যাটিং ভাষা।
খুব সহজেই এটা নতুনরা আয়ত্ত করতে পারবে। এই সিনটেক্সের গাইডলাইন নিয়ে আমাদের কমিউনিটির আরো কিছু পোষ্ট আছে। চাইলে দেখে নিতে পারেন,

- [মার্কডাউন সিন্টেক্স গাইড - মূল কোড রিপোতে পাবেন](https://linux-bangla.github.io/admin/markdown-syntax/)
- [কোড সিন্টেক্স গাইড - মূল কোড রিপোতে পাবেন](https://linux-bangla.github.io/admin/markdown-syntax/)
- [মার্কডাউন সিন্টেক্স গাইড - আমার ব্লগ থেকে](https://sharafat.pages.dev/markdown/)

> আপনি চাইলে অন্যদের দ্বারা লেখা নিবন্ধগুলোর সোর্স কোডও দেখতে পারবেন, এবং অনুপ্রেরণা নিতে পারবেন।

> এবার আপনি আপনার ফাইলটি সেভ করুন, এবং এইটুকুই! আপনার প্রথম পোস্ট তৈরি হয়ে গেছে, আপনাকে অভিনন্দন!

# পোস্ট পাবলিশ করা

## কমিট এবং পুশ

এবার বাকি কাজগুলো হলো আমাদেরকে আমাদের রিপোজিটরিতে একটি কমিট করে আপলোড করা। এটা খুবই সহজ।

```bash
git add .
git commit -m "আপনার মেসেজ"
git push origin main
```

## পুল রিকুয়েস্ট

এবার আমরা আমাদের রিপোজিটরিতে একটি পুল রিকুয়েস্ট করবো। পুল রিকোয়েস্ট টা হবে, আমাদের ফোর্ক করা রিপোজটিরে থেকে, লিনাক্স বাংলা ব্লগের মূল রিপোজিটরিতে!

# সমাপ্তি

এতোক্ষণ ধরে ধৈর্যধারণ করে লেখাগুলো পড়ার জন্য আপনাকে ধণ্যবাদ। যেকোনো স্টেপ এ গিয়ে, কোনো সমস্যার সম্মুক্ষীণ হলে, আমাদের কমিউনিটির সাথে নিশ্চিন্তে যোগাযোগ করতে পারবেন।

> উপরোক্ত লেখাটি এখনো অসম্পূর্ণ! আপনি চাইলেই অবদান রাখতে পারেন, এতে আমরা ঢের খুশি হবো।