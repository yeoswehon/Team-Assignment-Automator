# Team Assignment Automator (SC1003-Mini-Project)
This repository contains the scripts and notebooks used to automatically split each 50-student tutorial group into balanced, diverse teams of configurable size (4–10 members). We ensure that within every team:
- No more than two students share the same school affiliation
- No gender majority (>50%)
- CGPA averages remain roughly equal by first binning into quartiles

## Contributions
- Yeo Swe Hon (Algorithm Design, Implementation of Code)
- Caasi John Rian Domingo (Computational Thinking Process, Flowchart)
- Tanusri Balasubramanian (Computational Thinking Process)
- Jadelyn Minneke Sutopo (Computational Thinking Process, Data Visualisation)

## Considerations
- How can we group 50 students into teams of 4–10 so that no single school or gender dominates any team?
- How do we ensure academic balance, so that each team’s average CGPA is comparable?
- How do we handle leftovers when 50 is not a multiple of the chosen team size?

## Algorithm Summary
- Timsort (hybrid of Insertion Sort and Merge Sort) for fast sorting of CGPP Data
- Quartile binning to seed CGPA Teams
- Greedy Assignment to group students
