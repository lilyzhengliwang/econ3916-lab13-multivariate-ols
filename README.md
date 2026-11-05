# econ3916-lab13-multivariate-ols

# Multivariate OLS: What "Controlling For" Actually Does

## Objective
I used simulated data, where the true effects are known, to see what adding a control variable does to a regression coefficient, including when it helps and when it makes things worse.

## Methodology
- Simulated wages that depend on education and on an unobserved ability term, with a true return to education of 2,500. I ran the regression with and without ability.
- Computed the omitted-variable-bias formula (ability's effect on wages times the slope of ability on education) and compared it with the actual bias.
- Recovered the education coefficient with Frisch-Waugh-Lovell: I regressed education and wages each on ability, then regressed the leftover wages on the leftover education.
- Simulated a collider, a variable caused by both the treatment and the outcome, where the true effect is zero, and compared the regression with and without it.
- Simulated two nearly identical regressors to separate what multicollinearity affects (standard errors) from what it does not (the estimates), using VIF and a joint F-test.
- Fitted an interaction between experience and union membership to let the return to experience differ by group.
- Asked an AI to write a specification-table function, revised my prompt once, and checked its coefficients and standard errors against my own regressions.

## Key Findings
- Leaving ability out gave a return to education of 5,126 against a true 2,500. Putting ability in gave 2,546.
- The bias formula predicted a bias of 2,629, and the actual bias was 2,626.
- The Frisch-Waugh-Lovell two-step regression gave the same coefficient as the full regression: 2,546.4985 both ways.
- Controlling for a collider turned a true effect of zero into an estimate of -0.596, with a p-value that printed as 0.000. The same regression without the collider gave 0.001, with a p-value of 0.958.
- Multicollinearity made the standard errors about 12 times larger. The two coefficients still added up to 5.009 against a true 3 + 2 = 5.
- A year of experience was worth 903 to non-union workers and 504 to union members.
- The AI's specification-table function matched my own regressions on every coefficient and standard error once I fixed my prompt. The AI's code was not the cause of the earlier check failure; the failure came from my own cell reusing the name `wage`.
