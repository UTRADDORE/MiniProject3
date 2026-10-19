# Validation Reflection — jpark127

I validated the ten projects analyzed by kha5 (SOCR/SOCRAT, BBN-Q/QGL, microsoft/SPTAG,
allenai/scispacy, clawpack/pyclaw, isce-framework/isce2, facebookresearch/pytorch3d,
mundialis/actinia_core, Unidata/netcdf-cxx4, astro-informatics/ssht). Before discussion we
agreed on 36 of 50 project-field records (72%): 100% on HasRecovered and Currentstatus,
60% on WhyRecovered and ActivityPattern, and 40% on RecentThemes. All 14 disagreements were
resolved (13 ValidatorKept, 1 Compromise), which is lopsided but reflects the kind of
disagreements we had: most were not two readings of the same evidence but a generic or
non-codebook label on one side and a commit-level count on the other. Cohen's kappa for
ActivityPattern rose from 0.29 to 1.0; for HasRecovered it was 1.0 throughout, and for
Currentstatus it is undefined because every project was Active for both raters.

## What precedes a long gap

Across the adjudicated projects the long gaps were preceded by the same kind of signal:
activity had already thinned to maintenance-only work before it stopped. SOCRAT's last
pre-gap commits (2022-11 to 2023-02) were paper references and an About-page update, after
yearly commits had fallen from 561 (2017) to 3 (2023); the 27-month gap that followed was the
tail of a decline, not a sudden break. QGL shows the same shape: 411 commits in 2019, then
153, 61, 1, 0. netcdf-cxx4 went quiet right after a release ("released", 2011-10) and a single
Jira-driven fix. In other words, the adjudicated ActivityPattern label (declining) and the gap
are the same phenomenon seen at two time scales, which is why we resolved the irregular-vs-declining
cases (QGL) in favour of the long-term trend the codebook asks for. A second, more mundane
signal is a dependency going stale: ssht, QGL and pyclaw all stopped while their toolchain
(numpy, Cython, the deprecated `imp` module) moved on underneath them.

## What triggers recovery

The adjudicated WhyRecovered values fall into three recurring triggers. The most common is an
external break that forces someone's hand: numpy 2.0 removed `np.complex` and changed the
Cython C-API (QGL, ssht), Python dropped `imp` (pyclaw), and on my own side of the validation
NumPy 2.0 and CppAD 2024 did the same to py-sphviewer and CppADCodeGen. These recoveries start with a compatibility fix and only sometimes
grow into feature work (QGL's SWAP gates, pyclaw's limiter fixes). The second trigger is a new
person: a new maintainer taking over and preparing a release (netcdf-cxx4, W. Fisher), an
external contributor arriving with a batch of feature PRs (scispacy, C. T. Hoyt), or several new
organisation members formalising the project with CONTRIBUTING.md and license headers
(actinia_core). The third is a maintainer catching up on a PR backlog after a short pause
(isce2, 81 days), which is really continuous development with a scheduling hiccup rather than
a recovery. We adjudicated away reasons like "finished other task" because nothing in the
commits, issues or PRs supported them; a WhyRecovered label needs a named commit, PR or
contributor behind it.

## When a gap is not project death, and when "recovered" is not recovery

Several projects had gaps that would look fatal on a plot but were not: QGL resumed after 30
zero months and now has commits into 2026, netcdf-cxx4 survived two separate 11-month gaps,
ssht came back after 14 months with a release. The common factor is that the code was still
being *used*: the recovery commit is almost always a user or downstream maintainer fixing the
thing that stopped it working for them. Conversely, the reverse validation (kha5 reviewing my
projects) produced the clearest example of the opposite: py-sphviewer had post-gap commits (an
external PR fixing NumPy 2.0 dtypes, README edits) and I had labelled it "Partially"
recovered; we adjudicated it to No because nothing beyond the compatibility patch followed and
the README was later marked deprecated. SOCRAT is the same pattern on this side: one
"Add files via upload" commit does not end a gap. Related to this, Currentstatus by the codebook
rule (last commit on or after 2025-04-01) and status in substance can diverge: SOCRAT and ssht
are Active by rule on a single commit or an exact boundary date. We kept the rule but noted the
borderline cases in Comments.

## Recurring interpretation pitfalls and how we resolved them

1. **"Cyclical" for anything bursty.** Both SPTAG and actinia_core were coded cyclical because
   activity comes in repeated bursts. The codebook requires fixed intervals; bursts 10-30 months
   apart are irregular. Resolved by reading the definition together, and the fix generalised to
   the other case immediately. (The same pattern appeared in reverse on critic2, where kha5 read
   my "steady" as cyclical; we settled on steady with one spike.)
2. **Trend vs variance in ActivityPattern.** High month-to-month variance made QGL look
   irregular, but the yearly series is monotonically declining. We agreed the field is about the
   long-term trend, and irregular is reserved for series with no trend at all.
3. **Labels outside the codebook.** "Documentation-testing updates", "Bot dependency updates"
   and free text in yes/no fields ("Yes for 1 year then stopped", "Not really. Just added an
   image") were the single largest source of RecentThemes disagreement. In most cases the
   substance matched and we only normalised the label to codebook themes (testing work -> Other;
   bot bumps -> Automated bot contributions + Dependency updates).
4. **The 10-commit window.** scispacy's feature work sits in commits 11-20, so the author's
   "Feature development" was true of the recent history but not of the window the codebook
   defines. We applied the window strictly; the lesson is to count the ten commits explicitly
   rather than reading themes off the recent page.
5. **Documentation over-attributed.** For isce2 and netcdf-cxx4 "Documentation updates" was
   assigned where the commits were new-sensor support and a new `getPath()` API. Counting commit
   types (feature/fix/docs/CI) before choosing the top two themes resolved every one of these.
6. **Wrong data behind a right-looking label.** ssht's stats and plot in the author's analysis
   were the aggregate of all ten projects. HasRecovered happened to come out correct, but
   ActivityPattern and WhyRecovered were describing a series that does not exist. This was the
   only disagreement that no amount of discussion of definitions would have caught; it needed the
   validator to recompute from the raw data.

The main thing I take from the exercise is that most of our disagreements were about
*vocabulary and procedure* (what cyclical means, which ten commits count, which themes exist)
rather than about the projects themselves, and that almost all of them could be settled by
counting: commits per year for ActivityPattern, commit types in the window for RecentThemes,
and the first post-gap commit and its author for WhyRecovered. Writing those counts into
KeyEvidence up front made the discussion short and made the adjudicated labels defensible.
