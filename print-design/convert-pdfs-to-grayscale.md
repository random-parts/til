---
headline: 'Convert PDFs to grayscale for offset printing'
date: 2016-08-24
category: print-design
tags:
  - printing
---

When converting PDFs in Acrobat, the grayscale options include `Dot Gain` _N_% and `Gray Gamma` 1.8 & 2.2. I had been dismissing `Dot Gain` completely as `Gray Gamma 2.2` looked more inviting. It also seems to be the [accepted answer] to converting color PDFs.

`Gray Gamma 1.8/2.2` adjusts the gray [gamma] to match monitor display profiles of 1.8 [macs] or 2.2 [pc]. Not very helpful when I want the files to reproduce well. On paper.

---

#### What is Dot Gain
[yourdictionary.com]

```
An increase in size of each dot of ink when printed due to temperature, ink and paper type. 
A press operator tries to minimize dot gain, which can muddy the printed image.
```

The [Dot Gain Wiki] says:

```
It is defined as the increase in the area fraction (of the inked or colored region) of a halftone dot during the prepress and printing processes.
Total dot gain is the difference between the dot size on the film negative and the corresponding printed dot size. For example, a dot pattern that
covers 30% of the image area on film, but covers 50% when printed, is said to show a total dot gain of 20%.

However, with today's computer-to-plate imaging systems, which eliminates film completely, the measure of "film" is the original digital source
"dot." Therefore, dot gain is now measured as the original digital dot versus the actual measured ink dot on paper.
```

---

#### From the Printers

- So, use `Dot gain` _N_%. But which one? `10%, 15%, 20%, 25%, 30%`

Not really finding a simple answer online, I asked the people that had to deal with `dot gain` on a real level. 

The answer: `It doesn't really matter`. With the workflow using `computer-to-plate` and press adjustments they can make at runtime, plus what the finished product is, it just does not make enough of a difference. If it were 4 color process, then it would be something to look into.

---

#### What I Learned
- Convert using `Dot Gain 20%`. `15%` is also common.
- Next time, ask the printers how they want it output.

---
- [Extra Dot Gain Reading](http://www.imaging-resource.com/TIPS/LAWLER/DOTGAIN.PDF)

[Dot Gain Wiki]: https://en.wikipedia.org/wiki/Dot_gain#Definition
[accepted answer]: https://answers.acrobatusers.com/How-do-I-convert-a-color-pdf-to-a-greyscale-pdf-q64092.aspx
[gamma]: https://en.wikipedia.org/wiki/Gamma_correction
[yourdictionary.com]: http://www.yourdictionary.com/dot-gain