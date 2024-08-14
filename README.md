# Real MySQL 8.0 실습

<br/>

## 실습 결과

11. 쿼리 작성 및 최적화
    - [WHERE 절과 ORDER BY 절의 인덱스 이용](https://github.com/kimdev0206/realmysql80/wiki/WHERE-%EC%A0%88%EA%B3%BC-ORDER-BY-%EC%A0%88%EC%9D%98-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%9D%B4%EC%9A%A9)
    - [인덱스 여부에 따른 조인 순서](https://github.com/kimdev0206/realmysql80/wiki/%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%97%AC%EB%B6%80%EC%97%90-%EB%94%B0%EB%A5%B8-%EC%A1%B0%EC%9D%B8-%EC%88%9C%EC%84%9C)

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
