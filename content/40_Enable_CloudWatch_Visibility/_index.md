---
title: "Enable CloudWatch Visibility"
chapter: true
weight: 90
pre: "<b>5. </b>"
---

### Create a Cloud Watch Panel

The form of consumption of logs by Cloud One Network Security takes place through third party, you can use any Syslog Server/SIEM but in this case we will use AWS Cloud Watch.

To do it you can read the logs in the Cloud Watch service or we can use a custom Panel in AWS Cloud Watch. For this approach we can deploy another Cloud Formation template.





![CloudWatch1](/images/CF.png)

![CloudWatch2](/images/Create_Stack.png)

![CloudWatch3](/images/Stack_Details.png)

![CloudWatch4](/images/Stack_Details.png)

![CloudWatch5](/images/Stack_Details.png)

![CloudWatch6](/images/Stack_Details.png)

![CloudWatch7](/images/Stack_Details.png)

```
AWSTemplateFormatVersion: "2010-09-09"
Description: Creates Cloudwatch Dashboard for Cloud One Network Security
Parameters:
  DashboardName:
    Description: Insert the Name for the CloudWatch Panel
    Type: String
    Default: Cloud_One_Network_Security_Panel
  AlarmInstanceID:
    Description: Insert the Instance ID of Network Security Instance
    Type: String
  AlarmARN:
    Description: Insert the ARN for the Network Security Instance Alarm
    Type: String
  C1NSRegion:
    Description: Insert the Region where the Network Security Instance sits
    Type: String
    Default: us-east-1
Resources:
  BasicDashboard:
    Type: AWS::CloudWatch::Dashboard
    Properties:
      DashboardName: !Ref DashboardName
      DashboardBody:
        Fn::Sub: '{
              "widgets": [
                 {
                     "type": "alarm",
                     "x":0,
                     "y":0,
                     "width": 12,
                     "height": 3,
                     "properties": {
                         "alarms": [
                           "${AlarmARN}"
                           ],
                         "region": [
                           "${C1NSRegion}"
                           ],
                         "period": 60,
                         "title": "Cloud One Network Security - Status"
                     }
                  },
                  {
                     "type": "metric",
                     "x":0,
                     "y":4,
                     "width": 24,
                     "height": 6,
                     "properties": {
                         "region":"${C1NSRegion}",
                         "metrics": [
                            [ "AWS/EC2", "CPUUtilization", "InstanceId", "${AlarmInstanceID}" ],
                            [ ".", "NetworkIn", ".", "." ],
                            [ ".", "NetworkOut", ".", "." ],
                            [ ".", "NetworkPacketsIn", ".", "." ],
                            [ ".", "NetworkPacketsOut", ".", "." ],
                            [ ".", "StatusCheckFailed_System", ".", "." ],
                            [ ".", "StatusCheckFailed_Instance", ".", "." ]
                         ],
                         "view": "singleValue",
                         "period": 60,
                         "title": "Cloud One Network Security - Statistics",
                         "stat": "Average"
                     }
                  },
                  {
                     "type": "metric",
                     "x":0,
                     "y":11,
                     "width": 14,
                     "height": 6,
                     "properties": {
                         "region":"${C1NSRegion}",
                         "metrics": [
                            [ "AWS/EC2", "NetworkIn", "InstanceId", "${AlarmInstanceID}" ],
                            [ ".", "NetworkOut", ".", "." ]
                         ],
                         "view": "timeSeries",
                         "period": 60,
                         "title": "Data Transfered Bytes",
                         "stat": "Average"
                     }
                  },
                  {
                     "type": "metric",
                     "x":16,
                     "y":11,
                     "width": 8,
                     "height": 6,
                     "properties": {
                         "region":"${C1NSRegion}",
                         "metrics": [
                            [ "AWS/EC2", "NetworkIn", "InstanceId", "${AlarmInstanceID}" ],
                            [ ".", "NetworkOut", ".", "." ]
                         ],
                         "view": "singleValue",
                         "period": 60,
                         "title": "Bytes Consumed",
                         "stat": "Sum",
                         "setPeriodToTimeRange": true
                     }
                  },
                  {
                     "type": "metric",
                     "x":0,
                     "y":18,
                     "width": 14,
                     "height": 6,
                     "properties": {
                         "region":"${C1NSRegion}",
                         "metrics": [
                            [ "AWS/EC2", "NetworkPacketsIn", "InstanceId", "${AlarmInstanceID}" ],
                            [ ".", "NetworkPacketsOut", ".", "." ]
                         ],
                         "view": "timeSeries",
                         "period": 60,
                         "title": "Packets Transfered",
                         "stat": "Average"
                     }
                  },
                  {
                     "type": "metric",
                     "x":16,
                     "y":18,
                     "width": 8,
                     "height": 6,
                     "properties": {
                         "region":"${C1NSRegion}",
                         "metrics": [
                            [ "AWS/EC2", "NetworkPacketsIn", "InstanceId", "${AlarmInstanceID}" ],
                            [ ".", "NetworkPacketsOut", ".", "." ]
                         ],
                         "view": "singleValue",
                         "period": 60,
                         "title": "Packets Transfered",
                         "stat": "Sum",
                         "setPeriodToTimeRange": true
                     }
                  },
                  {
                     "type": "log",
                     "x":0,
                     "y":24,
                     "width": 24,
                     "height": 6,
                     "properties": {
                         "region":"${C1NSRegion}",
                         "view": "bar",
                         "period": 60,
                         "title": "Cloud One Network Security - BLOCK Action",
                         "stat": "Sum",
                         "query": "SOURCE \u0027network_security_logs\u0027 | fields @timestamp, @message \n| sort @timestamp desc \n| limit 20 \n| filter @message like \"Block\" \n| filter @message not like \"IP Reputation\" \n| stats count() by bin(30s) "
                     }
                  },
                  {
                     "type": "log",
                     "x":0,
                     "y":31,
                     "width": 24,
                     "height": 6,
                     "properties": {
                         "region":"${C1NSRegion}",
                         "view": "table",
                         "period": 60,
                         "title": "Cloud One Network Security - BLOCK Action",
                         "stat": "Sum",
                         "query": "SOURCE \u0027network_security_logs\u0027 | fields @timestamp, @message \n| sort @timestamp desc \n| limit 20 \n| filter @message like \"Block\" \n| filter @message not like \"IP Reputation\" "
                     }
                  },
                  {
                     "type": "log",
                     "x":0,
                     "y":38,
                     "width": 24,
                     "height": 6,
                     "properties": {
                         "region":"${C1NSRegion}",
                         "view": "bar",
                         "period": 60,
                         "title": "Cloud One Network Security - PERMIT Action",
                         "stat": "Sum",
                         "query": "SOURCE \u0027network_security_logs\u0027 | fields @timestamp, @message \n| sort @timestamp desc \n| limit 20 \n| filter @message like \"Permit\" \n| filter @message not like \"IP Reputation\" \n| stats count() by bin(30s) "
                     }
                  },
                  {
                     "type": "log",
                     "x":0,
                     "y":45,
                     "width": 24,
                     "height": 6,
                     "properties": {
                         "region":"${C1NSRegion}",
                         "view": "table",
                         "period": 60,
                         "title": "Cloud One Network Security - PERMIT Action",
                         "stat": "Sum",
                         "query": "SOURCE \u0027network_security_logs\u0027 | fields @timestamp, @message \n| sort @timestamp desc \n| limit 20 \n| filter @message like \"Permit\" \n| filter @message not like \"IP Reputation\" "
                     }
                  },
                  {
                     "type": "log",
                     "x":0,
                     "y":52,
                     "width": 24,
                     "height": 6,
                     "properties": {
                         "region":"${C1NSRegion}",
                         "view": "bar",
                         "period": 60,
                         "title": "Cloud One Network Security - Geo BLOCK",
                         "stat": "Sum",
                         "query": "SOURCE \u0027network_security_logs\u0027 | fields @timestamp, @message \n| sort @timestamp desc \n| limit 20 \n| filter @message like \"Block\" \n| filter @message like \"IP Reputation\" \n| stats count() by bin(30s) "
                     }
                  },
                  {
                     "type": "log",
                     "x":0,
                     "y":59,
                     "width": 24,
                     "height": 6,
                     "properties": {
                         "region":"${C1NSRegion}",
                         "view": "table",
                         "period": 60,
                         "title": "Cloud One Network Security - Geo BLOCK",
                         "stat": "Sum",
                         "query": "SOURCE \u0027network_security_logs\u0027 | fields @timestamp, @message \n| sort @timestamp desc \n| limit 20 \n| filter @message like \"Block\" \n| filter @message like \"IP Reputation\" "
                     }
                  }
              ]
          }'
```

After the creation of the Stack, you can check the Panel, to check it, go to AWS Cloud Watch service and click in Dashboard

![CloudWatch12](/images/CW_Dash.png) 

With that you can will be able to use the Dashboard to monitor the Appliance performance and also the Detection and Block statistics:

![CloudWatch13](/images/cloudwatchpanel.png) 



--------

### Well, we just generated our first automated AWS Well-Architect Framework report from Cloud One - Conformity :star-struck: :robot: :white_check_mark: :cloud:

![Report6](/images/report6.png) 