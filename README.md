# COGS 164 - Doodle Game Experiment (WI 2026)

### Our main structure:
- intrinsic.html = game code for intrinsic condition → public server INTRINSIC webgame.io
- extrinsic.html = game code for extrinsic condition → public server EXTRINSIC webgame.io
- wrapper.html = CORE wrapper file that manages the conditional, randomly assign participants to INTRINSIC webgame.io OR EXTRINSIC webgame.io

### Data collection path:
DataPipe → OSF (164 Doodle Experiment - exported data) → csv file for each participant

### Data analysis:
Merge csv files into one → clean data into an organized dataframe → use R to generate plots → statistical analysis (one-way ANOVA, between-subjects t test)

```
wrapper.html
│
├── 1. Fullscreen Trial
│      └── Switch participant to fullscreen mode
│
├── 2. Instructions Trial
│      └── Display experiment instructions
│
├── 3. Game Trial (iframe embedded in jsPsych)
│      ├── Randomly assign condition
│      │
│      ├── If condition === "intrinsic"
│      │      └── Load intrinsic.html
│      │
│      └── If condition === "extrinsic"
│             └── Load extrinsic.html
│
├── 4. Debrief Trial
│      └── Display completion message
│
├── 5. Save Data (jsPsychPipe → OSF)
│      ├── Generate subject_id
│      ├── Attach condition to dataset
│      └── Upload CSV file to OSF project
│
└── 6. Exit Fullscreen
       └── Return browser to normal view
```