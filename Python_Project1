# My program to manipulate a text file with a menu showing a number of operations that the user can 
# perform on the data given, the user will remain in the program until a quit operation (9) is entered by the user.
# The text file is given the name ('Emp_Dataset') for this program to be able to use the text file.


def main():
    # creates a loop that calls the menu until 9 is entered which exits the program.
    choice = True
    while choice:
        # menu that gives the user 9 options
        print('1. Print out a summary statement, which details the number of records '
              'successfully read into your program')
        print('2. Print out a list of employees and their respective details ')
        print('3. Print a report detailing the total salary bill ')
        print('4. Print a report detailing the average salary bill based on the number of employees ')
        print('5. Add a new employee to the current list ')
        print('6. Print a report detailing the number of employees grouped by each position type ')
        print('7. Query the list by providing a salary threshold above which employees are returned ')
        print('8. Delete an employee from the current list ')
        print('9. Quit the program')

        try:
            # user input with an option for the menu
            choice = int(input('Please enter from 1-9 what option you would like to use : '))
            print('\n')

            # if statements that call the different functions for each option
            if choice == 1:
                opt_1()
            elif choice == 2:
                opt_2()
            elif choice == 3:
                opt_3()
            elif choice == 4:
                opt_4()
            elif choice == 5:
                opt_5()
            elif choice == 6:
                opt_6()
            elif choice == 7:
                opt_7()
            elif choice == 8:
                opt_8()
            elif choice == 9:
                print('Thank You for using my program, bye!')
                exit(0)
            elif choice < 0 or choice > 9:
                print('An invalid option has been entered')
        except ValueError:
            print('\n')
            print('An Invalid option has been entered please try again ')
        print('\n')


def opt_1():  # Prints out how many employees there are in the text file
    # reads file
    infile = open('Emp_Dataset.txt', 'r')
    count = 0

    # increments a counter for each line(employee) and prints a message with the count
    for line in infile:
        # if the line starts with '#' i.e the first line it decrements the counter to ignore it from the final count
        if line.startswith('#'):
            count -= 1
        count += 1
    print('There are', count, 'current records successfully read into this program')
    infile.close()


def opt_2():  # Prints a list of employees in the file
    # reads file\
    infile = open('Emp_Dataset.txt', 'r')
    # reads the first line in the file and gives it the variable name header separating it from the rest of the file
    # this is the same for each function where the first line needs to be excluded
    header = infile.readline()

    # prints all the employees in the file
    line = infile.read()
    print(line)
    infile.close()


def opt_3():  # Works out and prints the total salary bill of all the employees
    # reads file
    infile = open('Emp_Dataset.txt', 'r')
    header = infile.readline()
    salary = 0

    # adds the salary on each line together and prints it
    for line in infile:
        emp_list = line.split(',')
        salary = salary + float(emp_list[-2])
    print('Total salary bill is: £', format(salary, '.2f'))
    infile.close()


def opt_4():  # Average salary based on number of employees
    # reads file
    salary = 0
    count = 0
    infile = open('Emp_Dataset.txt', 'r')
    header = infile.readline()

    # adds each salary together and increments a count for each line(employee)
    for line in infile:
        count += 1
        line = line.split(',')
        salary = salary + float(line[-2])
    average = salary/count  # calculates the average by dividing the total by the number of employees
    print('Average salary of employees is: £', format(average, '.2f'))
    infile.close()


def opt_5():  # Add a new employee to the list
    # read in program as infile
    # get user input for each column in the file and join it together in one line and name it emp_data
    # allowing me to validate the user input on employee number
    # check file for employee number and if it isn't open the file in write as (...)
    # append the line to the file
    # close both open files

    # reads file
    infile = open('Emp_Dataset.txt', 'r')
    header = infile.readline()

    # user inputs the employees's data one field at a time
    print('To add a new employee please enter their details bellow')
    emp_num = input('Please enter a new employee number: ')
    emp_name = input('Please enter the first and last name of the employee: ')

    try:  # error handling for if the user input characters instead of an integer value
        emp_age = int(input('Please enter the age of the employee: '))
        if emp_age < 0 or emp_age > 100:  # extreme user input validation
            emp_age = int(input('Invalid age entered please try again '))
    except ValueError:
        emp_age = int(input('Please enter a valid age for the employee: '))

    emp_position = input('Please enter the position that the employee has: ')

    try:  # error handling for if the user input characters instead of an integer value
        emp_salary = int(input('Please enter the salary for the new employee: '))
    except ValueError:
        emp_salary = int(input('Please enter a valid salary for the employee: '))

    try:  # error handling for if the user input characters instead of an integer value
        emp_years = int(input('Please enter how many years the employee has worked at the company for: '))
        if emp_years > emp_age:
            # validation if the user enters that they have worked in the company for longer than they have been alive
            emp_years = int(input("Invalid! The employee can't have worked at the company longer than they are alive,"
                                  "please enter a valid number"))
    except ValueError:
        emp_years = int(input('Please enter a valid number for the amount of years the '
                              'employee has worked at the company for: '))

    # validates the users input so no employee number entered is a copy of a number already in the data
    lines = infile.read()
    if emp_num in lines:
        print('\n')
        emp_num = input('That employee number is already used by an employee please enter a valid employee number: ')

    # concatenates the different user input fields into one string called emp_data
    emp_data = (emp_num + ', ' + emp_name + ', ' + str(emp_age) + ', ' + emp_position + ', '
                + str(emp_salary) + ', ' + str(emp_years))

    # writes the new string into the file if the employee number isn't already in the data
    if emp_num not in lines:
        write_file = open('Emp_Dataset.txt', 'a')
        write_file.write(emp_data + '\n')
        write_file.close()
    infile.close()


def opt_6():  # prints a report of employees based on their position type
    # reads file
    infile = open('Emp_Dataset.txt', 'r')
    header = infile.readline()

    # creates an empty list for each of the position types
    developer_list = []
    analyst_list = []
    devops_list = []

    # appends a line to a list based on the position
    for line in infile:
        line = line.strip()
        if 'Developer' in line:
            developer_list.append(line)
        if 'Analyst' in line:
            analyst_list.append(line)
        if 'DevOps' in line:
            devops_list.append(line)

    # prints each item that was appended to each list
    print("These are all the employee's with the position Developer ")
    for item in developer_list:
        print(item)
    print('\n' + "These are all the employee's with the position Analyst ")
    for item in analyst_list:
        print(item)
    print('\n' + "These are all the employee's with the position DevOps ")
    for item in devops_list:
        print(item)
    infile.close()


def opt_7():  # Runs a query and returns a list of employees above that threshold
    # reads file
    infile = open('Emp_Dataset.txt', 'r')
    header = infile.readline()

    try:
        query_salary = float(input('Please enter a salary and every employee earning above it will be displayed: £'))
    except ValueError:
        query_salary = float(input('Invalid threshold given please enter a valid threshold: '))

    # compares the input with a value in the file
    for line in infile:
        emp_list = line.split(',')
        salary = float(emp_list[-2])
        if query_salary < salary:
            print(line)
    print("These are the employee's that earn over: £", format(query_salary, '.2f'))
    infile.close()


def opt_8():  # Deletes an employee from the list
    # reads file
    infile = open('Emp_Dataset.txt', 'r')
    header = infile.readline()
    lines = infile.readlines()
    infile.close()

    # gets an input value to search the file for and if the value is in the file it doesn't write that line to the file
    emp_num = input('Enter the employee number of the employee you would like to delete: ')
    infile = open('Emp_Dataset.txt', 'w')
    infile.write(header)
    for line in lines:
        list = line.split(',')
        search = list[0]

        # writes the line to the file if the line doesn't include the value entered by the user
        if emp_num != search:
            infile.write(line)
    infile.close()


# calls the main menu function which in turn calls the other functions based on the users input
main()
