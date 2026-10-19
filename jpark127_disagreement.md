# Disagreement Examples — jpark127 (validator) & kha5 (author)

Validation of kha5's ten MiniProject2 projects by jpark127. 14 of 50 project-field
records disagreed before discussion (WhyRecovered 4, ActivityPattern 4, RecentThemes 6);
all 14 were resolved in discussion between jpark127 and kha5 on Oct 19, 2026.
The full list is in `jpark127_disagreement_resolution.csv`.

## Example 1 — allenai/scispacy (WhyRecovered)
**Parties:** kha5 (author), jpark127 (validator)
**Author:** Dependency updates needed then added more features
**Validator:** An external contributor (C. T. Hoyt) submitted a series of feature/refactor PRs in Aug–Sep 2025, then the maintainer cut release 0.6.0
**Evidence:** First post-gap commit (2025-06-16) is docs only. The substantive work is Hoyt's PRs #544, #547, #549 (entity linker from KB, KnowledgeBase refactor, TF-IDF caching) in Aug–Sep, followed by `build: relax spacy minor upper bound` (#551), `Bump version to 0.6.0` (#552) and `Fix publish action` (#554).
**Discussion:** The author's "dependency updates" element is real (pyproject.toml migration, spaCy bound) but it came alongside and after the feature PRs, not first; the trigger was a new external contributor.
**Resolution:** Compromise — both elements kept, sequence corrected: "new external contributor's feature/refactor PRs, with dependency/build updates alongside, ending in release 0.6.0."

## Example 2 — microsoft/SPTAG (ActivityPattern)
**Parties:** kha5 (author), jpark127 (validator)
**Author:** cyclical
**Validator:** irregular
**Evidence:** Bursts in 2019-03 (65 commits), 2020-06 (66), 2022-01 to 03 (69–114), 2022-12 (120), 2025-06 to 08 (78, 32, 60), separated by long low periods of 2–15 commits/month. Burst spacing is 10–30 months.
**Discussion:** The codebook defines *cyclical* as "predictable, repeated patterns at fixed intervals (e.g., quarterly or annually)". Repeated bursts are not enough; they must be periodic. These are not.
**Resolution:** ValidatorKept — irregular. The same reasoning was applied to mundialis/actinia_core (cyclical → irregular).

## Example 3 — astro-informatics/ssht (ActivityPattern and WhyRecovered)
**Parties:** kha5 (author), jpark127 (validator)
**Author:** ActivityPattern = declining; WhyRecovered = "Finished the previous work so adding new tasks" (for a 1-month gap)
**Validator:** ActivityPattern = irregular; WhyRecovered = numpy 2.0 broke the Cython build, prompting compatibility fixes and later release 1.5.3
**Evidence:** The author's stats row and plot for ssht (17,636 commits, 941 authors) are the aggregate of all ten projects, not ssht. Real ssht has 776 commits and 40 authors, two bursts (2010–11 and 2019–21) and a real longest gap of 2023-03-09 to 2024-06-17 (14 zero months) ended by `Add cnp.import_array for numpy>=2` (PR #75).
**Discussion:** Not an interpretation difference but a data error: the labels were read from the wrong series. Once both looked at the per-project data the validator's reading was uncontested.
**Resolution:** ValidatorKept for both fields. (HasRecovered = Yes happened to be right and was left as is.)

## Example 4 — clawpack/pyclaw (RecentThemes)
**Parties:** kha5 (author), jpark127 (validator)
**Author:** Documentation-testing updates:Bug fixes
**Validator:** Bug fixes:Other (CI/testing workflow)
**Evidence:** Last 10 real commits: 5 CI/testing-workflow commits by K. Mandli (`Turn off fast fail`, `Uniquely identify test results`, `Do not capture output in pytest`, ...) and 5 limiter bug fixes by D. Ketcheson. No documentation commits.
**Discussion:** Both read the same substance (testing work + bug fixes). "Documentation-testing updates" is not a codebook theme and conflates documentation with testing; the codebook has no testing theme, so CI/testing maps to *Other*.
**Resolution:** ValidatorKept — label normalized to codebook terms. Same terminology mismatch resolved the same way for Unidata/netcdf-cxx4.

## Example 5 — allenai/scispacy (RecentThemes)
**Parties:** kha5 (author), jpark127 (validator)
**Author:** Feature development:Dependency updates
**Validator:** Release:Dependency updates
**Evidence:** Within the 10-commit window: 4 release/version commits (`Bump version to 0.6.0` x2, `update version` x2), 3 dependency/CI commits, 1 fix, 0 features. The feature commits (TF-IDF caching, entity linker from KB) are commits 11–20.
**Discussion:** The author's reading is correct for the last ~20 commits but the codebook fixes the window at the most recent 10. Agreed to apply the window strictly.
**Resolution:** ValidatorKept — Release:Dependency updates.
