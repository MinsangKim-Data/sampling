# ASSIGNMENT: Sampling and Reproducibility in Python

Read the blog post [Contact tracing can give a biased sample of COVID-19 cases](https://andrewwhitby.com/2020/11/24/contact-tracing-biased/) by Andrew Whitby to understand the context and motivation behind the simulation model we will be examining.

Examine the code in `whitby_covid_tracing.py`. Identify all stages at which sampling is occurring in the model. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?

Modify the number of repetitions in the simulation to 1000 (from the original 50000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.

Alter the code so that it is reproducible. Describe the changes you made to the code and how they affected the reproducibility of the script file. The output does not need to match Whitby’s original blogpost/graphs, it just needs to produce the same output when run multiple times

# Author: Minsang Kim

```
This simulation is creating a population of 1000 people who attend two types of events (200 people at weddings and 800 people at brunches). This is done at event sampling with initial setup of the ppl Dataframe, created with 1000 rows, each reperesenting a person attending one of the two events. The sampling frame is the entire ppl Dataframe, representing all 1000 people. For the infection sampling stage, the sampling frame is the same but the sample size is determined randomly with the np.random.choice() function to select 10% of the 1000 people population to be infected. This uses a binomial distribution, where each person has 10% probability of being selected. Then in primary trace and secondary trace, the code uses ppl.loc[ppl['infected'], 'traced'] and events_traced to determine the people who are primary traced and secondary traced.

The code running with the original whitby_cvodi_tracing.py results in a overlaid distribution graph of infections from weddings (in blue) and traced to weddings (in red). It is similar to the article in the sense that the traced/observed distribution strays to the right of the true distribution of infections. The graph outputted has the observed/traced distribution mean approximately at 0.25 whereas the true is around 0.2. The original article has the observed distribution mean approximately at 0.5, more than double of the true distribution, signifying significant bias and overestimation with the observed method of sampling or collecting information about tracing. 

After modifying the python script to run 1000 times there is quite a lot more variability in the observed/traced distribution and the mean starts to vary up and down from 0.2. But like before, the variability or range of data seen is greater with the observed/traced sampling as opposed to the true distribution.

To lock down the reproducibility, we use a random seed (np.random.seed(42)) around the beginning of the code block in order to achieve reproducbility with the distribution graph, especially with a lower repetition of 1000 times instead of 50000. 




 Identify all stages at which sampling is occurring in the model. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

```


## Criteria

|Criteria|Complete|Incomplete|
|--------|----|----|
|Altercation of the code|The code changes made, made it reproducible.|The code is still not reproducible.|
|Description of changes|The author explained the reasonings for the changes made well.|The author did not explain the reasonings for the changes made well.|

## Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `HH:MM AM/PM - DD/MM/YYYY`
* The branch name for your repo should be: `sampling-and-reproducibility`
* What to submit for this assignment:
    * This markdown file (sampling_and_reproducibility.md) should be populated.
    * The `whitby_covid_tracing.py` should be changed.
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sampling/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `sampling-and-reproducibility`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-3-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
