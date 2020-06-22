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

## Table of Contents

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


## 1. বেসিক ম্যাচার

রেগুলার এক্সপ্রেশন হলো কিছু ক্যারেক্টার এর প্যাটার্ণ যা একটা টেক্সট এর ভেতরে কিছু খোঁজার জন্য কাজে লাগে । যেমনঃ রেগুলার এক্সপ্রেশন `the` মানেঃ `t` অক্ষরটির পরে `h` এবং তার পরে `e` ।

<pre>
"the" => The fat cat sat on <a href="#learn-regex"><strong>the</strong></a> mat.
</pre>

[রেগুলার এক্সপ্রেশনটি পরীক্ষা করে দেখুন](https://regex101.com/r/dmRygT/1)