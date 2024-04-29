---
layout: default
title: Export Format
parent: Software
nav_order: 5
---

# Export File Format
{: .no_toc }

This document contains the column names and descriptions for exports available via the [VoteAmerica+ customer portal](https://secure.voteamerica.com/export/).

Many columns will be blank in live exports for several reasons, including:
* States have varying field requirements and available methods for completing an action.
* Some columns have been deprecated and the data are no longer collected by VoteAmerica tools. These columns
are still included in reporting to provide access to historic data. Deprecated columns are marked below with `(DEPRECATED)`.

1. TOC
{:toc}

## Absentee Tool Export Format

| Column Title                             | Description                                                                                                                                                                                                                                          |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID                                       | The ID we store internally for the ballot request                                                                                                                                                                                                    |
| Subscriber                               | The name of the subscriber                                                                                                                                                                                                                           |
| Time Started (UTC)                       | The date and time that the first page of the ballot request was submitted, in UTC                                                                                                                                                                    |
| First Name                               | The user's first name                                                                                                                                                                                                                                |
| Middle Name                              | (DEPRECATED) The user's middle name                                                                                                                                                                                                                  |
| Last Name                                | The user's last name                                                                                                                                                                                                                                 |
| Suffix                                   | (DEPRECATED) The user's name suffix                                                                                                                                                                                                                  |
| Date of Birth                            | The user's date of birth                                                                                                                                                                                                                             |
| Email                                    | The user's email address                                                                                                                                                                                                                             |
| Phone                                    | The user's phone number                                                                                                                                                                                                                              |
| Address 1                                | The user's address1                                                                                                                                                                                                                                  |
| Address 2                                | The user's address2                                                                                                                                                                                                                                  |
| City                                     | The user's city                                                                                                                                                                                                                                      |
| Zipcode                                  | The user's zipcode                                                                                                                                                                                                                                   |
| State                                    | The user's state                                                                                                                                                                                                                                     |
| Mailing Address 1                        | (DEPRECATED) The user's mailing address1                                                                                                                                                                                                             |
| Mailing Address 2                        | (DEPRECATED) The user's mailing address2                                                                                                                                                                                                             |
| Mailing City                             | (DEPRECATED) The user's mailing city                                                                                                                                                                                                                 |
| Mailing State                            | (DEPRECATED) The user's mailing state                                                                                                                                                                                                                |
| Mailing Zipcode                          | (DEPRECATED) The user's mailing zipcode                                                                                                                                                                                                              |
| Subscriber SMS Opt In                    | True/False if the user has selected to opt-in to the subscriber's SMS list                                                                                                                                                                           |
| Completed                                | If the user has (1) clicked a link to visit their state's online ballot request portal, (2) had their ballot request submitted to their Local Election Official, and/or (3) emailed themselves a ballot request form and downloaded it at least once |
| PDF Emailed to Voter                     | If the user has emailed themselves a printable customized ballot request form                                                                                                                                                                        |
| Redirected To State Website              | If the user clicked a link to visit their state's ballot request portal                                                                                                                                                                              |
| PDF submitted to LEO                     | (DEPRECATED) If VoteAmerica's toolset directly submitted the ballot request to the user's Local Election Official                                                                                                                                    |
| PDF Download Count                       | For users who have emailed themselves a ballot request form, the number of times they clicked "download" in their email                                                                                                                              |
| Total Forms Mailed With Return Envelopes | (DEPRECATED) The number of forms mailed to the user's Local Election Official                                                                                                                                                                        |
| source                                   | The ?source= query param                                                                                                                                                                                                                             |
| utm_source                               | The ?utm_source= query param                                                                                                                                                                                                                         |
| utm_medium                               | The ?utm_medium= query param                                                                                                                                                                                                                         |
| utm_campaign                             | The ?utm_campaign= query param                                                                                                                                                                                                                       |
| utm_content                              | The ?utm_content= query param                                                                                                                                                                                                                        |
| utm_term                                 | The ?utm_term= query param                                                                                                                                                                                                                           |
| Embed URL                                | For submissions done inside an embed, the URL of the page where the tool was embedded                                                                                                                                                                |
| Session ID                               | The ID of a user's session. For tracking users across multiple tools or visits.                                                                                                                                                                      |
| Referring Tool                           | For users who were linked to the absentee tool by another tool, the name of the tool                                                                                                                                                                 |
| Updated At (UTC)                         | The date and time when this action's data was last updated, in UTC                                                                                                                                                                                   |


## FutureVoter Tool Export Format

| Column Title                | Description                                                                                                                                                                                                                                    |
|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID                          | The ID we store internally for the registration                                                                                                                                                                                                |
| Subscriber                  | The name of the subscriber                                                                                                                                                                                                                     |
| Time Started (UTC)          | The time that the first page of the registration was submitted                                                                                                                                                                                 |
| First Name                  | The user's first name                                                                                                                                                                                                                          |
| Date of Birth               | The user's date of birth                                                                                                                                                                                                                       |
| Zipcode                     | The user's zipcode                                                                                                                                                                                                                             |
| State                       | The user's state                                                                                                                                                                                                                               |
| Completed                   | If the user has (1) clicked a link to visit their state's online registration portal, (2) had their registration submitted to their Local Election Official, and/or (3) emailed themselves a registration form and downloaded it at least once |
| PDF Emailed to Voter        | If the user has emailed themselves a printable registration form                                                                                                                                                                               |
| Redirected To State Website | If the user clicked a link to visit their state's online registration portal                                                                                                                                                                   |
| Total Self Print Downloads  | For users who have emailed themselves a registration form, the number of times they clicked "download" in their email                                                                                                                          |
| source                      | The ?source= query param                                                                                                                                                                                                                       |
| utm_source                  | The ?utm_source= query param                                                                                                                                                                                                                   |
| utm_medium                  | The ?utm_medium= query param                                                                                                                                                                                                                   |
| utm_campaign                | The ?utm_campaign= query param                                                                                                                                                                                                                 |
| utm_content                 | The ?utm_content= query param                                                                                                                                                                                                                  |
| utm_term                    | The ?utm_term= query param                                                                                                                                                                                                                     |
| Embed URL                   | For submissions done inside an embed, the URL of the page where the tool was embedded                                                                                                                                                          |
| Session ID                  | The ID of a user's session. For tracking users across multiple tools or visits.                                                                                                                                                                |
| Referring Tool              | For users who were linked to the FutureVoter tool by another tool, the name of the tool                                                                                                                                                        |
| Updated At (UTC)            | The date and time when this action's data was last updated, in UTC                                                                                                                                                                             |

## Locate Tool Export Format

| Column Title          | Description                                                                                  |
|-----------------------|----------------------------------------------------------------------------------------------|
| ID                    | The ID we store internally for the verification                                              |
| Subscriber            | The name of the subscriber                                                                   |
| Time Started (UTC)    | The time that the first page of the verification was done, in UTC                            |
| Email                 | The email address of the user                                                                |
| Phone                 | The phone number of the user                                                                 |
| Unstructured Address  | The user's address as they submitted it, before parsing it into separate parts               |
| Address 1             | The user's address1                                                                          |
| Address 2             | The user's address2                                                                          |
| City                  | The user's city                                                                              |
| Zipcode               | The user's zipcode                                                                           |
| State                 | The user's state                                                                             |
| Subscriber SMS Opt In | True/False if the user opted into the subscriber's SMS list                                  |
| Registered            | True/False if VoteAmerica's data provider indicated that the user has an active registration |
| source                | The ?source= query param                                                                     |
| utm_source            | The ?utm_source= query param                                                                 |
| utm_medium            | The ?utm_medium= query param                                                                 |
| utm_campaign          | The ?utm_campaign= query param                                                               |
| utm_content           | The ?utm_content= query param                                                                |
| utm_term              | The ?utm_term= query param                                                                   |
| Embed URL             | For submissions done inside an embed, the URL of the page where the tool was embedded        |
| Session ID            | The ID of a user's session. For tracking users across multiple tools or visits.              |
| Updated At (UTC)      | The date and time when this action's data was last updated, in UTC                           |


## Register Tool Export Format

| Column Title                             | Description                                                                                                                                                                                                                                    |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID                                       | The ID we store internally for the registration                                                                                                                                                                                                |
| Subscriber                               | The name of the subscriber                                                                                                                                                                                                                     |
| Time Started (UTC)                       | The time that the first page of the registration was submitted                                                                                                                                                                                 |
| Previous Title                           | (DEPRECATED) The previous title the user had                                                                                                                                                                                                   |
| Previous First Name                      | (DEPRECATED) The previous first name the user had                                                                                                                                                                                              |
| Previous Middle Name                     | (DEPRECATED) The previous middle name the user had                                                                                                                                                                                             |
| Previous Last Name                       | (DEPRECATED) The previous last name the user had                                                                                                                                                                                               |
| Previous Suffix                          | (DEPRECATED) The suffix the user previously held                                                                                                                                                                                               |
| Title                                    | (DEPRECATED) The user's title                                                                                                                                                                                                                  |
| First Name                               | The user's first name                                                                                                                                                                                                                          |
| Middle Name                              | (DEPRECATED) The user's middle name                                                                                                                                                                                                            |
| Last Name                                | The user's last name                                                                                                                                                                                                                           |
| Suffix                                   | (DEPRECATED) The user's name suffix                                                                                                                                                                                                            |
| Date of Birth                            | The user's date of birth                                                                                                                                                                                                                       |
| Gender                                   | (DEPRECATED) The user's gender                                                                                                                                                                                                                 |
| Race-Ethnicity                           | (DEPRECATED) The user's race-ethnicity                                                                                                                                                                                                         |
| Email                                    | The user's email address                                                                                                                                                                                                                       |
| Phone                                    | The user's phone number                                                                                                                                                                                                                        |
| Address 1                                | The user's address1                                                                                                                                                                                                                            |
| Address 2                                | The user's address2                                                                                                                                                                                                                            |
| City                                     | The user's city                                                                                                                                                                                                                                |
| Zipcode                                  | The user's zipcode                                                                                                                                                                                                                             |
| State                                    | The user's state                                                                                                                                                                                                                               |
| Previous Address 1                       | (DEPRECATED) The user's previous address1                                                                                                                                                                                                      |
| Previous Address 2                       | (DEPRECATED) The user's previous address2                                                                                                                                                                                                      |
| Previous City                            | (DEPRECATED) The user's previous city                                                                                                                                                                                                          |
| Previous State                           | (DEPRECATED) The user's previous state                                                                                                                                                                                                         |
| Previous Zipcode                         | (DEPRECATED) The user's previous zipcode                                                                                                                                                                                                       |
| Mailing Address 1                        | (DEPRECATED) The user's mailing address1                                                                                                                                                                                                       |
| Mailing Address 2                        | (DEPRECATED) The user's mailing address2                                                                                                                                                                                                       |
| Mailing City                             | (DEPRECATED) The user's mailing city                                                                                                                                                                                                           |
| Mailing State                            | (DEPRECATED) The user's mailing state                                                                                                                                                                                                          |
| Mailing Zipcode                          | (DEPRECATED) The user's mailing zipcode                                                                                                                                                                                                        |
| Subscriber SMS Opt In                    | True/False if the user has selected to opt-in to the subscriber's SMS list                                                                                                                                                                     |
| Completed                                | If the user has (1) clicked a link to visit their state's online registration portal, (2) had their registration submitted to their Local Election Official, and/or (3) emailed themselves a registration form and downloaded it at least once |
| PDF Emailed to Voter                     | If the user has emailed themselves a printable registration form                                                                                                                                                                               |
| Redirected To State Website              | If the user clicked a link to visit their state's online registration portal                                                                                                                                                                   |
| PDF Submitted to LEO                     | (DEPRECATED) If VoteAmerica's toolset directly submitted the registration to the user's Local Election Official                                                                                                                                |
| Total Self Print Downloads               | For users who have emailed themselves a registration form, the number of times they clicked "download" in their email                                                                                                                          |
| Total Forms Mailed with Return Envelopes | (DEPRECATED) The number of forms mailed to the user's Local Election Official                                                                                                                                                                  |
| source                                   | The ?source= query param                                                                                                                                                                                                                       |
| utm_source                               | The ?utm_source= query param                                                                                                                                                                                                                   |
| utm_medium                               | The ?utm_medium= query param                                                                                                                                                                                                                   |
| utm_campaign                             | The ?utm_campaign= query param                                                                                                                                                                                                                 |
| utm_content                              | The ?utm_content= query param                                                                                                                                                                                                                  |
| utm_term                                 | The ?utm_term= query param                                                                                                                                                                                                                     |
| Embed URL                                | For submissions done inside an embed, the URL of the page where the tool was embedded                                                                                                                                                          |
| Session ID                               | The ID of a user's session. For tracking users across multiple tools or visits.                                                                                                                                                                |
| Referring Tool                           | For users who were linked to the register tool by another tool, perhaps after they found out they were not registered via the verify tool, the name of the tool                                                                                |
| Updated At (UTC)                         | The date and time when this action's data was last updated, in UTC                                                                                                                                                                             |

## Reminders Tool Export Format

| Column Title          | Description                                                                           |
|-----------------------|---------------------------------------------------------------------------------------|
| ID                    | The ID we store internally for the verification                                       |
| Subscriber            | The name of the subscriber                                                            |
| Time Started (UTC)    | The time that the first page of the verification was done                             |
| First Name            | The user's first name                                                                 |
| Last Name             | The user's last name                                                                  |
| Date of Birth         | The date of birth of the user                                                         |
| Email                 | The email address of the user                                                         |
| Phone                 | The phone number of the user                                                          |
| Address 1             | The user's Address1                                                                   |
| Address 2             | The user's Address2                                                                   |
| City                  | The user's city                                                                       |
| Zipcode               | The user's zipcode                                                                    |
| State                 | The user's state                                                                      |
| Subscriber SMS Opt In | True/False if the user opted into the subscriber's SMS list                           |
| source                | The ?source= query param                                                              |
| utm_source            | The ?utm_source= query param                                                          |
| utm_medium            | The ?utm_medium= query param                                                          |
| utm_campaign          | The ?utm_campaign= query param                                                        |
| utm_content           | The ?utm_content= query param                                                         |
| utm_term              | The ?utm_term= query param                                                            |
| Embed URL             | For submissions done inside an embed, the URL of the page where the tool was embedded |
| Session ID            | The ID of a user's session. For tracking users across multiple tools or visits.       |
| Updated At (UTC)      | The date and time when this action's data was last updated, in UTC                    |

## Upcoming Elections Tool Export Format

| Column Title          | Description                                                                                |
|-----------------------|--------------------------------------------------------------------------------------------|
| ID                    | The ID we store internally for the verification                                            |
| Subscriber            | The name of the subscriber                                                                 |
| Time Started (UTC)    | The time that the first page of the verification was done                                  |
| Email                 | The email address of the user                                                              |
| Phone                 | The phone number of the user                                                               |
| Address 1             | The user's address1                                                                        |
| Address 2             | The user's address2                                                                        |
| City                  | The user's city                                                                            |
| Zipcode               | The user's zipcode                                                                         |
| State                 | The user's state                                                                           |
| Lookup Type           | The value is 'point' if elections were retrieved by coordinates, 'state' if found by state |
| Subscriber SMS Opt In | True/False if the user opted into the subscriber's SMS list                                |
| source                | The ?source= query param                                                                   |
| utm_source            | The ?utm_source= query param                                                               |
| utm_medium            | The ?utm_medium= query param                                                               |
| utm_campaign          | The ?utm_campaign= query param                                                             |
| utm_content           | The ?utm_content= query param                                                              |
| utm_term              | The ?utm_term= query param                                                                 |
| Embed URL             | For submissions done inside an embed, the URL of the page where the tool was embedded      |
| Session ID            | The ID of a user's session. For tracking users across multiple tools or visits.            |
| Updated At (UTC)      | The date and time when this action's data was last updated, in UTC                         |

## Verify Tool Export Format

| Column Title          | Description                                                                                  |
|-----------------------|----------------------------------------------------------------------------------------------|
| ID                    | The ID we store internally for the verification                                              |
| Subscriber            | The name of the subscriber                                                                   |
| Time Started (UTC)    | The time that the first page of the verification was done                                    |
| First Name            | The user's first name                                                                        |
| Last Name             | The user's last name                                                                         |
| Date of Birth         | The date of birth of the user                                                                |
| Email                 | The email address of the user                                                                |
| Phone                 | The phone number of the user                                                                 |
| Address 1             | The user's Address1                                                                          |
| Address 2             | The user's Address2                                                                          |
| City                  | The user's city                                                                              |
| Zipcode               | The user's zipcode                                                                           |
| State                 | The user's state                                                                             |
| Subscriber SMS Opt In | True/False if the user opted into the subscriber's SMS list                                  |
| Registered            | True/False if VoteAmerica's data provider indicated that the user has an active registration |
| source                | The ?source= query param                                                                     |
| utm_source            | The ?utm_source= query param                                                                 |
| utm_medium            | The ?utm_medium= query param                                                                 |
| utm_campaign          | The ?utm_campaign= query param                                                               |
| utm_content           | The ?utm_content= query param                                                                |
| utm_term              | The ?utm_term= query param                                                                   |
| Embed URL             | For submissions done inside an embed, the URL of the page where the tool was embedded        |
| Session ID            | The ID of a user's session. For tracking users across multiple tools or visits.              |
| Updated At (UTC)      | The date and time when this actin's data was last updated, in UTC                            |
