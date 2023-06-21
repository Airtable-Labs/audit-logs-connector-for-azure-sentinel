# Azure Sentinel Connector for Airtable Audit Logs

This repository contains an example Microsoft Sentinel codeless connector ([`Azure_Sentinel_Codeless_Connector.json`](./Azure_Sentinel_Codeless_Connector.json)) to help you continuously ingest [Airtable Audit Logs](https://airtable.com/developers/web/api/audit-logs-overview) into the [Microsoft Sentinel](https://azure.microsoft.com/en-us/products/microsoft-sentinel/) ecosystem without the needing to write code or host additional infrastructure.

---

The software made available from this repository is not supported by Formagrid Inc (Airtable) or part of the Airtable Service. It is made available on an "as is" basis and provided without express or implied warranties of any kind.

---

### Overview

Microsoft Sentinel has [several options for creating custom connectors](https://learn.microsoft.com/en-us/azure/sentinel/create-custom-connector). Codeless Connectors are described as "Best for less technical audiences to create SaaS connectors using a configuration file instead of advanced development." and have the benefit of not requiring any infrastructure: Microsoft Sentinel will use the configuration to poll the Audit Log API for you.

While codeless connectors do not have code, the configuration is in JSON format and requires some familiarity with HTTP-based APIs and pagination. You can [learn more about how Microsoft Sentinel codeless connectors work](https://learn.microsoft.com/en-us/azure/sentinel/create-codeless-connector) from the same documentation that was used to create the example in this repository.

### About this codeless connector

The codeless connector in this repository is configured to poll the [Airtable Audit Logs event retrieval endpoint](https://airtable.com/developers/web/api/audit-log-events) every 5 minutes and request up to 100 events per page. If there is another page of results available, the connector will automatically retrieve the next page of events.

It is strongly recommended you use a personal access token belonging to a [service account](https://support.airtable.com/docs/en/service-accounts-overview). The service account will need to be made an admin for your enterprise account and the personal access token will need to have the [`enterprise.auditLogs:read`](https://airtable.com/developers/web/api/scopes#enterprise-audit-logs-read) scope.

### Setup / deploy

[Microsoft documents the steps to deploy a connector in Microsoft Sentinel here](https://learn.microsoft.com/en-us/azure/sentinel/create-codeless-connector?tabs=deploy-via-arm-template%2Cconnect-via-the-azure-portal#deploy-your-connector-in-microsoft-sentinel-and-start-ingesting-data). [`Azure_Sentinel_Codeless_Connector.json`](./Azure_Sentinel_Codeless_Connector.json) is the example ARM template JSON file you can use for step 1a.
