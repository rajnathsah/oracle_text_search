# Oracle Text Search

Oracle Text provides indexing, word and theme searching, and viewing capabilities for text in query applications and document classification applications.

## Getting started with Oracle text search setup

1. Create a user with CTXAPP role or assign CTXAPP role to existing user.
SQL statement to create user.
```sql
CREATE USER textsearchuser identified by textsearchpassword;
```
SQL statement to grant roles
```SQL
GRANT RESOURCE, CONNECT, CTXAPP TO textsearchuser;
```
2. Grant execute priviledge on the CTX PL/SQL package. Oracle text has many packages which helps in searching, indexing and synchronizing text index. Using below script all such grants can be given to user.
```sql
GRANT EXECUTE ON CTXSYS.CTX_CLS TO textsearchuser;
GRANT EXECUTE ON CTXSYS.CTX_DDL TO textsearchuser;
GRANT EXECUTE ON CTXSYS.CTX_DOC TO textsearchuser;
GRANT EXECUTE ON CTXSYS.CTX_OUTPUT TO textsearchuser;
GRANT EXECUTE ON CTXSYS.CTX_QUERY TO textsearchuser;
GRANT EXECUTE ON CTXSYS.CTX_REPORT TO textsearchuser;
GRANT EXECUTE ON CTXSYS.CTX_THES TO textsearchuser;
GRANT EXECUTE ON CTXSYS.CTX_ULEXER TO textsearchuser;
```

Let us start with example of Oracle text.
