---
title: "File details: merchant-order-status.csv"
last_updated: Feb 26, 2021
description: This document describes the merchant_profile.csv file to configure merchant information in your Spryker shop.
template: import-file-template
---


This document describes the `merchant-order-status.csv` file to configure the update of the regular order status information in your Spryker shop.

To import the file, run:

```bash
order-oms:status-import merchant-order-status
```

## Import file parameters

The file should have the following parameters:

| PARAMETER | REQUIRED? | TYPE | DEFAULT VALUE | REQUIREMENTS OR COMMENTS | DESCRIPTION |
|-|-|-|-|-|-|
| merchant_reference |   | String |   | Unique | Identifier of the merchant in the system. |
| merchant_order_reference |   | String |   | Unique | Identifier of the merchant order in the system. |
| order_item_reference | &check; | String |   | Unique | Identifier of the  item in the order. |
| merchant_order_item_event_oms | &check; | String |   | OMS events depend on the  [merchant state machine](https://spryker-docs.herokuapp.com/docs/marketplace/user/features/202106.0/marketplace-and-merchant-state-machines/marketplace-and-merchant-state-machines-feature-overview.html#merchant-state-machine) configured. | Desired order-item state. Only this parameter is updated in the database. |

## Import file dependencies

The file has no dependencies.

## Additional Information

When the merchant order item status is updated by importing the .csv file, the corresponding events in a merchant state machine are triggered, and the state gets updated. As a merchant order may contain several order items, the .csv file can have several rows of items for the same order.
`Merchant_order_item_reference` can repeat and have different states in the file. For example, in one case, it is `packed` and then `shipped`. That allows you to update the item through different merchant state machine statuses (for instance, `packed` and `shipped`) and avoid errors. If the merchant order item doesn't follow the existing sequence (the statuses flow in the merchant state machine), the state won't be updated, and you will get an error in the uploading process' report.

## Import template file and content example

Find the template and an example of the `merchant-order-status.csv` file below:

| FILE | DESCRIPTION |
|-|-|
| [template_merchant-order-status.csv](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Marketplace+setup/template_merchant-order-status.csv) | Import file template with headers only. |
| [merchant-order-status.csv](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Marketplace+setup/merchant-order-status.csv) | Exemplary import file with Demo Shop data. |