---

slug: industrial-water-pump-emc-fix
title: EMC Troubleshooting for an Industrial Electric Water Pump
seoTitle: EMC Troubleshooting for an Industrial Electric Water Pump | Linkon Tech
seoDescription: Learn how EMC problems in an industrial electric water pump were identified and reduced through common-mode chokes, capacitors, and BDL filters.
desc: A practical EMC troubleshooting case study for a high-power industrial electric water pump.
image: /images/blog/industrial-water-pump-emc-fix/cover.jpg
imageFit: cover
cardImageFit: contain
publishedAt: 2026-04-19
author: Linkon Tech
-------------------

Industrial electric water pumps often use high-speed motors and long cable routing, which can easily create EMC problems.

In this case, the product was a high-power industrial electric water pump with motor power above 200 W.

The product consisted of four main sections:

* control board
* motor
* protective housing
* impeller

The motor used a waterproof sealed design and could run at very high speed.

![Industrial Water Pump](/images/blog/industrial-water-pump-emc-fix/pump-overview.jpg)

## Initial EMC Investigation

EMC problems cannot be directly observed.

To find the real interference source, near-field probing inside a chamber was used.

This helped identify where the strongest radiation was generated and how the noise was coupled to the outside.

The near-field measurement result in the vertical direction is shown below.

![Figure 1. Near-field measurement result – vertical direction](/images/blog/industrial-water-pump-emc-fix/figure1-vertical-nearfield.jpg)

The near-field measurement result in the horizontal direction is shown below.

![Figure 2. Near-field measurement result – horizontal direction](/images/blog/industrial-water-pump-emc-fix/figure2-horizontal-nearfield.jpg)

## Root Cause Analysis

During dark-room testing, the product was powered directly by a laboratory DC power supply.

Because of this, power-supply noise could be excluded.

The main problem was identified as motor-generated noise.

When the motor rotates, the brushes create sparks at the commutator.

These sparks generate high-frequency noise, which can then radiate outward through the motor cable and housing gaps.

## Initial Solution Used by the Customer

The customer first used a conventional EMI filter approach.

This included:

* a ferrite rod inductor (3 uH) placed in series with the positive and negative supply lines
* two X capacitors (2.2 nF) connected between the power lines
* two Y capacitors (2.2 nF) connected from the power lines to ground

![Conventional EMI Filter Used by Customer](/images/blog/industrial-water-pump-emc-fix/customer-filter-solution.jpg)

The basic operating principle is shown below.

* The ferrite rod inductors help absorb differential-mode noise on the cable.
* The X capacitors reduce the differential-mode current path.
* The Y capacitors reduce common-mode current by providing a return path to ground.

![X Capacitor and Y Capacitor Current Paths](/images/blog/industrial-water-pump-emc-fix/x-y-capacitor-principle.jpg)

The actual EMC test results are shown below.

![Figure 3. Conventional solution – vertical direction](/images/blog/industrial-water-pump-emc-fix/figure3-conventional-vertical.jpg)

![Figure 4. Conventional solution – horizontal direction](/images/blog/industrial-water-pump-emc-fix/figure4-conventional-horizontal.jpg)

The conventional solution showed some improvement.

However, although the horizontal result could pass, the vertical direction still exceeded the limit.

The main reasons were:

1. The capacitor values were not optimized.
2. For common-mode noise, Y capacitors alone were less effective than a dedicated common-mode choke.

## Improved Solution 1: Add a Common-Mode Choke

To reduce low-frequency noise in the vertical direction, a common-mode choke was added in series with the power line.

The part used was TLDCM1211-2-701TF.

The result is shown below.

![Figure 5. Vertical result after adding a common-mode choke](/images/blog/industrial-water-pump-emc-fix/figure5-common-mode-vertical.jpg)

The common-mode choke reduced part of the low-frequency noise.

However, there was still room for further improvement.

## Improved Solution 2: Add a BDL Filter

A BDL filter was then added between the power lines.

The vertical result is shown below.

![Figure 6. Vertical result after adding the BDL filter](/images/blog/industrial-water-pump-emc-fix/figure6-bdl-vertical.jpg)

The horizontal result is shown below.

![Figure 7. Horizontal result after adding the BDL filter](/images/blog/industrial-water-pump-emc-fix/figure7-bdl-horizontal.jpg)

The BDL filter gave much better suppression performance.

Compared with the conventional capacitor-and-inductor method, the BDL filter provided a better overall reduction of motor EMI.

Its advantages included:

* better filtering performance across a wider frequency range
* lower total solution cost
* replacement of multiple discrete components with a single device
* easier SMT assembly and lower manual labor cost
* simpler manufacturing process
* less dependence on shielding and magnetic rings

The internal structure of the BDL filter is shown below.

![Figure 8. Internal structure of the BDL filter](/images/blog/industrial-water-pump-emc-fix/figure8-bdl-structure.jpg)

## Conclusion

This case shows that industrial motor EMC problems are often caused by brush-generated common-mode noise.

Although traditional X capacitors, Y capacitors, and ferrite inductors can help, they may not be enough for more severe EMI problems.

For motor-driven products, adding a common-mode choke or using a dedicated BDL filter can significantly improve EMC performance.

In practical EMC troubleshooting, tools such as dark-room testing, spectrum analyzers, oscilloscopes, and near-field probes are critical.

Only after the real interference path is identified can an effective solution be selected.

