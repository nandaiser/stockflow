# StockFlow — Business Requirements

## 1. Project Overview

StockFlow is an inventory management application designed for small businesses to monitor product availability, manage inventory records, and control access to inventory operations.

The goal is to provide a centralized view of product stock, reduce errors caused by manual tracking, and make inventory information easier to maintain and review.

## 2. Target Users

StockFlow is intended for small business owners and employees who need to manage or monitor product inventory.

The system supports different user roles so that each person can access only the operations permitted by their responsibilities.

## 3. Functional Requirements

### 3.1 Product Management

Users with the appropriate permissions can:

- Add new products to the inventory.
- View the product list and individual product details.
- Update product information.
- Delete products when permitted and when deletion will not compromise inventory records.
- Search for and locate products easily.

Each product should have enough information to distinguish it from other products, including its name, SKU, and current stock quantity.

### 3.2 Stock Monitoring

Users can view the current stock quantity of each product.

The inventory view should help users identify products with low stock and understand which products are currently available.

Stock information should remain consistent whenever inventory changes are recorded. Users should not need to manually calculate the current quantity from a list of transactions.

### 3.3 Stock Movement Management

Authorized users can record inventory changes, including:

- **Stock in:** products received or added to inventory.
- **Stock out:** products sold, issued, or removed from inventory.
- **Stock adjustment:** corrections to inventory quantities when discrepancies are discovered.

Each movement must record the affected product, quantity, movement type, date, and responsible user. A reason or explanation should be recorded where applicable.

The system must maintain a history of stock movements so users can review how and why inventory quantities changed.

### 3.4 Data Export

Users with the appropriate permissions can export inventory information for reporting and record-keeping.

The initial version should support exporting the product list with current stock quantities in CSV format.

Exported information should reflect the selected data and filters displayed by the user.

### 3.5 Role-Based Access Control

StockFlow must support different user roles with distinct permissions.

The initial roles are:

- **Admin:** manages product records, inventory operations, and user access.
- **Staff:** manages products and records stock movements as permitted by the business.
- **Viewer:** views inventory information without making changes.

Users must not be able to perform operations outside their assigned permissions.

### 3.6 Dashboard

The dashboard should provide a quick overview of inventory, including:

- Total number of products.
- Products with low stock.
- Recent stock movements.
- Current stock quantities and availability.

The dashboard should help users identify inventory issues without reviewing every product individually.

## 4. Non-Functional Requirements

### 4.1 Data Accuracy

Inventory quantities must remain accurate when stock movements are recorded. Failed operations must not leave inventory information partially updated.

### 4.2 Security

Users must authenticate before accessing protected functionality. Inventory and business data must only be accessible to authorized users.

### 4.3 Usability

The interface should be straightforward to navigate, with clear feedback when an operation succeeds or fails.

### 4.4 Reliability

The application should handle invalid input and unexpected failures without corrupting inventory records.

### 4.5 Maintainability

The application should be organized so that future features can be added without unnecessarily complicating existing functionality.

## 5. Scope

### Included in the Initial Release

- User authentication.
- Role-based permissions.
- Product management.
- Stock-in, stock-out, and stock adjustments.
- Current stock monitoring.
- Stock movement history.
- Low-stock indicators.
- CSV export of inventory information.
- Dashboard summaries.
- Automated testing and public deployment.

### Excluded from the Initial Release

- Multiple warehouse management.
- Barcode scanning.
- Purchase orders and supplier management.
- Sales invoicing and payment processing.
- Automated email or messaging notifications.
- Native mobile applications.

## 6. Success Criteria

The initial release is considered successful when:

1. Authorized users can manage products and view current inventory.
2. Stock movements update inventory quantities accurately.
3. The system prevents stock-out operations that exceed available inventory.
4. Users can review the history of inventory changes.
5. Users cannot perform actions outside their assigned permissions.
6. Inventory data can be exported to CSV.
7. The application is accessible through a public deployment and can be used end to end.
