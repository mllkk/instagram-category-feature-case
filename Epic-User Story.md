# Epic: Instagram Category Management 

This epic introduces a category management system for professional accounts on Instagram-like platform. It enables account owners to organize their posts through category creation, assignment, ordering, visibility control, and constraints such as max post limits. The goal is to improve content structure, discoverability, and management efficiency for business and influencer profiles.

## User Stories
### U.S.-1 As an account owner, I want to create a new category so that I can organize my products.

#### Description
The user can create a new category by entering a category name via the “Add Category” action.
  
#### Business Rules / Functional Details
- Category name is required
- Category name must be unique
- Newly created category should be immediately visible in the category list
- Only authorized account owners can create categories

#### Acceptance Criteria 
##### AC 1 – Successful creation
- **Given** the user is on category management screen
- **When** the user enters a valid category name and clicks “Save”
- **Then** the category is created and showed in the category list immediately
##### AC 2 – Empty name validation
- **Given** the user tries to create a category
- **When** the category name is empty
- **Then** an error message “Category name cannot be empty” is displayed
##### AC 3 – Duplicate category
- **Given** a category with the same name already exists
- **When** the user tries to create a new category with that name
- **Then** the system prevents creation and shows an appropriate error message
##### AC 4 – Unauthorized access
- **Given** the user is not authorized
- **When** they attempt to create a category
- **Then** the system returns an authorization error and informs the user

### U.S.-2 As an account owner, I want to assign a product to a category so that each product is placed under the correct category. 

#### Description 
The user can assign a product to a single category from the product list.

#### Business Rules / Functional Details
- A product can belong to **only one category at a time**
- If a product is already assigned to a category, assigning it to a new category **replaces the previous assignment**
- The category’s product list should reflect the change immediately
- The user can cancel the action without applying changes

##### Technical Notes: System should ensure one-to-one mapping between product and category

#### Acceptance Criteria
##### AC 1 – Successful assignment
- **Given** the user selects a product
- **When** the user assigns it to a category
- **Then** the product is added to that category
- **And** the category product list is updated accordingly
##### AC 2 – Reassignment (overwrite behavior)
- **Given** the product is already assigned to a category
- **When** the user assigns it to a different category
- **Then** the previous category assignment is removed
- **And** the product is assigned to the new category
##### AC 3 – Cancel action
- **Given** the user starts assigning a product to a category
- **When** the user cancels the action
- **Then** no changes are applied

### U.S.-3 As an account owner, I want to be notified when I reach the maximum number of products in a category so that I can manage my content effectively.

#### Description
Each category has a maximum product limit (50 products). The system prevents adding more products once the limit is reached.

#### Business Rules
- Maximum product limit per category = 50
- System must prevent adding products beyond the limit
- User must be informed when the limit is reached

#### Acceptance Criteria
##### AC 1 – Successful addition under limit
- **Given** the category has less than 50 products
- **When** the user adds a new product
- **Then** the product is successfully added
##### AC 2 – Limit reached scenario
- **Given** the category already has 50 products
- **When** the user tries to add another product
- **Then** the system prevents the action
- **And** the user sees a message: “This category can contain a maximum of 50 products”
