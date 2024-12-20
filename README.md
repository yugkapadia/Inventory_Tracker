# Inventory Tracker

# Initialize an empty inventory dictionary
inventory = {}

def add_item(name, quantity):
    if name in inventory:
        inventory[name] += quantity
    else:
        inventory[name] = quantity
    print(f"Added {quantity} {name}(s) to the inventory.")

def remove_item(name, quantity):
    if name in inventory and inventory[name] >= quantity:
        inventory[name] -= quantity
        if inventory[name] == 0:
            del inventory[name]
        print(f"Removed {quantity} {name}(s) from the inventory.")
    else:
        print("Not enough items to remove or item not found.")

def view_inventory():
    print("\nCurrent Inventory:")
    if not inventory:
        print("The inventory is empty.")
    else:
        for name, quantity in inventory.items():
            print(f"- {name}: {quantity}")

def get_user_choice():
    print("\nInventory Menu:")
    print("1. Add Item")
    print("2. Remove Item")
    print("3. View Inventory")
    print("4. Exit")
    while True:
        try:
            choice = int(input("Choose an option (1-4): "))
            if choice in [1, 2, 3, 4]:
                return choice
            else:
                print("Invalid choice. Please enter a number between 1 and 4.")
        except ValueError:
            print("Invalid input. Please enter a valid number.")

# Example Usage
while True:
    choice = get_user_choice()
    if choice == 1:
        item_name = input("Enter item name: ")
        while True:
            try:
                item_quantity = int(input("Enter quantity: "))
                break
            except ValueError:
                print("Invalid input. Please enter a valid number.")
        add_item(item_name, item_quantity)
    elif choice == 2:
        item_name = input("Enter item name: ")
        while True:
            try:
                item_quantity = int(input("Enter quantity: "))
                break
            except ValueError:
                print("Invalid input. Please enter a valid number.")
        remove_item(item_name, item_quantity)
    elif choice == 3:
        view_inventory()
    elif choice == 4:
        print("Exiting inventory tracker. Goodbye!")
        break
