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

## রেগুলার এক্সপ্রেশন কি?

> Regular Expression (রেগুলার এক্সপ্রেশন) হলো কিছু ক্যারেক্টার (character) এর সমষ্টি, যা একটা লেখনীর (text) এর নির্দিষ্ট কোন প্যাটার্ণ খুঁজতে সহায়তা করে । 

রেগুলার এক্সপ্রেশন হলো একটা প্যাটার্ণ যা একটা স্ট্রীং এর সাথে বাম থেকে ডানে ম্যাচ করতে সাহায্য করে । রেগুলার এক্সপ্রেশন একটা স্ট্রীং এর মধ্যে টেক্সট রিপ্লেস করতে, ফর্ম ভালিডেশন এর কাজে, প্যাটার্ণ ম্যাচিং এর জন্য ট্রীং থেকে সাবস্ট্রীং বের কথা কাজে   , এবং আরো নানান কাজে ব্যবহৃত হয়। 'রেগুলার এক্সপ্রেশন' একটা গারলভরা নাম, আপনি এটাকে 'রেজেক্স'(regex) অথবা 'রেজএক্সপি'(regexp) নামেই বেশি শুনতে পারবেন ।

ধরুন আপনি একটা এপ্লিকেশন লিখছেন যেখানে আপনি কিছু রুল নির্দিষ্ট করে দিতে চান কখন একজন ব্যবহারকারী কে ইউজারনেম ব্যাবহার করতে হবে। 
আপনি চান ইউজারনেম এর জন্য একজন ব্যবহারকারী Letter, number, underscore এবং hyphens ব্যাবহার করুক।আপনি চান ব্যবহারকারীকে character এর ব্যবহারে সীমাবদ্ধ রাখতে যাতে Username দেখতে বিচ্ছিরি না লাগে। এজন্য আমরা নিচের 'রেগুলার এক্সপ্রেশন' ব্যবহার করতে পারি, ইউজারনেম ভ্যালিডেশন এর জন্যঃ

<br/><br/>
<p align="center">
  <img src="./img/regexp-bn.png" alt="Regular expression">
</p>

এই 'রেগুলার এক্সপ্রেশন'টি `john_doe`, `jo-hn_doe` এবং  `jphn12_as` এগুলো নাম নেবে কিন্ত এটি `Jo` নিবে না কেননা এইক্ষেত্রে বড়হাতের অক্ষর (Uppercase) ব্যবহার হয়েছে এবং নামটা username হিসেবে ছোট।

## সূচীপত্র

- [বেসিক ম্যাচার](#1-basic-matchers)
- [মেটা ক্যারেক্টারস](#2-meta-characters)
  - [ফুলস্টপ](#21-the-full-stops)
  - [ক্যারেকটার সেটস](#22-character-sets)
    - [নিগেটেড ক্যারেকটার সেটস](#221-negated-character-sets)
  - [রিপিটিশন/পুনরাবৃত্তি](#23-repetitions)
    - [স্টার (*)](#231-the-star)
    - [The Plus](#232-the-plus)
    - [The Question Mark](#233-the-question-mark)
  - [ব্রেসেস / বন্ধনী](#24-braces)
  - [ক্যাপচারিং গ্রুপ ](#25-capturing-groups)
      - [নন-ক্যাপচারিং গ্রুপ ](#251-non-capturing-groups)
  - [অল্টারেশন](#26-alternation)
  - [এস্কেপিং স্পেশাল ক্যারেকটার (বিশেষ যতিচিহ্ন বাদ দেওয়া)](#27-escaping-special-characters)
  - [এ্যাংকরস](#28-anchors) 
    - [ক্যারেট](#281-the-caret)
    - [ডলার সাইন](#282-the-dollar-sign)
- [শর্টহ্যান্ড ক্যারেকটার সেটস](#3-shorthand-character-sets)
- [লুকএরাউন্ডস](#4-lookarounds)
  - [পজিটিভ লুকএহেড](#41-positive-lookahead)
  - [নেগেটিভ লুকএহেড](#42-negative-lookahead)
  - [পজিটিভ লুকবিহাইন্ড](#43-positive-lookbehind)
  - [নেগেটিভ লুকবিহাইন্ড](#44-negative-lookbehind)
- [ফ্ল্যাগস](#5-flags)
  - [কেস ইনসেন্সিটিভ](#51-case-insensitive)
  - [গ্লোবার সার্চ](#52-global-search)
  - [মাল্টিলাইন](#53-multiline)
- [গ্রীডি বনাম লেজি ম্যাচিং](#6-greedy-vs-lazy-matching)


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
|{n,m}|কার্লি ব্রেস. পূর্বের প্রতীক এর  সাথে ম্যাচিং এর জন্য নূন্যতম "n" কিন্তু "m" এর অনধিক পুনরাবৃত্তি|
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

ক্যারেকটার সেট এর মাঝে একটা পিরিওড (.) বসলে আক্ষরিক অর্থে ব্যাবহৃত হয় । যেমন ঃ রেগুলার এক্সপ্রেশন `ar[.]` এর মানেঃ ছোট হাতের `a`,এর পরে আসে  `r`, আর তার পরে আসে `.` ক্যারেকটার
<pre>
"ar[.]" => A garage is a good place to park a c<a href="#learn-regex"><strong>ar.</strong></a>
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/wL3xtE/1)

### ২.২.১ নিগেটেড ক্যারেকটার সেটস

সাধারণভাবে, ক্যারেট প্রতীকটি স্ট্রীং এর শুরু বুঝাতে কাজে লাগে, কিন্তু যখন এটা স্কোয়ার ব্রাকেটের পরে লিখা হয় তখন এটি ক্যারেকটার সেট কে নিগেশন করে (বাদ দেয়)। যেমনঃ রেগুলার এক্সপ্রেশন `[^c]ar` এর মানেঃ যেকোন ক্যারেকটার সেট `c`, বাদে , যার পরে আসে `a`, এবং তার পর `r`.

<pre>
"[^c]ar" => The car <a href="#learn-regex"><strong>par</strong></a>ked in the <a href="#learn-regex"><strong>gar</strong></a>age.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/nNNlq3/1)

## ২.৩ রিপিটিশন/পুনরাবৃত্তি

মেটা ক্যারেকটারস `+`, `*` অথবা `?` ব্যাবহৃত হয় এটা নির্দিষ্ট করার জন্য যে কতবার একটা সাব-প্যাটার্ণ হতে পারে । ভিন্ন ভিন্ন কারণে ভিন্ন ভিন্ন ক্যারেকটার হতে পারে । 

### ২.৩.১ স্টার (*)

স্টার বা এস্টারিস্ক সিম্বল `*`  

<pre>
"[a-z]*" => T<a href="#learn-regex"><strong>he</strong></a> <a href="#learn-regex"><strong>car</strong></a> <a href="#learn-regex"><strong>parked</strong></a> <a href="#learn-regex"><strong>in</strong></a> <a href="#learn-regex"><strong>the</strong></a> <a href="#learn-regex"><strong>garage</strong></a> #21.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/7m8me5/1)

### ২.৩.২ প্লাস

<pre>
"c.+t" => The fat <a href="#learn-regex"><strong>cat sat on the mat</strong></a>.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/Dzf9Aa/1)

### ২.৩.৩ কোয়াশ্চেন মার্ক

<pre>
"[T]he" => <a href="#learn-regex"><strong>The</strong></a> car is parked in the garage.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/cIg9zm/1)

<pre>
"[T]?he" => <a href="#learn-regex"><strong>The</strong></a> car is parked in t<a href="#learn-regex"><strong>he</strong></a> garage.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/kPpO2x/1)

### ২.৪ ব্রেসেস / বন্ধনী 

<pre>
"[0-9]{2,3}" => The number was 9.<a href="#learn-regex"><strong>999</strong></a>7 but we rounded it off to <a href="#learn-regex"><strong>10</strong></a>.0.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/juM86s/1)



<pre>
"[0-9]{2,}" => The number was 9.<a href="#learn-regex"><strong>9997</strong></a> but we rounded it off to <a href="#learn-regex"><strong>10</strong></a>.0.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/Gdy4w5/1)

<pre>
"[0-9]{3}" => The number was 9.<a href="#learn-regex"><strong>999</strong></a>7 but we rounded it off to 10.0.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/Sivu30/1)



### ২.৫ ক্যাপচারিং গ্রুপ 

<pre>
"(c|g|p)ar" => The <a href="#learn-regex"><strong>car</strong></a> is <a href="#learn-regex"><strong>par</strong></a>ked in the <a href="#learn-regex"><strong>gar</strong></a>age.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/tUxrBG/1)

### ২.৫.১ নন ক্যাপচারিং গ্রুপ 

<pre>
"(?:c|g|p)ar" => The <a href="#learn-regex"><strong>car</strong></a> is <a href="#learn-regex"><strong>par</strong></a>ked in the <a href="#learn-regex"><strong>gar</strong></a>age.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/Rm7Me8/1)

### অল্টারেশন / 

<pre>
"(T|t)he|car" => <a href="#learn-regex"><strong>The</strong></a> <a href="#learn-regex"><strong>car</strong></a> is parked in <a href="#learn-regex"><strong>the</strong></a> garage.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/fBXyX0/1)

### ২.৭ এস্কেপিং স্পেশাল ক্যারেকটার (বিশেষ যতিচিহ্ন বাদ দেওয়া)

<pre>
"(f|c|m)at\.?" => The <a href="#learn-regex"><strong>fat</strong></a> <a href="#learn-regex"><strong>cat</strong></a> sat on the <a href="#learn-regex"><strong>mat.</strong></a>
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/DOc5Nu/1)

## ২.৮ এ্যাংকরস
রেগুলার এক্সপ্রেশনে আমরা এ্যাংকরস ব্যাবহার করি এটা যাচাই করতে যে যেই ম্যাচিং সিম্বল নিয়ে আমরা কাজ করছি ঐটা ইনপুট স্ট্রীং এর শুরুতে আছে নাকি শেষে আছে ।
এ্যাংকরস ২ ধরণের হয়ঃ
প্রথম টাইপের এ্যাংকর হলো `^` (ক্যারেট চিহ্ন), এটা চেক করে যে ম্যাচিং ক্যারেকটার কি ইনপুটের প্রথম ক্যারেকটার কি না ।
 আরেক ধরণের এ্যাংকর হল `$` (ডলার সাইন), এটা চেক করে যে ম্যাচিং ক্যারেকটার কি ইনপুটের শেষ ক্যারেকটার কি না ।

### ২.৮.১ ক্যারেট 

`^` (ক্যারেট), চেক করে যে ম্যাচিং ক্যারেকটার কি ইনপুটের প্রথম ক্যারেকটার কি না । যেমনঃ `^a` আমরা যদি এই রেগুলার এক্সপ্রেশন এ(অর্থাৎ a কে অবশ্যই শুরুর ক্যারেকটার হতে হবে) `abc` এই স্ট্রীং এর মধ্যে, এটা `a` এর সাথে ম্যাচ করছে । কিন্তু উপরোক্ত স্ট্রীং এর সাথে যদি `^b` রেগুলার এক্সপ্রেশন ব্যাবহার করি তাহলে এটি ম্যাচ করবে না । কেননা `abc` এই স্ট্রীং এ "b" শুরুর ক্যারেকটার না। 
আরেকটি রেগুলার এক্সপ্রেশন `^(T|t)he` যদি চেক করতে যাই তাহলে 
আমরা দেখতে পাই , বড়হাতের `T` অথবা ছোটহাতের `t` স্ট্রীং এর প্রথম ক্যারেকটার হতে হবে এর পরে  ছোটহাতের `h` এবং তারপর ছোটহাতের `e` ।

<pre>
"(T|t)he" => <a href="#learn-regex"><strong>The</strong></a> car is parked in <a href="#learn-regex"><strong>the</strong></a> garage.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/5ljjgB/1)

<pre>
"^(T|t)he" => <a href="#learn-regex"><strong>The</strong></a> car is parked in the garage.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/jXrKne/1)

### ২.৮.২ ডলার সাইন 
<pre>
"(at\.)" => The fat c<a href="#learn-regex"><strong>at.</strong></a> s<a href="#learn-regex"><strong>at.</strong></a> on the m<a href="#learn-regex"><strong>at.</strong></a>
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/y4Au4D/1)

<pre>
"(at\.)$" => The fat cat. sat. on the m<a href="#learn-regex"><strong>at.</strong></a>
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/t0AkOd/1)

## ৩. শর্টহ্যান্ড ক্যারেকটার সেটস
কয়েক প্রকার শর্টহ্যান্ড ক্যারেকটার সেটস আছে যেগুলো সচরাচর বযাবহৃত হয়/
রেগুলার এক্সপ্রেশনঃ 

|শর্টহ্যান্ড|বর্ণনা|
|:----:|----|
|.|যেকোন ক্যারেক্টার, নিউলাইন বাদে|
|\w|আলফানিউমেরিক ক্যারেকটার এর সাথে ম্যাচ করে : `[a-zA-Z0-9_]`|
|\W|নন-আলফানিউমেরিক ক্যারেকটার এর সাথে ম্যাচ করে: `[^\w]`|
|\d|সংখ্যার সাথে ম্যাচ করে : `[0-9]`|
|\D|চিহ্নের সাথে ম্যাচ করে : `[^\d]`|
|\s|হোয়াইটস্পেস ক্যারেকটার এর সাথে ম্যাচ করে : `[\t\n\f\r\p{Z}]`|
|\S|নন -হোয়াইটস্পেস ক্যারেকটার এর সাথে ম্যাচ করে: `[^\s]`|

## ৪ লুকএরাউন্ডস

### ৪.১ পজিটিভ লুকএহেড

<pre>
"(T|t)he(?=\sfat)" => <a href="#learn-regex"><strong>The</strong></a> fat cat sat on the mat.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/IDDARt/1)

### ৪.৪ নেগেটিভ লুকএহেড

<pre>
"(T|t)he(?!\sfat)" => The fat cat sat on <a href="#learn-regex"><strong>the</strong></a> mat.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/V32Npg/1)


### ৪.৩ পজিটিভ লুকবিহাইন্ড
 পজিটিভ লুকবিহাইন্ড হলো ঐ সকল ম্যাচ চেক করে দেখা যা কোন নির্দিষ্ট(স্পেসিফিক) প্যাটার্ণ ফলো করে । পজিটিভ লুকবিহাইন্ড লিখার নিয়মঃ `(?<=...)` উদাহরণস্বরূপ রেগুলার এক্সপ্রেশন `(?<=(T|t)he\s)(fat|mat)` এর অর্থ ইনপুট স্ট্রীং এর মধ্যে সকল `fat` বা `mat` শন্দ খুঁজে বের করা, যখন এটা `The` বা `the` এর পরে আছে ।

 <pre>
"(?<=(T|t)he\s)(fat|mat)" => The <a href="#learn-regex"><strong>fat</strong></a> cat sat on the <a href="#learn-regex"><strong>mat</strong></a>.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/avH165/1)



### ৪.৪ নেগেটিভ লুকবিহাইন্ড

নেগেটিভ লুকবিহাইন্ড হলো সব ম্যাচ চেক করে দেখা যা কোন স্পেসফিক প্যাটার্ন ফলো করে না । নেগেটীভ লুকব্যাক লেখার পদ্ধতি ঃ `(?<!...)` যেমনঃ রেগুলার এক্সপ্রেশন `(?<!(T|t)he\s)(cat)` এর মানে, ইনপুত স্ট্রীং এর যত জায়গায় `cat` আছে সব চেক করা যেগুলো `The` বা `the` এর পরে আছে ।

<pre>
"(?&lt;!(T|t)he\s)(cat)" => The cat sat on <a href="#learn-regex"><strong>cat</strong></a>.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/8Efx5G/1)


### ৫.১ কেস সেনসিটিভ

কেস সেনসিটিভ ম্যাচিং এর জন্য `i` মডিফায়ার ব্যবহার করা হয়। যেমনঃ রেগুলার এক্সপ্রেশন `/The/gi` এর মানে বড়হাতের `T`এর পরে ছোটহাতের `h` এর পর ছোটহাতের `e` এবং সবার শেষে ছোটহাতেরর `i` ফ্ল্যাগ বলে দেয় এই কেসকে ইগনোর করতে। লক্ষ্য করলে দেখবেন আমরা `g` ফ্ল্যাগ ব্যবহার করেছি, এর কারণ হলো আমরা পুরো ইনপুট স্ট্রীং এর মধ্যে প্যাটার্ণটি সার্চ করতে চাই ।  
<pre>
"The" => <a href="#learn-regex"><strong>The</strong></a> fat cat sat on the mat.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/dpQyf9/1)

<pre>
"/The/gi" => <a href="#learn-regex"><strong>The</strong></a> fat cat sat on <a href="#learn-regex"><strong>the</strong></a> mat.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/ahfiuh/1)


### ৫.২ গ্লোবাল সার্চ

`g` মডিফায়ার ব্যাবহৃত হয় গ্লোবাল ম্যাচ করার জন্য( প্রথম ম্যাচের পর না থেমে পুরো টেক্সট এ ম্যাচ করার জন্য) । যেমনঃ `/.(at)/g` এর মানে হলো নিউলাইন বাদে যেকোন ক্যারেকটার এর পরে ছোটহাতের `a` এবং এর পরে ছোট হাতের `t`. যেহেতু আমরা একটা `g` ফ্ল্যাগ ব্যাবহার করেছি সেহেতু আমরা ইনপুট স্ট্রীং এর সব ম্যাচ করতে পারব শুধু প্রথমটা নয় (শুধু প্রথম ক্যারেকটার ম্যাচিং হলো ডিফল্ট বিহেভিয়ার) । 

<pre>
"/.(at)/" => The <a href="#learn-regex"><strong>fat</strong></a> cat sat on the mat.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/jnk6gM/1)

<pre>
"/.(at)/g" => The <a href="#learn-regex"><strong>fat</strong></a> <a href="#learn-regex"><strong>cat</strong></a> <a href="#learn-regex"><strong>sat</strong></a> on the <a href="#learn-regex"><strong>mat</strong></a>.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/dO1nef/1)

### ৫.৩ মাল্টিলাইন 

মাল্টিলাইন ম্যাচ এর জন্য `m` মডিফায়ার ব্যাবহার করা হয় । যেমন আমরা বলেছি প্রথমে, এ্যাংকরস(anchors) `(^, $)` 
ব্যবহার করা হয় এটা দেখতে যে প্যাটের কোন স্ট্রীং এর শুরুতে আছে নাকি শেষে । 
যদি আমরা প্রতি লাইনে এ্যাংকর দিয়ে কাজ করতে চাই, তাহলে আমরা `m` এ কাজ করবো। যেমনঃ রেগুলার এক্সপ্রেশন `/at(.)?$/gm` এর মানেঃ ছোটহাতের `a`, এর পর ছোটহাতের `t` এবং এর পর নিউলাইন বাদে যেকোন ক্যারেক্টার । যেহেতু এখানে `m` ফ্ল্যাগ রয়েছে এজন্য রেগুলার এক্সপ্রেশন ইঞ্জিন প্রত্যেক লাইনের শেষে স্ট্রীং ম্যাচিং এর চেষ্টা করে ।
<pre>
"/.at(.)?$/" => The fat
                cat sat
                on the <a href="#learn-regex"><strong>mat.</strong></a>
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/hoGMkP/1)

<pre>
"/.at(.)?$/gm" => The <a href="#learn-regex"><strong>fat</strong></a>
                  cat <a href="#learn-regex"><strong>sat</strong></a>
                  on the <a href="#learn-regex"><strong>mat.</strong></a>
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/E88WE2/1)


### ৬. গ্রীডি বনাম লেজি ম্যাচিং

ডিফল্টভাবেই, একটা রেজেক্স গ্রীডি ম্যাচিং অপারেশন করে, এর মানে যতক্ষণ পর্যন্ত ম্যাচিং সম্ভব ততক্ষণ পর্যন্ত ম্যাচিং হতে থাকবে । আমরা `?` ব্যবহার করতে পারি লেজি ম্যাচিং পরীক্ষা করার জন্য, এর অর্থ ম্যাচিং যত তাড়াতাড়ি করা সম্ভব তত তাড়াতাড়ি হবে ।

<pre>
"/(.*at)/" => <a href="#learn-regex"><strong>The fat cat sat on the mat</strong></a>. </pre>


[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/AyAdgJ/1)

<pre>
"/(.*?at)/" => <a href="#learn-regex"><strong>The fat</strong></a> cat sat on the mat. </pre>


[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/AyAdgJ/2)


## আপনার অবদান 

* একটা পুল রিকুয়েস্ট করুন আপনার অবদান সহ
* ইস্যুতে আপনার আইডিয়া আলোচনা করুন
* সবার মাঝে ছড়িয়ে দিন
* যে কোন মতামত জানাতে [![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/ziishaned.svg?style=social&label=Follow%20%40ziishaned)](https://twitter.com/ziishaned)

## লাইসেন্স

MIT &copy; [Zeeshan Ahmad](https://twitter.com/ziishaned)
