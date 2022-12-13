keywords:: [[Commit]], [[rollback]], sequential statements
summary:: Sequential statements that succeed or fail as one. Can [[commit]] or [[rollback]].

A group of sequential [[SQL]] statements such as INSERT, SELECT that is performed as a single job.
The changes made by this job can be committed or rolled-back. 
If any one of the statements in the job fails, the transaction fails and no changes are made.