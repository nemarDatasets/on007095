[![DOI](https://img.shields.io/badge/DOI-10.82901%2Fnemar.on007095-blue)](https://doi.org/10.82901/nemar.on007095)

Dataset of long-term iEEG invasively recorded in epilepsy patients implanted with responsive neurostimulation system  (RNS)
----------
We provided a long-term intracranial electroencephalography (iEEG) dataset of 8 epilepsy patients implanted with responsive neurostimulation (RNS) devices. The dataset was constituted by iEEG data recorded from bilateral epileptic lesion areas.

Each recording contains 90 seconds of dual-channel iEEG around each stimulation, 60 seconds before the start of the stimulation, and about 30 seconds after the end of the stimulation. The stimulation markers are contained in the events.tsv files, including the onset and duration for each stimulus. The ieeg.json files contain the electrical stimulation parameters for the current session, which were set by the neurosurgeon during each regular clinical follow-up of epilepsy patients. 

The iEEG data were saved in EDF format, stored as the Brain Imaging Data Structure (BIDS), and published on the OpenNeuro. The criterion for including patients in this dataset is to intracranially record the seizure events for more than six months. For each subject, one week is considered as a session, which includes all seizures within a day with high frequency seizure onset during that week.

The dataset can be used to evaluate the alterations of seizure onset pattern during the development of epilepsy, as well as the changes in iEEG characteristics after the electrical stimulation. We have technically validated the dataset through specific signal analysis, such as power spectral analysis, calculation of envelop length, and calculation of phase locking value.

## Channel names follow the data headers (18 Oct 2026)

In 1 recordings the channel list of channels.tsv did not equal the data-file header (names, order or count). In the 1 with a different channel count, `mne_bids.read_raw_bids` warned and kept the header names, so the channels.tsv types and bad-channel status reached only the channels whose names happen to be identical; a reader that applies the channels.tsv rows by position gives wrong labels wherever the two lists are not aligned. Since 18 Oct 2026 every channels.tsv lists exactly the header channels, in header order, with the header names (MNE names: duplicated header labels numbered -0, -1).

Rows were matched to header channels BY NAME, never by position (exact; then case/whitespace; then the recorder prefix 'EEG '/'POL ', '_' and zero padding; then a trailing '-<reference>' token). Matched rows keep all their columns (type, units, status, ...); 0 rows took the header name.

1 channels.tsv rows had no channel in the data file (1 files) and were removed; they are kept verbatim under `sourcedata/channels-removed-2026-10-18/` (same relative path). Examples: `sub-02_ses-17_task-seizure_run-19_ieeg.edf`: EEG002,1+,2-.
