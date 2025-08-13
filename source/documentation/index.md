---
title: View Self Assessment Account Service Guide
weight: 1
---

# View Self Assessment Account API Service Guide

Version 1.0 issued 12 August 2025
***

This service guide explains how you can integrate your software with the [View Self Assessment Account API][SA_ACCOUNT_API].

## Overview

The View Self Assessment Account API provides third-party systems and developers with access to a structured, itemised breakdown of charges, payments, credits, and interest applied to a taxpayer’s Self Assessment account.

This service is read-only and is designed to support better transparency and reconciliation of Self Assessment accounts, helping reduce user confusion and contributing to the wider HMRC goal of preventing misallocated payments.

### Purpose
To give third-party software real-time and on-demand access to a taxpayer’s Self Assessment account breakdown so that individuals and agents can:

* Verify how payments have been applied
* Reconcile account activity with their own records
* Understand the amount owed and due dates before making a payment

> It is recommended this API is used in conjunction with [Initiate Payment API][SA_PAYMENTS_API] to increase the likelihood of payments being correctly allocated based on current account data.

### Key features

* Granular breakdown of Self Assessment transactions: charges, payments, credits, and interest
* Effective dates for accurate reconciliation
* Status indicators (e.g. due, cleared, overdue)
* Totals and running balances where applicable

### What this service does

* Exposes detailed Self Assessment account data via a secure API
* Supports integration into agent and accounting platforms
* Facilitates user understanding of payment application and account balance

### What this service does not do

* Accept, process, or allocate payments
* Modify or update account data
* File returns or calculate tax liabilities

### Intended users

* Third-party developers building tax/accounting software
* Agents and software providers integrating with HMRC systems on behalf of clients

This API plays a supporting role in HMRC’s efforts to improve payment accuracy and user understanding by equipping external systems with reliable Self Assessment account data.

## Getting started

Before your software can access Self Assessment account data using this API, the end user must be fully registered with HMRC and have the correct credentials. This applies to both individual taxpayers and agents.

### Access requirements for individuals

To access their own Self Assessment account data, individuals must:

1. [Register for Self Assessment](https://www.gov.uk/register-for-self-assessment) if they have not done so before
2. Receive a Unique Taxpayer Reference (UTR). This is issued by HMRC after registration
3. Create or sign in with a Government Gateway account. This account is used to authenticate using OAuth

### Access requirements for agents

To access Self Assessment account data on behalf of clients, agents must:

1. [Register as a professional tax agent](https://www.gov.uk/guidance/find-out-how-to-register-as-a-professional-tax-agent-with-hmrc)
2. [Set up an Agent Services Account (ASA)](https://www.gov.uk/guidance/register-with-hmrc-to-use-an-agent-services-account)
3. Link the ASA to client Self Assessment authorisations. This can be done using the digital handshake or invitation process
4. Use ASA Government Gateway credentials to authenticate with HMRC systems on behalf of clients

## End-to-end user journey

This section outlines the key integration steps your software must support when working with the View Self Assessment Account API.

The API removes the complexity of HMRC’s internal systems. As a third-party developer, you only interact with HMRC’s public interfaces.

This diagram shows the full user journey when your software connects to the View Self Assessment Account API. It covers key steps from user authentication to retrieving and displaying account data, through to supporting further actions.

<a href="images/user-journey.svg" target="blank"><img src="images/user-journey.svg" alt="User Journey Diagram"/></a>

### 1. Authenticate the user

Users authenticate using their Government Gateway account. This provides your software with an access token and information about the user’s identity and permissions.

### 2. Request Self Assessment data

Your software uses the access token to request Self Assessment account data.

### 3. Handle and present the response

The API responds with a structured breakdown of Self Assessment account information. This may include charges, payments, credits, and interest.

You should present this data clearly to the user, helping them understand their account activity and any amounts due.

### 4. Support follow-on actions

You can link this API with other HMRC APIs, for example, to support making a payment using the [Initiate Payment API][SA_PAYMENTS_API]. This helps ensure payments are made against the correct liabilities.

## Related API documentation

Refer to the main [View Self Assessment Account API documentation][SA_ACCOUNT_API] for endpoints, example requests, and schema definitions.

## Fraud prevention headers

You must include fraud prevention headers in all API requests. This is required before we can approve your application and issue production credentials.

HMRC will assess the fraud prevention headers submitted by your application and must be satisfied that they meet accuracy and compliance standards.

You can use the [Test Fraud Prevention Headers API](/api-documentation/docs/api/service/txm-fph-validator-api) to check whether the headers submitted by your application meet the latest requirements.

Refer to the full [Fraud Prevention Headers specification](/guides/fraud-prevention) for guidance on how to construct and implement these headers correctly.

## Changelog

### Version 1.0 – 12 August 2025
- Added user journey diagram to main page.
- Added *Test the API* page.
- Updated error scenarios to include **404** cases.
- Renamed *Glossary* page to *Terminology*.
- Reordered page structure for improved flow.

### Version 0.7 – 6 August 2025
- Added *Test the API* page.
- Updated error scenarios to include **404** cases.
- Renamed *Glossary* page to *Terminology*.
- Reordered page structure.

### Version 0.6 – 23 July 2025
- Added fraud prevention header guidance.
- Added end-to-end user journey.
- Removed *Agent Services* page.
- Reordered page structure.

### Version 0.5 – 22 July 2025
- Updated overview for clarity and consistency.
- Revised error responses for improved guidance.
- Removed glossary terms not relevant to third-party users.
- Refined terminology for accuracy.

### Version 0.4 – 21 July 2025
- Added error responses section for common failure scenarios.

### Version 0.3 – 16 July 2025
- Added *Agent Services* content for key user groups.

### Version 0.2 – 15 July 2025
- Expanded overview section.
- Added initial change log structure.

### Version 0.1 – 1 July 2025
- Initial draft of service guide.

[SA_ACCOUNT_API]: /api-documentation/docs/api/service/self-assessment-liability-api
[SA_PAYMENTS_API]: /api-documentation/docs/api/service/third-party-payments-external-api