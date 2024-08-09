## ERD

```mermaid
erDiagram
  departments {
    char(4) dept_no PK
    varchar(40) dept_name
    int emp_count
  }

  dept_emp {
    char(4) dept_no PK, FK
    int emp_no PK, FK
    date from_date
    date to_date
  }

  dept_manager {
    char(4) dept_no PK, FK
    int emp_no PK, FK
    date from_date
    date to_date
  }

  employees {
    int emp_no PK
    date birth_date
    varchar(14) first_name
    varchar(16) last_name
    enum gender
    date hire_date
  }

  titles {
    int emp_no PK, FK
    date from_date PK
    varchar(50) title PK
    date to_date
  }

  salaries {
    int emp_no PK, FK
    date from_date PK
    int salary
    date to_date
  }

  departments || --o{ dept_emp : ""
  departments || --o{ dept_manager : ""
  employees || --o{ dept_emp : ""
  employees || --o{ dept_manager : ""
  employees || --o{ titles : ""
  employees || --o{ salaries : ""
```
