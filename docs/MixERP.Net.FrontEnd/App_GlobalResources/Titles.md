# Titles.resx Documentation

## Overview

`Titles.resx` is a resource file that contains localized string values used throughout the MixERP.Net.FrontEnd application. This file is part of the App_GlobalResources directory and stores user interface text elements like button labels, titles, and other textual content that appear in the application interface. The resource file follows the Microsoft ResX Schema format and allows for localization of the application by storing text values that can be retrieved programmatically.

## Resource File Documentation

### Structure

The file is structured as an XML document following the Microsoft ResX Schema Version 2.0 format. It includes:

1. **Header Information**: Standard ResX file metadata
2. **Resource Items**: Collection of data elements each containing:
   - `name`: Identifier used to access the resource
   - `value`: The actual text value
   - Optional `comment`: Additional information about the resource
   - Optional type information for non-string resources

### Resource Usage

Resources in this file are typically accessed through the auto-generated `Titles` class, which is defined in the associated [Titles.Designer.cs](Titles.Designer.cs) file. The application code can retrieve these values using syntax like `Titles.ResourceName` where ResourceName is the name attribute of the data element.

## Key Resource Categories

The resources in this file can be grouped into several functional categories:

### General UI Elements
- `Add`: "Add"
- `AddNew`: "Add New"
- `Cancel`: "Cancel"
- `Clear`: "Clear"
- `DeleteSelected`: "Delete Selected"
- `EditSelected`: "Edit Selected"
- `Go`: "Go"
- `GoToTop`: "Go To Top"
- `Load`: "Load"
- `OK`: "OK"
- `Print`: "Print"
- `Reset`: "Reset"
- `Run`: "Run"
- `Save`: "Save"
- `Save1`: "Save"
- `Search`: "Search"
- `Select`: "Select"
- `ShowAll`: "Show All"
- `ShowCompact`: "Show Compact"
- `Update`: "Update"

### Account and Finance Related
- `Account`: "Account"
- `AccountCode`: "Account Code"
- `BankAccounts`: "Bank Accounts"
- `ChartOfAccounts`: "Chart of Accounts"
- `Credit`: "Credit"
- `CreditTotal`: "Credit Total"
- `Debit`: "Debit"
- `DebitTotal`: "Debit Total"
- `GLAdvice`: "GL Advice"
- `GLDetails`: "GL Details"
- `TransactionDate`: "Transaction Date"
- `TransactionDetails`: "Transaction Details"

### Sales and Purchase Related
- `CustomerCode`: "Customer Code"
- `CustomerName`: "Customer Name"
- `CustomerPanNumber`: "Customer PAN Number"
- `DeliveryWithoutSalesOrder`: "Delivery Without Sales Order"
- `DirectSales`: "Direct Sales"
- `DirectPurchase`: "Direct Purchase"
- `InvoiceAmount`: "Invoice Amount"
- `InvoiceDetails`: "Invoice Details"
- `PurchaseInvoice`: "Purchase Invoice"
- `PurchaseOrder`: "Purchase Order"
- `PurchaseType`: "Purchase Type"
- `SalesInvoice`: "Sales Invoice"
- `SalesOrder`: "Sales Order"
- `SalesQuotation`: "Sales Quotation"
- `SalesType`: "Sales Type"
- `SalesPerson`: "Sales Person"
- `SupplierName`: "Supplier Name"

### Items and Inventory
- `Brands`: "Brands"
- `CompoundUnitsOfMeasure`: "Compound Units of Measure"
- `ItemCostPrices`: "Item Cost Prices"
- `ItemGroups`: "Item Groups"
- `ItemName`: "Item Name"
- `Items`: "Items"
- `ItemSellingPrices`: "Item Selling Prices"
- `QuantityAbbreviated`: "Qty"
- `UnitsOfMeasure`: "Units of Measure"

### Shipping Related
- `DeliverTo`: "Deliver To"
- `SalesDelivery`: "Sales Delivery"
- `SalesDeliveryNote`: "Sales Delivery Note"
- `Shipper`: "Shipper"
- `Shippers`: "Shippers"
- `ShippingAddress`: "Shipping Address"
- `ShippingAddressMaintenance`: "Shipping Address Maintenance"
- `ShippingCharge`: "Shipping Charge"
- `ShippingCompany`: "Shipping Company"

### Authentication and User Management
- `Password`: "Password"
- `RememberMe`: "Remember Me"
- `SelectYourBranch`: "Select Your Branch"
- `SignIn`: "Sign In"
- `String1`: "Sign In"
- `String2`: "Remember Me"
- `User`: "User"
- `UserId`: "User Id"

### Setup and Configuration
- `AgeingSlabSetup`: "Ageing Slab Setup"
- `AgentBonusSlabAssignment`: "Agent Bonus Slab Assignment"
- `AgentBonusSlabs`: "Agent Bonus Slabs"
- `AgentSetup`: "Agent Setup"
- `AutoVerificationPolicy`: "Auto Verification Policy"
- `CashRepositories`: "Cash Repositories"
- `CostCenters`: "Cost Centers"
- `Counters`: "Counters"
- `Currencies`: "Currencies"
- `DatabaseStatistics`: "Database Statistics"
- `Departments`: "Departments"
- `FlagSelection`: "Flag Selection"
- `Flags`: "Flags"
- `Frequencies`: "Frequencies"
- `OfficeSetup`: "Office Setup"
- `PartyMaintenance`: "Party Maintenance"
- `PartyTypes`: "Party Types"
- `RoleMaintenance`: "Role Maintenance"
- `Stores`: "Stores"
- `StoreTypes`: "Store Types"
- `TaxSetup`: "Tax Setup"
- `TaxTypes`: "Tax Types"
- `VoucherVerificationPolicy`: "Voucher Verification Policy"

### Transaction Related
- `Book`: "Book"
- `Checklists`: "Checklists"
- `DueDate`: "Due Date"
- `EnteredBy`: "Entered By"
- `JournalVoucherEntry`: "Journal Voucher Entry"
- `PostTransaction`: "Post Transaction"
- `PrintGLEntry`: "Print GL Entry"
- `ReferenceNumber`: "Reference Number"
- `ReferenceNumberAbbreviated`: "Ref#"
- `StatementReference`: "Statement Reference"
- `TransactionPostedSuccessfully`: "Transaction Posted Successfully"
- `TransactionStatus`: "Transaction Status"
- `VerificationReason`: "Verification Reason"
- `VerifiedBy`: "Verified By"
- `WithdrawThisTransaction`: "Withdraw This Transaction"
- `WithdrawTransaction`: "Withdraw Transaction"
- `WithdrawalReason`: "Withdrawal Reason"

### Totals and Calculations
- `Amount`: "Amount"
- `Discount`: "Discount"
- `GrandTotal`: "Grand Total"
- `Price`: "Price"
- `PriceType`: "Price Type"
- `Rate": "Rate"
- `RunningTotal`: "Running Total"
- `SubTotal`: "Sub Total"
- `Tax`: "Tax"
- `TaxTotal`: "Tax Total"
- `Total`: "Total"
- `Totals`: "Totals"

## Usage in Application

This resource file is used throughout the MixERP.Net application to provide localized text for:

1. **User Interface Elements**: Labels, buttons, and headings displayed in ASPX pages and master pages like [MixERPMaster.Master](MixERPMaster.Master) and its code-behind files.

2. **Reports and Printable Documents**: Text elements used in reports and printable documents, such as those in the [Reports](Reports/ReportViewer.aspx) section.

3. **Forms and Data Entry Screens**: Labels and captions for form fields in various modules like Sales, Purchase, Finance, etc.

4. **Error Messages and Notifications**: Text displayed to users for errors, warnings, or informational messages.

The resource-based approach allows for easier localization of the application to different languages by creating additional resource files with the same keys but translated values.

## Dependencies

This file is directly related to:

- [Titles.Designer.cs](Titles.Designer.cs): The auto-generated code file that provides strongly-typed access to these resources
- [Labels.resx](Labels.resx): Contains additional UI text resources
- [FormResource.resx](FormResource.resx): Contains form-specific text resources
- [Warnings.resx](Warnings.resx): Contains warning message resources

## Application Integration

Various pages in the application use these resources for display text. Some examples include:

- [SignIn.aspx](SignIn.aspx): Uses authentication-related resources
- [Finance/JournalVoucher.aspx](Finance/JournalVoucher.aspx): Uses transaction and GL-related resources
- [Sales/DirectSales.aspx](Sales/DirectSales.aspx): Uses sales and invoice-related resources
- [Purchase/DirectPurchase.aspx](Purchase/DirectPurchase.aspx): Uses purchase-related resources
- [Setup/Index.aspx](Setup/Index.aspx): Uses setup and configuration-related resources