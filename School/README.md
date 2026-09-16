# School

Coursework, one folder per class, grouped by term. `School.md` is the hub: the
current term's classes, meeting pattern, and links to a timetable note and a
deadline radar note that gathers every dated item across all classes.

## How a class folder works

```
<TERM>/<COURSE>/
├── <COURSE>.md     hub: instructor, schedule, syllabus, running notes
├── Lectures/       one transcript per lecture, written by the transcript script
├── Lessons/        one study note per lecture, written from the transcript
└── Assignments/    one note per assignment, paper, or exam
```

Lectures are recorded on a tablet, synced, transcribed by a watcher on the
desktop, and filed by matching the start time against the timetable. Turning a
transcript into a lesson note is a separate step done by a `class-lesson` skill.

Rule: school notes are input. Before adding another transcript, check that the
last one produced something (an Atlas note, an assignment draft, a study sheet).
