# assingment-4
fourth programming assignment 

#Name: Dylan Sen
#Assignment Number: 4
#Date: 3/4/2018
#Description: This is a transaction portal for Beautiful and Handsome T-shirts. It uses functions and loops to run a sequence for customers to purchase shirts.

#named constants
RED_SHIRT_PRICE = 8 #price for a red shirt
BLUE_SHIRT_PRICE = 18 #price for a blue shirt
YELLOW_SHIRT_PRICE = 8 #price for a yellow shirt
SALES_TAX = .0725 #sales tax
DONATION_AMOUNT = .01 #1% donation to United Way
MAX_RED_SHIRT = 8 #maximum red tshirt amount
MAX_YELLOW_SHIRT = 8 #maximum yellow tshirt amount
MAX_BLUE_TSHIRT = 19 #maximum blue tshirt amount

#displays customer menu
def display_menu(): 
        print("Welcome to Beautiful and Handsome!")
        print("-----------------------------------")
        print("(A) - Red T-shirt             $8.00")
        print("(B) - Blue T-shirt           $18.00")
        print("(C) - Yellow T-Shirt          $8.00")

#gets the customers choice for the shirt color
def get_customer_choice():

        customer_type_selected = input("What type of shirt would you like to purchase?")
        while customer_type_selected != 'A' and customer_type_selected != 'a' and customer_type_selected != 'B' and \
        customer_type_selected != 'b' and customer_type_selected != 'C' and customer_type_selected != 'c':
                print("Invalid input. Please try again.")
                customer_type_selected = input("What type of shirt would you like to purchase?")
        return customer_type_selected

#asks for user to input the amount of tshirts wanted
def get_tshirt_number(customer_choice_returned):

        if customer_choice_returned == 'A' or customer_choice_returned == 'a': #if customer selects red t-shirts
                customer_amount_ordered = int(input("How many red t-shirts would you like to order?"))
                while customer_amount_ordered < 0 or customer_amount_ordered > MAX_RED_SHIRT:
                        if customer_amount_ordered < 0:
                            print("Invalid Number! Enter a nonnegative number: ")
                            customer_amount_ordered = int(input("How many red t-shirts would you like to order?"))
                        elif customer_amount_ordered > MAX_RED_SHIRT:
                            print("Invalid Number! You can only order a max of 8 red shirts.")
                            customer_amount_ordered = int(input("How many red t-shirts would you like to order?"))
        
        elif customer_choice_returned == 'B' or customer_choice_returned == 'b': #if customer selects blue t-shirts
                customer_amount_ordered = int(input("How many blue t-shirts would you like to order?"))
                while customer_amount_ordered < 0 or customer_amount_ordered > MAX_BLUE_TSHIRT:
                        if customer_amount_ordered < 0:
                            print("Invalid Number! Enter a nonnegative number: ")
                            customer_amount_ordered = int(input("How many red t-shirts would you like to order?"))
                        elif customer_amount_ordered > MAX_BLUE_TSHIRT:
                            print("Invalid Number! You can only order a max of 19 blue shirts.")
                            customer_amount_ordered = int(input("How many blue t-shirts would you like to order?"))
        
        elif customer_choice_returned == 'C' or customer_choice_returned == 'c': #if customer selects yellow t-shirts
                customer_amount_ordered = int(input("How many yellow t-shirts would you like to order?"))
                while customer_amount_ordered < 0 or customer_amount_ordered > MAX_BLUE_SHIRT:
                        if customer_amount_ordered < 0:
                            print("Invalid Number! Enter a nonnegative number: ")
                            customer_amount_ordered = int(input("How many yellow t-shirts would you like to order?"))
                        elif customer_amount_ordered > MAX_YELLOW_SHIRT:
                            print("Invalid Number! You can only order a max of 8 yellow shirts.")
                            customer_amount_ordered = int(input("How many yellow t-shirts would you like to order?"))
        return customer_amount_ordered
        print("You have purchased a total of {amount:.2f} shirts." .format(amount=customer_amount_ordered))

#calculates the total cost of each shirt color purchased
def calculate_charge(shirt_price, shirts_ordered, SALES_TAX):
    if shirt_price == RED_SHIRT_PRICE or shirt_price == YELLOW_SHIRT_PRICE:
        charge = RED_SHIRT_PRICE * shirts_ordered * SALES_TAX #price of shirt * amount of color ordered * tax
    else: 
        charge = BLUE_SHIRT_PRICE * shirts_ordered * SALES_TAX #price of shirt * amount of color ordered * tax
        return charge

#asks the user if they want to buy more for the green shirt
def buy_more(total_shirts_bought):
    if total_shirts_bought > 1 and total_shirts_bought < 3:
        print("If you buy {amount-3:.2f}, you will qualify for a free green shirt") .format(total_shirts_bought - 3)
        more_shirts = input("Would you like to buy more(y or Y for yes?") #stores a Y or N to return to main and run again
        return more_shirts #returns the answer
    else:
        print("You will receive a free green shirt!")
        return 1 # 1 signifies getting the green shirt

def main():

        display_menu() #call to the display menu function
        customer_choice_returned = get_customer_choice() #stores the return value from customer choice
        if customer_choice_returned == 'A' or customer_choice_returned == 'a':
                red_shirts_ordered = get_tshirt_number(customer_choice_returned)
                total_red_charge = calculate_charge(RED_SHIRT_PRICE, red_shirts_ordered, SALES_TAX)
        elif customer_choice_returned == 'B' or customer_choice_returned == 'b':
                blue_shirts_ordered = get_tshirt_number(customer_choice_returned)
                total_blue_charge = calculate_charge(BLUE_TSHIRT_PRICE, blue_shirts_ordered, SALES_TAX)
        elif customer_choice_returned == 'C' or customer_choice_returned == 'c':
                yellow_shirts_ordered = get_tshirt_number(customer_choice_returned)
                total_yellow_charge = calculate_charge(YELLOW_SHIRT_PRICE, yellow_shirts_ordered, SALES_TAX)

        calculate_charge(shirt_price, shirts_ordered, SALES_TAX)

        buy_more(total_shirts_bought)
        
        while buy_more == 'Y' or buy_more == 'y': #loop until an N is reached for ordering more shirts
            display_menu()
            customer_choice_returned = get_customer_choice()
            if customer_choice_returned == 'A' or customer_choice_returned == 'a':
                red_shirts_ordered += get_tshirt_number(customer_choice_returned) # '+=' in case existing value
                total_red_charge += charge(RED_SHIRT_PRICE, red_shirts_ordered, SALES_TAX)
            elif customer_choice_returned == 'B' or customer_choice_returned == 'b':
                blue_shirts_ordered += get_tshirt_number(customer_choice_returned)
                total_blue_charge += charge(BLUE_TSHIRT_PRICE, blue_shirts_ordered, SALES_TAX)
            elif customer_choice_returned == 'C' or customer_choice_returned == 'c':
                yellow_shirts_ordered += get_tshirt_number(customer_choice_returned)
                total_yellow_charge += charge(YELLOW_SHIRT_PRICE, yellow_shirts_ordered, SALES_TAX)
            buy_more(total_shirts_bought)
                    
        total_shirts_bought = red_shirts_ordered + blue_shirts_ordered + yellow_shirts_ordered #stores total shirts ordered (of all colors)
        total_charge = total_red_charge + total_blue_charge + total_yellow_charge #total charge for all shirts
            
#print out the final sales report
        print("T-shirt sales report:")
        print("-----------------------------------")
        print("{amount:.2f} Red T-shirts") .format(amount=red_shirts_ordered) #insert total_red_charge
        print("{amount:.2f} Blue T-shirts") .format(amount=blue_shirts_ordered) #and etc for below
        print("{amount:.2f} Yellow T-Shirts") .format(amount=yellow_shirts_ordered)
        print("{amount:.2f}Total T-shirts") .format(ammount=total_shirts_bought)


        if buy_more == 1:
                print("You will also receive a free green T-shirt!")



main()
