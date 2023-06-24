# Do nonsense labels affect alignment and categoricality of sorts
Repo for data &amp; analysis of how labels affect alignment &amp; categoricality of sorts.
Below is the codebook for the analysis of match to sample and sorting data.

## Task 1: Match to sample

The match to sample task provided pre-exposure to the category structure for participants in:
the No Labels condition (who heard white noise instead of category labels);
and the With Labels condition (who heard non-words ‘gek’ and ‘talp’ as category labels).

### Column identifiers

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

## Task 2: sorting task

Participants sorted items (from 2 generated categories) on basis of perceived similarity. We analyze these sorts for alignment (similarity of sorts) and categoricality (distance between category A vs. category B items in the sorts).

### Column identifiers
### 2i) Individual level data (CEL_1/2_indiv_data.tsv)

	⁃	participant - ID column for participant.
	⁃	n_clusters - number of clusters formed by participant during the sorting task
	⁃	Cond_numeric - Numeric factor indicating which condition a participant experienced. -1 = Baseline; 0 = No Labels; 1 = With Labels.
	⁃	a_dist - average Euclidean distance between all ‘A’ category items in participant’s sort. Represents part of the within category distance measure.
	⁃	b_dist - average Euclidean distance between all ‘B’ category items in participant’s sort. Represents part of the within category distance measure.
	⁃	ab_dist - average Euclidean distance between all ‘A’ vs ‘B’ category items in participant’s sort. Represents the between category distance measure.
	⁃	log_cat_ratio - log transformed ratio between a_dist + b_dist vs ab_dist, as a proxy to the categoricality of the participant’s sort.
	⁃	cat_diff - absolute difference between the average of a_dist + b_dist vs. ab_dist. Represents the difference between within and between category distances, as a proxy to the categoricality of the participant’s sort.
	⁃	purity - the proportion (0-1) of within-category items of a cluster containing either the ‘A’ or ‘B’ prototype (the cluster used was that with the highest purity out of ‘A’ or ‘B’).
	⁃	n_items - average number of items used per cluster by participant.
	⁃	window_height - height of participant's screen measured in number of pixels.
	⁃	window_width - width of participant's screen measured in number of pixels.


###################################################################################

### 2ii) Pairwise data (CEL_1/2_pairwise_data.tsv)

	⁃	cond_numeric - Numeric factor indicating which condition a pair of participants experienced. -1 = Baseline; 0 = No Labels; 1 = With Labels.
	⁃	Condition - Factor indicating which condition a pair of participants experienced, Baseline, No Labels or With Labels.
	⁃	Pair - ID column for the pair of participants in this data row

	⁃	participant_a - ID column for participant a of the pair
	⁃	pp_a_n_clusters - number of clusters formed by participant a during the sorting task
	⁃	pp_a_a_dist - average Euclidean distance between all ‘A’ category items in participant a’s sort. Represents part of the within category distance measure.
	⁃	pp_a_b_dist - average Euclidean distance between all ‘B’ category items in participant a’s sort. Represents part of the within category distance measure.
	⁃	pp_a_ab_dist - average Euclidean distance between all ‘A’ vs ‘B’ category items in participant a’s sort. Represents the between category distance measure.
	⁃	real_cat_diff_a - absolute difference between the average of pp_a_a_dist + pp_a_b_dist vs. pp_a_ab_dist. Represents the difference between within and between category distances, as a proxy to the categoricality of the participant’s sort.
	⁃	real_cat_diff_log_ratio_a - log transformed ratio between pp_a_a_dist + pp_a_b_dist vs pp_a_ab_dist, as a proxy to the categoricality of the participant’s sort.
	⁃	window_height_a - height of participant a's screen measured in number of pixels.
	⁃	window_width_a - width of participant a's screen measured in number of pixels.

	⁃	participant_b - ID column for participant b of the pair
	⁃	pp_b_n_clusters - number of clusters formed by participant a during the sorting task
	⁃	pp_b_a_dist - average Euclidean distance between all ‘A’ category items in participant b’s sort. Represents part of the within category distance measure.
	⁃	pp_b_b_dist - average Euclidean distance between all ‘B’ category items in participant b’s sort. Represents part of the within category distance measure.
	⁃	pp_b_ab_dist - average Euclidean distance between all ‘A’ vs ‘B’ category items in participant b’s sort. Represents the between category distance measure.
	⁃	real_cat_diff_B - absolute difference between the average of pp_b_a_dist + pp_b_b_dist vs.  pp_b_ab_dist. Represents the difference between within and between category distances, as a proxy to the categoricality of the participant’s sort.
	⁃	real_cat_diff_log_ratio_b - log transformed ratio between pp_b_a_dist + pp_b_b_dist vs pp_b_ab_dist, as a proxy to the categoricality of the participant’s sort.
	⁃	window_height_b - height of participant b's screen measured in number of pixels.
	⁃	window_width_b - width of participant b's screen measured in number of pixels.

	⁃	real_cat_diff_pairwise - absolute difference between real_cat_diff_a and real_cat_diff_b, used as a measure of difference in categoricality of sorts between participant a and b.
	⁃	rank_r - the rank correlation between a pair of participants’ pairwise distance matrices.
	⁃	z_transformed_rank_r - standardized measure of rank_r column with Z transformation.
