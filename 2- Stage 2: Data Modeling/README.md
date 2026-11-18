# Stage 2 - Data Modeling

In Stage 1, 22 raw tables were transformed into 6 dimension tables, 6 fact tables and a security table. This stage connects those tables into a **galaxy schema** in Power BI and secures the data with **row-level security (RLS)**.

---

## Schema: before and after

**Before:** the tables after transformation, not yet connected.

![Schema before modeling](images/schema-before.png)

**After:** the finished galaxy schema, with several fact tables sharing dimensions.

![Schema after modeling](images/schema-after.png)

---

## Relationships and cardinality

Each fact table is connected to the dimensions it is analysed by. The relationship view below shows every connection and its cardinality.

![Model relationships and cardinality](images/relationships.png)

A galaxy schema has more than one fact table, and those fact tables share dimensions. This lets each business process (sales, targets, campaign spend, promotion coverage, inventory and order process) keep its own level of detail while being analysed by the same dimensions.

---

## Row-level security

Row-level security makes sure each user only sees the rows they are allowed to see. It is built from the `security` table (created from `user_details` in Stage 1) and applied to the customer data.

![Security roles](images/rls-roles.png)

**How it works:** each user is mapped to the data they can access, and a DAX filter on the customer data restricts every visual and total on the report to those rows only.

![Security in action](images/rls-test.png)

---

## What's next

With the model connected and secured, Stage 3 covers the analysis: DAX measures, the dashboard, findings and limitations.
