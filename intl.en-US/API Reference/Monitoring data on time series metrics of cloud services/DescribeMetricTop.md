# DescribeMetricTop {#doc_api_Cms_DescribeMetricTop .reference}

You can call this operation to query the monitoring data on time series metrics of cloud services sorted by specified fields in a specified period in time.

## Parameter description {#description .section}

-   For more information about how to assign values to the Project, Metric, Period, and Dimensions parameters for cloud services, call DescribeMetricMetaList or see [Preset metrics reference](~~28619~~).
-   The period specified by StartTime and EndTime includes the time point specified by EndTime but does not include the time point specified by StartTime. StartTime cannot be the same as or later than EndTime.
-   Cursor is a paging parameter. If this parameter is null, the current page is the last page. Otherwise, the current page is not the last page.
-   The typical values of Period is 60 \(1 minute\), 300 \(5 minutes\), and 900 \(15 minutes\). You can set this parameter based on related documents or your actual needs. For example, if you set Period to 60, 1,000 instead of 1,440 data records will be returned each day, because the maximum number of records that can be returned each day is 1,000. If you set Period to 300, 288 data records will be returned.

## Debugging {#apiExplorer .section}

You can use [API Explorer](https://api.aliyun.com/#product=Cms&api=DescribeMetricTop) to perform debugging. API Explorer allows you to perform various operations to simplify API usage. For example, you can retrieve APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeMetricTop| The operation that you want to perform. Set the value to DescribeMetricTop.

 |
|MetricName|String|Yes|cpu\_idle| The name of the metric.

 |
|Namespace|String|Yes|acs\_ecs\_dashboard| The namespace of the monitored service.

 |
|Dimensions|String|No|\[\{"instanceId":"i-abcdefgh12\*\*\*\*"\}\]| The resources to be monitored in the key-value format. The common key-value set is "instanceId:XXXXXX." If you hope to see a key-value map expressed by JSON strings, set Dimensions to ordered strings.

 |
|EndTime|String|No|2019-01-30 00:10:00| The end time. It can be the time that has passed since 00:00:00, January 1, 1970 in milliseconds, or a time in the 2015-10-20 00:00:00 format.

 |
|Express|String|No|\{"groupby":\["userId","instanceId"\]\}| The expression for real-time computation based on the existing results, such as`{"groupby":["instanceId"]}`.

 |
|Length|String|No|1000| The number of records returned by each query. It is used in paged queries. Default value: 1000.

 |
|OrderDesc|String|No|Average| The field by which values are sorted in descending order. You must set the Orderby parameter or the OrderDescp parameter.

 |
|Orderby|String|No|Average| The field by which values are sorted. You must set the Orderby parameter or the OrderDescp parameter.

 |
|Period|String|No|60| The time interval at which monitoring data is queried. Unit: second. If this parameter is not specified, raw data is queried at the report period specified when the corresponding metric was created. If this parameter is specified, raw data is queried at the specified period.

 |
|StartTime|String|No|2019-01-30 00:00:00| The start time. It can be the time that has passed since 00:00:00, January 1, 1970 in milliseconds, or a time in the 2015-10-20 00:00:00 format.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Code|String|200| The status code. A value of 200 indicates that the call is successful.

 |
|Datapoints|String|\[\{"timestamp":1548777660000,"userId":"123","instanceId":"i-abc","Minimum":9.92,"Average":9.92,"Maximum":9.92\}\]| The list of monitoring data in the following format: `{ “timestamp”:1490164200000, “Maximum”:100, “userId”:“123456789876****”, “Minimum”:4.55, “instanceId”:“i-bp18abl200xk9599****”, “Average”:93.84 }`.

 |
|Message|String|Success| The error message. This parameter is null when Code is 200.

 |
|Period|String|60| The time interval at which monitoring data is queried. Unit: second.

 |
|RequestId|String|3121AE7D-4AFF-4C25-8F1D-C8226EBB1F42| The request ID for troubleshooting.

 |

## Examples {#demo .section}

Sample requests

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeMetricTop
&MetricName=cpu_idle
&Namespace=acs_ecs_dashboard 
&<Common request parameters>

```

Successful response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeMetricTopResponse>
  <Period>60</Period> 
  <Datapoints> 
    <order>1</order>
    <timestamp>1551687360000</timestamp>
    <userId>12345****</userId>
    <instanceId>i-2zeehst1****</instanceId>
    <Maximum>16.41</Maximum>
    <Minimum>4.66</Minimum>
    <Average>7.74</Average>
    <_count>1</_count>
  </Datapoints> 
  <Datapoints> 
    <order>2</order>
    <timestamp>1551687360000</timestamp>
    <userId>12345****</userId>
    <instanceId>i-2zefxdy2****</instanceId>
    <Maximum>15.74</Maximum>
    <Minimum>5.03</Minimum>
    <Average>7.14</Average>
    <_count>1</_count>
  </Datapoints> 
  <RequestId>1F68A4E8-4488-48E7-9189-3E1F5165E64E</RequestId>
  <Code>200</Code>
</DescribeMetricTopResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"Period":"60",
	"Datapoints":[
		{
			"timestamp":1551687360000,
			"order":1,
			"_count":1,
			"Maximum":16.41,
			"userId":"12345****",
			"Minimum":4.66,
			"instanceId":"i-2zeehst1****",
			"Average":7.74
		},
		{
			"timestamp":1551687360000,
			"order":2,
			"_count":1,
			"Maximum":15.74,
			"userId":"12345****",
			"Minimum":5.03,
			"instanceId":"i-2zefxdy2****",
			"Average":7.14
		}
	],
	"RequestId":"1F68A4E8-4488-48E7-9189-3E1F5165E64E",
	"Code":"200"
}
```

## Error code {#section_tg6_haz_qfq .section}

[View error codes](https://error-center.aliyun.com/status/product/Cms)

