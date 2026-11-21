# Academic Year 2023–24 Enrollment Overview

Fall 2023 (20233), Spring 2024 (20241), Summer 2024 (20242).

## GitHub: start here

1. Create a NEW blank public repository: iya-academic-year-2023-24-overview. Confirm the name says 2023-24 before uploading.
2. Extract Academic_Year_2023_24_Dashboard.zip using Extract All. Open the folder academic-year-2023-24-overview INSIDE it.
3. Upload these nine root files: README.md, app.js, data.json, index.html, netlify.toml, overview.js, sources.json, styles.css, tests.js. Click Commit changes. Do not upload the ZIP or the enclosing folder.
4. Add file → Create new file. Name it scripts/refresh-data.js. Open the local scripts/refresh-data.js using Notepad, copy all text, paste into GitHub, and commit. Do not double-click a .js file to run it.
5. Return to the repository main page. Add file → Create new file. Name it .github/workflows/refresh-data.yml. Copy the text from the matching local .github/workflows/refresh-data.yml using Notepad, paste, and commit. Do not commit an empty editor.
6. Actions → Refresh 2023-24 historical snapshots → Run workflow → main. Wait for a green check on the newest run. Source outages are recorded on the dashboard, so inspect the semester cards too.

## Netlify

1. Add new project → Import an existing project → GitHub → iya-academic-year-2023-24-overview. If missing, Configure the Netlify app on GitHub and add access to this repo while keeping existing selections.
2. Project name: iya-academic-year-2023-24. Branch: main. Base directory: blank. Build command: node scripts/refresh-data.js. Publish directory: one period (.). Node 22. No environment variables or dependencies needed.
3. Deploy. Check the 2023–24 title, all three terms, annual enrollment and section totals, program dropdown and search.

## Data and verified totals

Retrieved 2026-11-20T23:51:15.798Z from USC's public CoursesByTermSchoolProgram endpoint with school=ACAD and each of ACAD, IDSN, PRIN for all three term codes. Empty PRIN summer results are valid, not missing data.

| Metric | Fall 2023 | Spring 2024 | Summer 2024 | Annual |
|---|---:|---:|---:|---:|
| Students Enrolled (course registrations) | 936 | 1028 | 104 | 2068 |
| Credit Hours / Units | 3015 | 3336 | 303 | 6654 |
| Sections | 52 | 60 | 11 | 123 |
| Available Seats | 382 | 566 | 126 | 1074 |
| Seat Capacity | 1317 | 1589 | 230 | 3136 |

Annual utilization: 65.9%. 63 distinct prefix+number course rows. Students Enrolled is NOT unique student headcount. Historical API counts are not verified census-date or certified final enrollment.

Count section identifiers by termCode:sectionNumber. Cross-listing duplicates count once under their scheduled ACAD/IDSN/PRIN prefix. Courses scheduled by other schools, cancellations, missing counts and nonpositive capacities are excluded. One summer section is excluded; its reason is retained in data.json. Available seats sum max(capacity-enrolled,0) per section, so overfilled sections do not subtract from other sections' open seats. That is why open seats may differ from aggregate capacity minus enrollment.

SCH uses enrolled × one published fixed-unit value. Variable/unknown units are omitted from SCH but stay in enrollment counts; known zero units contribute zero. Currently 28 counted sections representing 47 registrations are omitted from SCH. Course letter suffixes are preserved.

Daily refresh at 15:25 UTC, manual Actions refresh, and Netlify build refresh are included. Retrieval timestamps indicate when the API was queried, not when USC updated historical records. Failures preserve a labeled prior snapshot. Missing terms block annual totals. Retrievals over 48 hours old are marked outdated. Check Actions if a public-repository schedule is disabled after extended inactivity.

## Checks and preview

Node 22: node tests.js. Source/row/course sums, summer inclusion, missing terms, unique section identifiers, fixed/unknown units, stale status, and failure retention passed. All four program filter states and annual sections were checked in the rendering code. Browser visual inspection was not repeated for this reused layout.

A separate Academic_Year_2023_24_Preview.html is a double-clickable standalone snapshot. It does not refresh automatically. Existing dashboards and repositories are unchanged.
