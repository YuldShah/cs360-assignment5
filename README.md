# CS360 Assignment 5 - Maintenance: handling a bug report

Student: Shahriyor Yuldashev  
Student ID: 240416  
GitHub: [YuldShah](https://github.com/YuldShah)

## How to run

```bash
npm install
npm test
npm start
```

`npm start` serves the transcript API at `http://localhost:4001`.

## Tickets

| Ticket | Issue | Branch | Pull request | Fix |
| --- | --- | --- | --- | --- |
| BUG-101 | [#1](https://github.com/YuldShah/cs360-assignment5/issues/1) | `fix/bug-101-delete-removes-grades` | [#5](https://github.com/YuldShah/cs360-assignment5/pull/5) | Deleting a student also deletes their grades, and `getGrade` throws `Student not found` (API 404). |
| BUG-102 | [#2](https://github.com/YuldShah/cs360-assignment5/issues/2) | `fix/bug-102-duplicate-grade` | [#6](https://github.com/YuldShah/cs360-assignment5/pull/6) | A second `addGrade` for the same course throws `Grade already exists for course <COURSE>`. `changeGrade` still corrects a grade. |
| BUG-103 | [#3](https://github.com/YuldShah/cs360-assignment5/issues/3) | `fix/bug-103-name-search` | [#7](https://github.com/YuldShah/cs360-assignment5/pull/7) | Name search trims surrounding whitespace and ignores case. The stored display name is unchanged. |
| REF-201 | [#4](https://github.com/YuldShah/cs360-assignment5/issues/4) | `refactor/ref-201-shared-validation` | [#8](https://github.com/YuldShah/cs360-assignment5/pull/8) | Course normalization and grade validation live in one helper, `#parseCourseAndGrade`. Public behavior is unchanged. |

## Merge conflicts

Each bug branch was merged into `main` in order (#5, #6, #7), then the refactor. `main` was merged into the next branch first, with a merge commit, and the conflict was resolved before that pull request was merged.

- **#6 (BUG-102)** conflicted in `test/transcriptStore.test.js`. Both sides added a test after the same starter test. Both tests were kept: deleting a student removes grades, and a duplicate grade is rejected.
- **#7 (BUG-103)** conflicted in the same test file. The name-search test was kept together with the two regression tests already on `main`.
- **#8 (REF-201)** conflicted in `src/transcriptStore.js`, in `getGrade`. The resolution uses `#requireStudent` from BUG-101 and `#parseCourseAndGrade` from the refactor. `addGrade` keeps both the helper and the duplicate-grade check.

## Result

`npm test` on `main` passes **7/7** (4 starter tests and 3 regression tests).
