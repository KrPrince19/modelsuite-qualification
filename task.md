# ModelSuite Qualification Assignment Documentation

## Full-Stack MERN Developer Internship (Remote)

### Candidate

**Prince Kumar Yadav**

### Branch Name

```bash
17-16-14-10-9-prince-kumar-yadav
```

### Deadline

**12 June 2026**

---

# 1. Assignment Objective

The objective of this assignment is to complete and submit fixes/features for the following GitHub issues in a single Pull Request:

| Issue No. | Type    | Description                                     |
| --------- | ------- | ----------------------------------------------- |
| #10       | Bug     | Prevent race condition during task claiming     |
| #9        | Bug     | Prevent creation of empty tasks                 |
| #14       | Feature | Add Due Soon and Overdue badges                 |
| #17       | UI      | Replace browser alerts with toast notifications |
| #16       | UX      | Add loading indicators for async actions        |

All tasks must be completed on a single branch and submitted through one Pull Request.

---

# 2. Repository Setup

## Step 1: Fork Repository

Fork the repository from GitHub:

```text
https://github.com/modelsuite-ai/modelsuite-qualification
```

This creates a personal copy of the repository.

---

## Step 2: Clone Repository

Clone the forked repository locally:

```bash
git clone https://github.com/<your-github-username>/modelsuite-qualification.git
```

Move into the project directory:

```bash
cd modelsuite-qualification
```

---

## Step 3: Create Assignment Branch

Create the required branch:

```bash
git checkout -b 17-16-14-10-9-prince-kumar-yadav
```

Verify branch:

```bash
git branch
```

Expected output:

```text
* 17-16-14-10-9-prince-kumar-yadav
```

---

# 3. Install Dependencies

Install project dependencies:

```bash
npm install
```

If frontend and backend are separated:

Frontend:

```bash
cd client
npm install
```

Backend:

```bash
cd ../server
npm install
```

---

# 4. Run Application

Start backend:

```bash
npm run dev
```

Start frontend:

```bash
npm run dev
```

Open the application in browser.

Example:

```text
http://localhost:3000
```

or

```text
http://localhost:5173
```

---

# 5. Issue Implementation Plan

## Issue #9 - Task Creation API Allows Empty Payloads

### Problem

The backend currently accepts requests containing empty title and description fields.

Example:

```json
{
  "title": "",
  "description": ""
}
```

Such tasks are stored in the database and cause UI issues.

### Required Solution

Implement server-side validation.

### Validation Rules

* Title must not be empty.
* Description must not be empty.
* Whitespace-only values should be rejected.

### Expected Response

```json
{
  "message": "Title and description are required"
}
```

### Testing

Create a task using empty fields.

Expected Result:

```text
400 Bad Request
```

---

## Issue #10 - Race Condition Allows Simultaneous Claims

### Problem

Two users can claim the same task at nearly the same time.

Current result:

```text
User A claims task
User B claims task

Both requests succeed
```

Ownership becomes unpredictable.

### Required Solution

Implement atomic database updates.

### Expected Behavior

Only the first request should succeed.

Second request should receive:

```json
{
  "message": "Task already claimed"
}
```

### Testing

Attempt simultaneous task claims from multiple browser sessions.

Expected Result:

```text
One request succeeds
One request fails
```

---

## Issue #14 - Due Soon and Overdue Badges

### Problem

Users cannot easily identify urgent tasks.

### Required Solution

Add visual badges.

### Due Soon Badge

Display when:

```text
Deadline <= 24 hours
Deadline > Current Time
```

Badge:

```text
Due Soon
```

### Overdue Badge

Display when:

```text
Deadline < Current Time
```

Badge:

```text
Overdue
```

### Expected UI

```text
Build Dashboard
[Due Soon]
```

```text
Fix Login API
[Overdue]
```

### Testing

Create tasks with different due dates and verify badge display.

---

## Issue #17 - Replace Native Alerts

### Problem

Application currently uses:

```javascript
alert(error.message)
```

This creates a poor user experience.

### Required Solution

Integrate a toast notification library.

Possible libraries:

```bash
npm install react-hot-toast
```

or

```bash
npm install react-toastify
```

### Replace

```javascript
alert("Login Failed")
```

with

```javascript
toast.error("Login Failed")
```

### Success Messages

```javascript
toast.success("Task Created")
```

### Testing

Trigger both successful and failed API requests.

Expected Result:

Modern toast notifications appear.

---

## Issue #16 - Loading Indicators

### Problem

Users receive no feedback during API requests.

Buttons remain clickable and duplicate requests may occur.

### Required Solution

Add loading states.

### Requirements

* Disable submit buttons during requests.
* Show loading text or spinner.
* Prevent duplicate submissions.

### Example

Before:

```text
Submit
```

During request:

```text
Loading...
```

### Testing

Verify behavior for:

* Login
* Register
* Task Creation
* Other critical forms

---

# 6. Testing Checklist

## Issue #9

* [ ] Empty title rejected
* [ ] Empty description rejected
* [ ] Whitespace-only values rejected

## Issue #10

* [ ] Double claim prevented
* [ ] Atomic update implemented

## Issue #14

* [ ] Due Soon badge visible
* [ ] Overdue badge visible

## Issue #17

* [ ] All alerts replaced
* [ ] Success toasts working
* [ ] Error toasts working

## Issue #16

* [ ] Buttons disabled during requests
* [ ] Loading state visible
* [ ] Duplicate submissions prevented

---

# 7. Git Workflow

## Check Changes

```bash
git status
```

## Stage Files

```bash
git add .
```

## Commit Changes

```bash
git commit -m "Fix issues #17 #16 #14 #10 #9"
```

## Push Branch

```bash
git push origin 17-16-14-10-9-prince-kumar-yadav
```

---

# 8. Pull Request Creation

Open GitHub and create a Pull Request.

## PR Title

```text
Fix issues #17 #16 #14 #10 #9
```

## PR Description

```text
Closes #17
Closes #16
Closes #14
Closes #10
Closes #9

Implemented:
- Toast notifications
- Loading indicators
- Due Soon badge
- Overdue badge
- Backend validation
- Atomic task claiming
```

---

# 9. Walkthrough Video

Create a voice-over video demonstrating:

1. Application setup
2. Validation fix (#9)
3. Race condition fix explanation (#10)
4. Due Soon badge (#14)
5. Overdue badge (#14)
6. Toast notifications (#17)
7. Loading indicators (#16)
8. Code walkthrough

Recommended duration:

```text
5 to 10 minutes
```

Upload the video to Google Drive and make it publicly accessible.

---

# 10. Final Submission

Submit:

1. Pull Request Link
2. Google Drive Video Link

through the Talent Portal assignment page before the deadline.

---

# Final Deliverables

✅ Branch Created

✅ All 5 Issues Completed

✅ One Pull Request Submitted

✅ Walkthrough Video Uploaded

✅ Assignment Submitted Before Deadline
