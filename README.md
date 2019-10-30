# Oracle Text Search

Oracle Text provides indexing, word and theme searching, and viewing capabilities for text in query applications and document classification applications.

### Getting started with Oracle text search setup

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

### Let us start with example of Oracle text

1. Create table for the example.
```sql
CREATE TABLE docs (id NUMBER PRIMARY KEY, text VARCHAR2(200));
```
2. Load data in table
```sql
INSERT INTO docs VALUES(1, '<HTML>California is a state in the US.</HTML>');
INSERT INTO docs VALUES(2, '<HTML>Paris is a city in France.</HTML>');
INSERT INTO docs VALUES(3, '<HTML>France is in Europe.</HTML>');
```
3. Create index on column to used for searching data.
```sql
CREATE INDEX idx_docs ON docs(text)
     INDEXTYPE IS CTXSYS.CONTEXT PARAMETERS
     ('FILTER CTXSYS.NULL_FILTER SECTION GROUP CTXSYS.HTML_SECTION_GROUP');
```
3. Run search query
```sql
SELECT SCORE(1), id, text FROM docs WHERE CONTAINS(text, 'France', 1) > 0;
```
![Query output](https://github.com/rajnathsah/oracle_text_search/blob/master/images/run1.png)
