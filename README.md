# 2026 PCB Challenge: Results

## The Challenge

The 2026 PCB Challenge ran from the 12th to the 19th of October, and the results are finally in. Six universities took part: UCL, KCL, Oxford, Cambridge, Imperial and Edinburgh. Many thanks to Jane Street and PCBWay for sponsoring the prizes.

The idea was simple. Everyone was given the same schematic, with every component value, connection and footprint already set. Your job was to turn it into a fully wired four layer PCB in the smallest possible area. As an added twist, I never told anyone what the board actually does; deducing the logic function from the schematic alone was part of the challenge. For those still wondering, the circuit **was a 4 bit FIFO buffer.**

The main rules were: 0.15mm minimum trace width, 0.12mm minimum clearance, 0.3mm vias, no via in pad, unmodified KiCad footprints, and no traces or vias underneath an IC on the same layer. The full brief is on the [challenge GitHub](https://github.com/Fleming-Society/PCB-Challenge-2026).

## The Submissions

We received 42 submissions from Imperial, UCL and Edinburgh, including one team entry from Edinburgh, and 22 of them were valid. Among the valid submissions, board areas ranged from 1037mm² for the smallest all the way up to 7288mm² for the largest.

Every submission was scored out of 10, with area as the main factor. Breaking the rules lost you points, and the most common rule broken was routing traces underneath the ICs. Two submissions had a nice layout but no traces at all, so unfortunately there was not much I could review.

## The Winners

### 1st Place: Taylan Arslan (UCL), 2025mm²

Taylan used Opus 5.5 to do most of the work, and there was no rule against using AI. [View the repo](https://github.com/manyetox/PCB-Challenge-4-word-4-bit-asynchronous-FIFO/tree/main)

### 2nd Place: Lucas Cerezini (UCL), 2100mm²

Great submission, clearly a lot of effort put into it and also within the rules. [View the repo](https://github.com/Lucere211/PCB-Challenge-Fleming-Soc-2026)

### 3rd Place: Hashim Jastaniah (Imperial), 2340mm²

Cursed, but the traces are actually done very beautifully, and so is the layout of the components. [View the repo](https://git.liber8bits.com/PCB-Challenge-2026/)

### Smallest Board: Andy Guo (UCL), 1037mm²

At 39.30mm x 26.69mm, Andy's board was the smallest submission by a fair margin, and he spent around 26 hours on it. Andy also helped find and report issues with the original schematic, so thank you for that. Unfortunately he did route traces underneath the ICs, which is against the rules, and I am highly skeptical that the differential pair would work. Still, it earned him 4th place. [View the repo](https://github.com/dfdc1123/pcb-challenge-2026-submission)

## Common Mistakes

A lot of the same issues came up again and again, so here they are for anyone attempting this next year.

**Traces underneath the ICs:** This was against the rules, and it was the most common reason for points being deducted. It only applied if the trace and the IC were on the same layer.

**Differential pairs not matched in length:** The two traces of a differential pair need to be the same length. The receiver subtracts one line from the other, which is what cancels out common mode noise. If one trace is longer, the signals arrive at different times and that cancellation stops working.

**Differential pairs through vias:** Bad practice. Every via is a discontinuity in impedance, and it can break the continuous reference plane the pair needs underneath it.

**90 degree angles on the differential pair:** Usually this does not matter, but for USB 2.0 it does, since it runs at a frequency of 240MHz. Use 45 degree bends or curves instead.

**No ground reference:** A differential pair needs a continuous reference plane underneath it. A solid GND plane on the layer below is the easiest way to get this.

**The cursed TFL traces:** At least three submissions arrived with the same unusual, tube map looking traces. I still do not know what plugin was used for these, so if it was you, please tell me.

## Leaderboard

Congratulations to the top 10, who each win a Jane Street bottle. The top 3 also win an Amazon voucher.

| Place | Name | University | Score | Prize |
| --- | --- | --- | --- | --- |
| 1 | Taylan Arslan | UCL | 9.5/10 | £200 Amazon voucher + Jane Street bottle |
| 2 | Lucas Cerezini | UCL | 9/10 | £100 Amazon voucher + Jane Street bottle |
| 3 | Hashim Jastaniah | Imperial | 8/10 | £50 Amazon voucher + Jane Street bottle |
| 4 | Andy Guo | UCL | 7.5/10 | Jane Street bottle |
| 5 | Mickey Techachokwiwat | Imperial | 7/10 | Jane Street bottle |
| 6 | Tan Wei Zhe, Keith | Imperial | 7/10 | Jane Street bottle |
| 7 | Archie Kendall | Imperial | 7/10 | Jane Street bottle |
| 8 | David Lesman | Imperial | 6/10 | Jane Street bottle |
| 9 | jsg25 | Imperial | 6/10 | Jane Street bottle |
| 10 | Paul Vincent Bezzina (me) | UCL | 6/10 | Jane Street bottle |

Everyone who submitted also gets a Jane Street t-shirt, a PCBWay ruler and a PCBWay coupon. I will be emailing everyone individually about how to collect them.

## Final Thoughts

Thank you to everyone who took part, and to Jane Street and PCBWay for sponsoring the prizes. Thank you as well to Mickey Techachokwiwat, Andy Guo and Lutfi Cengiz for finding issues with the schematic and reporting them to me.
