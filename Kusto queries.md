# Kusto queries
## Kusto query for alerts if using Log Analytics

`AppTraces
| where TimeGenerated > ago(5m)
| where Properties.CategoryName startswith "RM.Gateway.Outbound"
| where Properties.EventName == "rm_api006_successfully_called_rm_api"
| top 1 by OperationId`

## Kusto query for alerts if using Application Insights

`traces
| where timestamp > ago(24h)
| where customDimensions.CategoryName startswith "RM.Gateway.Outbound"
| where customDimensions.EventName == "rm_api006_successfully_called_rm_api"
| top 1 by operation_Id`

## Kusto query for overall status
`let EventNames = datatable(EventName: string)
[
    "last_event_name_api_001",
    "last_event_name_api_002",
    "last_event_name_api_003",
    "rm_api006_successfully_called_rm_api"
];
let CustomEventNames = datatable(EventName: string, API: string)
[
    "rm_api006_successfully_called_rm_api", "API006",
    "last_event_name_api_001", "API001",
    "last_event_name_api_002", "API002",
    "last_event_name_api_003", "API003"
];
let EventCounts = AppTraces
| where TimeGenerated > ago(5m)
| where Properties.CategoryName startswith "IBIS.Gateway.Outbound" or Properties.CategoryName startswith "RM.Gateway.Outbound"
| extend EventName = tostring(Properties.EventName)
| join kind=inner (EventNames) on EventName
| summarize EventCount = count() by EventName;
EventNames
| join kind=fullouter (CustomEventNames) on EventName
| join kind=fullouter (EventCounts) on EventName
| extend SuccessOrFailure = case(
    coalesce(EventCount, 0) > 0, "success",
    "failed"
)
| project API, SuccessOrFailure
| order by API asc`

## Kusto query for links to log files of failed processes

`let ExcludedOperationIds = AppTraces
    | where Properties.To == "End"
    | summarize by OperationId;
AppTraces
| where TimeGenerated > ago(1h) and TimeGenerated < ago(1m)
| where Properties.CategoryName startswith "IBIS.Gateway.Outbound" or Properties.CategoryName startswith "RM.Gateway.Outbound"
| summarize RowCount = count(), ProcessStart = min(TimeGenerated) by OperationId
| where not(OperationId in (ExcludedOperationIds))
//| where RowCount != 4
| extend LinkQuery = url_encode_component(zlib_compress_to_base64_string(strcat("union isfuzzy=true AppRequests, AppExceptions, AppTraces, dependencies | where OperationId == '", tostring(OperationId), "'| order by TimeGenerated desc")))
| project ProcessStart, OperationId, QueryLink = strcat("https://portal.azure.com#@68b2d50a-57dd-4bd5-85bb-a249b0b19ddf/blade/Microsoft_OperationsManagementSuite_Workspace/Logs.ReactView/resourceId/%2Fsubscriptions%2Ff15d5cbc-5768-4932-9a2d-9d5aa8b8289a%2Fresourcegroups%2Fibo-dev-assess-intsvcs-01-rg%2Fproviders%2Fmicrosoft.operationalinsights%2Fworkspaces%2Fibo-dev-assess-int-01-log/source/LogsBlade.AnalyticsShareLinkToQuery/q/", LinkQuery, "/timespan/PT1H")
| order by ProcessStart desc`

[How to liink to a query in Log Analytics or Application Insights](https://zimmergren.net/deep-linking-azure-log-analytics-and-app-insight-queries/)

