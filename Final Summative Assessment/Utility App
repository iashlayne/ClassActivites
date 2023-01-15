# Vending Machine program
# Iashlayne Kane Medina

# Github repository: https://github.com/iashlayne/ClassActivites

# Color Text
# https://ozzmaker.com/add-colour-to-text-in-python/ link of color text (credits)

# Aligned Text
# {:<#} link: https://stackoverflow.com/questions/53908134/what-is-20-format-string-meaning-in-python

# This is a class to hold Snacks data


class ItemSnacks:
    def __init__(self, code, name, price, stock):
        self.code = code
        self.name = name
        self.price = price
        self.stock = stock

    def updateStock(self, stock):
        self.stock = stock

    def purchaseFromStock(self):
        if self.stock == 0:
            # raise not available
            pass
        self.stock -= 1

# This is a class to hold Drinks data


class ItemDrinks:
    def __init__(self, code, name, price, stock):
        self.code = code
        self.name = name
        self.price = price
        self.stock = stock

    def updateStock(self, stock):
        self.stock = stock

    def purchaseFromStock(self):
        if self.stock == 0:
            # raise not available
            pass
        self.stock -= 1

# This class is to hold historical data used for displaying the final receipt


class Reciept:
    def __init__(self):
        self.totalPAid = 0
        self.finalChange = 0
        self.SnackItems = []
        self.DrinkItems = []

    # add purchased Snacks
    def addSnackItem(self, item):
        self.SnackItems.append(item)

    # add purchased drinks
    def addDrinkItem(self, item):
        self.DrinkItems.append(item)

    # calculate total spend
    def addMoney(self, money):
        self.totalPAid += money

    # return the final change
    def setFinalChange(self, change):
        self.finalChange = change

    # check total inserted money
    def getTotalCash(self):
        ret = self.finalChange + self.totalPAid
        return ret

# this function is used for validating the inserted money, only accepts 5,10,20


def inputNumber(message):
    while True:
        try:
            userInput = int(input(message))
            if userInput == 5 or userInput == 10 or userInput == 20 or userInput == 50:
                True
                return userInput
            else:
                raise ValueError  # this will send it to the print message and back to the input option
            break
        except ValueError:
            print(
                "\033[1;31;40m\n""Inserted Note is not accepted, Please insert another note!")

# This is the class used to handle Snacks sales


class VendSnacks:
    def __init__(self):
        self.money = 0
        self.items = []


    # Function to add items to snacks collection
    def addItem(self, item):
        self.items.append(item)

    # function to show items that are available in stock
    def printItems(self):
        print('\033[1;37;40m\nItems Available \n')
        print('\033[1;30;40m*********************************')

        for item in self.items:
            if item.stock == 0:
                self.items.remove(item)
     # {:<#} Forces the area to align to the right of the available space (this is the default for numbers)
        print("\033[1;32;40m""{:<5} {:<15} {:<5} {:<5}".format(
            'Code', 'Name', 'Price', 'Stock'))
        print("{:<5} {:<15} {:<5} {:<5}".format(
            '----', '--------------', '-----', '-----'))
        for item in self.items:
            print("{:<5} {:<15} {:<5} {:<5}".format(
                item.code, item.name, item.price, item.stock))

        print('\033[1;30;40m*********************************\n')

    # Function to check if the item is available
    def availableItem(self, wanted):
        ret = False
        for item in self.items:
            if item.code == wanted:
                ret = True
                break
        return ret

    # call function to check if money is enough, purchase from available stock
    def buyItem(self, item):
        if self.money < item.price:
            print("\033[1;31;40m\n"'You can\'t buy this item. Insert more coins.')
        else:
            self.money -= item.price
            item.purchaseFromStock()
            print('\nItem dispensing...\n')
            print('You got ' + item.name)
            print('Cash remaining: ' + str(self.money))

    # Function to select the item and proceed with insert of Money
    def getItem(self, wanted):
        ret = None
        for item in self.items:
            if item.code == wanted:
                ret = item
                break
        return ret

    # function to get user input for the money Insert - needs to add validation for money not 5,10, 20, or 50
    def insertMoneyForItem(self, item):
        price = item.price
        while self.money < price:
            self.money = self.money + \
                float(inputNumber('\033[1;37;40m\nItem you selected is ' + str(price - self.money) +
                      '. Please insert notes - Accepted notes are AED 5, AED 10, AED 20, AED 50 : '))

    # function to calculate the change from last purchase
    def checkChange(self):
        if self.money > 0:
            print(str(self.money) + " is your Change.")
            # keep record of the money from the drinks sale
            # self.money = 0

        # print('\nThank you, Enjoy your day!\n')
    # function
# This is the class used to handle drinks sales


class VendDrinks:
    def __init__(self, changeMoney):

        self.money = changeMoney
        self.items = []

    # Function to add items to drinks collection
    def addItem(self, item):
        self.items.append(item)

    # function to show items that are available in stock
    def printItems(self):
        print('\033[1;37;40m\nItems Available \n')
        print('\033[1;30;40m*********************************')

        for item in self.items:
            if item.stock == 0:
                self.items.remove(item)
        print("\033[1;36;40m{:<5} {:<15} {:<5} {:<5}".format(
            'Code', 'Name', 'Price', 'Stock'))
        print("{:<5} {:<15} {:<5} {:<5} ".format(
            '----', '--------------', '-----', '-----'))
        for item in self.items:
            print("{:<5} {:<15} {:<5} {:<5} ".format(
                item.code, item.name, item.price, item.stock))

        print('\033[1;30;40m*********************************\n')

    # Function to check the the item is available
    def availableItem(self, wanted):
        ret = False
        for item in self.items:
            if item.code == wanted:
                ret = True
                break
        return ret

    # call function to check if money is enough, purchase from available stock
    def buyItem(self, item):
        if self.money < item.price:
            print("\033[1;31;40m\n"'You can\'t buy this item. Insert more coins.')
        else:
            self.money -= item.price
            item.purchaseFromStock()
            print('\nItem dispensing...\n')
            print('You got ' + item.name)
            print('Cash remaining: ' + str(self.money))

    # Function to select the item and proceed with insert of Money
    def getItem(self, wanted):
        ret = None
        for item in self.items:
            if item.code == wanted:
                ret = item
                break
        return ret

    # function to get user input for the money Insert - needs to add validation for money not 5,10 or 15
    def insertMoneyForItem(self, item):
        price = item.price
        while self.money < price:
            self.money = self.money + \
                float(inputNumber('Item you selected is ' + str(price - self.money) +
                      '. Please insert notes - Accepted notes are AED 5, AED 10, AED 20 : '))

    # function to calculate the change from last purchase
    def checkChange(self):
        if self.money > 0:
            print(str(self.money) + " is your Change.")
            # self.money = 0

        print('\nThank you, Enjoy your day!:)\n')



    # function if the user wants to print the receipt
    # def User_receipt(self):
    #    receipt_User = (input('Do you want to print your receipt? (y/n) '))
    #    if receipt_User[0] == 'y':
    #        print(self.finalReceipt)

    #    else:
    #        print('--------------------------------------------------')
    #        print('**** Thank you for going green ****')
    #        print('--------------------------------------------------')


# Executes the main program
def main():

    # Insert the initial stocks for Snacks
    machine1 = VendSnacks()
    snack1 = ItemSnacks('1A', 'Lays',  1.5,  2)
    snack2 = ItemSnacks('2A', 'Doritos', 2.75,  1)
    snack3 = ItemSnacks('3A', 'Snaku',  2.0,  3)
    snack4 = ItemSnacks('4A', 'Oreo',  1.50, 1)
    snack5 = ItemSnacks('5A', 'Mixed Nuts', 2.25,  3)
    snack6 = ItemSnacks('6A', 'Bugles', 2.0, 3)
    snack7 = ItemSnacks('7A', 'Maltesers', 3.0, 5)
    snack8 = ItemSnacks('8A', 'Pringles', 4.0, 3)
    snack9 = ItemSnacks('9A', 'Croissant', 2.0, 3)
    machine1.addItem(snack1)
    machine1.addItem(snack2)
    machine1.addItem(snack3)
    machine1.addItem(snack4)
    machine1.addItem(snack5)
    machine1.addItem(snack6)
    machine1.addItem(snack7)
    machine1.addItem(snack8)
    machine1.addItem(snack9)
    # Insert the initial stocks for drinks
    machine2 = VendDrinks(changeMoney=0)
    drinks1 = ItemDrinks('1B', 'Coca-Cola',  1.5,  2)
    drinks2 = ItemDrinks('2B', 'Fanta', 1.5,  2)
    drinks3 = ItemDrinks('3B', 'Sprite',  1.5,  3)
    drinks4 = ItemDrinks('4B', 'Water',  1.0, 5)
    drinks5 = ItemDrinks('5B', 'Sparkling Water',  2.25, 2)
    drinks6 = ItemDrinks('6B', 'Chocolate Milk', 1.75,  2)
    drinks7 = ItemDrinks('7B', 'Iced Coffee', 1.25,  2)
    drinks8 = ItemDrinks('8B', 'Apple Juice', 1.25,  3)
    drinks9 = ItemDrinks('9B', 'Orange Juice', 1.5,  3)
    machine2.addItem(drinks1)
    machine2.addItem(drinks2)
    machine2.addItem(drinks3)
    machine2.addItem(drinks4)
    machine2.addItem(drinks5)
    machine2.addItem(drinks6)
    machine2.addItem(drinks7)
    machine2.addItem(drinks8)
    machine2.addItem(drinks9)

    # create an instance of the receipt object
    receipt1 = Reciept()

    # print the title of the program
    print("\033[1;35;40m\n"'\n******************************\n Welcome to my Vending Machine\n\n    Iashlayne Kane Medina     \n******************************')
    # print('Iashlayne Kane Medina')

    contBuy = True
    while contBuy == True:
        machine1.printItems()
        selected = input(
            "\033[1;37;40m\n"'Select Snacks by inputting the Item Code: ').upper()
        if machine1.availableItem(selected):
            item = machine1.getItem(selected)

            machine1.insertMoneyForItem(item)
            machine1.buyItem(item)
            receipt1.addMoney(item.price)
            receipt1.addSnackItem(item)

            a = input('Do you want to buy something else? (y/n): ').lower()
            if a == 'n':
                # contBuy = False
                machine1.checkChange()
                b = input(
                    '\nHow about some drinks with your snacks? (y/n)').lower()
                if b == 'n':
                    contBuy = False
                    print('\nThank you, Enjoy your day!:)\n')

                    g = input(
                        'Do you want to print your receipt? (y/n) ').lower()
                    if g == 'n':
                        print('\033[1;30;40m--------------------------------------------------')
                        print('\033[1;32;40m     **** Thank you for going green ****        ')
                        print('\033[1;30;40m--------------------------------------------------')
                    else:
                        print('Here is your receipt.')

                        # print final receipt

                        receipt1.setFinalChange(machine1.money)
                        print("\033[1;33;40m\n"
                              '\n***************************\nPurchased Snacks are:\n===========================')
                        print("{:<5} {:<15} {:<5}".format(
                            'Code', 'Name', 'Price',))
                        print("{:<5} {:<15} {:<5}".format(
                            '----', '--------------', '-----',))
                        for item in receipt1.SnackItems:
                            print("{:<5} {:<15} {:<5}".format(
                                item.code, item.name, item.price))
                        print(
                            '\nTotal Paid: ' + str(receipt1.totalPAid + receipt1.finalChange) + ' AED')
                        print('\nTotal Bill: ' +
                              str(receipt1.totalPAid) + ' AED')
                        print('\nChange: ' +
                              str(receipt1.finalChange) + ' AED\n***************************')
                else:
                    # finalMoney = machine1.money
                    contBuyDrinks = True
                    machine2.money = machine1.money
                    while contBuyDrinks == True:
                        # machine2.money = finalMoney
                        machine2.printItems()
                        selectedDrink = input("\033[1;37;40m\n"
                                              'Select Drinks by inputting the Item Code: ').upper()
                        if machine2.availableItem(selectedDrink):
                            item2 = machine2.getItem(selectedDrink)

                            machine2.insertMoneyForItem(item2)
                            machine2.buyItem(item2)
                            receipt1.addMoney(item2.price)
                            receipt1.addDrinkItem(item2)
                            d = input(
                                'Do you want to buy more Drinks? (y/n)').lower()
                            if d == 'n':
                                contBuy = False
                                contBuyDrinks = False
                                machine2.checkChange()

                                g = input(
                                    'Do you want to print your receipt? (y/n) ').lower()
                                if g == 'n':
                                    print(
                                        '\033[1;30;40m--------------------------------------------------')
                                    print(
                                        '\033[1;32;40m      **** Thank you for going green ****        ')
                                    print(
                                        '\033[1;30;40m--------------------------------------------------')
                                else:
                                    print('Here is your receipt.')
                                # print final reciept
                                    receipt1.setFinalChange(machine2.money)
                                    print("\033[1;33;40m\n"
                                          '\n***************************\nPurchased Snacks are:\n===========================')
                                    print("{:<5} {:<15} {:<5}".format(
                                        'Code', 'Name', 'Price'))
                                    print("{:<5} {:<15} {:<5}".format(
                                        '----', '--------------', '-----'))
                                    for item in receipt1.SnackItems:
                                        print("{:<5} {:<15} {:<5}".format(
                                            item.code, item.name, item.price))
                                    print(
                                        '\nPurchased Drinks are:\n===========================')
                                    print("{:<5} {:<15} {:<5}".format(
                                        'Code', 'Name', 'Price'))
                                    print("{:<5} {:<15} {:<5}".format(
                                        '----', '--------------', '-----'))
                                    for item in receipt1.DrinkItems:
                                        print("{:<5} {:<15} {:<5}".format(
                                            item.code, item.name, item.price))
                                    print(
                                        '\nTotal Paid: ' + str(receipt1.totalPAid + receipt1.finalChange) + ' AED')
                                    print('\nTotal Bill: ' +
                                          str(receipt1.totalPAid) + ' AED')
                                    print('\nChange: ' +
                                          str(receipt1.finalChange) + ' AED\n***************************')

                            else:
                                # machine2.money = finalMoney
                                continue
                        else:
                            print(
                                "\033[1;31;40m\n"'Item not available. Select another Drink.')
                            continue

            else:
                continue

        else:
            print("\033[1;31;40m\n"'Item not available. Select another item.')
            continue


main()

# End of Vending Machine

