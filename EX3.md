# EX 3 SubQueries, Views and Joins 
## DATE:18/8/25

## Create employee Table
```sql
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
## Insert the values
```sql
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```

## Create department table
```sql
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
## Insert the values in the department table
```sql
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.


### QUERY:

```
CREATE VIEW details AS SELECT ENAME FROM EMP WHERE SAL >(select SAL from EMP where EMPNO=7566);
```
### OUTPUT:
![image](https://github.com/RANJEETH17/EX-3-SubQueries-Views-and-Joins/assets/120718823/8e5a1363-52e5-4238-a05d-2e95bfd17cb5)


### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
 ```
CREATE VIEW minimum AS select ENAME,JOB,SAL from EMP where SAL =(select MIN(SAL) from EMP);
```

### OUTPUT:
![image](https://github.com/RANJEETH17/EX-3-SubQueries-Views-and-Joins/assets/120718823/ef8640ac-19ab-460f-a468-4e5f5f3261e4)


### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
```
select ENAME,JOB from EMP where  DEPTNO=10 AND JOB='SALESMAN';
```
### OUTPUT:
![image](https://github.com/RANJEETH17/EX-3-SubQueries-Views-and-Joins/assets/120718823/cde53428-fc9c-4f92-a602-2d547e4b0ad9)




### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
```
create view empv5 as select EMPNO,ENAME,JOB from EMP where DEPTNO=10;
```

### OUTPUT:
![image](https://github.com/RANJEETH17/EX-3-SubQueries-Views-and-Joins/assets/120718823/3c2fb0d4-3c90-4a15-a066-c3dabce0d1bf)


### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
```
create view empv30 AS select EMPNO,ENAME,SAL from EMP where DEPTNO=30;
```

### OUTPUT:
![image](https://github.com/RANJEETH17/EX-3-SubQueries-Views-and-Joins/assets/120718823/63489d0d-5b9e-43c6-bedf-d04e82c7de42)



### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
```
update EMP set SAL=SAL*1.1 WHERE JOB='clerk';

create view empv8 as select EMPNO,ENAME,SAL,JOB from EMP;
```
### OUTPUT:
![image](https://github.com/RANJEETH17/EX-3-SubQueries-Views-and-Joins/assets/120718823/0cc9cfd9-4f7f-4c54-9577-3d9e08fa3237)


## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
```
SELECT salesman1.name AS "Salesman", customer1.cust_name AS "Customer Name", salesman1.city AS "City" from salesman1 INNER JOIN customer1 ON salesman1.city=customer1.city;
```


### OUTPUT:
![image](https://github.com/RANJEETH17/EX-3-SubQueries-Views-and-Joins/assets/120718823/07c30f83-cde4-459c-8188-79f5a485cc78)


### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.


### QUERY:
```
SELECT customer1.cust_name AS "Customer Name",customer1.city AS "Customer City",salesman1.name AS "Salesman",salesman1.commission AS "Commission" FROM salesman1 INNER JOIN customer1 ON salesman1.salesman_id=customer1.salesman_id WHERE salesman1.commission>0.13;
```

### OUTPUT:
![image](https://github.com/RANJEETH17/EX-3-SubQueries-Views-and-Joins/assets/120718823/a9a4a726-65b3-42f6-8153-0978cf2eb660)




### Q9) Perform Natural join on both tables

### QUERY:
```
SELECT customer1.cust_name AS "Customer Name",customer1.city AS "Customer City",salesman1.name AS "Salesman",salesman1.commission AS "Commission" FROM salesman1 INNER JOIN customer1 ON salesman1.salesman_id=customer1.salesman_id WHERE salesman1.commission>0.13;
```

### OUTPUT:
![image](https://github.com/RANJEETH17/EX-3-SubQueries-Views-and-Joins/assets/120718823/465f8f92-bd46-4c86-9e3a-f5877f4c04c9)


### Q10) Perform Left and right join on both tables

### QUERY FOR LEFT JOIN:

```
SELECT customer1.cust_name AS "Customer Name",customer1.city AS "Customer City",salesman1.name AS "Salesman",salesman1.commissioSELECT customer1.cust_name AS "Customer Name",customer1.city AS "Customer City",salesman1.name AS "Salesman",salesman1.commission AS "Commission" FROM salesman1 INNER JOIN customer1 ON salesman1.salesman_id=customer1.salesman_id WHERE salesman1.commission>0.13;
```
```
select * from customer1 natural join salesman1;
```
### OUTPUT FOR LEFT JOIN:
![image](https://github.com/RANJEETH17/EX-3-SubQueries-Views-and-Joins/assets/120718823/fa62819f-5537-460d-92aa-e3e0cc27664a)

### QUERY FOR RIGHT JOIN:
 ```
SELECT * FROM salesman1 RIGHT JOIN customer1 ON salesman1.salesman_id=customer1.salesman_id;
```
### OUTPUT FOR RIGHT JOIN:
![image](https://github.com/RANJEETH17/EX-3-SubQueries-Views-and-Joins/assets/120718823/6cd56a04-8134-4a91-9466-4b5f446f3672)

### RESULT;
 Queries Executed Successfully
