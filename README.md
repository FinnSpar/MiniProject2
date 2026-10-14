# bjy819 — MiniProject 2 results

For MiniProject 3, start with [bjy819_project_stats.csv](bjy819_project_stats.csv). Partner: **hawad**. All CSVs below use semicolons.

- **HasRecovered / WhyRecovered:** stats, the project reflections below, and [pre/post commits](bjy819_project_gap_commits.csv).
- **ActivityPattern:** [monthly plots](graphs/) and [monthly counts](commits_timeseries/).
- **Currentstatus / RecentThemes:** [saved GitHub evidence](bjy819_github_review_evidence.csv). Filter Sample to `status_2025-09-30` or `recent` for the project.
- **Code and source data:** [retrieval notebook](bjy819.ipynb), [visualization notebook](bjy819_vis.ipynb), [commit summary](bjy819_project_summary.csv).

## Definitions and limits

HasRecovered is Yes when commits resume after the longest gap, including a limited return. For gem_oq-engine it is No because no gap occurred, not because recovery failed. Currentstatus follows the assignment's April 1–September 30, 2025 window, independently of the 2026 metadata. RecentThemes uses the ten latest default-branch commits captured on October 14, 2026 UTC; per-commit labels and links are saved for review. One primary theme is assigned per commit; ties are alphabetical. Other covers refactoring, performance, tests and general maintenance.

Monthly activity uses WoC author timestamps in UTC, from first through last commit month, with zero months included. The earliest longest gap wins a tie. Only gaps of at least three months count in NumberOfGapsInTimeline. No-gap dates and commits-after-gap are intentionally blank. There are 217,028 retrieved pairs out of 217,072 expected (44 missing), which may affect small gaps. The actual timestamps extend into 2026 despite the original January 2025 coverage note. WoC histories can include branches or imported commits; raw author strings can overcount people. Gap causes are hypotheses unless directly documented.

GitHub stars/forks/latest dates retain the October 8, 2026 observation. The additional review evidence was captured later; its latest dates may differ. Assigned project IDs are retained even where GitHub repositories were renamed.

## Project files

| Project | Plot | Reflection |
|---|---|---|
| mobvoi_wenet | [Plot](graphs/bjy819_timeseries_mobvoi_wenet.png) | [Reflection](bjy819_reflection_mobvoi_wenet.md) |
| pbs-assess_gfsynopsis | [Plot](graphs/bjy819_timeseries_pbs-assess_gfsynopsis.png) | [Reflection](bjy819_reflection_pbs-assess_gfsynopsis.md) |
| pmlmodelling_ersem | [Plot](graphs/bjy819_timeseries_pmlmodelling_ersem.png) | [Reflection](bjy819_reflection_pmlmodelling_ersem.md) |
| vearch_vearch | [Plot](graphs/bjy819_timeseries_vearch_vearch.png) | [Reflection](bjy819_reflection_vearch_vearch.md) |
| hannorein_rebound | [Plot](graphs/bjy819_timeseries_hannorein_rebound.png) | [Reflection](bjy819_reflection_hannorein_rebound.md) |
| soedinglab_mmseqs2 | [Plot](graphs/bjy819_timeseries_soedinglab_mmseqs2.png) | [Reflection](bjy819_reflection_soedinglab_mmseqs2.md) |
| hpddm_hpddm | [Plot](graphs/bjy819_timeseries_hpddm_hpddm.png) | [Reflection](bjy819_reflection_hpddm_hpddm.md) |
| stephenslab_mr.mash.alpha | [Plot](graphs/bjy819_timeseries_stephenslab_mr.mash.alpha.png) | [Reflection](bjy819_reflection_stephenslab_mr.mash.alpha.md) |
| gem_oq-engine | [Plot](graphs/bjy819_timeseries_gem_oq-engine.png) | [Reflection](bjy819_reflection_gem_oq-engine.md) |
| sixin-zh_kymatio_wph | [Plot](graphs/bjy819_timeseries_sixin-zh_kymatio_wph.png) | [Reflection](bjy819_reflection_sixin-zh_kymatio_wph.md) |

## Running the notebooks

Open notebooks from this folder. The retrieval notebook defaults to loading saved files, so reviewing does not require repeating API requests. Run bjy819_vis.ipynb to rebuild monthly counts, plots and gap samples; its stats update preserves the reviewed text fields.

---

## Original assignment

# MP2 OSS Activity Analysis

### Overall research objective: Study commit patterns over time for scientific software projects.


# Work schedule
- Part 1: (Due Sept 28th) Retrieve all commits and associated data for
each of the 10 projects
- Part 2: (Due Oct 1st) Plot (and describe) commit trends over time for each project
- Part 3: (Due Oct 8th)  Investigate trends for large gaps, discontinued
contributions, and other anomalies and report topics of commits
before and after the gap
- Based on all available evidence make a judgment about the reasons for the gap or discontinued contribution and reasons for restarted contributions (if any)
- If you run requests in a loop, make sure the chunks are under 50
  commits and include some waits between the subsequent requests 
- You'll find the list of 10 projects in [net2prj.csv](https://github.com/fdac25/MP2/blob/main/net2prj.csv): your assigned projects
  are marked with your netid. Each row has a netid, WOCProjectID, and GitHubURL (project repository link)
- Example [Notebook](https://github.com/fdac25/MP2/blob/main/getinfo.ipynb) is provided for you modify in order to retrieve data for your projects.
- More info on obtaining the data from WoC: [API Docs](https://worldofcode.org/docs/#/guide_remote?id=task-4-batching)
  

### Notes & Tips
- what kind of source is worldofcode.org?
- pay attention to how many commits you are getting, check for
errors
- you may need to retrieve commit sha1's first, then get commit
content in batches
- validation: does the number of commits or authors match that on GH?
- WoC data is up to Jan 2025, so there may be some projects with
later commits on GH 

# Part 1 Steps

1. Fork fdac25/MP2
1. Create retrieval notebook copy (rename to yournetid.ipynb)
1. Edit/run your copy using hydra machines or google collab notebooks and save the
output to your forked repository
1. For each of the projects assigned to you, use your assigned projects' respective Github Repositories to report the following information in a text cell of your notebook:
    - [number of stars, number of forks, last commit date]
1. For each of the projects assigned to you, use the python WoC api to report the following information in a text cell of your notebook:
    - [number of commits, number of authors, max time, min time] 
1. Create a CSV file in your fork named netid_project_summary.csv
that is semicolon separated and containing the following columns:
```
project_wocid
commit_sha1
author
time
commit message
```

# Part 2 steps: data visualization

Visualize the commit timestamps you obtain in Task 1. Steps:

1. From your netid_project_summary.csv generated in Part 1, Group activity by month. Each row should represent one month, with the number of commits made during that month.
    - Even if a month had zero commits, still include it with a 0
count.
    - Begin with the first month in which the project had any commit.
    - End with the last month in which the project had a commit.
    - Your csv should have 2 columns with the following headers: [Month, #Commits]
1. Save this as:  Filename: netid_commits_timeseries_<WOCProjectID>.csv
   ```
   Columns/Format: Month;#Commits
   Example rows:
   2021-01;5
   2021-02;0
   2021-03;2
   ```
1. Create a line plot of the time series in Python. The plot should use the monthly data you just generated.
   ```
   Plot Format:
   X-axis = months (YYYY-MM)
   Y-axis = number of commits
   Title = WOCProjectID
   Add axis labels and grid lines
   Save the plot as: netid_timeseries_<WOCProjectID>.png
   Export resolution: ≥300 DPI
   ```
- Example code:
   ```
   import pandas as pd
   import matplotlib.pyplot as plt

   # Load CSV
   df = pd.read_csv("netid_commits_timeseries.csv", sep=";")

   # Plot
   plt.figure(figsize=(10,5))
   plt.plot(df["Month"], df["#Commits"], marker="o", linestyle="-")
   plt.xlabel("Time (YYYY-MM)")
   plt.ylabel("Number of Commits")
   plt.title("Commit Activity: <WOCProjectID>")
   plt.grid(True)
   plt.xticks(rotation=45)
   plt.tight_layout()

   # Save; Resolution 300 DPI
   plt.savefig("netid_timeseries_<WOCProjectID>.png", dpi=300)
   plt.close()
   ```


##### Identify the Longest Inactivity Gap
Using your monthly time series, determine the longest continuous period of zero commits.
To calculate:
1. Start in the first month with zero commits.
2. Count consecutive zero-commit months.
3. Track the maximum length.
4. Create netid_project_stats.csv with the following columns:
    - [project, number of commits, number of authors, max time,
min time] 
    - Also add the info you obtained from GitHub: [number of stars, number of forks, last commit date]. 
    - add
      ```
      LongestGapStart (YYYY-MM), 
      LongestGapEnd (YYYY-MM),
      LongestGapLength (months).
      ```
5. Add a [NumCommitsAfterLastGap] column containing the total commits to date after the LongestGapEnd. for the respective projects.
6. Add a [NumberOfGapsInTimeline] column containing the number of gaps (of at least three months of inactivity) there are there for each project.
7. Add a [ActivityPattern] column containing a classification of the project’s overall activity trajectory based on the charts you have produced your overall perception. Possible classifications to choose include: 
   - [steady, rising, declining, U-shaped, cyclical, irregular. ]
8. In the notebook, add a cell named "Interpretation" and add an explanation for the trends you noted. See the definitions below. Also specify the number of gaps (of at least three months of inactivity) are there for each project.

   Trends:
    - steady, rising, declining, U-shaped: Long-term, general movements in activity levels. An upward trend might indicate that a person is becoming more active over several months, while a downward trend could signal a decrease in mobility.

    - Seasonal/Cyclical patterns: Predictable and repeated patterns of activity that occur at fixed intervals, such as quarterly or annually. 

    - Irregular or random variations: Unpredictable changes in activity that cannot be explained by trends or seasonal patterns.

[Example Notebook](https://github.com/fdac25/MP2/blob/main/Vis.ipynb)

# Part 3.1 details: Examine Commits Before and After the Gap

Fore each of the ten projects
1. Collect the last 10 commits before the longest gap (or all if
fewer exist) from netid_project_summary.csv
2. Collect at least 10 commits after the longest gap (or all if fewer exist).
3. place them in netid_project_gap_commits.csv by prepending pre/post
   (valued pre or post)  column to data taken from netid_project_summary.csv
4. Summarize the top 2 themes of commits/commit messages before the
   gap and the top 2 themes of commits/commit messages after the gap. Possible themes of commits/commit messages include: 
    - Feature development
    - Bug fixes
    - Documentation updates
    - Dependency updates
    - Release (For releases  or release preparation)
    - Security patches
    - Automated bot contributions (For any bot upddatese.g., Dependabot updates, CI bots, formatting bots)
    - Other (for anything not covered in the list)
5. Record in netid_project_stats.csv:
   - column BeforeThemes: the top two themes from 10 commits before
   the gap; separated by a colon Example: Documentation updates:Dependency updates
   - column AfterThemes: the top two themes from 10 commits after
     gap separated by a colon Example: Automated bot contributions:Bug fixes



# Part 3.2 details: Interpret the Gap

1. Read the commit messages carefully looking for any hints about
 the reasons for the gap and reasons for the interruption of the
 gap. In addition, check the project’s GitHub issues, pull requests,
 and README updates immediately before and after the longest gap especially if
 the reasons are not completely obvious from the commit messages to
 clarifies why the project went inactive or became active again.
 For example, issues may show unanswered bug reports, which could be
 a possible cause of abandonment. A new pull request after the gap
 might be evidence of recovery. README changes may indicate
 maintainers marking the project as "archived" or "revived." 
2. Record in netid_project_stats.csv: use columns
   HypothesizedGapReason, HasRecovered, WhyRecovered, WhoRecovered
   to record your answers. Use commit
   messages as the primary evidence; supplement with GitHub issues, pull
   requests, or README updates. Each answer support with evidence
   pointing out factual data. 
   - Why did the project go inactive (Put ‘N/A active Project’ if no
   inactivity gap period exists)?
   - Did it recover?
   - If so, why?
   - If it recovered, are the same people contributing to it or did new people join that
drive the recovery?
3. Check Current Project Status 
   - Look at the most recent commit date on GitHub. If no commits in
   the last 6 months as of 2025-09-30 (i.e., last commit before April 1,
   2025). Mark Inactive , else Active. Record in netid_project_stats.csv: Currentstatus
   - Collect the last 10 commits (or all if fewer) before the most
   recent commit date (in part 3 you looked for commits after the
   longest gap, not necessarily the latest commits). Pick top 2
   themes of commits/commit messages, same categories as step 4.  Record in netid_project_stats.csv: RecentThemes
4. Write Reflections. For each project, write a reflection. Discuss:
inactivity patterns, whether the longest gap was easy/hard to interpret, and likely reasons for inactivity or recovery. If the
project was active always, capture activity patterns. Save as:
netid_reflection_WOCProjectID.md 
Summarize this reflection in 2-4 sentences Record in netid_project_stats.csv: Notes


# Final Submission Checklist
- netid_project_summary.csv (one file, semicolon-separated, with 10
  projects with format (project_wocid, commit_sha1, author, time, 'commit message') in Part 1
- netid.ipynb: the code used to retrieve the data in Part 1
- netid_timeseries_WOCProjectID.png (10 files) in Part 2
- netid_vis.ipynb: the code used to aggregate and visualize the data
  in Part 2
- netid_project_gap_commits.csv  (one file with 10 projects with format
  (pre/post, prj, commit, author, time, message) Part 3 
- netid_reflection_WOCProjectID.md (10 files) Part 4
- netid_project_stats.csv (single summary file with all projects
(parts 1-4) Colums:
   - Part 1: Project, ncommits, nauthors, from, to, nstars, nforks, and lastGHCommitDate
   - Part 2: LongestGapStart (YYYY-MM), LongestGapEnd (YYYY-MM), LongestGapLength (months), NumCommitsAfterLastGap, ActivityPattern, NumberOfGapsInTimeline
   - Part 3: BeforeThemes, AfterThemes
   - Part 4: HypothesizedGapReason, HasRecovered, WhyRecovered, WhoRecovered, Currentstatus, RecentThemes, Notes
