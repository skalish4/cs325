# Part A — Project 1 Test Cases

These are manual acceptance test cases for Project 1, the resume-to-job matching tool. The original Project 1 executable was not available for these tests, so **Actual Results: Not executed** and **Status: Suspended**. Do not mark as Passed until the application has been tested.

## TC-01 — Valid PDF resume yields ranked job matches

- **Priority:** High
- **Test Case ID:** TC-01
- **Test Date:** November 17, 2026
- **Test Conditions:** One-page readable PDF listing Python, SQL, and data analysis skills. Preloaded jobs: Python Data Analyst (Python/SQL/data analysis); Front-End Developer (JavaScript/CSS); Customer Support (phone support).
- **Test Designed By:** Sam
- **Test Executed By:** Not yet run
- **Execution Date:** Not yet run
- **Pre conditions:** ResumeMatch application running, resume parser available, job records loaded.
- **Test Description:** Confirm that parsing a valid resume shows ranked job results relevant to its skills.

| Test # | Step Details | Expected Results | Actual Results | Pass / Fail / Suspended |
|---|---|---|---|---|
| 1 | Open the ResumeMatch app. | Upload page appears. | Not executed. | Suspended |
| 2 | Upload sample_resume.pdf containing Python, SQL, data analysis. | Valid PDF accepted and parsed. | Not executed. | Suspended |
| 3 | Run matching against three seeded job descriptions. | Matching results appear. | Not executed. | Suspended |
| 4 | Inspect job ranking. | Python Data Analyst ranks above the other two. | Not executed. | Suspended |

## TC-02 — Corrupt PDF rejected without crashing

- **Priority:** High
- **Test Case ID:** TC-02
- **Test Date:** November 17, 2026
- **Test Conditions:** corrupt_resume.pdf contains plain text "not a real PDF" rather than PDF bytes.
- **Test Designed By:** Sam
- **Test Executed By:** Not yet run
- **Execution Date:** Not yet run
- **Pre conditions:** ResumeMatch app and parser running; invalid file ready.
- **Test Description:** Confirm corrupt resume upload shows a useful error and lets the user recover.

| Test # | Step Details | Expected Results | Actual Results | Pass / Fail / Suspended |
|---|---|---|---|---|
| 1 | Make a text file with "not a real PDF" and name it corrupt_resume.pdf. | Invalid input ready. | Not executed. | Suspended |
| 2 | Upload corrupt_resume.pdf in ResumeMatch. | App attempts to validate/read it. | Not executed. | Suspended |
| 3 | Attempt to match jobs using the corrupt upload. | User-friendly invalid PDF error; no fabricated matches. | Not executed. | Suspended |
| 4 | Upload a good PDF afterward. | App accepts another file without crashing. | Not executed. | Suspended |
