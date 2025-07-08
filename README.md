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
- Timsort (hybrid of Insertion Sort and Merge Sort) for fast sorting of CGPA Data
- Quartile binning to seed CGPA Teams
- Greedy Assignment to group students according to priorities:
### Priority 1: Uniqueness
For each student, scan teams and place them in the first one that satisfies all of:
1. School (no student from the same school)
2. Gender (no risk of majority gender)
3. CGPA Quartile (no student from the same CGPA quartile)
       
### Priority 2: Relaxed Thresholds
For remaining unassigned students, scan teams again under looser caps:
1. School: at most two from the same school
2. Gender: up to ⌈team_size/2⌉ of that gender (so adding one won’t tip past 50%)
3. Quartile: up to ⌈team_size/4⌉ of that quartile (so no more than ~25%)

### Priority 3-5: Single Criteria
If anyone remains unassigned, we do three quick sweeps, each enforcing just one constraint:
1. Priority 3: CGPA-only (cgpa_count < ⌈team_size/4⌉)
2. Priority 4: Gender-only (gender_count < ⌈team_size/2⌉)
3. Priority 5: School-only (school_count < 2)

### Priority 6: Final Round-Robin Assignment
Because 50 might not divide evenly by team_size, there can be leftovers. We simply:
1. Collect all unassigned students
2. Distribute them one by one to Team 1, Team 2, … in cyclic order
