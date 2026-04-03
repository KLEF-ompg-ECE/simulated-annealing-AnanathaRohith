# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling
## Observation Report

**Student Name  :** A.Rohith
**Student ID    :** 2310040026
**Date Submitted:** 03-04-2026 

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `sa_timetable.py` and read through it. Then answer these questions.

**Q1. What does `count_clashes()` measure? What value means a perfect timetable?**

```
The count_clashes() function measures the number of conflicts in the timetable where a student has more than one exam in the same time slot. It evaluates how good the timetable is. A value of 0 means a perfect timetable with no clashes.
```

**Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?**

```
The generate_neighbor() function creates a new timetable by making a small random change, such as moving one exam to a different time slot. This results in a slightly modified timetable. It helps explore nearby solutions in the search space.
```

**Q3. In `run_sa()`, there is this line:**
```python
if delta < 0 or random.random() < math.exp(-delta / T):
```
**What does this line decide? Why does SA sometimes accept a worse solution?**

```
This line decides whether to accept a new solution based on its quality and the current temperature. If the new solution is better, it is always accepted. If it is worse, it may still be accepted with some probability to avoid getting stuck in local optima.
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python sa_timetable.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of iterations completed | 1379 |
| Clashes at iteration 1 | 12 |
| Final best clashes | 3 |
| Did SA reach 0 clashes? (Yes / No) | No |

**Copy the printed timetable output here:**
```
Final Timetable
------------------------------------------
Slot 1:  Geography
Slot 2:  Chemistry, English
Slot 3:  History, Computer Science, Economics
Slot 4:  Biology, Statistics
Slot 5:  Mathematics, Physics
------------------------------------------
Total clashes : 3
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest drop in clashes happen? Does the curve flatten out?*
```
The graph shows a rapid decrease in clashes during the early iterations, indicating quick improvement. The biggest drop happens at the beginning of the process. After that, the curve gradually flattens, showing that the algorithm converges and improvements become smaller over time.
```

---

## Experiment 2 — Effect of Cooling Rate

**Instructions:** In `sa_timetable.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `cooling_rate` = **0.80**, **0.95**, and **0.995**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
|--------------|--------------|----------------------|--------------------|
| 0.80         | 8            | 31                   | No                 |
| 0.95         | 3            | 135                  | No                 |
| 0.995        | 3            | 1379                 | No                 |

**Compare the three plots. What do you notice about how fast vs slow cooling affects the result? (3–4 sentences)**  
*Hint: Fast cooling = temperature drops quickly. Does it have time to explore well?*
```
Fast cooling (0.80) reduces temperature quickly, so the algorithm stops early and gives a worse solution with more clashes. Moderate cooling (0.95) improves the solution and allows better exploration. Slow cooling (0.995) takes more iterations but gives a better and more stable result. Thus, slower cooling leads to better solutions but requires more time.
```

**Which cooling_rate gave the best result? Why do you think that is?**
```
The cooling rate of 0.995 gave the best result because it allowed more exploration and avoided getting stuck in poor solutions. It produced a lower number of clashes compared to fast cooling. Although it takes more iterations, it gives a more stable and better solution.
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final clashes | Main finding in one sentence |
|-----------|-------------|---------------|------------------------------|
| 1 — Baseline | cooling_rate = 0.995 | 3 | Slow cooling gives stable and better solutions |
| 2 — Cooling rate | cooling_rate = 0.995 | 3 | Slower cooling improves solution quality but increases time |

**In your own words — what is the most important thing you learned about Simulated Annealing from these experiments? (3–5 sentences)**
```
[ YOUR REFLECTION ]
```
I learned that Simulated Annealing works by gradually reducing randomness to reach an optimal solution. The cooling rate plays a key role in balancing exploration and convergence. Fast cooling leads to poor solutions due to limited exploration. Slow cooling allows better search and avoids local optima. Overall, SA is a powerful optimization technique inspired by physical annealing.
---

## Submission Checklist
- [x] Student name and ID filled in
- [x] Q1, Q2, Q3 answered
- [x] Experiment 1: table filled, timetable pasted, plot observation written
- [x] Experiment 2: results table filled (3 rows), observation and answer written
- [x] Summary table completed and reflection written
- [x] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`