**https://github.com/governify/zoo/tree/main/bluejay/tpa/showcase/basic/v1.1**

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

# **TP1: Number of “In Progress” issues (by Member, Hourly)**

**A developer should only be working on one issue at a time**

This TP provides information about team’s members in relation to the number of “In Progress” issues. The correct application of this practice is as follows:

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


