

### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:
### Create employee table
![trigempt](https://github.com/JananiSoundararajan/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119477549/5c3ff644-3b87-46e3-9aed-535ccdf0a6d8)

### Create salary_log table
![trig log sal](https://github.com/JananiSoundararajan/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119477549/6bdbf06a-e7fa-4f46-ad12-de327c35d791)

### PLSQL Trigger code:
```
DEVELOPED BY:  BARATHRAJ.B
REG NO:212222230019
```
```
-- Create the trigger
CREATE OR REPLACE TRIGGER log_sal_update
BEFORE UPDATE ON employee
FOR EACH ROW
BEGIN
  IF :OLD.salary != :NEW.salary THEN
    INSERT INTO sal_log (empid, empname, old_salary, new_salary, update_date)
    VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
  END IF;
END;
/
-- Insert the values in the employee table
insert into employee values(1,'Aarthi','IT',1000000);
insert into employee values(2,'Pooja','SALES',500000);

-- Update the salary of an employee
UPDATE employee
SET salary = 60000
WHERE empid = 1;
-- Display the employee table
SELECT * FROM employee;

-- Display the salary_log table
SELECT * FROM sal_log;
 ```               
### Output:
![triggeroutput](https://github.com/JananiSoundararajan/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119477549/67113741-bacd-4db3-b47f-3d472581a74e)

### Result:
A trigger is created using PL/SQL.
