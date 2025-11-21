---
layout: default
title: Upgrading from V1 to V2
parent: Civic Data API
nav_order: 1
---

# Upgrading from V1 to V2 of the Civic Data API
{: .no_toc }

[Version 2](/api) of the VoteAmericaPlus Civic Data API is now available. This guide outlines the changes from 
[Version 1](/api/v1) and their rationale. 

1. TOC
{:toc}

## New features

### Regional overrides

As if 51 different sets of laws governing elections weren't enough, sometimes specific regions within a state
do things differently. For instance, the state of Illinois doesn't have just one URL where people across the state
can request absentee ballots; some cities and counties have their own. 

This is where our new overrides endpoint comes in. It returns a list of override objects, each of which is a case 
where region-level information should override state-level information. For each override object, 
the state name, region name, name of the field being overridden and region-level value are provided. 
[See the V2 docs](/api/#get-electionoverride) for more information.

### Footnotes

As you know, election laws in the United States can be complicated. (Are you detecting a theme here?) 
Sometimes, a simple date, boolean or string value is not enough to capture the nuance of the situation in a
particular state. 

For these cases, we've added footnotes. You can find the new `footnotes` property on `state_information` objects
on the `GET /election/data/state/{state}/` endpoint. Typically, a `state_information` object will include, for 
the given state, a field and its value. If that value has exceptions or other nuances, those will be explained
in `footnotes`. [See the V2 docs](/api/#get-electiondatastatestate) for more information.

### Multi-select fields

{: .highlight }
See the [section on deleted fields](#deleted-fields) for breaking changes resulting from the move to 
multi-select fields. 

We've added a new field format to the API: `Multi-select`. 

This format is useful for cases where there's a finite set of options and each state employs some of them. 
For example: Absentee ballot request methods. In some states, voters can request a ballot in person, online, 
or via mail, fax or email. In other states, only in-person and mail requests are available. 

For a field like this (`absentee_request_methods`), you can see the available options via the `GET /election/field` 
endpoint. If the field format is `Multi-select`, the state information field object will include an `options` property 
that is a list of all available options. 

Then, when querying a state's data via the `GET /election/data/state/{state}/` endpoint, the state information object 
will have a property `multiselect_value` that is a list of the options applicable to the state.

### More consistent naming conventions

{: .highlight}
[See below](#breaking-changes) for information on breaking changes resulting from the new naming conventions.

Version 1 of the VoteAmericaPlus Civic Data API grew over time, and some inconsistencies crept in. With the release 
of V2, we've taking the opportunity to introduce some more consistent naming conventions for our 
field slugs. For example:

* We are more consistently using the terms `absentee` and `vote-by-mail` in line with 
[definitions from the League of Women Voters](https://www.lwv.org/blog/knowing-difference-voting-absentee-vs-mail). 
Per their guidance, we use `absentee` when talking about situations where a voter must request a ballot and
`vote-by-mail` (shortened to `vbm` in slugs) for cases where all voters automatically receive a ballot in the mail.

* All `Boolean` field slugs start with `is` or `has` so they are more easily recognizable as booleans.

* Each `Boolean` field represents a feature that tends to make voting more accessible, so `true` is a good thing.
(Ex: `has_sdr_election_day`, when `true`, means the state allows same-day registration on Election Day, 
which we think is great.)

* Any field representing a URL for an official state tool (ex: online voter registration) starts with `gov_tool`.

* Any field representing a URL that points to official election laws starts with `source`.

* Any field that lists steps a voter should take includes the word `directions`.

* Any field that describes a state's election laws includes the word `laws`.

* Any field that describes a deadline relative to Election Day includes the word `deadline`.
(Ex: The number of days prior to Election Day when a voter must submit online registration in order to vote
in that election.)

* In general, we tried to make each slug as short as possible while still clearly describing what it represents.

## Breaking changes

The sections below describe breaking changes to consider when migrating from V1 to V2 of the Civic Data API.

### Renamed property `description`

On the `GET /election/field` endpoint, the property `long_name` has been renamed to the more apt `description`.

### Renamed fields

The table below lists all one-to-one renamings of field slugs. In general, the rationale for renaming was the
same across the board: To adhere to [more consistent naming conventions](#more-consistent-naming-conventions) 
as described above.

| V1 name (deprecated)                     | V2 name                                                             |
|:-----------------------------------------|:--------------------------------------------------------------------|
| alert_registration                       | alerts_registration                                                 |
| alert_vbm                                | alerts_absentee                                                     |
| ballot_curing_correction_process         | ballot_curing_directions                                            |
| ballot_curing_instructions               | ballot_curing_laws_rejection_reasons                                |
| ballot_curing_notification_process       | ballot_curing_laws_notification_process                             |
| emergency_ballot_application             | pdf_emergency_ballot_application                                    |
| emergency_ballot_request_end             | emergency_ballot_request_deadline                                   |
| emergency_ballot_rules                   | emergency_ballot_laws                                               |
| external_tool_absentee_ballot_tracker    | gov_tool_absentee_tracker                                           |
| external_tool_ovr                        | gov_tool_registration                                               |
| external_tool_polling_place              | gov_tool_polling_place                                              |
| external_tool_provisional_ballot_tracker | gov_tool_provisional_tracker                                        |
| external_tool_vbm_application            | gov_tool_absentee_request                                           |
| external_tool_verify_status              | gov_tool_verify                                                     |
| felon_vote_fees                          | felony_laws_restoration_fees                                        |
| felon_vote_restoration                   | felony_laws_restoration_process                                     |
| id_requirements_in_person_registration   | id_laws_in_person_registration                                      |
| id_requirements_in_person_voting         | id_laws_in_person_voting                                            |
| id_requirements_ovr                      | id_laws_online_registration                                         |
| id_requirements_sdr                      | id_laws_sdr                                                         |
| id_requirements_students                 | id_laws_student_voters                                              |
| id_requirements_vbm_request              | id_laws_absentee_request                                            |
| id_requirements_vbm_return               | id_laws_ballot_return                                               |
| official_info_early_voting               | source_early_voting_info                                            |
| official_info_felon                      | source_rights_restoration_info                                      |
| official_info_registration               | source_registration_info                                            |
| official_info_students                   | source_student_voting_info                                          |
| official_info_vbm                        | source_absentee_info                                                |
| official_info_voter_id                   | source_voter_id_info                                                |
| overseas_fvap_directions                 | fvap_uocava_directions                                              |
| overseas_fvap_tool                       | gov_tool_uocava                                                     |
| registration_automatic_exists            | has_automatic_registration                                          |
| registration_minimum_age                 | minimum_age_register                                                |
| registration_nvrf_box_6                  | nvra_directions_box6                                                |
| registration_nvrf_box_7                  | nvra_directions_box7                                                |
| registration_nvrf_box_8                  | nvra_directions_box8                                                |
| registration_nvrf_submission_address     | nvra_submission_address                                             |
| registration_ovr_directions              | registration_directions_online                                      |
| registration_rules                       | registration_laws                                                   |
| sdr_early_voting                         | has_sdr_early_voting                                                |
| sdr_election_day                         | has_sdr_election_day                                                |
| sdr_where                                | sdr_locations                                                       |
| state_election_code                      | source_election_code                                                |
| vbm_absentee_ballot_rules                | absentee_voting_laws                                                |
| vbm_deadline_in_person                   | absentee_deadline_in_person                                         |
| vbm_deadline_mail                        | absentee_deadline_mail                                              |
| vbm_deadline_online                      | absentee_deadline_online                                            |
| vbm_first_day_to_apply                   | absentee_request_start_date                                         |
| vbm_no_excuse                            | has_no_excuse_absentee                                              |
| vbm_other_options                        | absentee_ballot_issues                                              |
| vbm_ovbm_directions                      | absentee_directions_online                                          |
| vbm_overview                             | absentee_process_summary                                            |
| vbm_permanent_anyone                     | has_pav_everyone                                                    |
| vbm_permanent_disabled                   | has_pav_disabled                                                    |
| vbm_request_directions_mail              | absentee_directions_mail                                            |
| vbm_state_provides_ballot_postage        | has_free_ballot_postage                                             |
| vbm_universal                            | has_automatic_vbm                                                   |
| vbm_voted_ballot_deadline_in_person      | ballot_return_deadline_in_person                                    |
| vbm_voted_ballot_deadline_mail           | ballot_return_deadline_mail                                         |
| vbm_warnings                             | warnings_absentee                                                   |

### Deleted fields

The table below lists all V1 fields that have been deleted in V2. In most cases, this information is still available;
it was simply redundant with another field or the information has been migrated into footnotes or a `Multi-select`
field.

| Deleted field                                   | Rationale / details                                                                                                                                     |
|-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| early_voting                                    | Redundant with the existence of data in `early_voting_starts` and `early_voting_ends`.                                                                  |
| early_voting_notes                              | Migrated to footnotes on `early_voting_starts` and `early_voting_ends`.                                                                                 |
| emergency_ballot_request_start                  | Not necessary to track. Generally, this is when the regular absentee ballot request deadline has passed.                                                |
| external_tool_felony_restoration_state_info     | Redundant with another field now called `source_rights_restoration_info`.                                                                               |
| external_tool_vbm_application_requires_printing | Not necessary to track with an independent field. South Carolina is the only state where a ballot request form is available online but must be printed. |
| external_tool_vbm_has_regional_urls             | No longer needed because the presence of overrides will suggest regional URLs exist.                                                                    |
| felon_vote_in_prison                            | Consolidated to a `Multi-select` field. If `felon_vote_in_prison` was true, `felony_voting_options` will include `imprisoned`.                          |
| felon_vote_notes                                | Migrated to footnotes on `felony_voting_options`.                                                                                                       |
| felon_vote_parole                               | Consolidated to a `Multi-select` field. If `felon_vote_parole` was true, `felony_voting_options` will include `parole`.                                 |
| felon_vote_post_sentence                        | Consolidated to a `Multi-select` field. If `felon_vote_post_sentence` was true, `felony_voting_options` will include `post_sentence`.                   |
| felon_vote_probation                            | Consolidated to a `Multi-select` field. If `felon_vote_probation` was true, `felony_voting_options` will include `probation`.                           |
| felon_vote_release_prison                       | Redundant with options in `felon_vote_release_prison`.                                                                                                  |
| id_laws_out_of_state_accepted                   | Too difficult to maintain because of many exceptions.                                                                                                   |
| id_laws_student_id_accepted                     | Too difficult to maintain because of many exceptions.                                                                                                   |
| id_requirements_in_person_registration          | Redundant with id_laws_same_day_registration                                                                                                            |
| overseas_voting                                 | Not necessary to track because it's available in all states.                                                                                            |
| provisional_voting                              | Not necessary to track because it's available in all states.                                                                                            |
| registration_directions_felony_conviction       | Most information was redundant with other fields. In general, we want to point folks to Restore Your Vote for detailed information.                     |
| registration_submission_email                   | Consolidated to a `Multi-select` field. If `registration_submission_email` was true, `registration_methods` will include `email`.                       |
| registration_submission_fax                     | Consolidated to a `Multi-select` field. If `registration_submission_fax` was true, `registration_methods` will include `fax`.                           |
| registration_submission_in_person               | Consolidated to a `Multi-select` field. If `registration_submission_in_person` was true, `registration_methods` will include `in_person`.               |
| registration_submission_mail                    | Consolidated to a `Multi-select` field. If `registration_submission_mail` was true, `registration_methods` will include `mail`.                         |
| registration_submission_phone                   | Consolidated to a `Multi-select` field. If `registration_submission_phone` was true, `registration_methods` will include `phone`.                       |
| sdr_notes                                       | Migrated to footnotes on `has_sdr_early_voting`, `has_sdr_election_day` and `sdr_locations`.                                                            |
| specific_ballot_drop_date                       | Deprecated 2022-specific field.                                                                                                                         |
| specific_ballot_return_deadline_by_mail         | Deprecated 2022-specific field.                                                                                                                         |
| specific_ballot_return_deadline_in_person       | Deprecated 2022-specific field.                                                                                                                         |
| specific_early_voting_ends                      | Deprecated 2022-specific field.                                                                                                                         |
| specific_early_voting_starts                    | Deprecated 2022-specific field.                                                                                                                         |
| specific_general_election_date                  | Deprecated 2022-specific field.                                                                                                                         |
| specific_minimum_dob                            | Deprecated 2022-specific field.                                                                                                                         |
| specific_official_election_calendar             | Deprecated 2022-specific field.                                                                                                                         |
| specific_registration_deadline_by_mail          | Deprecated 2022-specific field.                                                                                                                         |
| specific_registration_deadline_in_person        | Deprecated 2022-specific field.                                                                                                                         |
| specific_registration_deadline_online           | Deprecated 2022-specific field.                                                                                                                         |
| specific_vbm_request_deadline_by_in_person      | Deprecated 2022-specific field.                                                                                                                         |
| specific_vbm_request_deadline_by_mail           | Deprecated 2022-specific field.                                                                                                                         |
| specific_vbm_request_deadline_online            | Deprecated 2022-specific field.                                                                                                                         |
| vbm_app_submission_email                        | Consolidated to a `Multi-select` field. If `vbm_app_submission_email` was true, `absentee_request_methods` will include `email`.                        |
| vbm_app_submission_fax                          | Consolidated to a `Multi-select` field. If `vbm_app_submission_fax` was true, `absentee_request_methods` will include `fax`.                            |
| vbm_app_submission_in_person                    | Consolidated to a `Multi-select` field. If `vbm_app_submission_in_person` was true, `absentee_request_methods` will include `in_person`.                |
| vbm_app_submission_mail                         | Consolidated to a `Multi-select` field. If `vbm_app_submission_mail` was true, `absentee_request_methods` will include `mail`.                          |
| vbm_app_submission_phone                        | Consolidated to a `Multi-select` field. If `vbm_app_submission_phone` was true, `absentee_request_methods` will include `phone`.                        |
| vbm_counties_provides_dropboxes                 | Too difficult to maintain. See VoteAmerica's Locate tool for the data we have available on dropboxes for specific elections.                            |
| vbm_notes                                       | Migrated to footnotes on various absentee-related fields.                                                                                               |
| vbm_return_drop_box                             | Consolidated to a `Multi-select` field. If `vbm_return_drop_box` was true, `ballot_return_locations` will include `drop_box`.                           |
| vbm_return_early_voting                         | Consolidated to a `Multi-select` field. If `vbm_return_early_voting` was true, `ballot_return_locations` will include `early_voting_site`.              |
| vbm_return_election_office                      | Consolidated to a `Multi-select` field. If `vbm_return_election_office` was true, `ballot_return_locations` will include `local_election_office`.       |
| vbm_return_hand_deliver_allowed                 | Redundant with options in `ballot_return_locations`. Only TN and MS won't let you hand-deliver you voted ballot.                                        |
| vbm_return_polling_place                        | Consolidated to a `Multi-select` field. If `vbm_return_polling_place` was true, `ballot_return_locations` will include `polling_place`.                 |
| vbm_state_provides_dropboxes                    | Too difficult to maintain. See VoteAmerica's Locate tool for the data we have available on dropboxes for specific elections.                            |