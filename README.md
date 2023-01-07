# Pewlett-Hackard-Analysis
Pewlett Hackard is a large company with thousands of employees, many who will be reaching retirement age soon. The number of retirees will leave thousands of job openings. The company wants to prepare and be proactive for this. 

## Overview of Analysis 
To better prepare for the Baby Boomers who will be retiring, Pewlett-Hackard has asked us to determine the number of retiring employees by their title and then to identify employees who are eligible to participate in a mentorship program. This data will help the company prepare for the "silver tsunami" as thousands of employees reach retirement age. 

## Results 
  - Pewlett Hackard has 133,776 employees in their database that were born between January 1, 1952 and December 31, 1955. However, this is all employees on file, some of whom may no longer be with the company. 
  - There are 72,458 current employees company-wide who are reaching retirement age. All of these employees were born in the years 1952 through 1955. 
  - The largest number of employees will be retiring from the job title Senior Engineer. This is closely followed by Senior Staff. 
  ![image](https://user-images.githubusercontent.com/117782103/211128453-5c2285c2-9a49-4847-87ac-b3882a4583b4.png)
  - There are 1,549 employee who qualify for the Mentorship Program. These are employees who were born in the year 1965. 
  
  ## Summary 
  
  ### Roles Needed 
  Pewlett-Hackard will have 72,458 roles that need to be filled as the "silver tsunami" begins. 
  
  ### Qualified Mentors 
  In most roles, there will be hundreds of qualified, retirement-ready mentors to train the next generation of employees in their job roles. However, this pales in comparison to the number of employees that will be needed. 
  
  ### Additional Queries 
  The following two queries/tables will provide additional insight to the "silver tsunami". 
  
  By running this first query, you will have insight to valuable information that shows which departments the retiring employees belong  to. This table shows unique current employees born in the years 1952-1955.
  
         SELECT DISTINCT ON (e.emp_no) e.emp_no, d.dept_name, e.first_name, e.last_name, 
          e.birth_date, de.from_date, de.to_date, t.title
        INTO department_retires
        FROM employees AS e 
        INNER JOIN dept_emp AS DE
        ON (e.emp_no = de.emp_no)
        INNER JOIN titles AS t
        ON (e.emp_no = t.emp_no)
        LEFT JOIN departments AS d
        ON (de.dept_no = d.dept_no)
        WHERE (de.to_date = '9999-01-01') AND (e.birth_date BETWEEN '1952-01-01' AND '1955-12-31')
        ORDER BY e.emp_no;
  
Lastly, by running the count functions, we can determine how many people are retiring from each department and the number in each job title within that department. You could easily change this code slightly and figure out the number of people retiring for the department as a whole or could change your conditionals to determine how many mentor eligible employees are in each specific department. 
![image](https://user-images.githubusercontent.com/117782103/211130038-fb621a88-44e1-4bdc-bbc0-3324c46d41c8.png)
