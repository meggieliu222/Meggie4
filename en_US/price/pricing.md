# Pricing and Billing

EMQX Platform offers a variety of flexible product plans and pricing options to support the deployment of fully managed MQTT services exclusively for you on the leading cloud providers, so you can easily scale up or down as your needs change, without any hidden costs or fees.

## Serverless Plan

EMQX Serverless Plan is billed based on the actual usage of your deployment, including the number of session minutes and the amount of traffic generated by messages. Each user is given a certain amount of free credits at the beginning of each month, which will be used first before any charges are incurred. After this free quota (session minute or traffic) is used up, you will then be charged for any additional usage.

### Billing Unit

**Session Minute**: Represents a connection to the deployment for any duration within a one-minute timeframe. For billing purposes, any partial minute of connection is rounded up and considered as a full minute. 

**Session**: The total number of clients that are currently connected simultaneously, including offline clients that have enabled [persistent sessions](https://www.emqx.com/en/blog/mqtt-session).

**Traffic:** Traffic (including free traffic) refers to all public network traffic that flows in and out of your deployment.

**Rule Action:** The total number of action execution times in [Data Integration](../data_integration/introduction.md).

### Billing Plan

| Billing Unit | **Free quota**                  | **Price**           |
| -------------------- | -------------------------------------------- | ------------------|
| Session       |  1 million session minutes / month     | $ 2.00 per million session minutes                                |
| Traffic     | 1 GB / month              | $ 0.15 / GB              |
| Rule Action     | 1 million rule action executions / month | $ 0.25 per million rule action executions |

### Billing method

**Session fee** = sessions * connection span (measured per minute or part thereof) / 1,000,000 * 2 <br />
**Traffic fee** = Inbound and outbound traffic（byte）/ 1024 / 1024 / 1024 * 0.15 <br />
**Rule Action fee** = Number of rule action executions / 1,000,000 * 0.25

::: tip

Assume in a 24-hour billing period, a user has 120 sessions for 10 hours, 20 sessions for 10 hours, and 0 sessions for 4 hours, the total session minutes are: 120 * 60 * 10 + 20 * 60 * 10 + 0 = 84,000, and the session fee is 0 if this falls within the free quota. If the free quota has run out, the session fee will be 84,000 / 1,000,000 * 2 = 0.168, rounded up to $ 0.17. The traffic fee and the rule action fee are calculated in the same way as the session.

:::

The bill is calculated based on the fees accumulated in the previous 24 hours, with collections taking place at 0:00 daily. You can go to the [Billings](https://docs.emqx.com/en/cloud/latest/billing/overview.html) page in EMQX Platform console to find the details.

### Spend Limit

Spend Limit helps you control how much money your Serverless deployment spends each month, and you'll receive a reminder when you reach that limit. You can set the Spend Limit when you create your deployment, and you can change it later.

The spending limit can be an integer from 0 to 10000:

- If it is set to 0, the deployment will only consume the free quota, which is 1 million connection minutes, 1 GB of traffic, and 1 million rule action executions per month. When the free quota is used up, the deployment will be stopped.
- If it is set to an integer between 1 and 10,000, an action should also be selected when the consumption of the deployment reaches the limit for the month, such as stopping the deployment or reminding and continuing to charge. If there is an overdue bill, regardless of the action you previously set, the deployment will be stopped.

## Dedicated Plan

EMQX Dedicated Plan is charged based on the tier, and message transmission network traffic. There are no restrictions on the number of messages, API calls, or data integration usage. You can select the appropriate product plan based on your business needs, and be confident that the costs remain transparent and manageable even as your business expands.


### Billing Unit

**Session**: Total number of  clients that are currently connected simultaneously, including offline clients that have enabled [Persistent sessions](https://www.emqx.com/en/blog/mqtt-session).

**Base Fee**: The base fee for the instance is calculated based on the hourly unit price corresponding to the selected product plan and instance tier (maximum connection number, message TPS) at the time of deployment. In practical usage, this fee is only related to the duration of usage and will not be affected by changes in usage (connection number, message TPS).

**Traffic Fee**: Each instance tier includes a certain amount of free traffic, which is valid for the current month and will be automatically cleared at the end of the month if any remains. When device communication exceeds the gifted traffic, additional traffic fees will be charged. Here, traffic, including free traffic, measures all traffic flowing out of the deployment, including:

   - Traffic over VPC Peering or PrivateLink is not measured.
   - Traffic from messages received by the deployment, such as messages sent to the deployment from the clients, is not measured.
   - If the NAT gateway is enabled, outgoing traffic from deployment will be measured.

<table>
   <tr>
      <th>Plan</th>
      <th>tier</th>
      <th>Base Fee</th>
      <th>Free Traffic</th>
      <th>Traffic exceeded</th>
   </tr>
   <tr>
      <td rowspan="5">Dedicated</td>
      <td>1,000 connections / Up to 1,000 TPS</td>
      <td>$0.36 /hr </td>
      <td rowspan="4">100G/month</td>
      <td rowspan="4">$ 0.15/GB</td>
   </tr>
   <tr>
      <td>3,000 connections / Up to 30,000 TPS</td>
      <td>$0.64 /hr</td>
   </tr>
   <tr>
      <td>5,000 connections / Up to 10,000 TPS</td>
      <td>$0.99 /hr</td>
   </tr>
   <tr>
      <td>10,000 connections / Up to 20,000 TPS</td>
      <td>$1.49 /hr</td>
   </tr>
   <tr>
      <td>>10,000 connections</td>
      <td colspan="3" align="center">Contact us</td>
   </tr>
</table>

::: tip
Prices may vary depending on the public cloud platform selected and the deployment region. The actual price is based on the price displayed on the deployment page.
:::

### Billing Method

For Dedicated Plan deployments, charges are calculated every hour based on usage for the previous hour, and charged from your account balance. The hourly charges are then accumulated into monthly charges, which you can view in detail on the [Billing Overview](https://cloud.emqx.com/console/billing/overview) page.

### Pricing of suspended depoyment
**Dedicated deployment in hourly billing** will incur data retention fees at the following rates when suspended: **$0.06 / hour**

## BYOC Plan

EMQX BYOC will deploy the EMQX service in your cloud platform account, and the associated costs include cloud platform resource fees and EMQX BYOC license fees.

### Cost Components

| **Item**                 | **Description**                                                                                                                          |
|-------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| Cloud Platform Resources | When EMQX BYOC is deployed and running, it utilizes virtual machines, networks, and other resources under your cloud platform account. You will be billed by the cloud platform provider for the usage of these resources. |
| EMQX BYOC License  | To use the EMQX BYOC service, you need to subscribe and obtain an official EMQX BYOC license from EMQ. For details on license pricing, please [contact us](https://www.emqx.com/contact?product=cloud). |