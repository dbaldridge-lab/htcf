### Document names and versions of software used to generate data
Print software versions in logs if the software does not do this by default.

For scripts created by the data analysis team, consider outputting the current git commit to logs or capture manually as you process data. 
```
git log -1 --pretty=format:"%h - %s"
```

Keep records of the environment setup and resources used when the code was executed.

### Capture relevant experimental details
At the start of a project, agree how data will be handed back and forth from the experimental team to the data analysis team.

Even if the same person is executing protocols and processing the data for a given project, closely track:
- experimental variables that will inform the analysis
- the original data analysis plan
- how the analysis actually progressed
- interpretation of results
- when results led to subsequent experiments or changes to experimental methods

Our lab has a template stored in Lab Archives that provides a framework for documenting these items. 
- Relevant communications, equipment printouts, and notebooks(e.g. .ipynb) are attached
- A README with a link to this document is placed in the relevant raw data directory
Ideally, a new document should be created for each sequencing submission. It is essential if the data is intended for publication. 

### Make a data management plan
Document:
- where raw, processed, and finalized data sets will be stored
- what data --if any-- will be version controlled and how (Box or git)
- policies for handling sensitive data
- file naming conventions
- estimation of project data quota
