# Comprehensive Exercise

**Exercise: Coffee Machine**
1. Given the recipe of coffee and the stock material:
```py
coffe_menu = {
    "espresso": {"water": 50, "coffee": 18, "milk": 0, "cost": 1.5, "product": "☕️"},
    "latte": {"water": 200, "coffee": 24, "milk": 150, "cost": 2.5, "product": "🥤️"},
    "cappuccino": {"water": 250, "coffee": 24, "milk": 100, "cost": 3, "product": "🍹️"},
}

resources = {
    "water": 300,
    "milk": 200,
    "coffee": 100,
    "money": 0,
}
```
2. Let the user input what they want to buy.
3. When the user chooses a drink, the program should check if there are enough
resources to make that drink.
4. If there are sufficient resources to make the drink selected, then the program should
prompt the user to insert coins. Remember that quarters = $0.25, dimes = $0.10, nickles = $0.05, pennies = $0.01, calculate the menetary value of the coins inserted.
5. Check that the user has inserted enough money to purchase the drink they selected. E.g Latte cost $2.50, but they only inserted $0.52 then after counting the coins the
program should say `Sorry that's not enough money. Money refunded.` But if the user has inserted enough money, then the cost of the drink gets added to the
machine as the profit. If the user has inserted too much money, the machine should offer change.
6. If the transaction is successful and there are enough resources to make the drink the
user selected, then the ingredients to make the drink should be deducted from the
coffee machine resources, and ask the next user to insert their choices.
7. For maintainers of the coffee machine, they can use `off` or `report` as the secret word to turn off
the machine or to check the stock of resources. Your code should end execution when the maintainers use `off`.

**The code is:**
```py
# Define a coffee menu to store the recipe
coffee_menu = {
    "espresso": {"water": 50, "coffee": 18, "milk": 0, "cost": 1.5, "product": "☕️"},
    "latte": {"water": 200, "coffee": 24, "milk": 150, "cost": 2.5, "product": "🥤️"},
    "cappuccino": {"water": 250, "coffee": 24, "milk": 100, "cost": 3, "product": "🍹️"},
}

resources = {
    "water": 300,
    "milk": 200,
    "coffee": 100,
    "money": 0,
}
# Define a function to update the resources
def current_resources(resources, coffee_menu, order):
    resources = {
        "water": resources["water"] - coffee_menu[order]["water"],
        "coffee": resources["coffee"] - coffee_menu[order]["coffee"],
        "milk": resources["milk"] - coffee_menu[order]["milk"],
        "money": resources["money"] + order_cost,
    }
    return resources
def if_resources_sufficient(resources, order):
    insufficient_resources = []
    order_ingrediant = {
        "water": coffee_menu[order]["water"],
        "coffee": coffee_menu[order]["coffee"],
        "milk": coffee_menu[order]["milk"],
    }
    if resources["water"] > order_ingrediant["water"] and resources["coffee"] > order_ingrediant["coffee"]:
        return "yes"
    else:
        for ingrediant in order_ingrediant:
            if resources[ingrediant] < order_ingrediant[ingrediant]:
                insufficient_resources.append(ingrediant)
        return insufficient_resources

# Define a function to check the user have inserted enough money to purchase the drink they selected
def process_coins(order_cost):
    print(f"The cost of your {order} is ${order_cost}. Please insert coins.")
    insert_coins = 0.25 * int(input("How mant quarters?: "))
    insert_coins += 0.1 * int(input("How mant dimes?: "))
    insert_coins += 0.05 * int(input("How mant nickles?: "))
    insert_coins += 0.01 * int(input("How mant pennies?: "))
    insert_coins = round(insert_coins, 2)

    # If the user have inserted too much money, the machine should offer change
    if insert_coins >= order_cost:
        print(f"The coins you inserted are ${insert_coins} in total, here is ${round(insert_coins - order_cost, 2)} in change.\nHere is your {order} {coffee_menu[order]["product"]}. Enjoy!")
        return insert_coins
    else:
        print(f"The coins you inserted are ${insert_coins}, that's not enough money. Money refunded.")
        return None



# The prompt should show again to serve the next customer
should_continue = True
while should_continue:
    # Ask the user what kind of coffee do they want
    order = input("What would you like? (espresso/latte/cappuccino): ")
    # Print the current resource values when enters 'report'
    if order == "report":
        print(f"Water: {resources['water']}ml\nMilk: {resources['milk']}ml\nCoffee: {resources['coffee']}g\nMoney: ${resources['money']}")
    # Turn off the machine by entering 'off' to the prompt
    elif order == "off":
        should_continue = False
        print("The machine has turned off.")
    else:
        # Check whether the resources are sufficient
        check_resources = if_resources_sufficient(resources, order)
        order_cost = coffee_menu[order]["cost"]
        # If the resources are sufficient, the program should prompt the user to insert coins
        if check_resources == "yes":
            # Only if the user have inserted the enough money the cost of drink gets added to the machine
           process_coins(order_cost)
            # When one coffee is done, the ingredients to make the drink should be deducted from the coffee machine resources
           resources = current_resources(resources, coffee_menu, order)
        else:
            print(f"Sorry there is not enough {check_resources}.")
```

**Test the code:**
```py
What would you like? (espresso/latte/cappuccino): latte
The cost of your latte is $2.5. Please insert coins.
How mant quarters?: 7
How mant dimes?: 7
How mant nickles?: 7
How mant pennies?: 7
The coins you inserted are $2.87 in total, here is $0.37 in change.
Here is your latte 🥤️. Enjoy!
What would you like? (espresso/latte/cappuccino): report
Water: 100ml
Milk: 50ml
Coffee: 76g
Money: $2.5
What would you like? (espresso/latte/cappuccino): espresso
The cost of your espresso is $1.5. Please insert coins.
How mant quarters?: 9
How mant dimes?: 9
How mant nickles?: 9
How mant pennies?: 9
The coins you inserted are $3.69 in total, here is $2.19 in change.
Here is your espresso ☕️. Enjoy!
What would you like? (espresso/latte/cappuccino): cappuccino
Sorry there is not enough ['water', 'milk'].
What would you like? (espresso/latte/cappuccino): off
The machine has turned off.
```

# Using Class to Complete the Exercise (updating)

Collapse the chanllenge into small blocks:
1. Define a menu class to store the coffee menu, including type, ingrediant, and cost of the coffee, let the user insert their order, check whether their order is in the menu, return the drink if it is available.
2. Define resources class to check whether the resources are sufficient, return `True` if there are enough ingredients, return `False` if not.
3. Define a payment class to process the payment if the coffee can be made, let the user insert their coins, check whether they have inserted enough money, offer a change if they have inserted too much money, and cancel the order if the money is not enough. Add the successful payment to the profit.
4. Define a coffee maker class to make the coffee if the payment is successfully paid, and deduct the relevant ingredients from the resources.
5. Remember the scerect key words `off` and `report` that mentioned above.

**The code is:**
```py
# Define a Menu class:
class Menu:
    def __init__(self):
        self.m_menu = {} # Define a empty menu to store the added coffee.

    def add_coffee(self, name, ingredients, cost, product): # When call this method and insert the parameter, the menu will update the drink automatically.
        self.m_menu[name] = {"ingredients": ingredients, "cost": cost, "product": product}

    def list_item(self): # List the coffee in the menu in a format.
        list_coffee = ""
        for coffee in self.m_menu:
            list_coffee += coffee + "/"
        return list_coffee

    def check_order(self, order): # Check whether user's order is in the menu.
        for coffee in self.m_menu:
            if order == coffee:
                return "available"
            else:
                return "not available"
    

# Define a Resources class:
class Resources:
    def __init__(self):
        self.m_resources = {
            "water": 300,
            "milk": 200,
            "coffee": 100,
        }

    def is_enough(self, order):
        for ingredient in self.m_resources:
            if order["ingredients"][ingredient] > self.m_resources[ingredient]:
                print(f"Sorry, the {ingredient} is not enough.")
                return False
            else:
                return True
```

