+++
title: "Reverse Engineering"
date: 2023-11-27T16:27:25+13:00
draft: true
tags:
  - reverse_engineering
  - learning
  - crackmes.one
+++

### Learning reverse engineering: explained by a noob

I know little about reverse engineering, except that it sounds very cool and I want to do it. So let's dive in.

#### learning platforms

![crackmes.one logo](/image.png)

I started with crackmes.one, which was recommended to me as an easy way to get started. I'm starting with this box:
https://crackmes.one/crackme/5f907efe33c5d424269a15d1 

### Crypt0 - Beginner CrackMe

> Note: if you don't have a Windows VM set up, I recommend doing this first because it takes SO LONG to download.

1) Actually figuring out what to do 

* Download the provided zip file. It's password protected. The password to all crackmes should be `crackmes.one`. (It took a a few minutes to realise this, as it's listed in the FAQ and not in the download pages for the files.).

* Extract the files. We get a nice message and some ASCII art in the README file. Create a new project and drag the exe file into Ghidra.

* I used the following guide since I had not used Ghidra much previously. https://www.varonis.com/blog/how-to-use-ghidra 



2) Looking though the code in Ghidra

* Wow look at that code, it's definitely not hard to read at all. You should maybe do what I didn't and familiarise yourself with how Assembly works before you do this. Or you can do what I did and ask ChatGPT.

* This is a Windows executable (we can tell because of the .exe extension). We need to download a Windows VM to run this.

* I wasn't sure how to proceed with the code in Ghidra so I decided to try running the program first to see how it works.