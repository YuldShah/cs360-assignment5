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

## Assignment evidence

- **Screenshots:** [01-issues-closed.png](evidence/screenshots/01-issues-closed.png), [02-issue-1.png](evidence/screenshots/02-issue-1.png), [03-issue-2.png](evidence/screenshots/03-issue-2.png), [04-issue-3.png](evidence/screenshots/04-issue-3.png), [05-issue-4.png](evidence/screenshots/05-issue-4.png), [06-branches.png](evidence/screenshots/06-branches.png), [07-commits-main.png](evidence/screenshots/07-commits-main.png), [07b-commits-main.png](evidence/screenshots/07b-commits-main.png), [08-network-graph.png](evidence/screenshots/08-network-graph.png), [09-pulls-closed.png](evidence/screenshots/09-pulls-closed.png), [10-pr-5.png](evidence/screenshots/10-pr-5.png), [11-pr-6.png](evidence/screenshots/11-pr-6.png), [12-pr-7.png](evidence/screenshots/12-pr-7.png), [13-pr-8.png](evidence/screenshots/13-pr-8.png), [14-pr-9.png](evidence/screenshots/14-pr-9.png), [15-conflict-bug-102.png](evidence/screenshots/15-conflict-bug-102.png), [16-conflict-bug-103.png](evidence/screenshots/16-conflict-bug-103.png), [17-conflict-ref-201.png](evidence/screenshots/17-conflict-ref-201.png), [18-npm-test-final.png](evidence/screenshots/18-npm-test-final.png).
- **Conflict-resolution notes:** [BUG-102.txt](evidence/conflict-resolution/BUG-102.txt), [BUG-103.txt](evidence/conflict-resolution/BUG-103.txt), [REF-201.txt](evidence/conflict-resolution/REF-201.txt), [git-log-graph.txt](evidence/conflict-resolution/git-log-graph.txt).
- **Final test output:** [npm-test-final-output.txt](evidence/npm-test-final-output.txt).
- **GitHub username:** [GITHUB_USERNAME.txt](evidence/GITHUB_USERNAME.txt).
