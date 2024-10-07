# twolevelr2
Stata module to compute within, between, and overall R-squared in linear two-level models

`twolevelr2` computes the within, between, and overall R-squared for a two-level
model as proposed by [Karlson and Holm (2024)](https://doi.org/10.31235/osf.io/x6gva).

To install `twolevelr2` from GitHub, type

    . net from https://raw.githubusercontent.com/benjann/twolevelr2/main/
    . net install twolevelr2, replace

in Stata. Stata version 14.2 or newer is required.

---

Example:

    . use https://www.stata-press.com/data/r18/gsem_nlsy
    (NLSY 1968)
    
    . twolevelr2 ln_wage i.union grade ttl_exp tenure c.tenure#c.tenure, i(idcode)
    (level 1 predictors: 1.union ttl_exp tenure c.tenure#c.tenure)
    (level 2 predictors: grade)
    (omitted predictors: 0b.union)
    (estimating 10 pairwise models .......... done)

        Number of obs    =     1,885
        Number of groups =       405

    --------------------------------
               R-squared |   ln_wage 
    ---------------------+----------
        Within (level 1) |  .1582091 
       Between (level 2) |  .4048272 
                 Overall |  .3032047 
    --------------------------------

---

Changes:

    07oct2024
    - level-one weights were ignored in _l2zero subroutine; this is fixed
    - removed undocumented -plugin- option

