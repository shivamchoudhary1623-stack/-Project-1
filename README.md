# -Project-1
#Enter category (Type 1 for student section or Type 2 for faculty)
print("enter number for select category\n 1 = for student\n 2 = for faculty\n 3 = for visting / guest faculty section ")
a=int(input("enter category number:- "))

# Initialize variables that might be used later in total calculation
Base_fee = 0.0
discount = 0.0
parking_fee = 0.0
pc = 0.0


#for student
#for both UG/PG students
if a == 1:
    student = input("enter student name :- ")
    graduation_standard = input("enter student's graduation standard (UG/PG) :-").upper()
    hostel = input("are you a hostel resident (yes/No)").lower()

    if graduation_standard == "UG":
        #nom=number of months
        nom = int(input("enter number of months of staying :-"))
        if nom <= 0:
            print("number of months cannot be zero or negative")
            Base_fee = 0.0 # Set to 0 if invalid months
        else:
            Base_fee = nom * 500
        unit = float(input("enter electricity unit number :-"))

        if unit > 0 and unit <= 100:
            fsc = 50 #fixed service charge
            bill = unit * 3
            total_bill = bill + fsc
            print(f"electricity bill of {student} is {total_bill} with fixed service charge ")
        elif unit > 100 and unit <= 300:
            fsc = 100
            bill = unit * 3
            total_bill = bill + fsc
            print(f"electricity bill of {student} is {total_bill} with fixed service charge ")
        elif unit > 300 and unit <= 500:
            fsc = 150
            bill = unit * 3
            total_bill = bill + fsc
            print(f"electricity bill of {student} is {total_bill} with fixed service charge ")
        elif unit > 500:
            fsc = 250 #fixed service charge
            bill = unit * 3
            total_bill = bill + fsc
            print(f"electricity bill {student} is {total_bill} with fixed service charge ")
        else:
            print("electricity units cannot be negative or zero")
            total_bill = 0.0 # Initialize if units are invalid

        # CGPA related discount calculation for UG
        cgpa = float(input("enter CGPA :-"))
        if cgpa < 0.0 or cgpa > 10.0:
            print("wrong entry of CGPA ")
        else:
            print(f"Base fee before discount ={Base_fee}")
            if cgpa >= 8.5:
                discount = (0.2 * Base_fee)
                Base_fee = (Base_fee - discount) # Apply discount to Base_fee
                print(f"Base fee of {student} after discount is {Base_fee}")
            elif (cgpa >= 7.5 and cgpa < 8.5):
                discount = (0.10 * Base_fee)
                Base_fee = (Base_fee - discount) # Apply discount to Base_fee
                print(f"Base fee of {student} after discount is {Base_fee}")
            else:
                print("NO DISCOUNT")
                discount = 0.0


    elif graduation_standard == "PG":
        #nom=number of months
        nom = int(input("enter number of months of saying  :-"))
        if nom <= 0:
            print("number of months cannot be zero or negative")
            Base_fee = 0.0 # Set to 0 if invalid months
        else:
            Base_fee = nom * 350
        unit = float(input("enter electricity unit number :-"))

        if unit > 0 and unit <= 100:
            fsc = 50 #fixed service charge
            bill = unit * 3
            total_bill = bill + fsc
            print(f"electricity bill of {student} is {total_bill} with fixed service charge ")
        elif unit > 100 and unit <= 300: # Added this missing block
            fsc = 100 #fixed service charge
            bill = unit * 3
            total_bill = bill + fsc
            print(f"electricity bill of {student} is {total_bill} with fixed service charge ")
        elif unit > 300 and unit <= 500:
            fsc = 150 #fixed service charge
            bill = unit * 3
            total_bill = bill + fsc
            print(f"electricity bill of {student} is {total_bill} with fixed service charge ")
        elif unit > 500:
            fsc = 250 #fixed service charge
            bill = unit * 3
            total_bill = bill + fsc
            print(f"electricity bill {student} is {total_bill} with fixed service charge ")
        else:
            print("electricity units cannot be negative or zero")
            total_bill = 0.0 # Initialize if units are invalid


        # CGPA related discount calculation for PG
        cgpa = float(input("enter CGPA :-"))
        if cgpa < 0.0 or cgpa > 10.0:
            print("wrong entry of CGPA ")
        else:
            print(f"Base fee before discount = {Base_fee}")
            if cgpa >= 8.5:
                discount = (0.20 * Base_fee)
                Base_fee = (Base_fee - discount) # Apply discount
                print(f"Base fee of {student} after discount is {Base_fee}")
            elif (cgpa > 7.5 and cgpa < 8.5):
                discount = (0.10 * Base_fee)
                Base_fee = (Base_fee - discount) # Apply discount
                print(f"Base fee of {student} after discount is {Base_fee}")
            else:
                print(f"Base fee of {student} is :- {Base_fee}")
                discount = 0.0

    else:
        print(f"{student} is not a student of our university ")

    # Parking section

    parking = int(input("Enter type of parking (0 for none, 2 for 2-wheeler, 4 for 4-wheeler):- "))

    if parking == 2:
        parking_fee = 200.00
        print(f"parking fee (2-wheeler) ={parking_fee}rs/month")
        pc = 0.00
    elif parking == 4:
        parking_fee = 600.00
        pc = 150.00
        print(f"parking fee (4-wheeler) ={parking_fee}rs/month")
        print(f"student peak charge =  {pc}rs")
    elif parking == 0:
        parking_fee = 0.0
        pc = 0.0
    else:
        parking_fee = 0.00
        pc = 0.00
        print("Invalid parking option entered. No parking fee applied.")

    # Total calculation for student
    total = Base_fee - discount + parking_fee + pc
    print(f"Net pass & parking total = {total}")

#for faculty
elif a == 2:
    faculty = input("enter faculty name :- ")
    #nom=number of months
    nom = int(input("enter number of months of staying :- "))
    if nom <= 0:
        print("number of months cannot be zero or negative")
        Base_fee = 0.0 # Handle invalid months
    else:
        Base_fee = nom * 800
    wt = int(input("enter year of service :- "))
    if wt > 10:
        print(f"Base fee of mr/mrs {faculty} before discount is {Base_fee}")
        discount = (0.15 * Base_fee)
        Base_fee = (Base_fee - discount)
        print(f"Base fee of mr/mrs {faculty} after discount is {Base_fee}")
    elif wt < 0:
        print("years cannot be negative ")
    else:
        print(f"base fee of ms/mrs {faculty} is {Base_fee}")
    print(f"Total fee for {faculty} is {Base_fee}")


#for guest faculty
elif a == 3:
    guest = input("enter visiting/guest faculty name :-")
    #nom=number of months
    nom = int(input("enter number of months of staying :-"))
    if nom <= 0:
        print("number of months cannot be zero or negative")
        Base_fee = 0.0 # Handle invalid months
    else:
        Base_fee = nom * 1200
    print(f"Base fee of mr/mrs {guest} is {Base_fee} ")

else:
    print("invalid category number entered. ")
