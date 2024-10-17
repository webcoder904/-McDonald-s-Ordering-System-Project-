Project Title: McDonald's Ordering System

Overview:
This project simulates a virtual McDonald's ordering experience, allowing users to interact with a menu, place their orders, and receive a detailed bill. The system uses Python's data structures, loops, and conditional statements, with the OpenCV library to display the menu. The ordering process includes inputting the desired items, specifying the quantity, and calculating the final bill with an added GST.

Features:

View a dynamic menu with items and nutrition details.
Place orders by selecting item numbers and quantities.
Receive a detailed bill with itemized costs and total amount, including GST.
Technologies Used:

Python
OpenCV (for displaying the menu)
How It Works:

The menu is displayed using OpenCV.
The user selects items from the menu by entering the corresponding numbers.
Quantities for each item are specified.
A detailed bill is generated, listing all ordered items, their quantity, and the total price, with GST applied.
Setup Instructions:

Install OpenCV using the command:

pip install opencv-python

Download or clone the project to your local system.
Ensure the menu image is available at the specified file path:
"meanu.jpg" (download image )
Run the Python script to start the ordering system.
Future Enhancements:

Adding more item categories.
Improving the user interface for a more interactive experience.
Implementing real-time updates to the menu using computer vision.


import cv2 as cv  

def Mcdonals_ordering_system():
    # Load the menu image and resize it for display
    menu = cv.imread("meanu.jpg" # add your file path)
    menu_ = cv.resize(menu, (800, 700))
    
    # Display the menu image using OpenCV
    cv.imshow("menu", menu_)
    cv.waitKey(0)
    
    ordered_item_list = []  # List to store ordered items and their quantities
    while True:
        # Dictionary storing menu items categorized by type
        dic = {
            "chicken": {
                1: "{ 1 } MCCHICKEN [400 Calories 21g Fat 39g Carbs 14g Protein]",
                2: "{ 2 } FILET-O-FISH [380 Calories 18g Fat 39g Carbs 16g Protein]",
                3: "{ 3 } CRISPY CHICKEN SANDWICH [470 Calories 20g Fat 45g Carbs 27g Protein]",
                4: "{ 4 } SPICY CRISPY CHICKEN [530 Calories 26g Fat 47g Carbs 27g Protein]",
                5: "{ 5 } DELUXE CRISPY CHICKEN [530 Calories 26g Fat 47g Carbs 27g Protein]",
                6: "{ 6 } DELUXE SPICY CRISPY CHICKEN [540 Calories 26g Fat 48g Carbs 27g Protein]"
            },
            "FRIES": {
                7: "{ 7 } SMALL FRIES [220 Calories 10g Fat 29g Carbs 3g Protein]",
                8: "{ 8 } MEDIUM FRIES [320 Calories 15g Fat 43g Carbs 5g Protein]",
                9: "{ 9 } LARGE FRIES [490 Calories 23g Fat 66g Carbs 7g Protein]"
            },
            "MCNUGGETS": {
                10: "{ 10 } 4PC. CHICKEN MCNUGGETS [170 Calories 10g Fat 10g Carbs 9g Protein]",
                11: "{ 11 } 6 PC. CHICKEN MCNUGGETS [250 Calories 15g Fat 15g Carbs 14g Protein]",
                12: "{ 12 } 10 PC. CHICKEN MCNUGGETS [420 Calories 25g Fat 25g Carbs 23g Protein]"
            }
        }

        print("-" * 20)
        
        # Ask the user for their category choice
        place_order = input("Enter your order from the given menu [chicken, Fries, Mcnuggets]: ")

        # Chicken category ordering process
        if place_order == "chicken":
            print("-" * 50)
            while True:
                for i in dic["chicken"].values():
                    print(i)
                item = int(input("Enter your item number: "))
                
                # Based on selected item, ask for quantity and calculate cost
                if item == 1:
                    quantity = int(input("Enter your Quantity: "))
                    multi_qut = quantity * 100
                    ordered_item_list.append([dic["chicken"][1], multi_qut, quantity])
                elif item == 2:
                    quantity = int(input("Enter your Quantity: "))
                    multi_qut = quantity * 170
                    ordered_item_list.append([dic["chicken"][2], multi_qut, quantity])
                # Additional items follow similar structure...
                
                # Option to exit the chicken menu
                exit_1 = input("Enter [ 'e' ] to exit or ['n'] to continue: ")
                if exit_1 == "e":
                    break
        
        # Fries category ordering process
        elif place_order.lower() == "fries":
            print("-" * 50)
            while True:
                for i in dic["FRIES"].values():
                    print(i)
                item = int(input("Enter your item number: "))
                
                # Process fries orders similarly by asking for quantity
                if item == 7:
                    quantity = int(input("Enter your Quantity: "))
                    multi_qut = quantity * 50
                    ordered_item_list.append([dic["FRIES"][7], multi_qut, quantity])
                # Additional items follow similar structure...

                # Option to exit the fries menu
                exit_2 = input("Enter [ 'e' ] to exit or ['n'] to continue: ")
                if exit_2 == "e":
                    break
        
        # McNuggets category ordering process
        elif place_order == "mcnuggets":
            print("-" * 50)
            while True:
                for i in dic["MCNUGGETS"].values():
                    print(i)
                item = int(input("Enter your item number: "))
                
                # Process McNuggets orders similarly by asking for quantity
                if item == 10:
                    quantity = int(input("Enter your Quantity: "))
                    multi_qut = quantity * 100
                    ordered_item_list.append([dic["MCNUGGETS"][10], multi_qut, quantity])
                # Additional items follow similar structure...
        
        # Error handling for invalid inputs
        else:
            print("Error: Please choose from the given options")
            exit_3 = input("Enter [ 'e' ] to exit or ['n'] to retry: ")
            if exit_3 == "e":
                break
        
        # Option to reorder or exit
        reorder = input("Anything else? Type [y] to continue or [n] to exit: ")
        if reorder == "n":
            break

    # Bill generation process
    print("-" * 70)
    v = 0
    print("Your Bill".title())
    for index, item in enumerate(ordered_item_list):
        name = item[0]
        value = item[1]
        quantity = item[2]
        print("-" * 70)
        print(f"{index}: '{name}': (QTY:) {quantity}: AMOUNT: '{value}'")
        print("-" * 70)
        v += value
    
    if v == 0:
        print("Your bill is empty")
    else:
        print("Sub Total: ", v)
        print(f"Adding GST [18%] on {v}")
        Gst = v + 180
        print(f"Your Total Bill is: [{Gst}]")
        print("-" * 70)
        print("Thank you for visiting".title())

# Run the McDonald's Ordering System
Mcdonals_ordering_system()
