**https://github.com/governify/zoo/tree/main/bluejay/tpa/US/PSG2-2526/v1.0**

**Support:** <https://app.gitter.im/#/room/#governify_community:gitter.im>

## **Changelog**

|**Version**|**Date**|**Description**|**Authors**|
| - | - | - | - |
|**v1.1**|**2024-10-31**|**Complete description**|**Javier Fernández**|

## <a name="_page3_x72.00_y72.00"></a>**Introduction and context**

This document provides a detailed explanation on how to correctly interpret the TPA in Bluejay.

Some definitions in relation to the Governify ecosystem (more precisely, for Bluejay) that will facilitate the understanding of the TPA are explained in the following points:

1. A **TPA (Team Practices Agreement)** is made up of **TPs (Team Practices)**.
1. Each **TP** is made up of one **guarantee.**
1. A **guarantee** defines what a work team must comply with to ensure its proper functioning.
1. Each **guarantee** needs an **objective**, which will be using one or more **metrics** along with a threshold value, and a **period** that defines the time boundary for the compliance of the guarantee.
1. Each **metric** represents a single variable that will be measured from a project.



|**Example**|
| - |
|<p>If we want the work team to make at least one pull request weekly, that will be our **TP**, which will be included in the **TPA**. We will then need to create a **guarantee,** which will have an **objective** that will need a **metric** to represent the variable “number of pull requests created by the team” (we will give it the ID “NUMBER\_PR\_CREATED”) and a **period**, which will be “weekly” in this case.</p><p>Given all the previous context, our **guarantee’s objective** would be “NUMBER\_PR\_CREATED >= 1” and the **period** would be “weekly”.</p>|



6. Each **guarantee** is represented by a **block** in the **dashboard** view of Bluejay. A block is characterized by a title and a series of graphs (one or more).
6. **Blocks** have different display **styles** according to the guarantee. In this TPA we will use the following blocks:
- **Timegraph by member**: Evolution of the value that a guarantee takes over time. This block requires 1 guarantee and can be used for displaying data by team or by each member.

---

# Summary

- TPa: At least 75% of 'In Progress' issues must match creation of a branch.(by Team, Hourly)
- TPb: At least 75% of 'In Progress' issues must have different branches associated.(by Team, Hourly)
- TPc: At least 75% of 'In Review' issues must match the creation of a Pull Request.(by Team, Hourly)
- TPd: At least 75% of 'Done' issues must match the merge of a Pull Request.(by Team, Hourly)
- TPe: Number of "In Progress" issues is less than or equal to 1.(by Member, Hourly)
- TPf: Number of "Done" issues is greater than or equal to 1.(by Member, Weekly)
- TPg: Each Pull Request should be approved before merging.(by Team, Weekly)
- TPh.1: At least 75% of merged Pull Requests are approved.(By Member, Weekly)
- TPh.2: At least 1 of the merged Pull Requests is approved.(By Member, Weekly)
- TPi.1: At least 20% of PRs opened by others are approved or commented on.(By Member, Weekly)
- TPi.2: Number of teammate PRs approved or commented.(By Member, Weekly)


---
# **TPa: At least 75% of 'In Progress' issues must match creation of a branch.(by Team, Hourly)**

**When an issue is moved to In Progress, a branch associated with this issue must be created​.**

This TP provides information about team in relation to creation of new branches associated to an issue in the "In Progress" column. Create the associated branch right after the task is moved to the “In Progress” column. Associate the branch to the task The correct application of this practice requires the following actions:

1. An issue in the "Todo" column is moved to the "In Progress" column.​
2. A new branch is created from the “In Progress” issue (Development section)​.

|**Example**|
| - |
|<p>1. The issue called “Creation of pets for vets **#35**” is moved from the "Todo" column to the "In Progress" column.<br>2. The branch called "pets-form" is created.<br>3. The branch called "pets-form" is associated to the issue called “Creation of pets for vets **#35**” located in the "In Progress" column.</p>|

### **Metrics:**

- **COUNT_INPROGRESS_ISSUES_WITH_ASSOCIATED_BRANCHES**: number of in progress issues with associated branches.
- **COUNT_INPROGRESS_ISSUES**: number of in progress issues.

### **Guarantee:**

- **CORRELATION_INPROGRESSISSUES_NEWBRANCH**:

| COUNT_INPROGRESS_ISSUES_WITH_ASSOCIATED_BRANCHES/COUNT_INPROGRESS_ISSUES x 100 ≥ 75 <br> HOURLY by TEAM |
| - |

### Dashboard block:
![image](https://github.com/user-attachments/assets/69d96cbd-8b98-44f0-a666-ab7021a73fef)

- **Gauge 1**: Mean percentage of CORRELATION_INPROGRESSISSUES_NEWBRANCH since the beginning of the project.
  - **Low range**: [0%, 50%)
  - **Mid range**: [50%,75%)
  - **High range**: [75%, 100%]

- **Gauge 2**: Mean percentage of the CORRELATION_INPROGRESSISSUES_NEWBRANCH on the selected period in Grafana.
  - **Low range**: [0%, 50%)
  - **Mid range**: [50%,75%)
  - **High range**: [75%, 100%]

- **Timegraph (team)**: Evolution of CORRELATION_INPROGRESSISSUES_NEWBRANCH over time.
  - **Acceptable threshold**: Greater or equal than 75%
  - **Unacceptable threshold**: lower than 75%.

- **Correlation**: Correlation between the metrics COUNT_INPROGRESS_ISSUES_WITH_ASSOCIATED_BRANCHES and COUNT_INPROGRESS_ISSUES on the period selected in Grafana
  - X axis: COUNT_INPROGRESS_ISSUES
  - Y axis: COUNT_INPROGRESS_ISSUES_WITH_ASSOCIATED_BRANCHES

---

# **TPb: At least 75% of 'In Progress' issues must have different branches associated.(by Team, Hourly)**

**Each issue In Progress must have a different branch associated with it​.**

This TP provides information about team in relation to creation of new branches associated to an issue in the "In Progress" column. Ensure that each task in the “In Progress”
column is associated with a different branch​. Branches should not be reused for other tasks​. The correct application of this practice requires the following actions:

1. An issue in the "Todo" column is moved to the "In Progress" column.​
2. A new branch is created from the “In Progress” issue (Development section)

|**Example**|
| - |
|<p>1. The issue called “Creation of vets **#38**” is moved from the "Todo" column to the "In Progress" column.<br>2. The branch called "vets-form" is created.<br>3. The branch called "vets-form" is associated to the issue called “Creation of vets **#38**” located in the "In Progress" column and will not be associated with any other issue.</p>|

### **Metrics:**

- **COUNT_BRANCHES_ASSOCIATED_TO_INPROGRESS_ISSUES**: number of different branches associated to in progress issues.
- **COUNT_INPROGRESS_ISSUES**: number of in progress issues.

### **Guarantee:**

- **CORRELATION_BRANCHESASSOCIATED_INPROGRESSISSUES**:

| COUNT_BRANCHES_ASSOCIATED_TO_INPROGRESS_ISSUES/COUNT_INPROGRESS_ISSUES x 100 ≥ 75 <br> HOURLY by TEAM |
| - |

### Dashboard block:
![image](https://github.com/user-attachments/assets/31b2573a-942d-4656-81cf-2a60b6e74f79)

- **Gauge 1**: Mean percentage of CORRELATION_BRANCHESASSOCIATED_INPROGRESSISSUES since the beginning of the project.
  - **Low range**: [0%, 50%)
  - **Mid range**: [50%,75%)
  - **High range**: [75%, 100%]

- **Gauge 2**: Mean percentage of the CORRELATION_BRANCHESASSOCIATED_INPROGRESSISSUES on the selected period in Grafana.
  - **Low range**: [0%, 50%)
  - **Mid range**: [50%,75%)
  - **High range**: [75%, 100%]

- **Timegraph (team)**: Evolution of CORRELATION_BRANCHESASSOCIATED_INPROGRESSISSUES over time.
  - **Acceptable threshold**: Greater or equal than 75%
  - **Unacceptable threshold**: lower than 75%.

- **Correlation**: Correlation between the metrics COUNT_BRANCHES_ASSOCIATED_TO_INPROGRESS_ISSUES and COUNT_INPROGRESS_ISSUES on the period selected in Grafana
  - X axis: COUNT_INPROGRESS_ISSUES
  - Y axis: COUNT_BRANCHES_ASSOCIATED_TO_INPROGRESS_ISSUES

---

# **TPc: At least 75% of 'In Review' issues must match the creation of a Pull Request.(by Team, Hourly)**

**When an issue is moved to In Review, a Pull Request associated with that issue must be created​.**

This TP provides information about team in relation to creation of new pull requests associated to an issue in the "In Review" column. Create the associated pull request right after the task is moved to the “In Review” column. Associate the PR to the task​. The correct application of this practice requires the following actions:

1. An issue in the “In Progress" column is moved to the "In Review" column.​
2. A Pull Request is created for the branch associated to the issue (If you created a PR for the branch you associated in the TPa, the PR will be associated automatically). Otherwise, you must assign it from the Development section.​

|**Example**|
| - |
|<p>1. The issue called “Creation of user **#40**” is moved from the "In Progress" column to the "In Review" column.<br>2. The pull request called "user-form" is created.<br>3. The open pull request called "user-form" is associated to the issue called “Creation of user **#40**” located in the "In Review" column.</p>|

### **Metrics:**

- **COUNT_INREVIEW_ISSUES_WITH_ASSOCIATED_OPEN_PR**: number of in review issues with associated open pull request.
- **COUNT_INREVIEW_ISSUES**: number of in review issues.

### **Guarantee:**

- **CORRELATION_INREVIEWISSUES_OPENPR**:

| COUNT_INREVIEW_ISSUES_WITH_ASSOCIATED_OPEN_PR/COUNT_INREVIEW_ISSUES x 100 ≥ 75 <br> HOURLY by TEAM |
| - |

### Dashboard block:
![image](https://github.com/user-attachments/assets/7418ae4a-aa8e-4bc1-bd22-90961e61e56a)

- **Gauge 1**: Mean percentage of CORRELATION_INREVIEWISSUES_OPENPR since the beginning of the project.
  - **Low range**: [0%, 50%)
  - **Mid range**: [50%,75%)
  - **High range**: [75%, 100%]

- **Gauge 2**: Mean percentage of the CORRELATION_INREVIEWISSUES_OPENPR on the selected period in Grafana.
  - **Low range**: [0%, 50%)
  - **Mid range**: [50%,75%)
  - **High range**: [75%, 100%]

- **Timegraph (team)**: Evolution of CORRELATION_INREVIEWISSUES_OPENPR over time.
  - **Acceptable threshold**: Greater or equal than 75%
  - **Unacceptable threshold**: lower than 75%.

- **Correlation**: Correlation between the metrics COUNT_INREVIEW_ISSUES_WITH_ASSOCIATED_OPEN_PR and COUNT_INREVIEW_ISSUES on the period selected in Grafana
  - X axis: COUNT_INREVIEW_ISSUES
  - Y axis: COUNT_INREVIEW_ISSUES_WITH_ASSOCIATED_OPEN_PR

---

# **TPd: At least 75% of 'Done' issues must match the merge of a Pull Request.(by Team, Hourly)**

**When an issue is moved to Done, the Pull Request associated with that issue must be merged​.**

This TP provides information about the team regarding the merging of pull requests associated to an issue in the 'Done' column. Merge the associated pull request right after the task is moved to “Done” column​. The correct application of this practice requires the following actions:

1. An **issue** in the "In Review" column is moved to the "Done" column.
2. The **pull request** associated to the issue is merged (TP3).

|**Example**|
| - |
|<p>1. The issue called “Creation of admin **#42**” is moved from the "In Review" column to the "Done" column.<br>2. The open pull request called "admin-form" is merged.|

### **Metrics:**

- **COUNT_DONE_ISSUES_WITH_ASSOCIATED_CLOSED_PR**: number of done issues with associated merged pull request.
- **COUNT_DONE_ISSUES**: number of done issues.

### **Guarantee:**

- **CORRELATION_DONEISSUES_MERGEDPR**:

| COUNT_DONE_ISSUES_WITH_ASSOCIATED_CLOSED_PR/COUNT_DONE_ISSUES x 100 ≥ 75 <br> HOURLY by TEAM |
| - |

### Dashboard block:
![image](https://github.com/user-attachments/assets/712eb97e-b535-47a6-a462-ee992bb469d6)

- **Gauge 1**: Mean percentage of CORRELATION_DONEISSUES_MERGEDPR since the beginning of the project.
  - **Low range**: [0%, 50%)
  - **Mid range**: [50%,75%)
  - **High range**: [75%, 100%]

- **Gauge 2**: Mean percentage of the CORRELATION_DONEISSUES_MERGEDPR on the selected period in Grafana.
  - **Low range**: [0%, 50%)
  - **Mid range**: [50%,75%)
  - **High range**: [75%, 100%]

- **Timegraph (team)**: Evolution of CORRELATION_DONEISSUES_MERGEDPR over time.
  - **Acceptable threshold**: Greater or equal than 75%
  - **Unacceptable threshold**: lower than 75%.

- **Correlation**: Correlation between the metrics COUNT_DONE_ISSUES_WITH_ASSOCIATED_CLOSED_PR and COUNT_DONE_ISSUES on the period selected in Grafana
  - X axis: COUNT_DONE_ISSUES
  - Y axis: COUNT_DONE_ISSUES_WITH_ASSOCIATED_CLOSED_PR

---

# **TPe: Number of “In Progress” issues is less than or equal to 1.(by Member, Hourly)**

**Each developer should only be working on one issue at a time​.**

This TP provides information about team’s members in relation to the number of “In Progress” issues. Each developer should work on only one story/task at a time (at most one task in “In Progress” at any given time assigned to him/her). The correct application of this practice requires the following actions:

1. An issue is moved to the "In Progress" column only if we are not working on another task.

|**Example**|
| - |
|1. The member Alexander does not have any issues “In Progress” <br>2. He decides to move an issue that is assigned to him into the "In Progress" column. <br>3. He wants to take on a new issue, but prior to moving it into "In Progress", he must move the issue that is already "In Progress" into the “In Review” column. Then, he will be able to start a new task.|

### **Metrics:**

- **COUNT_INPROGRESSISSUES_MEMBER**: number of issues in the “In Progress” column by member in the last hour.

### **Guarantee:**

| COUNT_INPROGRESSISSUES_MEMBER ≤ 1 <br>HOURLY by MEMBER|
| - |

### Possible False-Positive:

- **Sample sequence**:
  1. The issue is moved to the “In Progress” column.
  2. The same issue is moved to another column within the same hour.

### Dashboard block:

- **Timegraph (member)**: Amount of issues in the “In Progress” column over time by member (COUNT_INPROGRESSISSUES_MEMBER)
  - **Acceptable threshold**: Lower or equal to 1.
  - **Unacceptable threshold**: Greater than 1.

![pixelized](https://github.com/governify/zoo/assets/100673872/4876a7e1-265b-4134-a25c-6a07f3ae7fb4)

---

# **TPf: Number of “Done” issues is greater than or equal to 1.(by Member, Weekly)**

**Each developer should be finishing at least one issue per week.**

This TP provides information about team’s members in relation to the number of “Done” issues each week. Each developer should finish at least one story/task every week (i.e. one task or more moved to “Done” every week). The correct application of this practice requires the following actions:

1. An issue is moved to the “Done" column.

|**Example**|
| - |
|1. The member Paul has not put any issues into the “Done” column this week yet. So he must
finish an issue before the weekends in order to comply with the established team practice. <br>3. Paul has a pull request approved by his team, so he proceeds to move the issue related to that pull request from the “In Review” column to the “Done” column, thus complying with the team practice.|

### **Metrics:**

- **COUNT_DONEISSUES_MEMBER**: number of issues in the “Done” column by member in the last week.

### **Guarantee:**

| COUNT_DONEISSUES_MEMBER ≥ 1 <br>WEEKLY by MEMBER|
| - |

### Dashboard block:

- **Timegraph (member)**: Amount of issues in the “Done” column over time by member (COUNT_DONEISSUES_MEMBER).
  - **Acceptable threshold**: Greater or equal than 1
  - **Unacceptable threshold**: Lower than 1.

![image](https://github.com/user-attachments/assets/fe66f73e-9c75-4c77-927a-6a72948d325f)

---

# **TPf: Each Pull Request should be approved before merging.(by Team, Weekly)**

**Each Pull Request should be approved before merging.**

This TP provides information about the team in relation to the reviews on each merged pull request. There should be at least one positive review associated with each merged pull request. The correct application of this practice requires the following actions:

1. A pull request is created by a member.​
2. A different member reviews the pull request with an approval.
3. The pull request is merged.

|**Example**|
| - |
| John creates a new pull request. Then, Elon reviews the pull request with approval, so that the pull request can now be merged.|

### **Metrics:**

- **COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_TEAM**: number of merged pull requests with at least one positive review by the team in the last week.
- **COUNT_PR_MERGED_TEAM**: number of merged pull requests by the team in the last week.

### **Guarantee:**

| COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_TEAM / COUNT_PR_MERGED_TEAM x 100 ≥ 75 <br> WEEKLY by TEAM |
| - |

### Dashboard block:

![image](https://github.com/user-attachments/assets/d41c2fdf-e38e-4312-9189-1aeb5be59aac)

- **Gauge 1**: Mean percentage of CORRELATION_APPROVEDMERGEDPULLREQUEST_TOTALMERGEDPULLREQUEST_TEAM since the beginning of the project.
  - **Low range**: [0%, 50%)
  - **Mid range**: [50%,75%)
  - **High range**: [75%, 100%]

- **Gauge 2**: Mean percentage of the CORRELATION_APPROVEDMERGEDPULLREQUEST_TOTALMERGEDPULLREQUEST_TEAM on the selected period in Grafana.
  - **Low range**: [0%, 50%)
  - **Mid range**: [50%,75%)
  - **High range**: [75%, 100%]

- **Timegraph (team)**: Evolution of CORRELATION_APPROVEDMERGEDPULLREQUEST_TOTALMERGEDPULLREQUEST_TEAM over time.
  - **Acceptable threshold**: Greater or equal than 75%
  - **Unacceptable threshold**: Lower than 75%.

- **Correlation**: Correlation between the metrics COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_TEAM and COUNT_PR_MERGED_TEAM on the period selected in Grafana
  - X axis: COUNT_PR_MERGED_TEAM
  - Y axis: COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_TEAM

---

# **TPh.1: At least 75% of merged Pull Requests are approved.(By Member, Weekly)**

**Each developer should only merge a Pull Request if it is approved.**

This TP provides information about members in relation to the reviews on each merged pull request. Each developer should merge his/her own pull requests only if they are already approved by other team members.​ The correct application of this practice requires the following actions:

1. A pull request is created by a member.
2. A different member reviews the pull request with an approval.
3. The pull request is merged.

|**Example**|
| - |
| John creates a new pull request. Then, Elon reviews the pull request with approval, so that the pull request can now be merged.|

### **Metrics (for a given member M):**

- **COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_MEMBER**: number of merged pull requests by member M with at least one positive review during the last week.
- **COUNT_PR_MERGED_MEMBER**: number of merged pull requests by the same member M during the last week.

### **Guarantee:**

| COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_MEMBER / COUNT_PR_MERGED_MEMBER x 100 ≥ 75 <br> WEEKLY by MEMBER |
| - |

### Dashboard block:

- **Timegraph (member)**: Evolution of CORRELATION_APPROVEDMERGEDPULLREQUEST_TOTALMERGEDPULLREQUEST_MEMBER over time.
  - **Acceptable threshold**: Greater or equal than 75%
  - **Unacceptable threshold**: Lower than 75%.
 
![image](https://github.com/user-attachments/assets/409115a3-6e1c-4fe7-912e-1d565288fc2d)

---

# **TPh.2: At least 1 of the merged Pull Requests is approved.(By Member, Weekly)**

**Each developer should only merge a Pull Request if it is approved​.**

This TP provides information about members in relation to the reviews on each merged pull request. The number of merged approved pull requests should be significant​. The correct application of this practice requires the following actions:

1. A pull request is created by a member.
2. A different member reviews the pull request with approval.
3. The pull request is merged.

|**Example**|
| - |
| John creates a new pull request. Then, Elon reviews the pull request with approval, so that the pull request can now be merged.|

### **Metrics:**

- **COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_MEMBER**: number of merged pull requests by a member with at least one positive review during the last week.

### **Guarantee:**

| COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_MEMBER ≥ 1 <br> WEEKLY by MEMBER |
| - |

### Dashboard block:

- **Timegraph (member)**: Number of merged pull requests by a member with at least one positive review over time (COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_MEMBER).
  - **Acceptable threshold**: Greater or equal than 1
  - **Unacceptable threshold**: Lower than 1.

![image](https://github.com/user-attachments/assets/0a620f16-1d84-4f3f-8f75-7c072810e155)

---

# **TPi.1: At least 20% of PRs opened by others are approved or commented on.(By Member, Weekly)**

**Each developer should add comments or approve several other teammates’ Pull Requests each week.**

This TP provides information about the team members in relation to the open pull requests with at least one comment. Each developer should make comments on or approve pull requests not created by him/her, including positive reviews and requests for changes​. The correct application of this practice requires the following actions:

1. A pull request is created by a member.
2. A different member comments or approves the pull request at least one time every week the PR remains open.​

|**Example**|
| - |
| Andrew creates a new pull request during week 3. Then, Logan comments on the pull request in the same week, but the pull request is not closed until week 4, so Logan will need to comment again in week 4 too.|

### **Metrics for a member M:**

- **COUNT_PRS_WITH_AT_LEAST_ONE_COMMENT_OR_ONE_REVIEW_COMMENT_BY_MEMBER**: number of open pull requests (not created by member M) with at least one comment by member M during the last week.
- **COUNT_PR**: number of open pull requests not created by member M during the last week.

### **Guarantee:**

| COUNT_PRS_WITH_AT_LEAST_ONE_COMMENT_OR_ONE_REVIEW_COMMENT_BY_MEMBER / COUNT_PR x 100 ≥ 20 <br> WEEKLY by MEMBER |
| - |

### Dashboard block:

- **Timegraph (member)**: Evolution of CORRELATION_COUNTPRSWITHATLEASTONECOMMENTORONEREVIEWCOMMENTBYMEMBER_AND_COUNTPR over time.
  - **Acceptable threshold**: Greater or equal than 20%
  - **Unacceptable threshold**: Lower than 20%.

![image](https://github.com/user-attachments/assets/09e0bb10-8f5d-4979-bd93-871a9f497c51)

---

# **TPh.2: Number of teammate PRs approved or commented (By Member, Weekly)**

**Each developer should add comments or approve several other teammates’ Pull Requests each week.**

This TP provides information about the team members in relation to the open pull requests with at least one comment. The number of pull requests commented on should be significant.​ The correct application of this practice requires the following actions:

1. A pull request is created by a member.
2. A different member comments or approves the pull request at least one time every week the PR remains open.​

|**Example**|
| - |
| Andrew creates a new pull request during week 3. Then, Logan comments on the pull request in the same week, but the pull request is not closed until week 4, so Logan will need to comment again in week 4.|

### **Metrics:**

- **COUNT_PRS_WITH_AT_LEAST_ONE_COMMENT_OR_ONE_REVIEW_COMMENT_BY_MEMBER**: number of pull requests not created by the member with at least one comment by the member during the last week.

### **Guarantee:**

| COUNT_PRS_WITH_AT_LEAST_ONE_COMMENT_OR_ONE_REVIEW_COMMENT_BY_MEMBER ≥ 1 <br> WEEKLY by MEMBER |
| - |

### Dashboard block:

- **Timegraph (member)**: Number of pull requests not created by the member in which the member has made a comment over time (COUNT_PRS_WITH_AT_LEAST_ONE_COMMENT_OR_ONE_REVIEW_COMMENT_BY_MEMBER).
  - **Acceptable threshold**: Greater or equal than 1
  - **Unacceptable threshold**: Lower than 1.

![image](https://github.com/user-attachments/assets/6dc03b03-cf16-4515-a23e-60cac64d8b18)
