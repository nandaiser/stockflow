# StockFlow — Business Rules

## 1. Product Management

- Every product belongs to a business.
- Each product has a name, SKU, current stock quantity, and active status.
- A product's SKU must be unique within its business.
- Product records can be created, viewed, and updated by users with the appropriate permissions.
- Products cannot have negative stock quantities.
- Inactive products are excluded from normal product lists and stock monitoring views.

## 2. Product Deactivation and Deletion

- Deleting a product through the application deactivates it instead of immediately removing it from the database.
- Deactivation sets the product's `is_active` status to `false`.
- Inactive products cannot be used for new stock movements.
- Existing stock movement history must remain accessible to authorized users.
- A product may be reactivated by a user with the appropriate permissions, provided it has not been permanently deleted.
- Permanent deletion after 30 days is a planned enhancement, not part of the initial release.
- Before permanent deletion is implemented, the system must ensure that historical inventory records and related data are not unintentionally lost.

## 3. Stock Management

- Stock can be increased through a stock-in transaction.
- Stock can be decreased through a stock-out transaction.
- Stock can be corrected through a stock-adjustment transaction.
- Every stock movement must record the affected product, movement type, quantity, date and time, responsible user, and reason.
- Stock-out transactions cannot reduce available stock below zero.
- Stock adjustments must not result in negative stock.
- Stock changes and their corresponding movement-history records must succeed or fail together.
- Users must not be able to change stock quantities by bypassing the authorized inventory operations.

## 4. Stock Visibility

- The system displays each product's current stock quantity.
- The dashboard identifies products that meet their configured low-stock threshold.
- Stock information is refreshed when the user refreshes the page or reloads the relevant view.
- The initial release does not require automatic live updates when another user changes stock.
- The displayed quantity must reflect the latest successfully committed stock changes after the data is reloaded.

## 5. Stock Movement History

- Authorized users can view the history of stock movements.
- Each movement must be associated with the correct product and responsible user.
- Historical movements must not be silently altered or removed through ordinary product-management operations.
- Deactivating a product must not erase its historical movements.
- Movement history should provide enough information to understand why and when stock changed.

## 6. User Roles and Permissions

StockFlow initially supports three roles:

### Admin
- Manage product records.
- Perform stock-in, stock-out, and stock-adjustment operations.
- Manage user access and roles.
- View inventory and stock movement history.
- Export permitted inventory data.

### Staff
- View inventory.
- Create and update product records where permitted.
- Record stock movements.
- View stock movement history.
- Export permitted inventory data.

### Viewer
- View inventory and stock movement history.
- Cannot modify products, change stock, or manage users.
- May export data if the business grants that permission.

- Every protected action must be authorized by the backend.
- Users cannot access or modify another business's data unless explicitly authorized.
- Hiding a button in the interface is not sufficient to enforce a permission.

## 7. Data Export

- Users with export permission can export the product list and current stock quantities as a CSV file.
- The export must respect the user's business access and applicable filters.
- Exported quantities should reflect the latest committed data available when the export is generated.

## 8. Data Integrity and Reliability

- Stock quantities must remain accurate when multiple users perform transactions concurrently.
- Failed stock transactions must not leave partial changes in the database.
- Duplicate product SKUs within the same business must be rejected.
- Invalid quantities and unsupported movement types must be rejected.
- Unauthorized requests must not modify inventory data.
