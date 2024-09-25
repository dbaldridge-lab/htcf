### Documentation
- [HTCF Storage](https://htcf.wustl.edu/docs/storage/)
- [RIS Storage](https://docs.ris.wustl.edu/doc/storage/03_storage.html#designing-a-storage-layout)

### Raw Data
- Backup raw data files to long-term storage (LTS or RIS).
- Add README to raw data folder containing link to relevant Lab Archives pages.

### Processed Data
- After processing, delete large intermediate files that can be re-generated.
- Retain log files in the same folder as the finalized results.
- Regularly backup results to long-term storage using scheduled Globus transfers.
- If you need to keep files on scratch longer than 30 days, use the following command periodically. Update `/scratch/path` to relect the path to the directory containing the files you want to retain. This will update the timestamp to keep files from being deleted by the auto-cleanup policy:
```
find /scratch/path -type f -mtime +1 -exec touch {} \;
```
