# Template Zabbix for Brascloud Invoice

![alt text](https://www.brascloud.com.br/assets/dist/site/images/logo.png)



## Overview

- **You need to set the macros according to your account.**
- Shows different operating values of your Brascloud account:
 - Current and previous month invoice status and cost;

## Macros used

| Name | Description | Default | Type |
| ------ | ------ | ------ | ------ |
| {$BRASCLOUD_ACCESS_KEY} | Your API key | api-key | Text |
| {$BRASCLOUD_ACCOUNT} | Your e-mail account | conta-email | Text |
| {$BRASCLOUD_SECRET_KEY} | Your API secret key | secret-key | Text |
| {$BRASCLOUD_URL_INVOICE} | Do not modify | https://portal.brascloud.com.br/restapi/invoice/listByClient | Text |

## Template links
There are no template links in this template.
## Discovery rules
There are no discovery rules in this template.

## Items collected
| Name | Description | Type | Key and additional info |
| ------ | ------ | ------ | ------ |
| Brascloud Invoice Monitoring API | Master Item - Origin Request | HTTP Agent | id.[{$BRASCLOUD_ACCOUNT}] |
| currentCost | Invoice Current Cost (R$) | Dependent item | currentCost |
| pastCost | Invoice Past Cost (R$) | Dependent item | pastCost |
| statusCurrent | Invoice Current Status (DRAFT)| Dependent item | statusCurrent |
| statusPast | Invoice Past Status (PAID/DUE/OVER_DUE) | Dependent item | statusPast |

## Triggers
| Name | Description | Expression | Severity |
| ------ | ------ | ------ | ------ |
| {$BRASCLOUD_ACCOUNT} is overdue invoice | - | **Expression:**  {Template Brascloud Invoice:statusPast.str(OVER_DUE)}=1 **Recovery Expression:** {Template Brascloud Invoice:statusPast.str(OVER_DUE)}=0 | High |

Support/Contact/Suggestions: Leonardo Miranda (leonardomiranda.ti@outlook.com)
