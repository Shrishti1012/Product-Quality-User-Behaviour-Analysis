# Product Quality & User Behaviour Analysis

## Project Overview

This project analyses user behaviour in a speech transcription workflow to identify patterns that may indicate poor-quality or low-effort transcription.

The analysis focuses on task completion behaviour, listening time, and editing behaviour to identify potential warning signals. Based on these findings, a data-driven monitoring framework was proposed to help identify potentially problematic transcribers while reducing the risk of false positives.

---

## Objective

The objective of this project was to:

- Identify behavioural warning signs that may indicate poor-quality transcription
- Analyse patterns in task completion and transcription editing behaviour
- Develop measurable indicators for identifying potentially suspicious activity
- Design a fair and data-driven system for monitoring problematic transcribers

---

## Analysis Workflow

The project followed the following approach:

**Raw Data → Data Exploration → Feature Creation → Behaviour Analysis → Warning Signals → Monitoring Framework**

---

## Data Analysis

The provided transcription dataset was analysed using Microsoft Excel.

Additional calculated columns and metrics were created to explore user behaviour and identify potential quality-risk patterns.

The analysis included:

- Audio duration and task completion time
- Listening behaviour
- Editing behaviour
- User-level task patterns
- Fast task completion behaviour
- Combined behavioural signals

---

## Key Metric: Listening Ratio

To fairly compare tasks with different audio durations, a new metric called the **Listening Ratio** was created:

**Listening Ratio = Time Taken by User ÷ Audio Duration**

This metric helped identify tasks that were completed unusually quickly compared with the duration of the audio.

A Listening Ratio below **0.5** was treated as a potential warning signal, meaning that a task was completed in less than half of the audio duration.

However, fast completion alone was not considered sufficient evidence of poor-quality work.

---

## Key Warning Signals

### 1. Extremely Low Listening Time

A transcriber repeatedly completing tasks significantly faster than the audio duration may indicate rushed work or insufficient audio verification.

However, a single fast task can have legitimate explanations, such as:

- Simple or short audio
- Experienced transcribers
- Faster audio playback
- Accurate and easy-to-verify transcription

Therefore, repeated behaviour was considered more meaningful than an individual task.

### 2. Fast Submission Without Editing

A stronger behavioural signal was identified by combining:

**Listening Ratio < 0.5 + No Editing of Whisper Transcription**

This pattern may indicate that a transcriber submitted AI-generated transcription without sufficiently reviewing the audio.

However, this was also treated as a warning signal rather than direct evidence of poor-quality work because an AI-generated transcription may sometimes already be accurate.

---

## Proposed Monitoring Framework

Instead of blocking a transcriber based on a single suspicious task, a multi-stage monitoring system was proposed.

### Stage 1: Task-Level Flag

A task receives a warning flag when:

**Listening Ratio < 0.5 AND is_edited = No**

The task is flagged for monitoring, but no immediate account-level action is taken.

### Stage 2: User-Level Monitoring

The platform should analyse repeated behaviour across multiple completed tasks.

A user-level metric can be calculated as:

**Fast No Edit Rate = Fast No Edit Tasks ÷ Total Completed Tasks**

The analysis recommended observing at least **10 completed tasks** before making an account-level decision.

If **50% or more** of a user's tasks show the Fast No Edit pattern, the user can be classified as high risk and selected for further review.

### Stage 3: Quality Review

For high-risk users, a sample of completed transcription tasks should be reviewed against the original audio.

This helps distinguish genuinely poor-quality work from users who simply work efficiently.

### Stage 4: Action or Blocking Decision

Account restrictions or blocking should only be considered when:

- Suspicious behaviour is repeatedly observed
- The pattern persists across multiple tasks
- A quality review confirms transcription inaccuracies
- The behaviour continues after a warning or intervention

---

## Key Learning

The analysis demonstrated that a single behavioural metric should not be used to make an account-level decision.

Fast task completion does not necessarily mean poor-quality transcription, and not editing an AI-generated transcription does not automatically indicate that the output is incorrect.

A more reliable system should combine:

**Repeated Behaviour + Multiple Risk Signals + Actual Quality Review**

This approach can help identify potentially problematic behaviour while reducing false positives and avoiding unfair action against efficient transcribers.

---

## Tools Used

- Microsoft Excel
- Data Analysis
- Behavioural Pattern Analysis
- Data-Driven Decision Making

---

## Repository Contents

### Raw Transcription Data

The original dataset used for the analysis.

### Transcription Behaviour Analysis

The Excel analysis file containing additional calculated columns, derived metrics, and analysis of transcription behaviour.

### Transcription Quality Monitoring Report

The final report containing the identified warning signals and the proposed monitoring and decision-making framework.

---

## Conclusion

This project demonstrates how behavioural data can be transformed into meaningful product and operational insights.

Rather than relying on a single suspicious activity, the proposed approach uses repeated behavioural patterns and quality verification to support more reliable decision-making.

The project highlights the importance of combining data analysis with practical product thinking when designing systems that monitor user behaviour and quality risks.
