**https://github.com/governify/zoo/tree/main/bluejay/metric/github/COUNT_INPROGRESSISSUES_MEMBER**

**Support:** <https://app.gitter.im/#/room/#governify_community:gitter.im>

## **Changelog**

|**Version**|**Date**|**Description**|**Authors**|
| - | - | - | - |
|**v1.0**|**2024-09-01**|**Complete description**|**Javier Fernández**|

## <a name="_page3_x72.00_y72.00"></a>**COUNT_INPROGRESSISSUES_MEMBER**
This metric provides information about the number of issues in progress that each team member has in their repository project.


### API Data**
This metric makes use of the github GraphQL API. The following request is made to obtain all the issues associated with the projects of a repository:

```
{repository(name: "%PROJECT.github.repository%", owner: "%PROJECT.github.repoOwner%") {
    projectsV2(first: 5) {
      nodes {
        items(first: 100) {
          nodes {
            content {
              ... on Issue {
                bodyText
                updatedAt
                number
                author {
                  login
                }
                assignees(first: 5  ) {
                    nodes {
                        login
                    }
                }
              }
            }
            fieldValues(first: 100) {
              nodes {
                ... on ProjectV2ItemFieldUserValue {
                    field {
                        ... on ProjectV2Field {
                            name
                        }
                    }
                }
                ... on ProjectV2ItemFieldRepositoryValue {
                  field {
                    ... on ProjectV2Field {
                      name
                    }
                  }
                  repository {
                    nameWithOwner
                  }
                }
                ... on ProjectV2ItemFieldTextValue {
                  text
                  field {
                    ... on ProjectV2Field {
                      name
                    }
                  }
                }
                ... on ProjectV2ItemFieldMilestoneValue {
                    field {
                        ... on ProjectV2Field {
                            name
                        }
                    }
                    milestone {
                        number
                        title 
                    }
                }
                ... on ProjectV2ItemFieldSingleSelectValue {
                  name
                  updatedAt
                  creator {
                    login
                  }
                  field {
                    ... on ProjectV2SingleSelectField {
                      name
                    }
                  }
                }
              }
            }
          }
        }
      }
    }
  }
}
```

You can reproduce this request in the [web explorer](https://docs.github.com/es/graphql/overview/explorer) provided by github.

### Post-processing**
Once the information is obtained, it is processed by choosing the first project in the repository, all issues are filtered by selecting only those in which the user is assigned, and finally, only the issues that are in the In Progress column are chosen.

```json
{
    "0": {
        "type": "queryGetObject",
        "query": "{repository(name: \"%PROJECT.github.repository%\", owner: \"%PROJECT.github.repoOwner%\") {\r\n    projectsV2(first: 5) {\r\n      nodes {\r\n        items(first: 100) {\r\n          nodes {\r\n            content {\r\n              ... on Issue {\r\n                bodyText\r\n                updatedAt\r\n                number\r\n                author {\r\n                  login\r\n                }\r\n                assignees(first: 5  ) {\r\n                    nodes {\r\n                        login\r\n                    }\r\n                }\r\n              }\r\n            }\r\n            fieldValues(first: 100) {\r\n              nodes {\r\n                ... on ProjectV2ItemFieldUserValue {\r\n                    field {\r\n                        ... on ProjectV2Field {\r\n                            name\r\n                        }\r\n                    }\r\n                }\r\n                ... on ProjectV2ItemFieldRepositoryValue {\r\n                  field {\r\n                    ... on ProjectV2Field {\r\n                      name\r\n                    }\r\n                  }\r\n                  repository {\r\n                    nameWithOwner\r\n                  }\r\n                }\r\n                ... on ProjectV2ItemFieldTextValue {\r\n                  text\r\n                  field {\r\n                    ... on ProjectV2Field {\r\n                      name\r\n                    }\r\n                  }\r\n                }\r\n                ... on ProjectV2ItemFieldMilestoneValue {\r\n                    field {\r\n                        ... on ProjectV2Field {\r\n                            name\r\n                        }\r\n                    }\r\n                    milestone {\r\n                        number\r\n                        title \r\n                    }\r\n                }\r\n                ... on ProjectV2ItemFieldSingleSelectValue {\r\n                  name\r\n                  updatedAt\r\n                  creator {\r\n                    login\r\n                  }\r\n                  field {\r\n                    ... on ProjectV2SingleSelectField {\r\n                      name\r\n                    }\r\n                  }\r\n                }\r\n              }\r\n            }\r\n          }\r\n        }\r\n      }\r\n    }\r\n  }\r\n}",
        "cache": true
    },
    "1": {
        "type": "objectGetSubObjects",
        "location": "data.repository.projectsV2.nodes.0.items.nodes"
    },
    "2": {
        "type": "objectsFilterObjects",
        "filters": [
            "content.assignees.nodes.0.login == '%MEMBER.github.username%'"
        ]
    },
    "3": {
        "type": "runScript",
        "variables": {},
        "script": "module.exports.generic = function getFieldValues(inputData, variables) {\r\n    let result = [];\r\n    for (const issue of inputData) {\r\n        for (const fieldValue of issue.fieldValues.nodes) {\r\n            if (fieldValue.name === 'In Progress') {\r\n                               result.push(issue);\r\n                \r\n            }\r\n        }\r\n    }\r\n    return result;\r\n}"
    }
}

```
