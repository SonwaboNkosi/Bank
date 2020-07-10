# Bank
A banking system 
import random


class Bank:
    cards = dict()
    state = 0
    curr_card = 0
    curr_pin = 0

    def main_menu(self):
        global inp
        if self.state == 0:
            print("1. Create an account\n2. Log into account\n0. Exit\n""")
        else:
            print("1. Balance\n2. Log out\n0. Exit\n""")
        inp = int(input())

    def create_acc(self):
        num = "400000" + str(random.random())[2: 12]
        pin = str(random.random())[2: 6]
        self.cards[num] = {pin: 0}
        print("Your card has been created")
        print("Your card number:")
        print(num)
        print("Your card PIN:")
        print(pin)
        print()

    def login(self):
        num = input("Enter your card number:")
        pin = input("Enter your PIN:")
        if num not in self.cards or pin not in self.cards[num]:
            print("Wrong card number or PIN!\n")
        else:
            print("You have successfully logged in!\n")
            self.state = 1
            self.curr_card = num
            self.curr_pin = pin

    def balance(self):
        print("\nBalance: {}\n".format(self.cards[self.curr_card][self.curr_pin]))

    def logout(self):
        print("\nYou have successfully logged out!\n")
        self.state = 0
        self.curr_card = 0
        self.curr_pin = 0


bank = Bank()
inp = -1
while inp != 0:
    bank.main_menu()
    if inp == 1 and bank.state == 0:
        bank.create_acc()
    elif inp == 2 and bank.state == 0:
        bank.login()
    elif inp == 1 and bank.state == 1:
        bank.balance()
    elif inp == 2 and bank.state == 1:
        bank.logout()
print("\nBye!")

