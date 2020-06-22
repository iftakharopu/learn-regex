<p align="center">
    <br/>
    <a href="https://github.com/ziishaned/learn-regex">
        <img src="https://i.imgur.com/bYwl7Vf.png" alt="Learn Regex">
    </a>
    <br /><br />
    <p>
        <a href="https://twitter.com/ziishaned">
            <img src="https://img.shields.io/twitter/follow/ziishaned.svg?style=social" />
        </a>
        <a href="https://github.com/ziishaned">
            <img src="https://img.shields.io/github/followers/ziishaned.svg?label=Follow%20%40ziishaned&style=social" />
        </a>
    </p>
</p>

## Translations:

* [English](README.md)
* [Español](translations/README-es.md)
* [Français](translations/README-fr.md)
* [Português do Brasil](translations/README-pt_BR.md)
* [中文版](translations/README-cn.md)
* [日本語](translations/README-ja.md)
* [한국어](translations/README-ko.md)
* [Turkish](translations/README-tr.md)
* [Greek](translations/README-gr.md)
* [Magyar](translations/README-hu.md)
* [Polish](translations/README-pl.md)
* [Русский](translations/README-ru.md)
* [Tiếng Việt](translations/README-vn.md)
* [فارسی](translations/README-fa.md)
* [বাংলা](translations/README-bn.md)

## Regular Expression কি?

> Regular Expression (রেগুলার এক্সপ্রেশন) হলো কিছু ক্যারেক্টার (character) এর সমষ্টি, যা একটা লেখনীর (text) এর নির্দিষ্ট কোন প্যাটার্ণ খুঁজতে সহায়তা করে । 

রেগুলার এক্সপ্রেশন হলো একটা প্যাটার্ণ যা একটা স্ট্রীং এর সাথে বাম থেকে ডানে ম্যাচ করতে সাহায্য করে । রেগুলার এক্সপ্রেশন একটা স্ট্রীং এর মধ্যে টেক্সট রিপ্লেস করতে, ফর্ম ভালিডেশন এর কাজে, প্যাটার্ণ ম্যাচিং এর জন্য ট্রীং থেকে সাবস্ট্রীং বের কথা কাজে   , এবং আরো নানান কাজে ব্যবহৃত হয়। 'রেগুলার এক্সপ্রেশন' একটা গারলভরা নাম, আপনি এটাকে 'রেজেক্স'(regex) অথবা 'রেজএক্সপি'(regexp) নামেই বেশি শুনতে পারবেন ।

ধরুন আপনি একটা এপ্লিকেশন লিখছেন যেখানে আপনি কিছু রুল নির্দিষ্ট করে দিতে চান কখন একজন ব্যবহারকারী কে ইউজারনেম ব্যাবহার করতে হবে। 
আপনি চান ইউজারনেম এর জন্য একজন ব্যবহারকারী Letter, number, underscore এবং hyphens ব্যাবহার করুক।আপনি চান ব্যবহারকারীকে character এর ব্যবহারে সীমাবদ্ধ রাখতে যাতে Username দেখতে বিচ্ছিরি না লাগে। এজন্য আমরা নিচের 'রেগুলার এক্সপ্রেশন' ব্যবহার করতে পারি, ইউজারনেম ভ্যালিডেশন এর জন্যঃ

<br/><br/>
<p align="center">
  <img src="./img/regexp-en.png" alt="Regular expression">
</p>

এই 'রেগুলার এক্সপ্রেশন'টি `john_doe`, `jo-hn_doe` এবং  `jphn12_as` এগুলো নাম নেবে কিন্ত এটি `Jo` নিবে না কেননা এইক্ষেত্রে বড়হাতের অক্ষর (Uppercase) ব্যবহার হয়েছে এবং নামটা username হিসেবে ছোট।

## সূচীপত্র

- [Basic Matchers](#1-basic-matchers)
- [Meta Characters](#2-meta-characters)
  - [The Full Stop](#21-the-full-stops)
  - [Character Sets](#22-character-sets)
    - [Negated Character Sets](#221-negated-character-sets)
  - [Repetitions](#23-repetitions)
    - [The Star](#231-the-star)
    - [The Plus](#232-the-plus)
    - [The Question Mark](#233-the-question-mark)
  - [Braces](#24-braces)
  - [Capturing Groups](#25-capturing-groups)
      - [Non-Capturing Groups](#251-non-capturing-groups)
  - [Alternation](#26-alternation)
  - [Escaping Special Characters](#27-escaping-special-characters)
  - [Anchors](#28-anchors)
    - [The Caret](#281-the-caret)
    - [The Dollar Sign](#282-the-dollar-sign)
- [Shorthand Character Sets](#3-shorthand-character-sets)
- [Lookarounds](#4-lookarounds)
  - [Positive Lookahead](#41-positive-lookahead)
  - [Negative Lookahead](#42-negative-lookahead)
  - [Positive Lookbehind](#43-positive-lookbehind)
  - [Negative Lookbehind](#44-negative-lookbehind)
- [Flags](#5-flags)
  - [Case Insensitive](#51-case-insensitive)
  - [Global Search](#52-global-search)
  - [Multiline](#53-multiline)
- [Greedy vs Lazy Matching](#6-greedy-vs-lazy-matching)


## ১. বেসিক ম্যাচার

রেগুলার এক্সপ্রেশন হলো কিছু ক্যারেক্টার এর প্যাটার্ণ যা একটা টেক্সট এর ভেতরে কিছু খোঁজার জন্য কাজে লাগে । যেমনঃ রেগুলার এক্সপ্রেশন `the` মানেঃ `t` অক্ষরটির পরে `h` এবং তার পরে `e` ।

<pre>
"the" => The fat cat sat on <a href="#learn-regex"><strong>the</strong></a> mat.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/dmRygT/1)

## ২. মেটা ক্যারেক্টারস 

মেটা ক্যারেকটারস হলো রেগুলার এক্সপ্রেশন এর বিল্ডিং ব্লক। মেটা ক্যারেক্টারস নিজস্ব কোন অর্থ বহন করে না কিন্তু তারা কিছু বিশেষ স্থানে বসে ভাষান্তর করে। কিছু মেটা ক্যারেকটারস এর বিশেষ অর্থ রয়েছে এবং তাদের স্কোয়ার ব্রাকেট এর ভেতরে লিখতে হয়। নিচে মেটা ক্যারেকটারস এর বর্ণনা দ্রষ্টব্যঃ

|মেটা ক্যারেকটারস|বর্ণনা|
|:----:|----|
|.|পিরিওড (.) লাইন ব্রেক বাদে অন্য যেকোন সিঙ্গেল ক্যারেকটার এর সাথে ম্যাচ করে । |
|[ ]|ক্যারেকটার ক্লাস. স্কোয়ার ব্রাকেটের ভেতরের যেকোন ক্যারেক্টার এর সাথে ম্যাচ করে.|
|[^ ]|নিগেটেড ক্যারেকটার ক্লাস. স্কোয়ার ব্রাকেটের ভেতরের ছাড়া যেকোন ক্যারেক্টার এর সাথে ম্যাচ করে|
|*| পূর্বের প্রতীক 0 বা এর অধিক পুনরাবৃত্তির সাথে ম্যাচ করে ।|
|+|পূর্বের প্রতীক 1 বা এর অধিক পুনরাবৃত্তির সাথে ম্যাচ করে ।|
|?|পূর্বের প্রতীককের ঐচ্ছিক বানায়|
|{n,m}|কার্লি ব্রেস. পূর্বের প্রতীক এর  সাথে ম্যাচিং এর জন্য নূন্যতম "n" কিন্তু অনধিক "m" এর পুনরাবৃত্তি|
|(xyz)|ক্যারেকটার গ্রুপ. xyz এর সাথে একই ক্রমবিন্যাসে ম্যাচ করে.|
|&#124;|Alternation. হয় প্রতীকের আগের ক্যারেকটার এর সাথে অথবা পরের ক্যারেকটার এর সাথে ম্যাচ করে.|
|&#92;|পরবর্তী ক্যারেকটারকে বাদ দিয়ে এগিয়ে যায় । এটা রিসার্ভ ক্যারেকটার ম্যাচিং এর জন্য ব্যবহৃত হয় <code>[ ] ( ) { } . * + ? ^ $ \ &#124;</code>|
|^|ইনপুটের প্রারম্ভে ম্যাচিং করে |
|$|ইনপুটের শেষের সাথে ম্যাচিং করে । |

## ২.১ ফুলস্টপ

মেটা ক্যারেকটার এর একটি সহজ উদাহরণ হলো ফুলস্টপ `.` । এই মেটা ক্যারেকটারটি অন্য সিঙ্গেল ক্যারেকটার এর সাথে ম্যাচ করে । এটি রিটার্ণ অথবা কোন নতুন লাইন ম্যাচ করে না ।
উদাহরণস্বরুপঃ একটি রেগুলার এক্সপ্রেশন `.ar` এর মানেঃ যেকোন ক্যারেকটার যেটিতে `a` এবং `r` পর পর রয়েছে।

<pre>
".ar" => The <a href="#learn-regex"><strong>car</strong></a> <a href="#learn-regex"><strong>par</strong></a>ked in the <a href="#learn-regex"><strong>gar</strong></a>age.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/xc9GkU/1)

## ২.২ ক্যারেকটার সেটস

ক্যারেকটার সেটস কে ক্যারেকটার ক্লাসও বলা হয় । ক্যারেকটার সেটস বুঝানোর জন্য স্কোয়ার ব্রাকেট ব্যবহার করা হয় । ক্যারেকটার এর রেঞ্জ বুঝানোর জন্য হাইফেন (-) ব্যবহার করা হয়। স্কোয়ার ব্রাকেট এর ভেতরে ক্যারেকটার রেঞ্জ এর ধর্তব্য বিষয় নয় । যেমনঃ রেগুলার এক্সপ্রেশন `[Tt]he` মানেঃ বড়হাতের `T` অথবা ছোটহাতের `t` অক্ষরটির পরে `h` এবং তার পরে `e` ।
<pre>
"[Tt]he" => <a href="#learn-regex"><strong>The</strong></a> car parked in <a href="#learn-regex"><strong>the</strong></a> garage.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/2ITLQ4/1)

 আক্ষরিক অর্থে, একটি ক্যারেকটার সেট এর মাঝে একটা পিরিওড (.) এর
মানে 
<pre>
"ar[.]" => A garage is a good place to park a c<a href="#learn-regex"><strong>ar.</strong></a>
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/wL3xtE/1)