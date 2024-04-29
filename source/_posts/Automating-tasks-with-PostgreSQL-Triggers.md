---
title: Automating tasks with PostgreSQL Triggers
date: 2024-04-29 20:00:24
tags: [PostgreSQL, Database, Triggers]
---

Triggers in PostgreSQL provide a powerful mechanism to automate tasks within the database. Let's explore how to use triggers to automate common tasks.

### 1. Automatically Copying User Data to Orders

```sql
CREATE OR REPLACE FUNCTION copy_user_data_to_order()
RETURNS TRIGGER AS $$
BEGIN
    -- Concatenate user data into a string
    SELECT u.firstname || ' ' || u.lastname || ', ' || u.email
    INTO NEW.user
    FROM users u
    WHERE u.id = NEW.user_id;

    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER insert_order_trigger
BEFORE INSERT OR UPDATE ON public.orders
FOR EACH ROW
EXECUTE FUNCTION copy_user_data_to_order();
```

Whenever a new order is inserted or updated in the `orders` table, this trigger function automatically fetches the corresponding user data and stores it as a concatenated string in the `user` column of the order.

### 2. Updating Timestamp on Record Modification

```sql
CREATE OR REPLACE FUNCTION public.update_timestamp()
 RETURNS trigger
 LANGUAGE plpgsql
AS $function$
BEGIN
    NEW.updated := NOW();
    RETURN NEW;
END;
$function$
```

This trigger function updates the `updated` timestamp column of a record with the current timestamp whenever the record is modified.

### 3. Using INSTEAD OF Trigger on a View

Want to update the underlying tables by View? Use the `INSTEAD OF` trigger

```sql
CREATE OR REPLACE FUNCTION update_order_user_view()
RETURNS TRIGGER AS $$
BEGIN
    -- Update the underlying tables as needed
    UPDATE orders
    SET paid = NEW.paid,
        register_success = NEW.register_success,
        enable = NEW.enable
    WHERE order_id = NEW.order_id;

    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER update_order_user_trigger
INSTEAD OF UPDATE ON order_user_view
FOR EACH ROW
EXECUTE FUNCTION update_order_user_view();
```

This INSTEAD OF trigger intercepts UPDATE operations on the `order_user_view` and updates the corresponding rows in the `orders` table based on the new values in the view.

Triggers in PostgreSQL allow for automation of repetitive tasks, enhancing the functionality and efficiency of your database.
