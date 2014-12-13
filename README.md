stata-last-exam
===============
use "/Users/pitraharun/Downloads/Growth.dta"
sum growth
sum tradeshare
sum assasinations
sum oil

twoway scatter growth tradeshare

graph twoway (lfit growth tradeshare) (scatter growth tradeshare) *** line fit and scatter plot

reg growth tradeshare
predict growthhat *** retrieve predicted values
predict ehat, resid *** retrieve residuals

twoway scatter ehat tradeshare

gen etradeshare = ehat*tradeshare
gen egrowth = ehat*growth

sum etradeshare
sum egrowth

reg growth tradeshare if rev_coups == 0
reg growth tradeshare if assasinations != 0 

clear
exit

log close
