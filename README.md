# Social Dominance Active Inference

## Pilot 3
- 6 cages of mice with 4 mice in each cage
  - C57 Mice: Cage 1, 2, 3
  - CD1 Mice: Cage 4, 5, 6

## How to use
- 1. Create environment with [conda environment yaml](./bin/elo_score_env.yml)
- 2. Run the [SLEAP distance calculation notebook](./results/2023_09_18_rc_sleap_analysis/tone_distance_analysis.ipynb)
  - The coordinate data is included in the repo so there's no need to download anything
- 3. Run the [notebook that combines the weights, ELO Score, and SLEAP data](./results/2023_09_18_pilot_3_elo_rating_calculation/pilot_3_consolidation.ipynb)

## Dataframe Overview
- The main dataframe with the weight, ELO Score, and reward competition SLEAP data is `results/2023_09_18_pilot_3_elo_rating_calculation/elo_score_and_rc_distance.pkl`
- Each row is one subject's information for one trial for any experiment
  - Because we are looking at social dominance/competition, each trial will have two rows. One for each subject.

### Columns

- `rc`: Reward Competition
- `tt`: Tube Test
- `hco`: Home Cage Observation
- `uma`: Urine Marking Assay

#### General Columns

```
strain
experiment_type
date
cage_#
tuple_animal_id
subject_id
agent_id
winner
loser
win_draw_loss
- `1`: win, `0`: lose, `0.5`: tie
original_elo_rating
updated_elo_rating
subject_ranking
agent_ranking
```

#### Weight Columns
```
subject_weight
subject_percent_body_weight
- Current weight's percentage compared to original when first being weighed for experiment
subject_amount_fed
- Amount fed after being weighed
agent_weight
agent_percent_body_weight
agent_amount_fed
```

#### Reward Competition
```
pairing_index
trial_number
```

#### Home Cage Observation
```
action
```

#### Urine Marking
```
left_number_of_spots
right_number_of_spots
spot_number_difference
percent_difference
- Calculated as "dividing the absolute value of the difference between two numbers by the average of those two numbers"
```

#### Pair social dominance stability
```
hco_tuple_animal_id
hco_winner
- List of who won between the pair
hco_loser
hco_averaged_winner
- Overall winner
hco_averaged_loser
hco_averaged_winner_win_count
- How many times the winner won
hco_averaged_loser_win_count
hco_count_difference
hco_match_count
- How many total matches/trials between this pair
hco_percent_win
- The percent of wins for all trials between this pair for this subject
hco_percentage_tie
rc_tuple_animal_id
rc_winner
rc_loser
rc_average_number_of_switches
rc_winner_no_ties
rc_loser_no_ties
rc_averaged_winner
rc_averaged_loser
rc_averaged_winner_win_count
rc_averaged_loser_win_count
rc_tie_count
rc_all_match_count_including_ties
rc_averaged_winner_win_count_minus_loser_win_count
rc_win_to_win_plus_lost_ratio
rc_win_to_all_ratio
rc_is_win_to_win_and_loss_ratio_tie
rc_tie_to_all_ratio
tt_tuple_animal_id
tt_winner
tt_loser
tt_averaged_winner
tt_averaged_loser
tt_averaged_winner_win_count
tt_averaged_loser_win_count
tt_count_difference
tt_match_count
tt_percent_win
tt_percentage_tie
```


#### SLEAP
```
File Name
Frame Start
FPS
Strain
file_base
all_subj
subj_id
subj_index
all_tone_frame
- List of frames that the trials started
corner_file
pose_estimation_file
corner_sleap

- This section is for the coordinates of each part of the operant chamber
- Which was used to calculate the actual lengths and distances within the operant chamber in the video
box_bottom_left_coordinates
reward_port_coordinates
box_bottom_right_coordinates
box_top_left_coordinates
box_top_right_coordinates
bottom_width
top_width
right_height
left_height
average_height
average_width
width_ratio
height_ratio
reward_port_scaled

track_names
track_id
rc_trial_number

- This section is for distance/coordinates/velocity for each frame in the trial
- The ones that say trial are from tone onset to a specified time(like 10 seconds after). The ones that say baseline are from a specified time before the tone onset to tone onset.
thorax_to_reward_port_baseline_slices
thorax_to_reward_port_trial_slices
scaled_coordinates_baseline_slices
scaled_coordinates_trial_slices
distance_between_subject_baseline_slices
distance_between_subject_trial_slices
thorax_velocity_baseline_slices
thorax_velocity_trial_slices
```