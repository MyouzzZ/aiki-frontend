# Instructor-Facing Copywriting Review

This review covers instructor-facing copy in the current dashboard and course authoring components. It keeps behavior unchanged and focuses on clearer wording for course creators.

## Goals

- Use simple, professional language for instructor actions.
- Make status text specific enough to tell instructors what to do next.
- Keep button labels action-oriented and consistent across upload flows.
- Avoid vague placeholder copy that sounds like unfinished implementation text.

## Reviewed surfaces

| File | Surface |
|------|---------|
| `app/dashboard/instructor/page.tsx` | Instructor dashboard summary cards, performance placeholder, recent activity feed. |
| `components/course/CourseVideoUpload.tsx` | Video section upload flow and toast messages. |
| `components/course/CourseTextUpload.tsx` | Text section authoring flow and validation messages. |
| `components/course/CourseDiagramUpload.tsx` | Diagram upload flow, validation messages, and section labels. |

## Recommended copy updates

| Surface | Current copy | Suggested copy | Reason |
|---------|--------------|----------------|--------|
| Dashboard card | Your Courses | Courses | Shorter and matches admin-style metric labels. |
| Dashboard status | 2 pending approval | 2 awaiting review | More explicit and avoids implying the instructor approves their own courses. |
| Dashboard card | Total Students | Enrolled learners | More learner-friendly and consistent with education language. |
| Dashboard status | +28 this week | 28 new learners this week | Easier to scan without interpreting a shorthand metric. |
| Dashboard card | Assignments | Submissions | Better matches the instructor action of reviewing learner work. |
| Dashboard status | 12 need review | 12 ready for review | More actionable and positive. |
| Dashboard card | Messages | Learner messages | Clarifies who the messages are from. |
| Dashboard placeholder | Course performance metrics would be displayed here | Course performance insights will appear here after learners engage with your course. | Replaces implementation placeholder with learner-facing context. |
| Activity title | Recent Student Activity | Recent learner activity | Keeps terminology consistent with `learners`. |
| Activity item | Completed assignment | Submitted an assignment | Clearer instructor action cue. |
| Activity item | Watched lecture | Watched a lesson video | Matches course content language. |
| Activity item | Asked a question | Asked a course question | Adds context. |
| Video heading | Course Videos | Course video lessons | Clarifies videos are lesson material. |
| Video action | Save All Changes | Save video lessons | More specific action label. |
| Video empty state | Drag and drop your video here, or click to browse | Drag a lesson video here, or browse your files. | Shorter and clearer. |
| Video toast | Video selected | Video ready to save | Explains upload is not final until save. |
| Video toast description | will be uploaded when you save changes | will upload after you save this course. | More natural and course-specific. |
| Add video heading | Add New Video Section | Add video lesson | More concise. |
| Add video validation | Video title cannot be empty | Add a video lesson title before continuing. | Gives the instructor a next step. |
| Text heading | Course Text Content | Course reading sections | More concrete for instructors. |
| Text action | Save All Changes | Save reading sections | Specific and consistent. |
| Text placeholder | Write section content here... | Write the lesson text learners will read here. | Explains audience and purpose. |
| Add text heading | Add New Text Section | Add reading section | Concise and consistent. |
| Add text validation | Section title cannot be empty | Add a section title before continuing. | Direct next-step language. |
| Diagram heading | Course Diagrams | Course diagrams and visuals | Covers diagrams, concept maps, and images. |
| Diagram action | Save All Changes | Save diagrams | Specific action label. |
| Diagram empty state | Drag and drop your diagram here, or click to browse | Drag a course visual here, or browse your files. | Allows diagrams and other learning visuals. |
| Diagram validation | Please upload an image file | Upload a PNG, JPG, or other image file. | More helpful format guidance. |
| Add diagram heading | Add New Diagram | Add course visual | More flexible wording. |
| Add diagram validation | Diagram title cannot be empty | Add a visual title before continuing. | Direct next-step language. |

## Tone guide for future instructor copy

- Prefer `learner` over `student` when the app is speaking broadly to course creators.
- Prefer specific save labels such as `Save video lessons` over `Save All Changes`.
- Use validation messages that tell instructors how to fix the issue.
- Avoid placeholders that describe implementation state, such as `would be displayed here`.
- Keep upload copy clear that selecting a file is not the same as saving it.

## Suggested implementation approach

These wording changes can be applied in a follow-up UI PR without changing component behavior. The safest order is:

1. Update dashboard metric labels and empty-state text.
2. Update upload headings, button labels, and validation toasts.
3. Review screenshots for text wrapping on mobile widths.
4. Keep copy-only changes separate from layout or state-management changes.
