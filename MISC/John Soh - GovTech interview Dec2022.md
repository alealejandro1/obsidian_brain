General Questions:
* What's an APPLIED SCIENTIST (Machine Learning) at AWS?

ML Questions:
* In Resume > Marketing Optimization Science: Mentions [[Locality-sensitive hashing]], for high dimensional unsupervised clustering. Can you share how LSH works? why LSH?
* [[Double Machine Learning]] is used to solve the HDB effect on noise by highway.
* In FAQ of readme, he says : "Rich and deep trove of data available for modelling but no time" -> some examples?

# John's Readme:
John prepared in addition the very bare "business slides" a 2 page readme document aimed at technical folks. I think the readme file contains a great summary of the datascience followed. The structure is as follows:
* Overview ~ business goals
* Tenets and Assumptions ~ list down guiding principles for analysis and assumptions on data
* Results ~ share numerical take aways super summarized
* Experimental Setup & Methodology
	* Experimental ~ A table highlighting variables of interest, covariates, baseline methodology (e.g. OLS) and main methodology (Double Machine Learning), Control definition, Treatment Definition
	* Metrics ~ Results and parameters found in both methodology compared
* Conclusion and Next steps ~ Business recommendations for next steps in studying the topic (not on policy)
* Appendix: FAQs ~ self-asked questions to highlight that he is aware of shortcomings:
	* *What trade-offs did you ahve to make when modelling this?
	* *What is your top shortcoming and how do you intend to adress it?*

# John's observation during interview
Seems to be strong on statistics, at least usign correct terms. Mentions a lot
[[covariates]] 

Aspiring to Leadership position (Team lead)

Presentation of Section 2 : 
Preference on iterative approach:
First: use commonly well known approaches that are simple.

Note: He tallks about avoiding "detours" regarding domain knowledge and assumptions of the data.

No Hidden Confounders: "Exchangibility assumption" said by econometrics?
No reverse causation: Safe to assume that the following is not likely "because HDB price change, LTA decides to build expressway"

Contextualized results in term of user perspective (as a buyer of HDB flat), how much money is extra to pay for distance to Expressway. Mention other things that people will pay extra to be near/far something like school.

Explained Counterfactual as: take note of prices of HDB, then go back in time to knock-down expressway and wait for time to pass and measure new price
 --> measure difference of effect. 

OLS: Good enough to know if you are directionally correct, but not good enough to be reliant on this
DoubleMachine Learning: 

Propensity Score Overlap: Good way to understand what's on the ground??

Mention's Bala's curve as feature engineering

Lots of big words, but I feel like some explanations don't really answer question. Part Art/Part Science. --> Avoids questions by saying a lot of lightly related things. --> Potentially better fit for IAPF and not FDT.

Meta learner vs Double Machine Learning? Asked by Victor. Difference in Differences, but issues depend on linear dependence of variables.





