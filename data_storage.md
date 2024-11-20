### Documentation
- [HTCF Storage](https://htcf.github.io/docs/storage/)
- [RIS Storage](https://docs.ris.wustl.edu/doc/storage/03_storage.html#designing-a-storage-layout)

### Raw Data
- Backup raw data files to long-term storage (LTS or RIS).
- Add README to raw data folder containing link to relevant Lab Archives pages.

### Processed Data
- Consider outputting intermediate data to a seperate temp folder and backup or touch these files as needed.
  - If you need to keep files on scratch for longer than 30 days, use the following command periodically. Update `/scratch/path` to relect the path to the directory containing the files you want to retain. This will update the timestamp to keep files from being deleted by the auto-cleanup policy:
```
find /scratch/path -type f -mtime +1 -exec touch {} \;
```
- After processing, delete large intermediate files that can be re-generated. 
- Retain log files, preferably in the same folder as the finalized results.
- Regularly backup results to long-term storage using scheduled Globus transfers.

### Check size of files
```
du -sh /path/to/project_directory/
```

### Globus Timer Options

Use automated Globus transfers to regularly backup the results on scratch to long term storage.

1. Select the "Transfer & Timer Options" dropdown.
2. Check the following options:
   sync - only transfer new or changed files
   preserve source file modification times
   encrypt transfer
   (optional) Disable success notification to avoid flooding your inbox
3. Set Repeat to every 1 days
4. end never (note: user setting up the timer will need to reauthenticate at least every 30 days for the timer to remain active)

Note that if you move or rename files in a directory backed up using these options, both copies will be retained at the destination. 

### Data Compression
Do not decompress .gz files unless absolutely necessary. Most bioinformatic tools accept gzipped files as input.

Use zcat if you need to view compressed files.
```
zcat Sample_Yeast_L005_R1.cat.fastq.gz | head
```

Be mindful that compressing/decompressing large files is I/O intensive.

