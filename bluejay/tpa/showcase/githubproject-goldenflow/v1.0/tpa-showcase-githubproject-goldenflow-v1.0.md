**https://github.com/governify/zoo/tree/main/bluejay/tpa/showcase/githubproject-goldenflow/v1.0**

**Support:** <https://app.gitter.im/#/room/#governify_community:gitter.im>

## **Changelog**

|**Version**|**Date**|**Description**|**Authors**|
| - | - | - | - |
|**v1.0**|**2024-09-04**|**Complete description**|**Javier Fernández**|

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

# **TP1: At least 75% of 'In Progress' issues must match creation of a branch.(by Team, Hourly)**

**When an issue is moved to In Progress, a branch associated to this issue must be created.**

This TP provides information about team in relation to creation of new branches associated to an issue in the "In Progress" column. The correct application of this practice requires that the following actions are done:

1. An **issue** in the "Todo" column is moved to the "In Progress" column.
2. A **new branch** is created.
3. New branch is associated to the "In Progress" issue.

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

# **TP2: At least 75% of 'In Progress' issues must have different branches associated.(by Team, Hourly)**

**When an issue is moved to In Progress, a new branch associated to this issue must be created.**

This TP provides information about team in relation to creation of new branches associated to an issue in the "In Progress" column. This team practice also requires that each issue in In Progress have a different branch associated with it. The correct application of this practice requires that the following actions are done:

1. An **issue** in the "Todo" column is moved to the "In Progress" column.
2. A **new branch** is created.
3. New branch is associated to the "In Progress" issue and will not be associated with any other issue.

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

# **TP3: At least 75% of 'In Review' issues must match creation of a Pull Request.(by Team, Hourly)**

**When an issue is moved to In Review, a Pull Request associated to that issue must be created.**

This TP provides information about team in relation to creation of new pull requests associated to an issue in the "In Review" column. The correct application of this practice requires that the following actions are done:

1. An **issue** in the "In Progress" column is moved to the "In Review" column.
2. A **pull request** is created.
3. New open pull request is associated to the "In Review" issue.

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

# **TP4: At least 75% of 'Done' issues must match merge of a Pull Request.(by Team, Hourly)**

**When an issue is moved to Done, the Pull Request associated to the issue must be merge.**

This TP provides information about the team regarding the merging of pull requests associated to an issue in the 'Done' column. The correct application of this practice requires that the following actions are done:

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
