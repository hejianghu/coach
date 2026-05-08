# Bloom's Two Sigma Problem — Research Background

"Two Sigma Problem" refers to Benjamin Bloom's 1984 finding that students receiving one-on-one tutoring with mastery learning performed two standard deviations (2 sigma) better than students in conventional classrooms — meaning the average tutored student outperformed 98% of the control group.

## The Original Research

Bloom, B. S. (1984). "The 2 Sigma Problem: The Search for Methods of Group Instruction as Effective as One-to-One Tutoring." *Educational Researcher*, 13(6), 4-16.

### Key Findings

- One-on-one tutoring + mastery learning produced the 2 sigma effect
- Mastery learning alone (group instruction but with mastery requirements) produced ~1 sigma improvement
- Tutoring alone (without mastery requirements) produced ~0.5 sigma improvement
- The combination was dramatically more effective than either alone

### Why It Matters

Bloom's question was not "does tutoring work?" — that was already known. The question was: **can we design group instruction methods that approach the effectiveness of one-on-one tutoring at scale?** The answer in 1984 was "not yet." Forty years later, AI changes the equation.

## The Two Conditions

### Condition 1: One-on-One Tutoring

Not small-group instruction, not recorded lectures — a human teacher working exclusively with one student, adapting in real time to their comprehension.

**Why it works:**
- Immediate feedback loops prevent misconception entrenchment
- Pacing matches the individual, not the median
- Explanations can be customized to the learner's mental models and prior knowledge
- The teacher detects confusion from verbal and nonverbal cues and adjusts instantly

### Condition 2: Mastery Learning

The learner must demonstrate 80-90% competency on current material before advancing to the next unit.

**Key principles (from Bloom's student John B. Carroll):**
- Aptitude is not a measure of how much a student can learn, but how *fast* they can learn given optimal conditions
- Given sufficient time and appropriate instruction, most students can achieve the same level of learning
- The variable is time and method, not fixed ability

**Why it works:**
- Prevents cumulative knowledge gaps (the "Swiss cheese" problem where later concepts have no foundation)
- Builds confidence through demonstrated competence
- Transforms errors from failures into diagnostic information

## Why Traditional AI Interaction Falls Short

The dominant pattern — user asks a question, AI answers — is the reverse of effective pedagogy.

| Aspect | Effective Learning | "User asks, AI answers" |
|--------|-------------------|------------------------|
| Initiative | Teacher drives | Student drives |
| Unknown unknowns | Teacher identifies gaps | Student must self-diagnose |
| Pacing | Adaptive to learner | Fixed to question asked |
| Assessment | Embedded, continuous | None or self-assessed |
| Review | Scheduled and targeted | None |

The paradox: a novice in a domain doesn't know what they don't know. Asking them to formulate questions about something they haven't learned yet places the cognitive load in exactly the wrong place.

## Why Persistent State Matters

Learning is not a single session. It involves:
- Sleep consolidation between sessions
- Spaced repetition for long-term retention
- Progressive knowledge building over weeks

Dialog-based AI loses all of this between sessions. Local file persistence solves this by maintaining:
- What has been learned (module completion)
- Current mastery levels per topic
- Items needing review
- Session history for spaced recall scheduling

## References

- Bloom, B. S. (1984). The 2 Sigma Problem. *Educational Researcher*, 13(6), 4-16.
- Carroll, J. B. (1963). A Model of School Learning. *Teachers College Record*, 64(8), 723-733.
- Guskey, T. R. (2007). Closing Achievement Gaps: Revisiting Benjamin S. Bloom's "Learning for Mastery." *Journal of Advanced Academics*, 19(1), 8-31.
- Kulik, C. C., Kulik, J. A., & Bangert-Drowns, R. L. (1990). Effectiveness of Mastery Learning Programs: A Meta-Analysis. *Review of Educational Research*, 60(2), 265-299.
