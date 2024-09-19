**https://github.com/governify/zoo/tree/main/bluejay/guarantee/github/NUMBER_INPROGRESSISSUES_HOURLY_UNDER_1**

**Support:** <https://app.gitter.im/#/room/#governify_community:gitter.im>

## **Changelog**

|**Version**|**Date**|**Description**|**Authors**|
| - | - | - | - |
|**v1.0**|**2024-09-01**|**Complete description**|**Javier Fernández**|

## <a name="_page3_x72.00_y72.00"></a>**NUMBER_INPROGRESSISSUES_HOURLY_UNDER_1**
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

