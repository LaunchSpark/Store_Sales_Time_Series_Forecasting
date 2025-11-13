Create a knitable R document for the report

Set it up so that it will compile into a single, polished PDF, HTML, or Word report when knitted.

Make sure it has a clear project title and the full list of team members near the beginning. 

Project Instructions

Follow the required report section order and headings exactly

Problem Statement and Background

Data and Exploratory Analysis

Methods

Tools

Results

Summary and Conclusions

Appendix

At the start of each main section, list who wrote it and their contribution percentages 

Project Instructions

For each section, directly under the heading, write the names of the team members who contributed to that section and the percentage for each.

Ensure that:

Every team member is credited on at least one section plus the Results section.

All percentages in a section add up to 100%.

Everyone on the team agrees to these percentages.

Write the “Problem Statement and Background” section so it fully earns 15/15
In this section, do all of the following:

State clearly and completely what problem you are solving, in plain language.

Explain who cares about this problem and why it is important (impact, real-world relevance, stakeholders).

Describe at a high level where the data comes from and its basic characteristics (for example: what each row represents, what the main variables are, how many records there are), but do not go into detailed cleaning yet.

Define informal success measures for your project (for example: “We will consider the project successful if we reach a certain accuracy, error rate, or other metric” without yet specifying detailed formulas).

Provide background information and a brief summary of related work or similar approaches in competitions, research, or industry.

Mention the competition or data source you are using and note that the full link will appear in the Appendix.

Write the “Data and Exploratory Analysis” section so it fully earns 15/15
In this section, make sure you:

Describe the dataset in detail:

Where you obtained it.

The number of rows and columns.

The main variables and their types (numeric, categorical, etc.).

Explain all data cleaning steps you performed and why you did them (for example: handling missing values, fixing inconsistent categories, removing impossible values).

Discuss any anomalies, outliers, or unusual patterns discovered during exploration and how you handled them.

Describe any imputation or transformations done to make the data usable (for example: replacing missing values, normalizing, encoding categories).

Summarize the exploratory data analysis you performed:

Describe the distributions of important variables.

Describe any relationships or correlations you discovered that informed your modeling choices.

Clearly reference any tables or figures you create (for example: “Figure 1 shows…”, “Table 1 summarizes…”), so that a reader can connect the narrative to the visualizations.

Clearly state what R and data tools were used in this section (but save deeper tool discussion for the Tools section).

Write the “Methods” section so it fully earns 10/10
In this section, make sure you:

Describe every method you attempted, not just the one that worked best.

For each method or model:

Explain what the method is (for example: type of model, algorithm family).

Explain why you chose it based on the problem and your data.

Explain how it connects to the Problem Statement and your success measures.

Clearly identify a baseline model, explaining why it is a reasonable minimal or simple approach to compare against.

Clearly identify your primary model (or models) and why you expected it to perform better than the baseline.

For any methods that did not work well or were abandoned:

Explain how they failed (for example: poor performance metrics, overfitting, instability, too slow, etc.).

Explain what evaluation metric or practical issue led you to stop using them.

Ensure that the explanation is detailed enough that someone reading the report can understand your modeling “story” from first attempt to final choice.

Write the “Tools” section so it fully earns 10/10
In this section, do all of the following:

List all major tools and packages used, besides base R.

Include tools for data cleaning, modeling, evaluation, and visualization.

For each tool or package:

Explain what you used it for (for example: preprocessing, model fitting, plotting, cross-validation, etc.).

Explain why you chose it, connecting back to the problem and the methods (for example: it supports a particular algorithm, it works well with large data, it integrates with other tools, etc.).

Discuss what worked well about each tool and any limitations or frustrations you encountered.

Mention any tools you tried but ultimately did not use, and briefly explain what went wrong or why they were not a good fit.

Write the “Results” section so it fully earns 35/35
This is the most heavily weighted section and must be detailed and clear. Do all of the following:

Clearly state the evaluation metrics you used and why they are appropriate for the problem (for example: accuracy, precision, recall, F1, RMSE, MAE, ROC AUC, etc.).

Present results for the baseline model with the chosen metrics.

Present results for the primary model(s) with the same metrics.

Include tables and/or figures that summarize:

Model performance comparisons.

Any relevant error analyses or diagnostic plots.

Interpret the results in text:

Explain how well each model performed.

Explain how the primary model compares to the baseline (better, worse, similar, and by how much).

Point out any particularly interesting or surprising results.

If relevant, mention runtime or throughput or any other performance-related measures (for example: how long training/prediction takes, whether the method scales to larger data).

Explain what these results mean in the real-world context of the original problem (for example: what does a given accuracy imply for actual users or stakeholders?).

Ensure that every team member has contributed to at least one model’s coding, testing, or documentation and reflect that participation in the section’s contribution note.

Write the “Summary and Conclusions” section so it fully earns 10/10
In this section, ensure it is a self-contained, high-level overview by doing the following:

Summarize the overall goal of the project in one or two clear sentences.

Summarize the most important findings in a concise way, referencing key metrics or qualitative outcomes without repeating all details.

Highlight any unexpected or surprising results and what you learned from them.

Discuss limitations of your approach (for example: data issues, modeling assumptions, computational constraints).

Describe lessons learned during the project, both technically and in terms of process/teamwork.

Suggest future work and improvements, such as:

Methods you would like to try next.

Additional data you would collect.

Ways to improve performance or interpretability.

Make sure that someone who only reads this section can still understand what you did and what the outcome was.

Write the “Appendix” section so it fully earns 5/5
In this section, make sure you:

Provide a link to the repository (for example: GitHub or GitLab) containing all the R scripts and project files needed to reproduce your work.

Provide a link to the data source or competition page you used.

Optionally include any large tables, additional figures, or extra details that support the main text but would clutter the main sections.

Make sure all links are clearly labeled and easy for the instructor to access.

Ensure the entire document meets the grading criteria: Quality, Completeness, Creativity, Grammar 

Project Report and Presentation…


Before knitting, review the entire report and confirm that:

Every required section is present and fully written.

Each section answers all parts of its description from the project instructions. 

Project Instructions

The writing is clear, logically organized, and free of spelling and grammar errors.

The project demonstrates thoughtful choices, interesting analysis, and not just minimal or default methods.

Figures and tables are labeled and referenced correctly in the text.

Check that the document knits successfully and looks professional

Knit the document and confirm that:

All sections appear in the correct order.

Headings, subheadings, lists, tables, and figures are properly formatted.

There are no visible error messages or warnings in the rendered output.

If anything looks confusing or unprofessional, revise the text and layout, then knit again until the report is clean and polished.

If you follow all of these instructions carefully in a knitable R document, your written project report will match the template and rubric requirements and can earn the full 100 points on the report portion.