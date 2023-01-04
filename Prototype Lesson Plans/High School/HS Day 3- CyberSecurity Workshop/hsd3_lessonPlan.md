# High School Day 3: CyberSecurity Workshop

## *Goal: Foster interest in participants to explore topics in the field of Cyber Security.*

## Learning Objectives

- Introduce Students to various subcategories of topics within Cyber Security, including OSINT, Cryptography, and Forensics

## Resources and Materials

- Internet-connected Windows computers with the following Software installed
  <!-- - stegsolve -->
  - python3
  <!-- - Wireshark -->
- Access to the following websites and web tools
  - CyberChef
  - picoCTF
- Paper
- Writing Utensils

## Agenda Overview

1. [Staying Safe Online + Netiquette recap](#topic-1-staying-safe-online--netiquette-recap)
2. [Intro to OSINT](#topic-2-intro-to-osint)
3. [Intro to Cryptography](#topic-3-intro-to-cryptography)
4. [Intro to Forensics](#topic-4-intro-to-forensics)

### `Time-permitting Activities`

1. [More picoCTF](#more-picoctf)

## Agenda

### Topic 1: Staying Safe Online + Netiquette recap

> 20 minutes

1. Briefly review topics from the Day 1 session with a short mini-whiteboard quiz game displayed on a Slideshow. (TODO: Make slideshow)

---

### Topic 2: Intro to OSINT

> 30 minutes

1. Introduce Students to the topic of Open Source Intelligence (OSINT), the foundation of many Cyber Security Operations.

<!-- TODO: Create more challenge problems -->

2. Have the students attempt the following problems (WIP):

    1. Who was president of the United States in 1940?

    2. What was the year that the security bug known as "Shell Shock" was discovered?

    3. A suspect was seen entering the below building. What are the coordinates (in Latitude, Longitude) of their approximate location?
    ![Picture of S_____ O____ H____](image/hsd3_lessonPlan/1653879529813.png)

---

### Topic 3: Intro to Cryptography

> 40 minutes

1. Introduce students to picoCTF

2. picoCTF: [Obedient Cat](https://play.picoctf.org/practice/challenge/147?page=1&solved=0)

3. Introduce ROT13, explain how it functions, then do an example by hand on the whiteboard/ on the slideshow.
   - Note: Make sure to describe a very cheesy scenario around the problem to increase engagement.

4. picoCTF: [13](https://play.picoctf.org/practice/challenge/62?category=2&page=1&search=) (Encourage students to find an online solver to solve the problem.)

5. Introduce students to [CyberChef](https://gchq.github.io/CyberChef/) and show how it can be used to easily test and reverse similar cryptographic algorithms.

6. Have students attempt the following picoCTF problems:
    - [Mod 26](https://play.picoctf.org/practice/challenge/144?page=1&solved=0) | Rot 13
    - [caesar](https://play.picoctf.org/practice/challenge/64?category=2&page=1&search=) | Caesar Cipher
    - [The Numbers](https://play.picoctf.org/practice/challenge/68?category=2&page=1&search=) | Ascii numbers to text
    - [Lets Warm Up](https://play.picoctf.org/practice/challenge/22) | Hex number to text
    - [2Warm](https://play.picoctf.org/practice/challenge/86?category=5&page=1) | Convert Base 10 to Base 2
    - [what's a net cat?](https://play.picoctf.org/practice/challenge/34) | Connect with `netcat`
    - [Nice netcat...](https://play.picoctf.org/practice/challenge/156?page=1&solved=0) | `netcat` + Ascii numbers to text

7. Provide the following resources while students solve the above problems:
    - [Ascii table](https://www.asciitable.com/asciifull.gif)
    ![Image of Ascii table](https://www.asciitable.com/asciifull.gif)

---

### Topic 4: Intro to Forensics

> 20 minutes

<!-- TODO: add more content to this section -->

8. Introduce the Webshell, and go over the following basic commands
    - ls, cd, mkdir, wget, file, cat

9. Have the students attempt the following problems:
    - [Lookey here](https://play.picoctf.org/practice/challenge/279?category=4&page=1) | `grep` command or <kbd>Ctrl</kbd>+<kbd>F</kbd>
    - [strings it](https://play.picoctf.org/practice/challenge/37?page=4&solved=0) | `strings` command
    - [extensions](https://play.picoctf.org/practice/challenge/52?category=4&page=2) | `file` command
    - [Information](https://play.picoctf.org/practice/challenge/186?page=1&solved=0) | View EXIF data

---

### More picoCTF

1. Introductory Level cybersecurity challenges delivered in a fun and rewarding manner

- Recommended Beginner Challenges:
  - [Obedient Cat](https://play.picoctf.org/practice/challenge/147?page=1&solved=0)
  - [Mod 26](https://play.picoctf.org/practice/challenge/144?page=1&solved=0)
  - [Python Wrangling](https://play.picoctf.org/practice/challenge/166?page=1&solved=0)
  - [Information](https://play.picoctf.org/practice/challenge/186?page=1&solved=0)
  - [what's a net cat?](https://play.picoctf.org/practice/challenge/34)
  - [Lets Warm Up](https://play.picoctf.org/practice/challenge/22)
  - [2Warm](https://play.picoctf.org/practice/challenge/86?category=5&page=1)
  - [Nice netcat...](https://play.picoctf.org/practice/challenge/156?page=1&solved=0)
  - [strings it](https://play.picoctf.org/practice/challenge/37?page=4&solved=0)
  - [Lookey here](https://play.picoctf.org/practice/challenge/279?category=4&page=1)
  - [extensions](https://play.picoctf.org/practice/challenge/52?category=4&page=2)
