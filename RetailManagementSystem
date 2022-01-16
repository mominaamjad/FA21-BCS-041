import datetime
import random

date = datetime.datetime.now()
emp_name = ['Qaiser Malik', 'Saif ur Rehman', 'Khalid Saleem', 'Ayesha Faisal', 'Fizza Anwar']
emp_id = ['EMP100', 'EMP101', 'ADM110', 'EMP115', 'EMP102']
emp_contact = ['03331234567', '03345695959', '03321456284', '03498527401', '03429447364']
emp_designation = ['Employee', 'Employee', 'Admin', 'Employee', 'Employee']
emp_password = ['123', '1234', '12345', '123456', '1234567']
item = ['Perfume', 'Soap', 'Notebook', 'Bread', 'Tea', 'Detergent', 'Salt', 'Spices', 'Biscuit', 'Ketchup']
price = [250, 50, 100, 123, 250, 305, 167, 150, 130, 200]
stock = [230, 500, 200, 344, 580, 130, 900, 400, 230, 100]
bill = []
total = []


def main():
    print('')
    print(format('\033[93m' + "RETAIL MANAGEMENT SYSTEM FA21-BCS-041" + '\033[0m', '>80s'))
    l = 'y'
    while l != 'x':
        print('0-Employee Portal')
        print('1-Admin Portal')
        print('2-Exit')
        portal = eval(input('>>'))

        # Employee Portal
        if portal == 0:
            print('\033[1m' + 'EMPLOYEE PORTAL' + '\033[0m')
            print('\033[93m' + "--------Employee Login--------" + '\033[0m')
            id = emp_login()
            emp_portal(id)

        # Admin Portal
        elif portal == 1:
            print('\033[1m' + 'ADMIN PORTAL' + '\033[0m')
            print('\033[93m' + "--------Admin Login--------" + '\033[0m')
            adm_id = input('Enter ID: ')
            adm_pass = input('Enter Password: ')
            if adm_id == 'ADM110' and adm_pass == '12345':
                print('Login Successful')
                print('Welcome', '\033[1m' + emp_name[2] + '\033[0m', '!')
                o = 'y'
                while o != 'x':
                    print('0-Employees')
                    print('1-Inventory')
                    print('2-Invoices')
                    admin = eval(input('>>'))
                    if admin == 0:
                        print('\033[93m' + 'EMPLOYEES' + '\033[0m')
                        print('0-VIEW        1-ADD')
                        employee = eval(input('>>'))
                        if employee == 0:
                            view_emp()
                        else:
                            print('\033[93m' + '\\\\ NEW EMPLOYEE \\\\' + '\033[0m')
                            add_emp()
                            print('\033[1m' + 'New Employee Has been Added' + '\033[0m')
                    elif admin == 1:
                        print('\033[93m' + 'INVENTORY' + '\033[0m')
                        print('0-VIEW         1-ADD')
                        inventory = eval(input('>>'))
                        if inventory == 0:
                            view_inv()
                        else:
                            print('\033[93m' + '\\\\ NEW ITEM \\\\' + '\033[0m')
                            add_inv()
                            print('\033[1m' + 'ITEM HAS BEEN ADDED' + '\033[0m')
                    else:
                        print('\033[93m' + 'INVOICES' + '\033[0m')
                        view_invoices()
                    o = input('x to quit:')
            else:
                print('You are not Admin')
        else:
            print('\033[93m' + 'GOODBYE' + '\033[0m')
            break


def emp_login():
    id = input("Enter Employee ID: ")
    correct = checkid(id)
    while correct != 1:
        id = input("Enter Employee ID: ")
        correct = checkid(id)
    print('Login Successful')
    variable = emp_id.index(id)
    print('Welcome', '\033[1m' + emp_name[variable] + '\033[0m', '!')
    return id


def checkid(id):
    global bool_id
    length = len(emp_id)
    for i in range(0, length):
        if id == emp_id[i]:
            bool_id = True
            break
        else:
            bool_id = False
    if bool_id:
        variable = emp_id.index(id)
        password = input("Enter Password:")
        check = checkpassword(password, variable)
        while check != 1:
            print('Try Again')
            password = input("Enter Password:")
            check = checkpassword(password, variable)
        return True
    else:
        print('Invalid ID')
        return False


def checkpassword(password, index):
    if password == emp_password[index]:
        return True
    else:
        return False


def emp_portal(id):
    m = 'y'
    while m != 'x':
        print('0-Billing System')
        print('1-Log out')
        login = eval(input('>>'))
        if login == 0:
            n = 'y'
            while n != 'x':
                billing(id)
                n = input('New bill? (x to quit):')
        else:
            break
        m = input('x to quit: ')


def billing(id):
    print('\033[93m' + "--------Billing System--------" + '\033[0m')

    # bill calculation
    bill_no = input("Enter Bill number (XXXXXX): ")
    customer_id = input("Enter customer ID: ")
    total_bill = 0
    print("\\\\SCAN THE ITEMS\\\\")

    # bill generation
    print('\033[93m' + "----------------------------------------" + '\033[0m')
    print(format("Bill #", ">20s"), bill_no)
    print(format("Customer ID:", ">23s"), customer_id)
    print(format("Employee ID:", ">23s"), id)
    print(format("Date:", ">18s"), date.strftime("%x"))
    print('\033[93m' + "----------------------------------------" + '\033[0m')
    print("Name", format("Price", ">35s"))
    print('\033[93m' + "----------------------------------------" + '\033[0m')
    for i in range(0, 3):
        j = random.randint(0, 9)
        total_bill = total_bill + price[j]
        print(format(item[j], "<34s"), price[j])
    print(format("Total:", ">34s"), total_bill)
    print('\033[93m' + "----------------------------------------" + '\033[0m')
    bill.append(bill_no)
    total.append(total_bill)


def view_emp():
    print('\033[1m' + format('Name', '<17s'), format('ID', '<10s'), format('Contact', '<15s'),
          format('Designation', '<15s') + '\033[0m')
    print('------------------------------------------------------------')
    length = len(emp_id)
    for i in range(0, length):
        print(format(emp_name[i], '<17s'), format(emp_id[i], '<10s'),
              format(emp_contact[i], '<15s'), format(emp_designation[i], '<15s'))
    print('------------------------------------------------------------')


def add_emp():
    fName = input("Enter First Name:")
    lName = input("Enter Last Name:")
    emp_name.append(fName + ' ' + lName)
    phone = input("Enter valid phone number:")
    emp_contact.append(phone)
    email = input("Enter Email:")
    password = input("Enter Password: ")
    emp_password.append(password)
    designation = 'Employee'
    emp_designation.append(designation)
    identity = input('Enter ID (EMPXXX): ')
    emp_id.append(identity)


def view_inv():
    print(format('Item', '<20s'), format('Price', '<10s'), format('Quantity', '<10s'))
    print('-----------------------------------------')
    length = len(item)
    for i in range(0, length):
        print(format(item[i], '<20s'), format(str(price[i]), '<10s'),
              format(str(stock[i]), '<10s'))
    print('-----------------------------------------')


def add_inv():
    name = input('Enter item name:')
    item.append(name)
    mrp = eval(input('Enter price:'))
    price.append(mrp)
    quantity = eval(input('Enter quantity: '))
    stock.append(quantity)


def view_invoices():
    if len(bill) > 0:
        print(format('Bill no', '<10s'), format('Total', '<10s'))
        print('--------------------')
        length = len(bill)
        for i in range(0, length):
            print(format(bill[i], '<10s'), format(str(total[i]), '<10s'))
        print('--------------------')
    else:
        print('no invoices available')


main()
