# -Classes-and-Inheritance
a. Define a Python class named Employee:
# Example Employee class
class Employee:
    def __init__(self, name, age, salary):
        self.name = name
        self.age = age
        self.__salary = salary  # Private attribute

    # Getter for salary
    def get_salary(self):
        return self.__salary

    # Setter for salary
    def set_salary(self, salary):
        self.__salary = salary

    # Method to display employee details
    def display_employee(self):
        print(f"Name: {self.name}, Age: {self.age}, Salary: {self.__salary}")
b. Explain inheritance and class hierarchy:
class Manager(Employee):
    def __init__(self, name, age, salary, department):
        super().__init__(name, age, salary)
        self.department = department

    # Override the display method to add department info
    def display_employee(self):
        print(f"Name: {self.name}, Age: {self.age}, Salary: {self.get_salary()}, Department: {self.department}")

class Intern(Employee):
    def __init__(self, name, age, salary, duration):
        super().__init__(name, age, salary)
        self.duration = duration

    def display_employee(self):
        print(f"Name: {self.name}, Age: {self.age}, Salary: {self.get_salary()}, Duration: {self.duration} months")

        c. Create a program where Manager extends Employee:
        # Main program to demonstrate inheritance
class Employee:
    def __init__(self, name, age, salary):
        self.name = name
        self.age = age
        self.__salary = salary

    def get_salary(self):
        return self.__salary

    def set_salary(self, salary):
        self.__salary = salary

    def display_employee(self):
        print(f"Name: {self.name}, Age: {self.age}, Salary: {self.__salary}")

class Manager(Employee):
    def __init__(self, name, age, salary, department, position):
        super().__init__(name, age, salary)
        self.department = department
        self.position = position
         def display_employee(self):
        print(f"Name: {self.name}, Age: {self.age}, Salary: {self.get_salary()}, Department: {self.department}, Position: {self.position}")

# Example usage:
emp1 = Employee("John Doe", 30, 50000)
emp1.display_employee()

mgr1 = Manager("Jane Smith", 40, 80000, "IT", "Head of Development")
mgr1.display_employee()

2. Reading and Slicing Datasets
3. import csv

def read_csv_to_dict(file_path, limit=20):
    data = []
    with open(file_path, 'r') as file:
        reader = csv.DictReader(file)
        for i, row in enumerate(reader):
            if i >= limit:
                break
            data.append(row)
    return data

# Example Usage
file_path = 'your_csv_file.csv'
data = read_csv_to_dict(file_path)
for row in data:
    print(row)
    b. Slice the Dataset for Employees with Salary Above Average:
    def get_employees_above_average_salary(data):
    # Calculate average salary
    total_salary = sum(int(emp['Salary']) for emp in data)
    average_salary = total_salary / len(data)
    
    # Filter employees with salary above average
    employees_above_avg = [emp for emp in data if int(emp['Salary']) > average_salary]
    
    # Extract Name and Department, and sort by name
    employees_sorted = sorted([(emp['Name'], emp['Department']) for emp in employees_above_avg], key=lambda x: x[0])
    
    return employees_sorted

# Example usage
employees_above_avg = get_employees_above_average_salary(data)
for emp in employees_above_avg:
    print(emp)
    3. Integrating Classes with Dataset Operations
  class Employee:
    def __init__(self, name, age, salary, department):
        self.name = name
        self.age = age
        self.salary = salary
        self.department = department

def create_employee_objects(file_path):
    employees = []
    with open(file_path, 'r') as file:
        reader = csv.DictReader(file)
        for row in reader:
            employee = Employee(row['Name'], int(row['Age']), int(row['Salary']), row['Department'])
            employees.append(employee)
    return employees
  i. Employees Over 30 Years Old:
  def employees_over_30(employees):
    return [emp.name for emp in employees if emp.age > 30]

# Example usage
over_30 = employees_over_30(employees)
print(over_30)
ii. Employees Younger Than 25:
def employees_under_25(employees):
    return [emp.name for emp in employees if emp.age < 25]

# Example usage
under_25 = employees_under_25(employees)
print(under_25)
iii. Employees Between 28 and 35 Years Old:
def employees_between_28_and_35(employees):
    return [emp.name for emp in employees if 28 <= emp.age <= 35]

# Example usage
between_28_and_35 = employees_between_28_and_35(employees)
print(between_28_and_35)

iv. Employees Exactly 40 Years Old:
def employees_exactly_40(employees):
    return [emp.name for emp in employees if emp.age == 40]

# Example usage
exactly_40 = employees_exactly_40(employees)
print(exactly_40)
Filtering by Salary:
v. Employees With Salary Higher than ₦1,500,000:
def employees_salary_above(employees, threshold):
    return [emp.name for emp in employees if emp.salary > threshold]

# Example usage
above_1500000 = employees_salary_above(employees, 1500000)
print(above_1500000)
vi. Employees Earning Less than ₦800,000:
def employees_salary_below(employees, threshold):
    return [emp.name for emp in employees if emp.salary < threshold]

# Example usage
below_800000 = employees_salary_below(employees, 800000)
print(below_800000)
3. Additional Employee Queries
c. Employees With a Salary Between ₦500,000 and ₦1,200,000:
d. Top 5 Highest Paid Employees (Sorted by Salary):
def top_5_highest_paid(employees):
    sorted_employees = sorted(employees, key=lambda emp: emp.salary, reverse=True)
    return [(emp.name, emp.salary) for emp in sorted_employees[:5]]

# Example usage
top_5_employees = top_5_highest_paid(employees)
for emp in top_5_employees:
    print(emp)
    4. Department-Wise Employee Data:
a. Number of Employees in Each Department:
from collections import Counter

def count_employees_by_department(employees):
    department_counts = Counter(emp.department for emp in employees)
    return dict(department_counts)

# Example usage
department_counts = count_employees_by_department(employees)
print(department_counts)\

b. Employees Grouped by Department:

from collections import defaultdict

def employees_grouped_by_department(employees):
    department_dict = defaultdict(list)
    for emp in employees:
        department_dict[emp.department].append(emp.name)
    return dict(department_dict)

# Example usage
employees_by_dept = employees_grouped_by_department(employees)
for dept, emp_list in employees_by_dept.items():
    print(f"{dept}: {emp_list}")
a. Total Monthly Payroll for the Company:
def total_monthly_payroll(employees):
    return sum(emp.salary for emp in employees)

# Example usage
total_payroll = total_monthly_payroll(employees)
print(f"Total Monthly Payroll: {total_payroll}")
b. Employee(s) with the Highest Salary:
def employee_with_highest_salary(employees):
    max_salary = max(emp.salary for emp in employees)
    highest_paid = [emp.name for emp in employees if emp.salary == max_salary]
    return highest_paid, max_salary

# Example usage
highest_paid_emp, salary = employee_with_highest_salary(employees)
print(f"Highest Paid Employee(s): {highest_paid_emp}, Salary: {salary}")
c. Employee(s) with the Lowest Salary:
def employee_with_lowest_salary(employees):
    min_salary = min(emp.salary for emp in employees)
    lowest_paid = [emp.name for emp in employees if emp.salary == min_salary]
    return lowest_paid, min_salary

# Example usage
lowest_paid_emp, salary = employee_with_lowest_salary(employees)
print(f"Lowest Paid Employee(s): {lowest_paid_emp}, Salary: {salary}")

6. Removing Employees Based on Experience Level:
class Employee:
    def __init__(self, name, age, salary, department, experience_level):
        self.name = name
        self.age = age
        self.salary = salary
        self.department = department
        self.experience_level = experience_level

def remove_junior_employees(employees):
    return [emp for emp in employees if emp.experience_level.lower() != 'junior']

# Example usage (assuming experience levels are included in your data)
filtered_employees = remove_junior_employees(employees)
print(f"Remaining Employees: {len(filtered_employees)}")
7. Ranking Employees by Salary within Each Department:
def rank_employees_by_salary_within_dept(employees):
    employees_by_dept = defaultdict(list)
    for emp in employees:
        employees_by_dept[emp.department].append(emp)
    
    ranked_by_dept = {}
    for dept, emps in employees_by_dept.items():
        ranked_by_dept[dept] = sorted(emps, key=lambda emp: emp.salary, reverse=True)
    
    # Format for display: [(name, salary), ...]
    return {dept: [(emp.name, emp.salary) for emp in emps] for dept, emps in ranked_by_dept.items()}

# Example usage
ranked_employees = rank_employees_by_salary_within_dept(employees)
for dept, emps in ranked_employees.items():
    print(f"{dept}: {emps}")
        
