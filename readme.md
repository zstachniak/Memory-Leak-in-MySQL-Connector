# Memory Leak in MySQL Connector
### Version 8.0.11
### Submitted to Oracle as Bug #93711
The "prepare_for_mysql" function in connection_cext.py builds a strong-reffed list or dict. These references are never deleted, creating a memory leak that persists even after closing and deleting the connection. In situations where large amounts of data need to be inserted in an iterative process, the memory leak can quickly fill the entire available RAM leading to system crash.
See the Jupyter Notebook in this repository for an example of the memory leak.
