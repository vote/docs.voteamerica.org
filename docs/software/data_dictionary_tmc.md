---
layout: default
title: TMC sync
parent: Data dictionaries
grand_parent: Software
nav_order: 3
---

# Data dictionary: The Movement Cooperative sync
{: .no_toc }

This document contains the column names and descriptions for data synced from VoteAmerica+ to TMC's data warehouse 
via the [TMC sync](/integrations/the_movement_cooperative/).

Note: Some columns have been deprecated and the data are no longer collected by VoteAmerica tools. 
These columns are still included in syncs to provide access to historic data. 
Deprecated columns are marked below with `(DEPRECATED)`.

The sync is available for these VoteAmerica+ tools:

1. TOC
{:toc}

## Absentee tool sync

| Column Title              | Description                                                                                                                                                                                                                                          |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| slug                      | An identifier for your customer                                                                                                                                                                                                                      |
| uuid                      | The ID we store internally for the absentee ballot request                                                                                                                                                                                           |
| subscriber_name           | The name of the subscriber (i.e. your customer name)                                                                                                                                                                                                 |
| subscriber_id             | VoteAmerica's internal identifier for the subscriber / customer                                                                                                                                                                                      |
| created_at                | The date and time that the first page of the ballot request flow was submitted, in UTC                                                                                                                                                               |
| updated_at                | The date and time when this action's data was last updated, in UTC                                                                                                                                                                                   |
| first_name                | The user's first name                                                                                                                                                                                                                                |
| middle_name               | (DEPRECATED) The user's middle name                                                                                                                                                                                                                  |
| last_name                 | The user's last name                                                                                                                                                                                                                                 |
| suffix                    | (DEPRECATED) The user's name suffix                                                                                                                                                                                                                  |
| date_of_birth             | The user's date of birth                                                                                                                                                                                                                             |
| email                     | The user's email address                                                                                                                                                                                                                             |
| phone                     | The user's phone number                                                                                                                                                                                                                              |
| address1                  | The user's address1                                                                                                                                                                                                                                  |
| address2                  | The user's address2                                                                                                                                                                                                                                  |
| city                      | The user's city                                                                                                                                                                                                                                      |
| zipcode                   | The user's zipcode                                                                                                                                                                                                                                   |
| state_id                  | The 2-letter code for the user's state                                                                                                                                                                                                               |
| mailing_address1          | (DEPRECATED) The user's mailing address1                                                                                                                                                                                                             |
| mailing_address2          | (DEPRECATED) The user's mailing address2                                                                                                                                                                                                             |
| mailing_city              | (DEPRECATED) The user's mailing city                                                                                                                                                                                                                 |
| mailing_state_id          | (DEPRECATED) The 2-letter code for the user's mailing state                                                                                                                                                                                          |
| mailing_zipcode           | (DEPRECATED) The user's mailing zipcode                                                                                                                                                                                                              |
| sms_opt_in_subscriber     | True/False if the user has selected to opt-in to the subscriber's SMS list                                                                                                                                                                           |
| source                    | The ?source= query param                                                                                                                                                                                                                             |
| utm_source                | The ?utm_source= query param                                                                                                                                                                                                                         |
| utm_medium                | The ?utm_medium= query param                                                                                                                                                                                                                         |
| utm_campaign              | The ?utm_campaign= query param                                                                                                                                                                                                                       |
| utm_content               | The ?utm_content= query param                                                                                                                                                                                                                        |
| utm_term                  | The ?utm_term= query param                                                                                                                                                                                                                           |
| embed_url                 | The URL of the page where the Absentee tool was embedded                                                                                                                                                                                             |
| session_id                | The ID of a user's session. For tracking users across multiple tools or visits.                                                                                                                                                                      |
| finished                  | If the user has (1) clicked a link to visit their state's online ballot request portal, (2) had their ballot request submitted to their Local Election Official, and/or (3) emailed themselves a ballot request form and downloaded it at least once |
| self_print                | If the user has emailed themselves a printable customized ballot request form                                                                                                                                                                        |
| finished_external_service | If the user clicked a link to visit their state's ballot request portal                                                                                                                                                                              |
| leo_message_sent          | (DEPRECATED) If VoteAmerica's toolset directly submitted the ballot request to the user's Local Election Official                                                                                                                                    |
| total_downloads           | For users who have emailed themselves a ballot request form, the number of times they clicked "download" in their email                                                                                                                              |
| referring_tool            | For users who were linked to the absentee tool by another tool, the name of the tool                                                                                                                                                                 |
| forms_sent                | (DEPRECATED) The number of forms mailed to the user's Local Election Official                                                                                                                                                                        |

## Register tool sync


| Column Title              | Description                                                                                                                                                                                                                                    |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| slug                      | An identifier for your customer                                                                                                                                                                                                                |
| uuid                      | The ID we store internally for the registration                                                                                                                                                                                                |
| subscriber_name           | The name of the subscriber (i.e. your customer name)                                                                                                                                                                                           |
| subscriber_id             | VoteAmerica's internal identifier for the subscriber / customer                                                                                                                                                                                |
| created_at                | The date and time that the first page of the registration flow was submitted, in UTC                                                                                                                                                           |
| updated_at                | The date and time when this action's data was last updated, in UTC                                                                                                                                                                             |
| previous_title            | (DEPRECATED) The previous title the user had                                                                                                                                                                                                   |
| previous_first_name       | (DEPRECATED) The previous first name the user had                                                                                                                                                                                              |
| previous_middle_name      | (DEPRECATED) The previous middle name the user had                                                                                                                                                                                             |
| previous_last_name        | (DEPRECATED) The previous last name the user had                                                                                                                                                                                               |
| previous_suffix           | (DEPRECATED) The suffix the user previously held                                                                                                                                                                                               |
| title                     | (DEPRECATED) The user's title                                                                                                                                                                                                                  |
| first_name                | The user's first name                                                                                                                                                                                                                          |
| middle_name               | (DEPRECATED) The user's middle name                                                                                                                                                                                                            |
| last_name                 | The user's last name                                                                                                                                                                                                                           |
| suffix                    | (DEPRECATED) The user's name suffix                                                                                                                                                                                                            |
| date_of_birth             | The user's date of birth                                                                                                                                                                                                                       |
| gender                    | (DEPRECATED) The user's gender                                                                                                                                                                                                                 |
| race_ethnicity            | (DEPRECATED) The user's race-ethnicity                                                                                                                                                                                                         |
| email                     | The user's email address                                                                                                                                                                                                                       |
| phone                     | The user's phone number                                                                                                                                                                                                                        |
| address1                  | The user's address1                                                                                                                                                                                                                            |
| address2                  | The user's address2                                                                                                                                                                                                                            |
| city                      | The user's city                                                                                                                                                                                                                                |
| zipcode                   | The user's zipcode                                                                                                                                                                                                                             |
| state_id                  | The 2-letter code for the user's state                                                                                                                                                                                                         |
| previous_address1         | (DEPRECATED) The user's previous address1                                                                                                                                                                                                      |
| previous_address2         | (DEPRECATED) The user's previous address2                                                                                                                                                                                                      |
| previous_city             | (DEPRECATED) The user's previous city                                                                                                                                                                                                          |
| previous_state_id         | (DEPRECATED) The 2-letter code for the user's previous state                                                                                                                                                                                   |
| previous_zipcode          | (DEPRECATED) The user's previous zipcode                                                                                                                                                                                                       |
| mailing_address1          | (DEPRECATED) The user's mailing address1                                                                                                                                                                                                       |
| mailing_address2          | (DEPRECATED) The user's mailing address2                                                                                                                                                                                                       |
| mailing_city              | (DEPRECATED) The user's mailing city                                                                                                                                                                                                           |
| mailing_state_id          | (DEPRECATED) The 2-letter code for the user's mailing state                                                                                                                                                                                    |
| mailing_zipcode           | (DEPRECATED) The user's mailing zipcode                                                                                                                                                                                                        |
| sms_opt_in_subscriber     | True/False if the user has selected to opt-in to the subscriber's SMS list                                                                                                                                                                     |
| source                    | The ?source= query param                                                                                                                                                                                                                       |
| utm_source                | The ?utm_source= query param                                                                                                                                                                                                                   |
| utm_medium                | The ?utm_medium= query param                                                                                                                                                                                                                   |
| utm_campaign              | The ?utm_campaign= query param                                                                                                                                                                                                                 |
| utm_content               | The ?utm_content= query param                                                                                                                                                                                                                  |
| utm_term                  | The ?utm_term= query param                                                                                                                                                                                                                     |
| embed_url                 | The URL of the page where the Register tool was embedded                                                                                                                                                                                       |
| session_id                | The ID of a user's session. For tracking users across multiple tools or visits.                                                                                                                                                                |
| referring_tool            | For users who were linked to the register tool by another tool, perhaps after they found out they were not registered via the verify tool, the name of the tool                                                                                |
| finished                  | If the user has (1) clicked a link to visit their state's online registration portal, (2) had their registration submitted to their Local Election Official, and/or (3) emailed themselves a registration form and downloaded it at least once |
| self_print                | If the user has emailed themselves a printable registration form                                                                                                                                                                               |
| finished_external_service | If the user clicked a link to visit their state's online registration portal                                                                                                                                                                   |
| leo_message_sent          | (DEPRECATED) If VoteAmerica's toolset directly submitted the registration to the user's Local Election Official                                                                                                                                |
| total_downloads           | For users who have emailed themselves a registration form, the number of times they clicked "download" in their email                                                                                                                          |
| forms_sent                | (DEPRECATED) The number of forms mailed to the user's Local Election Official                                                                                                                                                                  |

## Verify tool sync

| Column Title          | Description                                                                                  |
|-----------------------|----------------------------------------------------------------------------------------------|
| slug                  | An identifier for your customer                                                              |
| uuid                  | The ID we store internally for the verification                                              |
| subscriber_name       | The name of the subscriber (i.e. your customer name)                                         |
| subscriber_id         | VoteAmerica's internal identifier for the subscriber / customer                              |
| created_at            | The time that the first page of the verification flow was submitted                          |
| updated_at            | The date and time when this action's data was last updated, in UTC                           |
| first_name            | The user's first name                                                                        |
| last_name             | The user's last name                                                                         |
| date_of_birth         | The date of birth of the user                                                                |
| email                 | The email address of the user                                                                |
| phone                 | The phone number of the user                                                                 |
| address1              | The user's Address1                                                                          |
| address2              | The user's Address2                                                                          |
| city                  | The user's city                                                                              |
| zipcode               | The user's zipcode                                                                           |
| state_id              | The 2-letter code for the user's state                                                       |
| sms_opt_in_subscriber | True/False if the user opted into the subscriber's SMS list                                  |
| registered            | True/False if VoteAmerica's data provider indicated that the user has an active registration |
| source                | The ?source= query param                                                                     |
| utm_source            | The ?utm_source= query param                                                                 |
| utm_medium            | The ?utm_medium= query param                                                                 |
| utm_campaign          | The ?utm_campaign= query param                                                               |
| utm_content           | The ?utm_content= query param                                                                |
| utm_term              | The ?utm_term= query param                                                                   |
| embed_url             | The URL of the page where the Verify tool was embedded                                       |
| session_id            | The ID of a user's session. For tracking users across multiple tools or visits.              |
