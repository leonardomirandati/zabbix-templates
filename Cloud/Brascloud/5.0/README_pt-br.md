# Template Zabbix para monitoramento de faturas Brascloud

![alt text](https://www.brascloud.com.br/assets/dist/site/images/logo.png)



## Visão geral

- **Você precisa configurar as macros para utilizar o template.**
- Monitore as faturas da sua conta Brascloud:
 - Obtenha o valor e status da fatura e atual e a anterior;

## Macros usadas

| Nome | Descrição | Valor Padrão | Tipo |
| ------ | ------ | ------ | ------ |
| {$BRASCLOUD_ACCESS_KEY} | Sua chave API | api-key | Text |
| {$BRASCLOUD_ACCOUNT} | Seu e-mail da conta | conta-email | Text |
| {$BRASCLOUD_SECRET_KEY} | Sua chave secreta de API | secret-key | Text |
| {$BRASCLOUD_URL_INVOICE} | Não modificar | https://portal.brascloud.com.br/restapi/invoice/listByClient | Text |

## Template links
Não possui.
## Regras de descoberta
Não possui.

## Itens coletados
| Nome | Descrição | Tipo | Chave ou informação adicional |
| ------ | ------ | ------ | ------ |
| Brascloud Invoice Monitoring API | Master Item - Origin Request | HTTP Agent | id.[{$BRASCLOUD_ACCOUNT}] |
| currentCost | Invoice Current Cost (R$) | Dependent item | currentCost |
| pastCost | Invoice Past Cost (R$) | Dependent item | pastCost |
| statusCurrent | Invoice Current Status (DRAFT)| Dependent item | statusCurrent |
| statusPast | Invoice Past Status (PAID/DUE/OVER_DUE) | Dependent item | statusPast |

## Triggers
| Nome | Descrição | Espressão | Severidade |
| ------ | ------ | ------ | ------ |
| {$BRASCLOUD_ACCOUNT} is overdue invoice | - | **Expression:**  {Template Brascloud Invoice:statusPast.str(OVER_DUE)}=1 **Recovery Expression:** {Template Brascloud Invoice:statusPast.str(OVER_DUE)}=0 | High |

Support/Contact/Suggestions: Leonardo Miranda (leonardomiranda.ti@outlook.com)
