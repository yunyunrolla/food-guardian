# Food Inventory Model

## Purpose

The food inventory model represents food that a person might have in their fridge, pantry, or freezer.

---

## Model

| Field | Type | Required | Description |
|------|------|----------|-------------|
| id | UUID | Yes | Unique inventory item |
| user_id | UUID | Yes | Owner |
| food_reference_id | String | Yes | External food identifier |
| quantity | Decimal | Yes | Amount currently owned |
| unit | Enum | Yes | g, ml, package, piece |
| expiration_date | Date | No | Expiration date if known |
| storage_location | Enum | Yes | Pantry, Fridge, Freezer |
| notes | String | No | User notes |

---

# Relationships

1 User -> Many Food Inventory -> 1 Food Reference per Food Inventory

--- 

## Design Decisions

### Why did I separate Food Inventory and Food?

I didnt want to have to define all the food calories and make a dataset, and instead I wanted to use open source data.

The nutritional value of food is not dependent on the user inventory, and you can have multiple exp dates for the same food, depending on when you bought the food.

Ie)
- Food: Chicken Breast
- Quantity: 2 (100g servings)
- Storage: Freezer
- Expiration: 2026/08/30
