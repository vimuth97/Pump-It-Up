# Pump-It-Up

This is a solution for the classification challenge `Pump it Up: Data Mining the Water Table` by `DrivenData` available at <br /> https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/ using sklearn on jupyter notebook.

Followings are the pre-processing and feature engineering techniques I used in my solution.

<br />
<br />

## Pre-processing and Feature Engineering Techniques
1. Converted all categorical values in the dataframe to lowercase.
2. Every value repeats less than 30 times in each column(categorical features only) was replaced with `other`. 
3. Handling missing values. <br />
   Missing values of following features were filled with corresponding values.<br />

    | Feature Name | Value |
    | ------ | ------ |
    | construction_year | 1959|
    | longitude | mean of the longitude grouped by `district_code` |
    | latitude | mean of the latitude grouped by `district_code` |
    | scheme_name | -1|
    | scheme_management | -1 |
    | funder | -1 |
    | subvillage | -1 |
    | installer | -1 |
4. One-hot encoding was done to features `public_meeting` and `permit` ignoring missing values.
5. Label encoding was done to following features.
    * funder
    * installer
    * basin
    * subvillage
    * lga
    * ward 
    * scheme_management 
    * scheme_name
    * extraction_type
    * extraction_type_class
    * management
    * management_group
    * payment_type
    * water_quality
    * quantity_group
    * source
    * source_class
    * waterpoint_type
6. Standard normalization was done to following features.
    * amount_tsh
    * population
    * num_private
    * gps_height
    * num_days(created feature)
7. Following features were removed due to corresponding reasons.<br />
    | Feature Name | Reason |
    | ------ | ------ |
    | region | redundant with `region_code` |
    | wpt_name | unique for every record |
    | recorded_by | same for every record |
    | id | unique for every record |
    | extraction_type_group | highly correlated with `extraction_type` |
    | quantity | highly correlated with `quantity_group` |
    | payment | highly correlated with `payment_type` |
    | quality_group | highly correlated with `water_quality_` |
    | waterpoint_type_group | highly correlated with `waterpoint_type` |
    | source_type | highly correlated with `source` |
8. Created a new feature `num_days` using existing feature `date_recorded` and carried out standard normalization.
9. Features `permit_False` (derived from applying one-hot encoding to `permit`) and `num_private` were dropped due to low feature importance (<0.002).
