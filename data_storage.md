### Documentation
- [HTCF Storage](https://htcf.wustl.edu/docs/storage/)
- [RIS Storage](https://docs.ris.wustl.edu/doc/storage/03_storage.html#designing-a-storage-layout)

### Raw Data
- Backup raw data files to long-term storage (LTS or RIS).
- Add README to raw data folder containing link to relevant Lab Archives pages.

### Processed Data
- After processing, delete large intermediate files that can be re-generated.
- Retain log files, preferably in the same folder as the finalized results.
- Regularly backup results to long-term storage using scheduled Globus transfers.
- If you need to keep files on scratch for longer than 30 days, use the following command periodically. Update `/scratch/path` to relect the path to the directory containing the files you want to retain. This will update the timestamp to keep files from being deleted by the auto-cleanup policy:
```
find /scratch/path -type f -mtime +1 -exec touch {} \;
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


