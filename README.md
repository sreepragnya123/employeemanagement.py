# employeemanagementclass Employee:
    def __init__(self, emp_id, name, age, department, position):
        self.emp_id = emp_id
        self.name = name
        self.age = age
        self.department = department
        self.position = position

    def __str__(self):
        return f"ID: {self.emp_id}, Name: {self.name}, Age: {self.age}, Department: {self.department}, Position: {self.position}"


class EmployeeManagementSystem:
    def __init__(self):
        self.employees = []

    def add_employee(self):
        emp_id = input("Enter Employee ID: ")
        name = input("Enter Employee Name: ")
        age = input("Enter Employee Age: ")
        department = input("Enter Department: ")
        position = input("Enter Position: ")

        employee = Employee(emp_id, name, age, department, position)
        self.employees.append(employee)
        print(f"Employee {name} added successfully.\n")

    def view_employees(self):
        if not self.employees:
            print("No employees found.\n")
        else:
            for emp in self.employees:
                print(emp)

    def update_employee(self):
        emp_id = input("Enter the Employee ID to update: ")
        employee = next((emp for emp in self.employees if emp.emp_id == emp_id), None)

        if employee:
            employee.name = input(f"Enter new name (current: {employee.name}): ")
            employee.age = input(f"Enter new age (current: {employee.age}): ")
            employee.department = input(f"Enter new department (current: {employee.department}): ")
            employee.position = input(f"Enter new position (current: {employee.position}): ")
            print(f"Employee {emp_id} updated successfully.\n")
        else:
            print("Employee not found.\n")

    def delete_employee(self):
        emp_id = input("Enter the Employee ID to delete: ")
        employee = next((emp for emp in self.employees if emp.emp_id == emp_id), None)

        if employee:
            self.employees.remove(employee)
            print(f"Employee {emp_id} deleted successfully.\n")
        else:
            print("Employee not found.\n")

    def display_menu(self):
        while True:
            print("\nEmployee Management System")
            print("1. Add Employee")
            print("2. View Employees")
            print("3. Update Employee")
            print("4. Delete Employee")
            print("5. Exit")

            choice = input("Enter your choice: ")

            if choice == '1':
                self.add_employee()
            elif choice == '2':
                self.view_employees()
            elif choice == '3':
                self.update_employee()
            elif choice == '4':
                self.delete_employee()
            elif choice == '5':
                print("Exiting Employee Management System...")
                break
            else:
                print("Invalid choice, please try again.")


if __name__ == "__main__":
    system = EmployeeManagementSystem()
    system.display_menu()

