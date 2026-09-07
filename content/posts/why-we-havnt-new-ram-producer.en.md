---
title: "Why don't new companies enter the RAM market?"
date: 2026-09-07T20:10:30+03:30
draft: false
categories:
- Technology
tags:
- Economy
- Infrastructure
---

Actually building DRAM chips is one of the **most complex, expensive, and concentrated engineering tasks in human history**.

Big tech's appetite for the enormous profits of Samsung, SK Hynix, and Micron is entirely reasonable. The barriers to entry, though, are so high that they keep new companies out.

---

## 1. The difference between “making a chip” and “assembling a module”

Companies such as Corsair, Kingston, Lexar, Adata, or SanDisk — the names you see on RAM sticks, memory cards, and SSDs — **do not manufacture the memory chips themselves**.

* **Module makers:** These companies buy raw silicon chips (DRAM dies) from the actual manufacturers, solder them onto a printed circuit board (PCB), add a heatsink, and sell the finished module.
* **The real silicon fabs:** The process of making those black silicon chips from raw wafers belongs to Samsung, SK Hynix, and Micron, which together control more than **90 to 95 percent of the global market**.

---

## 2. Astronomical capital and a locked supply chain

A new DRAM fab costs **$15 to $25 billion** in upfront investment:

* **Exclusive equipment:** Building modern DRAM requires EUV (extreme ultraviolet) lithography tools. The only maker of those machines is the Dutch company ASML. Each tool costs more than $300 million, and its production capacity is fully booked for years ahead.
* **Ultra-advanced cleanrooms:** Chipmaking needs environments thousands of times cleaner than a hospital operating room. A single dust particle a few nanometers across can destroy a wafer worth hundreds of thousands of dollars.

---

## 3. A patent minefield and manufacturing complexity

DRAM is structurally denser and more intricate even than CPUs or SSD memory (NAND flash):

* **Nanometer-scale capacitors:** Unlike an SSD, RAM is made of millions of microscopic capacitors that must charge and discharge billions of times per second. Building these vertical capacitors below 10 nanometers pushes the limits of physics and chemistry.
* **Patent lock-in:** Over the past 40 years, Samsung and its rivals have filed tens of thousands of patents covering every stage of DRAM design and lithography. Any newcomer faces a wall of lawsuits before it ever ships a first chip.

---

## 4. Deadly boom-and-bust cycles

The memory market is extremely cyclical:

1. **Boom:** Periods like the current one, with the AI surge and intense demand for HBM and DDR5, produce staggering profits.
2. **Bust:** A few years later, oversupply crashes prices.

In downturns, even giants like Samsung post billion-dollar losses. A startup would almost certainly go bankrupt in the first bust, before it had recovered the cost of building the fab.

---

## 5. Early yield rates

When a new fab comes online, its **yield** of good chips in the first months can sit below 20 percent. That means 80 percent of output is scrap. Years of work and billions of dollars in R&D are needed to push yield above 90 percent.

> **The only exception: China, with state money**
> The only new player that has managed to enter this field is China’s **CXMT**, and it did so not with private capital but with tens of billions of dollars in direct Chinese government funding, aimed at technological self-sufficiency. Even so, because of sanctions and the technical difficulty, it still lags Samsung and Hynix by several years in lithography and advanced HBM.

**HBM (High Bandwidth Memory)** is an advanced, three-dimensional memory architecture designed to solve one of computing’s largest problems: **the data-transfer bottleneck**.

---

## 1. How HBM architecture works

In ordinary RAM (DDR4 or DDR5), memory chips sit spaced out on a circuit board and connect to the processor over long copper traces. In HBM:

* **3D stacking:** Between 4 and 16 DRAM dies are stacked on top of one another.
* **TSV interconnects:** The layers connect through thousands of microscopic vertical channels called **TSVs (Through-Silicon Vias)** that run through the silicon itself.
* **Proximity to the processor:** The entire stacked memory assembly sits on a silicon interposer **just a few millimeters from the main chip (the GPU)**.

---

## 2. HBM versus ordinary RAM

| Feature | Ordinary DDR5 | Advanced HBM3e |
| --- | --- | --- |
| **Layout** | Single layer in a board slot | 3D, multiple layers stacked |
| **Bus width** | 64 bits | 1,024 to 2,048 bits |
| **Bandwidth** | About 64 to 80 GB/s | More than 1,200 GB/s |
| **Distance to the processor** | Several centimeters (on the motherboard) | A few millimeters (in a shared package) |
| **Power use** | Relatively high per bit | Much more efficient |

---

## 3. Why HBM produced enormous profits for Samsung and Hynix

### 1. AI is crippled without HBM

Large language models (ChatGPT, Claude, and the like) need to process billions of parameters to answer a query. The world’s fastest GPUs, such as Nvidia’s H100 or B200, would spend most of their time waiting for data if they used ordinary RAM. HBM is the only memory that can feed data at terabyte-class speed.

### 2. Enormous average selling prices (high ASP)

Each gigabyte of HBM costs about **5 to 10 times** more than ordinary DDR5. With frantic demand from large tech companies (Microsoft, Google, Meta, and Nvidia), HBM makers have extraordinary pricing power.

### 3. Engineering complexity and high scrap rates

Building HBM is like constructing a multi-story tower at nanometer scale. In a 12-layer stack, a single bad microscopic connection ruins the entire stack, which can be worth hundreds of dollars.
**SK Hynix**, with its liquid-resin injection process (MR-MUF), and **Samsung**, with its huge manufacturing capacity, are the only players that have pushed yield to an economically viable level. That concentration has driven their operating profits to historic highs.

### 4. Fully pre-sold capacity

Almost 100 percent of Samsung’s and SK Hynix’s HBM output has been sold months ahead. That means guaranteed sales, locked-in profit, and no risk of inventory piling up in a warehouse.

**HBM4** is not a simple speed bump. It is a **fundamental redesign of memory architecture**. In earlier generations, speed came from raising pin clocks. In HBM4, for the first time, the physical structure of the bus and the memory’s base layer has changed.

---

## 1. Fundamental changes in HBM4 architecture

* **Doubling the bus width (2048-bit interface):** From the first generation through HBM3e, the data interface stayed at 1,024 bits. In HBM4 it rises to **2,048 bits with 32 independent channels**, doubling the density of vertical connections.
* **Turning the base layer into a logic chip (advanced logic base die):** The bottom layer of the stack (the base die, or buffer die) routes signals. A 2,048-bit interconnect is too dense for traditional DRAM processes, so the base die is now built on **advanced logic nodes (such as 4 nm and 5 nm)**.
* **Custom HBM:** Because the base die uses logic processes, companies such as Nvidia can embed control commands, proprietary test circuitry, or even some lightweight compute directly inside the memory stack.
* **Height and 16-high stacks (16-Hi):** Capacities of **48 to 64 GB per stack** and bandwidth beyond **2 to 3 TB/s**.

| Spec | HBM3e | New HBM4 |
| --- | --- | --- |
| **Bus width** | 1,024 bits | **2,048 bits** |
| **Base-die technology** | Conventional DRAM lithography | **Advanced logic lithography (5 nm / 4 nm / 12 nm)** |
| **Maximum DRAM layers** | 12-Hi | **16-Hi** |
| **Capacity per stack** | Up to 36 GB | **Up to 64 GB** |
| **Bandwidth per stack** | About 1.2 to 1.3 TB/s | **More than 2 to 3.3 TB/s** |

---

## 2. TSMC’s strategic, indispensable role

This architectural shift has pulled **TSMC** (the world’s largest foundry) directly into RAM modules:

### 1. Logic base dies for SK Hynix and Micron

Specialist memory makers such as SK Hynix do not have sub-5 nm logic lines. That is why **SK Hynix and Micron partnered with TSMC**. In that arrangement, TSMC fabricates the logic base die on advanced processes (N5 or 12FFC+, for example), and the memory maker stacks its DRAM layers on top.
*(Only Samsung, because it has both a memory business and a logic foundry, has been able to keep the entire chain in-house on its own 4 nm node.)*

### 2. Advanced packaging (CoWoS-L and CoWoS-R)

A 2,048-bit interconnect needs interposers with extremely dense wiring. TSMC has optimized its proprietary advanced packages, **CoWoS-L**, to host as many as 12 HBM4 stacks beside extremely large AI processors (such as Nvidia’s Vera Rubin generation).

### 3. Toward a baseless, direct connection (hybrid bonding)

In later phases of HBM4, layer-to-layer links will move from micrometer-scale copper pillars to **direct copper-to-copper bonding**. TSMC’s 3D bonding (SoIC) brings interconnect thickness down to a few microns and eases the heat-transfer bottleneck between chips.

**Yes, Samsung phones got more expensive too.** In the Galaxy S26 series, Samsung raised the starting price of the S26 and S26 Plus by **$100** (to $899 and $1,099 respectively) and, to offset that jump, dropped the 128 GB base model and made 256 GB storage with 12 GB of RAM the minimum. In the mid-range (Galaxy A series) the pressure was even sharper and squeezed Samsung’s margins hard.

Why Samsung’s chip division did not give RAM away cheap, or free, to its own phone division comes down to corporate governance, international rules, and economic logic:

---

### 1. Independent profit centers (independent P&L)

Samsung Electronics is not run as a single block. It is made of independent units:

* **DS (Device Solutions):** the semiconductor, chip, and memory division.
* **MX (Mobile eXperience):** the phone and tablet division.

Each unit has its own CEO, board, and P&L. Bonuses, rankings, and the survival of chip-division managers depend on selling chips at **the highest possible price** on the open market. DS will not sacrifice its own profit so that MX’s phones can cost less.

---

### 2. Transfer-pricing rules and tax

Under international accounting and tax standards, a transaction between two units of the same holding company must follow the **arm’s-length principle**.
That means the internal selling price must be roughly the same as the price charged to outside customers (Apple or Xiaomi, for example). If the semiconductor division sold RAM to the mobile division at half price:

* Tax authorities would treat it as tax avoidance and artificial profit shifting.
* Regulators and market rivals (Apple, or US and European regulators) would accuse Samsung of **dumping** and unfair competition.

---

### 3. Enormous opportunity cost

Silicon wafer capacity in the fabs is finite. Every production line given over to mobile RAM (LPDDR) is a line that cannot make HBM3e or server memory for Nvidia and Microsoft.
When AI giants will pay enormous sums for every memory chip, handing silicon cheaply to the phone division means **burning billions in profit** for Samsung as a whole.

---

### 4. The mobile division’s diversified supply chain

Samsung’s mobile division (MX), to avoid internal monopoly and dependence on a single supplier, buys about **20 to 30 percent of its RAM from Micron and SK Hynix**. When the global price rises, that whole supply chain gets more expensive, and MX pays Micron’s steep prices too.

---

> **The odd paradox inside Samsung:**
> While Samsung’s chip division (DS) was breaking its own profit records, the mobile division (MX), hit by exploding RAM and chipset costs, saw its margins collapse and even posted a quarterly operating loss — because even internal discounts could not offset a doubling of RAM prices for phones.
