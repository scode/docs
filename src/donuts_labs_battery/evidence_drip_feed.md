# Evidence drip feed

## Mar 9 2026 - Self-discharge

VTT report: [VTT_CR_00125_26.pdf](20260309_self_discharge/VTT_CR_00125_26.pdf)

Their [video](https://www.youtube.com/watch?v=77kF5GEnQM8) had this wording:

> As in previous tests, the test starts with the same 1C capacity test to show the cell is exactly the same as our other
> test articles.

I'm skeptical that simply having a capacity test is sufficient to prove the cells are equivalent, though I'm not a
battery expert. It's probably a good indication but it doesn't strike me as impossible to artificially produce a similar
behavior across this one dimension in different kinds of cells. I keep harping on this because the _same cell_
performing well across all the claimed dimensions is critical to the veracity of the overall claim here.

This time there is, however, a little more clarity in the wording in the VTT report:

> Three visually identical cells were provided for testing and labeled DL1, DL2, and DL3. Each cell was subjected to
> different tests conducted in parallel, all of which began with an initial capacity test. This report presents the
> results of the self‑discharge tests performed on cell DL1.

I think this is more explicitly (than in past reports) that there is a single set of three cells provided to VTT for use
across all the tests that they are trickling results out from.

Note that it still does not tell us whether VTT was instructed which cell to use for which tests, or whether it was up
to VTT to make that choice.

Regarding the self discharge test, quoting the report:

> Cycle 1: The cell was charged at a constant current of 24 A until a charge throughput of 6.668 Ah was reached,
> followed by a one‑hour idle period. The cell was then charged again at 24 A to an additional 6.667 Ah, corresponding
> to a total state of charge of approximately 50 %. Subsequently, a 240-hour idle period at ambient temperature was
> initiated. During the idle period, the cell voltage was recorded at a sampling interval of 10 s. After the idle
> period, the cell was discharged at 24 A current until the voltage reached 2.7 V. At the end of the tests, the cell was
> charged to approximately 25 % state of charge before it was disconnected.

It is unclear to me why a 50% state of charge was chosen, and who made that choice. For real life applications it would
matter a lot if the self discharge rate was much higher at higher states of charge, so I would expect either tests based
on a very high state of charge or alternatively one at a high level and one at a lower. Because the test only addresses
50%, it leaves it open that the self discharge rate could be very high at higher states of charge.

## Mar 2 2026 - High Temperature performance

VTT report: [VTT_CR_00124_26.pdf](20260302_high_temp_capacity/VTT_CR_00124_26.pdf)

I was specifically looking for any clear conformation that the cell being tested is the same physical sample as
participated in the previous test because on top of the individual claims about this battery, it matters more than
anything else that they can all be achieved by the _exact same battery_ (demonstrating the properties they have claimed
independently for different units is much less interesting). Quoting from the report:

> The aim of the project was to conduct independent high-temperature discharge performance tests on the energy storage
> device supplied by the customer, which the customer identified as a solidstate battery cell. Three visually identical
> cells were provided for testing and labeled DL1, DL2, and DL3. Each cell was subjected to different tests conducted in
> parallel, all of which began with aninitial capacity test. This report presents the results of the high‑temperature
> discharge tests performed on cell DL2.

And slightly later:

> All tests described in this report were carried out on the same cell, in accordance with the customer’s test plan.

And in the conclusion:

> This project included an independent high-temperature discharge performance test on an energy storage device supplied
> by the customer, which the customer identified as a solid-state battery cell.

Given this wording my take is that:

- There is NO explicit confirmation that Donut Labs is not providing a different cell or set of sells for each test.
- However, the _charitable_ interpretation appears to me to be that that VTT was given 3 cells in total to perform a
  number of tests - given that they do explicitly say 3 cells in this report, yet also say only one cell was used for
  tests. The wording around parallel tests also strongly, to me, indicates they are referring to parallel tests that
  will produce different reports.
- However, no such wording appears in the previous report.
- Additionally, this means Donut Labs could have presented VTT with three visually similar but different units. There is
  no confirmation of weather VTT or Donut Labs prescribed which cell was used for which test. If Donut Labs made that
  pick, merely presenting the units ahead of time doesn't help the case.

Overall this test seems very clearly aimed at manufacturers who will have have concerns on what kind of cooling is
required to integrate a battery in their product.

Updates since initial writing:

- https://www.youtube.com/watch?v=AzIpgYi4rjM - another good Two Bit da Vinci video

## Feb 23 2026 - Charging speed

VTT report: [VTT_CR_00092_26.pdf](20260223_c_rate_heat_test/VTT_CR_00092_26.pdf)

Initially written: Feb 24 2026

My commentary:

- A perfect 11C rate would by definition imply a 5m27s 0-100% charging time.
- The report states that a 11C rate test was made, but the speed was slower, indicating the 11C was not reached.
  - Best 0-80%: 4m27s, which implies average C rate of 10.8
  - Best 0-100%: 7m18s, which implies an average C rate of 8.2
- The tests were all done using passive cooling.
- From memory, I believe Donut has stated at least in one interview that the 5 minute charging time is only expected
  with active cooling. This makes sense and explains they they are quoting "less than 10" minutes for the motorcycles,
  which are claimed to be passively cooled. (This bullet is not from the report, it's me providing context.
- It is possible that a C rate of 11 or a higher could be achieved with active cooling, but that is speculation.
- It is unclear to me:
  - Why did they not run an active cooling test? On the presumption that they have what they claim, I would have
    expected that they would want to demonstrate that rather than release numbers that will look worse than claims.
  - Why was 11C picked? Did VTT pick this, or Donut? If Donut, why would they choose a C rate which, even if achieved,
    would not meet the target 5 minutes 0-100% time? There is no wording I can find that explains the choice of C rate.

_Strictly_ speaking these results, contrary to what youtubers are saying, do not contradict their claims because it is
possible a higher C rate could be achieved with active cooling. If this is the case and they still chose to drip feed a
result that is so obviously going to be interpreted as less than their claim, that's a very questionable move.

Other concerns:

- They are drip feeding one piece of evidence at a time. Will we get verification that future tests, presumably by VTT,
  are made with the _same battery packs_? Otherwise it's not very useful since producing a battery that does really well
  in one dimension at a time is vastly less likely/hard than producing a battery that does well in all dimensions at the
  same time. In the next report I want to see VTT explicitly state that they are still testing the same battery unit as
  the earlier tests.

Updates since initial writing:

- https://www.youtube.com/watch?v=3PwEA-tBufI is a good video with a deep analysis.
