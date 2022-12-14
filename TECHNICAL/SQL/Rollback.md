article_type:: [[SQL]]
summary:: Control transactions before they are commited. After commiting, rollback is useless.
keywords:: Transactions, Commit, [[Transaction Control Language]]

[[Rollback]] statements provides control over transactions. A rollback statement undoes a current transaction, cancelling its changes. Once changes are commited, a rollback does nothing.

[[Data Definition Language]] such as DROP or ALTER cannot be rolledback, by definition.
[[Data Manipuation Language]] such as INSERT, DELETE can be rolled back, before its commited

Rollback is part of [[Transaction Control Language]]
