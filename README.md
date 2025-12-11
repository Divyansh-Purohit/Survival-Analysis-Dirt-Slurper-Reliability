# Survival-Analysis-Dirt-Slurper-Reliability
Survival analysis of DirtSlurper3100 warranty data — characterizing component lifetimes (Battery, IR sensor, Impact sensor) using Kaplan-Meier estimation, Cox regression, and reliability modeling.

## Key findings from the project description:

Vacuum cleaners registered later in the study period have less opportunity to fail before the study ends, since registration dates span from January 2015 to the end of December 2019. This introduces Type I right censoring: once the study concludes, we cannot observe whether a vacuum cleaner that hadn't yet failed would eventually do so.

To address this censoring, we introduce a new column:

time: For vacuums sent for repair, this represents the number of days between the registration date and the failure date. For vacuums that did not fail during the study period, it represents the number of days between the registration date and 31 December 2019.

This approach handles Type I right censoring appropriately — failed vacuums contribute an observed lifetime, while non-failed vacuums contribute a censored lifetime.
