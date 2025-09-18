**https://github.com/governify/zoo/tree/main/bluejay/tpa/castillalamancha/ISII-2526/v1.0**

**Support:** <https://app.gitter.im/#/room/#governify_community:gitter.im>

## **Changelog**

|**Version**|**Date**|**Description**|**Authors**|
| - | - | - | - |
|**v1.0**|**2025-09-18**|**Complete description**|**Javier Fernández**|

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

# **TPa: At least 75% of 'In Progress' issues with the 'Task' type must match creation of a branch.(by Team, Hourly)**

**When an issue with the 'Task' type is moved to In Progress, a branch associated to this issue must be created.**

This TP provides information about team in relation to creation of new branches associated to an issue in the "In Progress" column with the "Task" type. The correct application of this practice requires that the following actions are done:

1. An **issue** in the "Todo" column with the "Task" type is moved to the "In Progress" column.
2. A **new branch** is created.
3. New branch is associated to the "In Progress" issue.

|**Example**|
| - |
|<p>1. The issue with the "Task" type called “Creation of pets for vets **#35**” is moved from the "Todo" column to the "In Progress" column.<br>2. The branch called "pets-form" is created.<br>3. The branch called "pets-form" is associated to the issue with the "Task" type called “Creation of pets for vets **#35**” located in the "In Progress" column.</p>|

### **Metrics:**

- **COUNT_INPROGRESS_ISSUES_WITH_ASSOCIATED_BRANCHES**: number of in progress issues with the "Task" type and associated branches.
- **COUNT_INPROGRESS_ISSUES**: number of in progress issues with the "Task" type.

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

# **TPb: At least 75% of 'In Progress' issues with the 'Task' type must have different branches associated.(by Team, Hourly)**

**When an issue with the 'Task' type is moved to In Progress, a new branch associated to this issue must be created.**

This TP provides information about team in relation to creation of new branches associated to an issue in the "In Progress" column with the "Task" type. This team practice also requires that each issue in In Progress with the "Task" type have a different branch associated with it. The correct application of this practice requires that the following actions are done:

1. An **issue** in the "Todo" column with the "Task" type is moved to the "In Progress" column.
2. A **new branch** is created.
3. New branch is associated to the "In Progress" issue with the "Task" type and will not be associated with any other issue with the "Task" type.

|**Example**|
| - |
|<p>1. The issue with the "Task" type called “Creation of vets **#38**” is moved from the "Todo" column to the "In Progress" column.<br>2. The branch called "vets-form" is created.<br>3. The branch called "vets-form" is associated to the issue with the "Task" type called “Creation of vets **#38**” located in the "In Progress" column and will not be associated with any other issue with the "Task" type.</p>|

### **Metrics:**

- **COUNT_BRANCHES_ASSOCIATED_TO_INPROGRESS_ISSUES**: number of different branches associated to in progress issues with the "Task" type.
- **COUNT_INPROGRESS_ISSUES**: number of in progress issues with the "Task" type.

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

# **TPc: At least 75% of 'In Review' issues with the 'Task' type must match creation of a Pull Request.(by Team, Hourly)**

**When an issue with the 'Task' type is moved to In Review, a Pull Request associated to that issue must be created.**

This TP provides information about team in relation to creation of new pull requests associated to an issue in the "In Review" column with the "Task" type. The correct application of this practice requires that the following actions are done:

1. An **issue** in the "In Progress" column with the "Task" type is moved to the "In Review" column.
2. A **pull request** is created.
3. New open pull request is associated to the "In Review" issue with the "Task" type.

|**Example**|
| - |
|<p>1. The issue with the "Task" type called “Creation of user **#40**” is moved from the "In Progress" column to the "In Review" column.<br>2. The pull request called "user-form" is created.<br>3. The open pull request called "user-form" is associated to the issue with the "Task" type called “Creation of user **#40**” located in the "In Review" column.</p>|

### **Metrics:**

- **COUNT_INREVIEW_ISSUES_WITH_ASSOCIATED_OPEN_PR**: number of in review issues with the "Task" type and associated open pull request.
- **COUNT_INREVIEW_ISSUES**: number of in review issues with the "Task" type.

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

# **TPd: At least 75% of 'Done' issues with the 'Task' type must match merge of a Pull Request.(by Team, Hourly)**

**When an issue with the 'Task' type is moved to Done, the Pull Request associated to the issue must be merge.**

This TP provides information about the team regarding the merging of pull requests associated to an issue in the 'Done' column with the "Task" type. The correct application of this practice requires that the following actions are done:

1. An **issue** in the "In Review" column with the "Task" type is moved to the "Done" column.
2. The **pull request** associated to the issue is merged (TP3).

|**Example**|
| - |
|<p>1. The issue with the "Task" type called “Creation of admin **#42**” is moved from the "In Review" column to the "Done" column.<br>2. The open pull request called "admin-form" is merged.|

### **Metrics:**

- **COUNT_DONE_ISSUES_WITH_ASSOCIATED_CLOSED_PR**: number of done issues with the "Task" type and associated merged pull request.
- **COUNT_DONE_ISSUES**: number of done issues with the "Task" type.

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

# **TPe: Number of “In Progress” issues with the 'Task' type (by Member, Hourly)**

**A developer should only be working on one issue with the 'Task' type at a time.**

This TP provides information about team’s members in relation to the number of “In Progress” issues with the 'Task' type. The correct application of this practice is as follows:

|**Example**|
| - |
|1. The member Alexander does not have any issues “In Progress” with the 'Task' type. <br>2. He decides to move an issue with the "Task" type that is assigned to him into the "In Progress" column. <br>3. He wants to take on a new issue with the "Task" type, but prior to moving it into "In Progress", he must move the issue with the "Task" type that is already "In Progress" into the “In Review” column. Then, he will be able to start a new task.|

### **Metrics:**

- **COUNT_INPROGRESSISSUES_MEMBER**: number of issues in the “In Progress” column with the "Task" type by member in the last hour.

### **Guarantee:**

| COUNT_INPROGRESSISSUES_MEMBER ≤ 1 <br>HOURLY by MEMBER|
| - |

### Possible False-Positive:

- **Sample sequence**:
  1. The issue with the "Task" type is moved to the “In Progress” column.
  2. The same issue is moved to another column within the same hour.

### Dashboard block:

- **Timegraph (member)**: Amount of COUNT_INPROGRESSISSUES_MEMBERover time by member.
  - **Acceptable threshold**: Lower or equal to 1.
  - **Unacceptable threshold**: Greater than 1.

![pixelized](https://github.com/governify/zoo/assets/100673872/4876a7e1-265b-4134-a25c-6a07f3ae7fb4)

---

# **TPf: Number of “Done” issues with the 'Task' type (by Member, Weekly)**

**Each developer should be finishing at least 1 issue with the 'Task' type per week.**

This TP provides information about team’s members in relation to the number of “Done” issues with the "Task" type each week. The
correct application of this practice is as follows:

|**Example**|
| - |
|1. The member Paul has not put any issues with the "Task" type into the “Done” column this week yet. So he must
finish an issue with the "Task" type before the weekends in order to comply with the established team practice. <br>3. Paul has a pull request approved by his team, so he proceeds to move the issue with the "Task" type related to that pull request from the “In Review” column to the “Done” column, thus complying with the team practice.|

### **Metrics:**

- **COUNT_DONEISSUES_MEMBER**: number of issues in the “Done” column with the "Task" type by member in the last week.

### **Guarantee:**

| COUNT_DONEISSUES_MEMBER ≥ 1 <br>WEEKLY by MEMBER|
| - |

### Dashboard block:

- **Timegraph (member)**: Amount of COUNT_DONEISSUES_MEMBER over time by member.
  - **Acceptable threshold**: Greater or equal than 1
  - **Unacceptable threshold**: Lower than 1.

![image](https://github.com/user-attachments/assets/fe66f73e-9c75-4c77-927a-6a72948d325f)

---

# **TPg: Percentage of approved merged PR (by Team, Weekly)**

**Most merged PRs should be approved**

This TP provides information about the team in relation to the reviews on each merged pull request. The correct application of this practice is as follows:

1. A pull request is created by a member.
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

# **TPh.1: Percentage of approved merged PR (By Member, Weekly)**

**Most of your merged PRs should be approved by your teammates**

This TP provides information about members in relation to the reviews on each merged pull request. The correct application of this practice is as follows:

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

# **TPh.2: Number of approved mergedPR (By Member, Weekly)**

**If you merge a PR, it should be approved by at least 1 teammate**

This TP provides information about members in relation to the reviews on each merged pull request. The correct application of this practice is as follows:

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
