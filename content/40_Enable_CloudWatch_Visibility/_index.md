---
title: "Enable CloudWatch Visibility"
chapter: true
weight: 40
pre: "<b>5. </b>"
---

# Enable CloudWatch Visibility

### Create an Amazon CloudWatch Panel

The form of consumption of logs by Trend Micro Cloud One - Network Security takes place through third party integrations, you can use any Syslog Server/SIEM but in this workshop we will use Amazon CloudWatch.

To do it you can read the logs in the CloudWatch service or we can create a custom Panel in Amazon CloudWatch. For this approach we can deploy CloudFormation template to simplify our life.

> Let's create the Panel with CloudFormation :laptop: :cloud: :bar_chart:

---

#### 1. Navigate to the [AWS console](https://aws.amazon.com/) 
- Navigate to **CloudFormation**
- Click on **Create Stack > With new resources(standard)**

{{% notice note %}}
<p style='text-align: left;'>
If you follow the steps before correctly you will see the other previous two stacks that we created in the AWS CloudFormation stack list.
</p>
{{% /notice %}}

![CloudWatch1](/images/CF1.png)

---

#### 2. Download the CloudFormation Template

**Download** -> [Network Security CloudWatch Template](/cft/Network_Security_CloudWatch.yml)

<details><summary markdown="span"><code>View CloudFormation template contents here</code></summary>

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

</details>
<br/>

---

#### 3. Create Stack.
- Select the **Upload a template file**
- Choose the template: **Network_Security_CloudWatch.yml**
- click on **Next**

![CloudWatch2](/images/Create_Stack.png)

---

#### 4. Open a new tab and navigate to [AWS](https://aws.amazon.com/)
- Navigate to **CloudWatch**
- In left-hand menu, under Alarms click on **All alarms**
- Use the search filter: **Modernization-Workshop-Network-Security-Appliance**
- Select the **Name** of the alarm

![CloudWatch10](/images/panel_details.png)

---

#### 5. Copy the Alarm's **ARN** value and the **InstanceId** value.

![CloudWatch10](/images/panel_values.png)

---

#### 6. Switch back to the CloudFormation's specify stack details tab.
- **Stack name**: <code>Demo-Cloud-One-Network-Security-Panel</code>
- **AlarmARN**: paste the alarm ARN value here
- **AlarmInstanceID**: paste the InstanceId value here
- **C1NSRegion**: aws region Network Security appliance is in
- **DashboardName**: CloudWatch Panel dashboard name
- Click on **Next**

![CloudWatch3](/images/Stack_Details.png)

---

#### 7. (Optional) Configure stack options
- Add **Tags** if desired 
- Click on **Next**

![CloudWatch10](/images/panel_tags.png)

---

#### 8. Review deployment.
- Click on **Create stack**

![CloudWatch11](/images/panel_review.png)
![CloudWatch12](/images/panel_review2.png)

---

#### 9. After the CloudWatch Panel Stack has reached Create_Complete, you can check the CloudWatch Panel.

- Navigate to **CloudWatch**
- Select **Dashboards** from left-hand menu
- Open Dashboard: **Cloud_One_Network_Security_Panel**

![CloudWatch14](/images/CW_Dash.png) 

With that you can will be able to use the Dashboard to monitor the Appliance performance and also the Detection and Block statistics:

![CloudWatch15](/images/cloudwatchpanel.png) 



--------

### Congrats on your custom CloudWatch view from Cloud One - Network Security :star-struck: :robot: :white_check_mark: :cloud:

