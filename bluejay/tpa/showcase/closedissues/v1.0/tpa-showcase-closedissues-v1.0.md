**https://github.com/governify/zoo/tree/main/bluejay/tpa/showcase/closedissues/v1.0**

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

# **TP1: At most 1 closed issue every weeks.(by Member, Weekly)**

**A developer should close 1 issue every weeks.**

This TP provides information about members in relation to close issues. The correct application of this practice requires that the following actions are done:

1. An **issue** is created and assigned to a member.
2. An **issue** is closed.

|**Example**|
| - |
|<p>1. The issue called “Creation of pets for vets **#35**” is created and assigned to Kevin. Then, after completing the task the issue is closed.</p>|

### **Metrics:**

- **COUNT_CLOSEDISSUES_MEMBER**: number of closed issues assigned to a member in the week.

### **Guarantee:**

| COUNT_CLOSEDISSUES_MEMBER ≥ 1 <br> WEEKLY by MEMBER |
| - |

### Dashboard block:

- **Timegraph (member)**: Number of closed issues over time by member (COUNT_CLOSEDISSUES_MEMBER).
  - **Acceptable threshold**: Greater or equal than 1.
  - **Unacceptable threshold**: lower than 1.

![image](https://github.com/user-attachments/assets/e404fdf2-8b0f-42d6-9264-3ab3bb8f1b33)


# **TP2: At least 75% of the issues closed by a member should have at least one comment from any member.(by Member, Weekly)**

**A developer should close an issue only if it has at least comment.**

This TP provides information about members in relation to close issues with at least one comment. The correct application of this practice requires that the following actions are done:

1. An **issue** is created and assigned to a member.
2. An **issue** is commented for any member.
3. An **issue** is closed.

|**Example**|
| - |
|<p>1. The issue called “Creation of pets for vets **#35**” is created and assigned to Kevin. George comments in the issue. Then, after completing the task the issue is closed.</p>|

### **Metrics:**

- **COUNT_CLOSEDISSUES_MEMBER**: number of closed issues assigned to a member in the week.
- **COUNT_COMMENTED_CLOSEDISSUES_MEMBER**: number of commented closed issues assigned to a member in the week.

### **Guarantee:**

| COUNT_COMMENTED_CLOSEDISSUES_MEMBER/COUNT_CLOSEDISSUES_MEMBER ≥ 75 <br> WEEKLY by MEMBER |
| - |

### Dashboard block:

- **Timegraph (member)**: Correlation between commented closed issues and closed issues by member (COUNT_CLOSEDISSUES_MEMBER and COUNT_COMMENTED_CLOSEDISSUES_MEMBER).
  - **Acceptable threshold**: Greater or equal than 75%.
  - **Unacceptable threshold**: lower than 75%.

![image](https://github.com/user-attachments/assets/547ce836-f593-4bdf-99f2-45be18a99556)
