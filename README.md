<div align="center">

# Quickeebooks

Ruby integration for QuickBooks Online and QuickBooks Windows/Desktop through the Intuit Data Services REST API v2.

</div>

## ⚠️ Status

Quickeebooks is abandoned and depends on Intuit’s QuickBooks Online v2 Data Services REST API.

Intuit announced that the v2 API would be discontinued on June 1, 2016. Because of that API shutdown, this library should not be expected to work for current QuickBooks Online integrations.

For new QuickBooks Online work, the original README points users toward the QBO v3 API and the `quickbooks-ruby` library.

## 📌 Overview

Quickeebooks is a Ruby library for working with Intuit QuickBooks data through the older Intuit Data Services REST API v2.

It was designed to support QuickBooks Online and QuickBooks Windows/Desktop resources using OAuth authentication, XML serialization, and service objects for common accounting entities such as customers, invoices, accounts, vendors, payments, items, bills, and related records.

The library exposes service classes for operations such as:

- Creating supported records
- Updating supported records
- Listing collections
- Fetching records by ID
- Deleting supported records
- Retrieving invoice PDFs for QuickBooks Online invoices

## 🧰 Technology

| Area | Details |
| --- | --- |
| Language | Ruby |
| API | Intuit QuickBooks Data Services REST API v2 |
| Authentication | OAuth |
| XML handling | ROXML, Nokogiri |
| Validation support | ActiveModel |
| Historical Ruby versions | Ruby REE, Ruby 1.9.2, Ruby 1.9.3 |

## 🔐 Authentication Flow

The original documentation describes an OAuth-based connection flow with Intuit.

A typical Rails-oriented flow included:

1. Creating an OAuth consumer with an Intuit app key and secret.
2. Sending users through Intuit’s “Connect to QuickBooks” authorization flow.
3. Receiving an OAuth callback with verifier information.
4. Storing the OAuth token, OAuth secret, and Realm ID.
5. Using those credentials to initialize Quickeebooks service clients.

The same concepts could be adapted outside Rails, but the original examples were Rails-focused.

## 🧾 Service Model

Quickeebooks uses service classes under namespaces such as:

- `Quickeebooks::Online::Service`
- `Quickeebooks::Windows::Service`
- `Quickeebooks::Shared::Service`

Service objects are configured with an OAuth access token and a Realm ID before making API calls.

Common service methods documented by the project include:

- `create(object)`
- `update(object)`
- `list`
- `fetch_by_id(object_id)`
- `delete(object)`

Support varies by entity and by QuickBooks Online versus QuickBooks Windows/Desktop.

## 🔎 Querying Data

The original README documents support for list operations with pagination, sorting, and filters.

The `list` method accepts arguments for:

- Filters
- Page number
- Results per page
- Sort options
- Additional options

Filtering support includes:

- Text filters
- Date/time filters
- Boolean filters
- Number filters

QuickBooks Online supported the documented filter types more broadly. QuickBooks Windows/Desktop had more limited filtering based on which fields Intuit allowed for each entity.

## 📚 Supported Resource Areas

The original documentation lists support for many QuickBooks resource types, including:

- Accounts
- Bills
- Bill payments
- Customers
- Employees
- Invoices
- Items
- Journal entries
- Jobs
- Payments
- Sales receipts
- Sales terms
- Time activities
- Tracking classes
- Vendors

QuickBooks Online and QuickBooks Windows/Desktop support differ. Some entities support full CRUD operations, while others only support listing, fetching, loading metadata, retrieving status, or no operation.

## 🧾 Invoice PDF Support

For QuickBooks Online invoices, the invoice service includes support for retrieving an invoice as a PDF document.

The documented method is:

`invoice_as_pdf(invoice_id, destination_file_name)`

The caller is responsible for managing the downloaded file after use.

## 📝 Logging

The original README documents a simple logging toggle:

`Quickeebooks.log = true`

## ⚖️ License

Quickeebooks is released under the MIT License.

Copyright © 2012.
