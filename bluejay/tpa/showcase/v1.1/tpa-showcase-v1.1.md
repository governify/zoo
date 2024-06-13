**https://github.com/governify/zoo/tree/main/bluejay/tpa/showcase/v1.1**

**Support:** <https://app.gitter.im/#/room/#governify_community:gitter.im>

## **Changelog**

|**Version**|**Date**|**Description**|**Authors**|
| - | - | - | - |
|**v1.0**|**2024-06-06**|**Complete description**|**Javier Fernández**|

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

# **TP1: Percentage of new branches related to “In Progress” <a name="_page5_x72.00_y89.25"></a>issues (by Team, Hourly)**

**When an issue is started, it should usually get its own branch.**

This TP provides information about the team in relation to creating branches right after moving an issue to "In Progress". The correct application of this practice requires that the following actions are done simultaneously (checked every hour):

1. An **issue** is moved from the "Todo" column to the "In Progress" column.
1. A **branch** that contains the number of the **issue** moved to "In Progress" in the title, in the format **/number**, is **created**.



|**Example**|
| - |
|<p>1. The issue called “Creation of pets for vets **#35**” is moved from “Todo” to “In Progress”.</p><p>2. Then, a new branch is created with the number of the issue included in its name as follows: “PetsCreation**/35**”, “feature**/35**-Pets-creation”, etc.</p>|

### **Calculation Pre-Requirements** (if not met, a point won’t be created in the corresponding period):

- A new branch was created during the last hour.

### **Metrics:**

- **ATP1**: number of branches created including in its name the number of an issue in the column of “In Progress” by the team in the last hour.
- **BTP1**: number of branches created by the team in the last hour.

### **Guarantee:**

| ATP1/BTP1 × 100 ≥ 75 ![](Aspose.Words.4ec03acd-2318-481d-93b7-f01ad26fb58d.006.png)1 |
| - |

HOURLY by TEAM

### Possible False-Positive:

- **Sample sequence**:
  1. The issue is moved to the “In Progress” column.
  2. The same issue is moved to another column within the same hour.

### Dashboard block:

- **Timegraph (member)**: Amount of issues in the “In Progress” column over time by member (ATP4).
  - **Acceptable threshold**: Lower or equal to 1.
  - **Unacceptable threshold**: Greater than 1.
