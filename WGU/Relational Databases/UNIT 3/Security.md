
## CREATE USER/ROLE

CREATE ROLE myaccount LOGIN PASSWORD 'mypassword';

Creates a login role (or user) named myaccount with the designated password

CREATE ROLE options
```
CREATE ROLE <rolename> 
<WITH> 
[SUPERUSER] - Adds superuser priv
[CREATEDB] - Adds ability to create a db
[CREATEROLE] - Allows creation/modification of roles
[INHERIT] - Inherit all privs of roles you belong to
[LOGIN] 
[CONNECTION LIMIT] 
[IN ROLE];
```

GRANT allows roles to be granted to a user
```
GRANT adminrole TO myadmin;
```

REVOKE removes roles from user
```
REVOKE adminrole_db FROM myadmin;
```

Let us say we have a group role called employee_role. We may want to allow the querying of the employee table, but not allow any changes to the data. As such, we would run the following:

```

GRANT SELECT ON employee TO employee_role;
```

We could also grant the employee_role edit access and query access on the customer table:

```

GRANT SELECT, INSERT, UPDATE, DELETE ON customer TO employee_role;
```

As another example, for an admin_role, you could grant all privileges to the customer table:

```

GRANT ALL ON customer TO admin_role;
```

If we wanted to grant access to specific columns, we would add those columns in round brackets after the privilege type. For example, if we wanted to grant UPDATE privileges to the employee_role on the track table, but only on the unit_price, we would do the following:

```

GRANT UPDATE(unit_price) ON track TO employee_role;
```

This grants only the ability to update the price, but none of the other columns.