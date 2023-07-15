# Task 1

SELECT d.NAME AS DEPT_NAME, AVG(s.AMT) AS AVG_MONTHLY_SALARY_USD
FROM Salaries s
JOIN Employees e ON e.id = s.EMP_ID
JOIN Departments d ON d.ID = e.DEPT_ID
GROUP BY d.NAME                        -- Group the results by department name
ORDER BY AVG(s.AMT) DESC               -- Sort the average salary in descending order
LIMIT 3;                               -- Limit the output to the top 3 departments with the highest average salary

--------------------------------------------------------------------------------------------------------------------------


# Task 2

import pandas as pd
departments=pd.read_csv("C:\Users\mail2\OneDrive\Desktop\Assignment\ASDE-Departments.csv")
employees=pd.read_csv("C:\Users\mail2\OneDrive\Desktop\Assignment\ASDE-Employees.csv")
salaries=pd.read_csv("C:\Users\mail2\OneDrive\Desktop\Assignment\ASDE-Salaries.csv")
df=pd.merge(departments,employees, left_on = 'ID',right_on='DEPT_ID')
data=pd.merge(df,salaries,left_on='ID_y',right_on='EMP_ID')
x=data.groupby(['NAME_x'])['AMT'].mean()
x.sort_values(ascending=False).head(3)


-----------------------------------------------------------------------------------------------------------------------------

# Task 3

def compute(n):
    if n < 10:
        out = n ** 2
    elif n < 20:
        out = 1
        for i in range(1, n-9):   //Here we need to change the value from (n-10)--> (n-9)
            out *= i
    else:
        lim = n - 19              //Here alse from (n-20) --> (n-19)
        out = lim * lim
        out = out - lim
        out = out / 2 
    print(out)


n = int(input("Enter an integer: "))
compute(n)




