---
headline: 'Conditional formatting of Google Sheets'
date: 2017-07-12
category: google-apps-scripts
tags:
  - spreadsheets
  - advanced-sheets-services
---

### Advanced Sheets Services

Adding Conditional Formatting programmatically requires that [Advanced Google Services] is enabled in the script. This is basically just enabling a Sheets class in the script that interacts with the [Google Sheets API] v4.

#### JSON Object

Navigate through the JSON representation object to piece together the [request]:

- [AddConditionalFormatRuleRequest]
  - [ConditionalFormatRule]
    - [GridRange]
    - [BooleanRule]
      - [BooleanCondition]
        - [ConditionType]
      - [CellFormat]

```js
// Conditionally sets the background of cells to red within range B2:J1000
function setConditionalFormat() {
  var ss = SpreadsheetApp.getActiveSpreadsheet()
  var sheet = ss.getSheets()[0]

  var format_req = {
    "requests": [{
      "addConditionalFormatRule": { 
        "rule": {
          "ranges": [{
            "sheetId": sheet.getSheetId(),
            "startRowIndex": 1,
            "endRowIndex": sheet.getMaxRows(),
            "startColumnIndex": 1,
            "endColumnIndex": 10
            }],
          "booleanRule": {
            "condition": {
              "type": "BLANK"
            },
            "format": {
              "backgroundColor": {
                "red": 1,
                "green": 0,
                "blue": 0,
                "alpha": 1
              }
            }
          }
        },
        "index": 0,
      }
    }],
  "includeSpreadsheetInResponse": false,
  }

  Sheets.Spreadsheets.batchUpdate(JSON.stringify(format_req), ss.getId())
}
```

[Advanced Google Services]: https://developers.google.com/apps-script/advanced/sheets
[Google Sheets API]: https://developers.google.com/sheets/api/reference/rest/
[request]: https://developers.google.com/sheets/api/reference/rest/v4/spreadsheets/request
[AddConditionalFormatRuleRequest]: https://developers.google.com/sheets/api/reference/rest/v4/spreadsheets/request#AddConditionalFormatRuleRequest
[ConditionalFormatRule]: https://developers.google.com/sheets/api/reference/rest/v4/spreadsheets#ConditionalFormatRule
[GridRange]: https://developers.google.com/sheets/api/reference/rest/v4/spreadsheets#GridRange
[BooleanRule]: https://developers.google.com/sheets/api/reference/rest/v4/spreadsheets#BooleanRule
[BooleanCondition]: https://developers.google.com/sheets/api/reference/rest/v4/spreadsheets#BooleanCondition
[ConditionType]: https://developers.google.com/sheets/api/reference/rest/v4/spreadsheets#ConditionType
[CellFormat]: https://developers.google.com/sheets/api/reference/rest/v4/spreadsheets#CellFormat