---
title: "Data Analysis"
date: 2020-09-10
featured: true
weight: 19
---

Looking into a large and complex set of data to draw statistical inferences.

I've spent a lot of time playing with data.
It might not qualify as data science in that I haven't used machine/deep learning, rather I've coded pipelines to regroup, label and visualise raw data.
Proper visualisation of a noisy and complex database goes a long way in revealing hidden patterns or anomalies.

My favourite language used to be _Matlab_, but to do my PhD, I learnt _Python_ and now I do not want to go back!
Below, I elaborate how the things I have done and my tools of choice.


# Python _3.x_
The personal experience of moving to Python from Matlab belongs to another place _[coming soon]_.
In my PhD, I used [Anaconda environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) for each project to meet the dependencies and avoid conflicts, which frequently happen in the python ecosystem and are devastating.

# Jupyter notebooks
[Notebooks](https://jupyter.org/) are awesome for tinkering, which is most of what one does when performing new analyses or developing new tools.
I extensively used [Jupyter Lab](https://jupyterlab.readthedocs.io/en/stable/) to develop a complete data processing pipeline in Python, incorporating behavioural, video, and electrophysiological data (see an [example](/cv/ephy)) and generate fully reproducible publication-ready figures.

Our experimental setups saved the raw position and other behavioural measures in _text_ files.
These data were automatically imported, synchronised, pre-processed and saved as python-native _pickle_ files (`*.p`).
These files were used to visualise the data, enabling me to monitor the ongoing experiments, and at the end, to produce the final publication figures, without any human interference in the inclusion or exclusion of animals and/or sessions.

# Publication-ready plotting
I used _Matplotlib_ to generate figures as PDF files that will be directly inserted in the final manuscript, that is without **any** manipulation, thus promoting reproducible science.
Take a look at the relatively complex figure below.

<object data="/images/skills/data-analysis/Task_Example_Group.pdf" type="application/pdf" width="600px" height="450">
    <embed src="/images/skills/data-analysis/Task_Example_Group.pdf" type="application/pdf">
        <p>This browser does not support PDFs. Please download the PDF to view it: <a href="/images/skills/data-analysis/Task_Example_Group.pdf">Download PDF</a>.</p>
    </embed>
</object>

Note that every part of the figure (other than histological images) is vectorised, meaning that zooming would not impair the visual quality.

![zoomed in section](/images/skills/data-analysis/zoomed.png)

Also, _Panel A_ has been designed in a graphical software and programmatically embedded in the final figure for increased repeatability.

![zoomed in panel A](/images/skills/data-analysis/panelA.png)

All of the above, in addition to the practice of openly sharing the database as well as the codebase, for instance through the [Open Science Foundation](https://osf.io/), contribute to _open science_ and improved reproducibility.

# Statistical inference

[...]