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

# Using Class to Complete the Exercise (Updated in 23/12/2023)

Collapse the chanllenge into small blocks:
1. Define a menu class to store the coffee menu, including type, ingrediant, and cost of the coffee, let the user insert their order, check whether their order is in the menu, return the drink if it is available.
2. Define resources class to check whether the resources are sufficient, return `True` if there are enough ingredients, return `False` if not.
3. Define a payment class to process the payment if the coffee can be made, let the user insert their coins, check whether they have inserted enough money, offer a change if they have inserted too much money, and cancel the order if the money is not enough. Add the successful payment to the profit.
4. Define a coffee maker method to make the coffee if the payment is successfully paid, and deduct the relevant ingredients from the resources.
5. Remember the secret key words `off` and `report` that mentioned above.

**The code is:**
```py
# Define a Menu class:
class Menu:
    def __init__(self):
        self.m_menu = {}

    def add_coffee(self, name, ingredients, cost, product):
        self.m_menu[name] = {"ingredients": ingredients, "cost": cost, "product": product}

    def list_item(self):
        options = ""
        for coffee in self.m_menu:
            options += coffee + "/"
        return options

    def check_item(self, order):
        for coffee in self.m_menu:
            if order == coffee:
                return self.m_menu[coffee]
        print(f"Sorry, the {order} is not available.")


# Define a Resources class:
class Resources:
    def __init__(self):
        self.m_resources = {
            "water": 300,
            "milk": 200,
            "coffee": 100,
        }
        self.m_unit = {
            "water": "ml",
            "milk": "ml",
            "coffee": "g",
        }

    def report(self):
        for ingredient in self.m_resources:
            print(f"{ingredient}: {self.m_resources[ingredient]}{self.m_unit[ingredient]}")

    def is_enough(self, order):
        can_make = True
        for ingredient in self.m_resources:
            if order["ingredients"][ingredient] > self.m_resources[ingredient]:
                print(f"Sorry, the {ingredient} is not enough.")
                can_make = False
        return can_make

    def coffee_maker(self, order):
        print(f"This is your {order_name} {order["product"]}, please enjoy!")
        for ingredient in self.m_resources:
            self.m_resources[ingredient] -= order["ingredients"][ingredient]


class Payment:
    def __init__(self):
        self.m_profit = 0
        self.m_money_inserted = 0
        self.m_coin_values = {
            "quarters": 0.25,
            "dimes": 0.01,
            "nickles": 0.05,
            "pennies": 0.01,
        }

    def process_coins(self, order):
        print(f"The price is ${order["cost"]}, please insert coins:")
        for coin in self.m_coin_values:
            self.m_money_inserted += float(input(f"How many {coin}?")) * self.m_coin_values[coin]
        if self.m_money_inserted < order["cost"]:
            print(f"The money you inserted is {self.m_money_inserted}, that's not enough money. Money refunded.")
            return False
        else:
            print(f"Here is ${round(self.m_money_inserted - order["cost"], 2)} in change.")
            self.m_profit += order["cost"]
            return True

    def report(self):
        print(f"Money: ${self.m_profit}")


coffee_menu = Menu()
coffee_menu.add_coffee("espresso", {"water": 50, "coffee": 18, "milk": 0}, 1.5, "☕️")
coffee_menu.add_coffee("latte", {"water": 200, "coffee": 24, "milk": 150}, 2.5, "🥤️")
coffee_menu.add_coffee("cappuccino", {"water": 250, "coffee": 24, "milk": 100}, 3, "🍹️")
list_coffee = coffee_menu.list_item()

check_resources = Resources()

payment = Payment()


is_on = True
while is_on:
    order_name = input("What would you like?" + " " + list_coffee + ": ").lower()
    if order_name == "report":
        check_resources.report()
        payment.report()
    elif order_name == "off":
        is_on = False
        print("The machine is logged out.")
    else:
        check_order = coffee_menu.check_item(order_name)
        if check_order != None:
            is_sufficient = check_resources.is_enough(check_order)
            if is_sufficient:
                process_payment = payment.process_coins(check_order)
                if process_payment:
                    check_resources.coffee_maker(check_order)
```

**Run the code:**
```py
What would you like? espresso/latte/cappuccino/: report
water: 300ml
milk: 200ml
coffee: 100g
Money: $0
What would you like? espresso/latte/cappuccino/: latte
The price is $2.5, please insert coins:
How many quarters?9
How many dimes?9
How many nickles?9
How many pennies?9
Here is $0.38 in change.
This is your latte 🥤️, please enjoy!
What would you like? espresso/latte/cappuccino/: cappuccino
Sorry, the water is not enough.
Sorry, the milk is not enough.
What would you like? espresso/latte/cappuccino/: espresso
The price is $1.5, please insert coins:
How many quarters?12
How many dimes?12
How many nickles?12
How many pennies?12
Here is $5.22 in change.
This is your espresso ☕️, please enjoy!
What would you like? espresso/latte/cappuccino/: report
water: 50ml
milk: 50ml
coffee: 58g
Money: $4.0
What would you like? espresso/latte/cappuccino/: off
The machine is logged out.
```

_**Issues Recorded:**_

_**There are so many issues when I was writing the code, this is a difficult challenge for me, I recorded some of the issues below:**_

_**1. For loop will end immediately after `return` is excuted:**_
```py
 def check_item(self, order):
        for coffee in self.m_menu:
            if order == coffee:
                return self.m_menu[coffee]
            else:
                return "not available"
```
_**When I frist wrote the `check_item` methods, I set two `return` output under a if statement within a for loop, this caused I can only get the right output when I insert the first item in the `self.m_menu`.**_     
_**For example, the items in the `self.m_menu` are `espresso/latte/cappuccino/`, if I input `latte`, the method will loop the `espresso` first, so the `order == coffee` is not matched, the `not available` will be returned, once the `return` is completed, the for loop will end, I will not get the output I want.**_

_**2. Try to put the constructors you want to call into one class:**_  
_**When I collapsed the exercise into small blocks for the first time, I wanted to build the resouces class and the coffee maker class separately, however, I found it was hard to deduct the resources I already used to make coffee if I put them into two classes, so I adjusted my plan in the end, and in this way, the code performed better.**_


