# Do nonsense labels affect alignment and categoricality of sorts
Repo for data &amp; analysis of how labels affect alignment &amp; categoricality of sorts.
Below is the codebook for the analysis of match to sample and sorting data.

# 1_match_to_sample_task/
## Task 1: Match to sample (analysis: match_to_sample_analysis.RMD)

The match to sample task provided pre-exposure to the category structure for participants in:
the No Labels condition (who heard white noise instead of category labels);
and the With Labels condition (who heard non-words ‘gek’ and ‘talp’ as category labels).

### Column identifiers (data: s1/2_match_to_sample.csv)

	⁃	subjCode - ID column for a participant.
	⁃	label_cond - condition a given participant experienced. -0.5 = “No Labels”; 0.5 = “With Labels”
	⁃	block - which block of the task the data corresponds to of blocks 1-3.
	⁃	label - the audio played on a given trial. For participants in the No Labels condition, this is always ‘white noise’. 
		For participants in the With Labels condition, this is ‘talp’ or ‘gek’, counterbalanced across ‘A’ and ‘B’ category items.
	⁃	first_stim - the sample stimulus which appeared in the top centre of a trial.
	⁃	second_stim - the stimulus which appeared in the bottom left of a trial.
	⁃	third_stim - the stimulus which appears in the bottom right of a trial.
	⁃	first_stim_cat - whether the sample/target is from category ‘A’ or ‘B’
	⁃	isRight - whether participants correctly matched the target and sample - 1 = correct; 0 = incorrect.
	⁃	RT - response time per trial in milliseconds.

################################################################################

################################################################################

# 2_sort_task/
## Task 2: sorting task (analysis: free_sort_analyses.RMD)

Participants sorted items (from 2 generated categories) on basis of perceived similarity. We analyze these sorts for alignment (similarity of sorts) and categoricality (distance between category A vs. category B items in the sorts).

### Column identifiers
### 2i) Individual level data (CEL_1/2_indiv_data.tsv)

	⁃	participant - ID column for participant.
	⁃	n_clusters - number of clusters formed by participant during the sorting task
	⁃	Cond_numeric - Numeric factor indicating which condition a participant experienced. -1 = Baseline; 0 = No Labels; 1 = With Labels.
	⁃	log_cat_ratio - log transformed ratio between a_dist + b_dist vs ab_dist, as a proxy to the categoricality of the participant’s sort.
	
	^For log_cat_ratio:
		⁃	a_dist = average Euclidean distance between all ‘A’ category items in participant’s sort. Represents part of the within category distance measure.
	⁃	b_dist = average Euclidean distance between all ‘B’ category items in participant’s sort. Represents part of the within category distance measure.
	⁃	ab_dist = average Euclidean distance between all ‘A’ vs ‘B’ category items in participant’s sort. Represents the between category distance measure.


###################################################################################

### 2ii) Pairwise data (CEL_1/2_pairwise_data.tsv)

	⁃	cond_numeric - Numeric factor indicating which condition a pair of participants experienced. -1 = Baseline; 0 = No Labels; 1 = With Labels.
	⁃	Condition - Factor indicating which condition a pair of participants experienced, Baseline, No Labels or With Labels.
	⁃	participant_a - ID column for participant a of the pair
	⁃	participant_b - ID column for participant b of the pair
	⁃	z_transformed_rank_r - standardized measure the rank correlation between a pair of participants’ pairwise distance matrices
	⁃	pp_a_n_clusters - number of clusters formed by participant a during the sorting task
	⁃	pp_b_n_clusters - number of clusters formed by participant b during the sorting task
	⁃	cat_diff_log_ratio_a - log transformed ratio between pp_a_a_dist + pp_a_b_dist vs pp_a_ab_dist, as a proxy to the categoricality of the participant’s sort
	⁃	cat_diff_log_ratio_b - log transformed ratio between pp_b_a_dist + pp_b_b_dist vs pp_b_ab_dist, as a proxy to the categoricality of the participant’s sort
	⁃ mean_alignment_within - average alignment of pair's sorts within category
	⁃ mean_alignment_between - average alignment of pair's sorts between category
	
### Supplementary: multimember models (see supp_multimember_models.rmd)

A more conservative analysis using lmerMultiMember (van Paridon et al., 2022), an R package that allows for specifying multiple membership random effects and attribute the variance associated with both individuals comprising each dyad from non-aggregated data.

