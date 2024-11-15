### Capturing information about software that was used to generate data
Consider outputting the current git commit to logs or capture manually as you process data. 
```
git log -1 --pretty=format:"%h - %s"
```

### Capturing relevant experimental details
At the start of a project, agree how data will be handed back and forth from the experimental team to the data analysis team.

Even if the same person is executing protocols and processing the data for a given project, closely track:
- experimental variables that will inform the analysis
- the original data analysis plan
- how the analysis actually progressed
- interpretation of results
- when results led to subsequent experiments or changes to experimental methods
