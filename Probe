import os, random, time
class Game:
    def __init__(self):
        self.balance = 0
        self.diamonds = 0

    def clear_screen(self):
        # Für Linux/Unix-Umgebungen
        os.system('clear')  # Auf Linux wird `clear` verwendet
        # Alternativ könnte auch `print("\033[H\033[J", end="")` funktionieren

    def gambling(self):
        self.clear_screen()
        while True:
            self.clear_screen()
            print("\n--- Hauptmenü ---")
            print("1 = The Bank")
            print("2 = Slot Machine")
            print("3 = Store")
            print("4 = Exit")
            gam_auswahl = int(input("Was möchtest du tun? (1-4): "))
            if gam_auswahl == 1:
                self.balance = self.bank(self.balance)
            elif gam_auswahl == 2:
                self.slot_machine(self.balance)
            elif gam_auswahl == 3:
                self.balance = self.store(self.balance)
            elif gam_auswahl == 4:
                print("Goodbye!")
                break
            else:
                print("Ungültige Auswahl! Bitte versuche es noch einmal.")

    def bank(self, balance):
        is_running = True

        def deposit():
            self.clear_screen()
            amount = float(input("Enter an amount to deposit: "))
            if amount < 0:
                print("Ungültige Eingabe!")
                return 0
            return amount

        def withdraw(balance):
            self.clear_screen()
            amount = float(input("Enter an amount to withdraw: "))
            if amount > balance:
                print("Not enough balance!")
                return 0
            if balance != amount > 1.5:
                taxes = amount * 0.10
            else:
                taxes = 0
            print(f"Taxes: {taxes:.2f}")
            return balance - (amount + taxes)

        def show_balance(balance):
            self.clear_screen()
            print(f"You have ${balance:.2f}")

        while is_running:
            self.clear_screen()
            print("1. Show balance\n2. Deposit\n3. Withdraw\n4. Back")
            choice = input("Enter your choice (1-4): ")
            if choice == "1":
                show_balance(balance)
            elif choice == "2":
                balance += deposit()
            elif choice == "3":
                balance = withdraw(balance)
            elif choice == "4":
                is_running = False
            else:
                print("Invalid choice.")
        return balance

    def slot_machine(self, balance):
        def spin_raw():
            symbols = ["🏅", "🌟", "👑"]
            return [random.choice(symbols) for _ in range(3)]

        def print_raw(raw):
            self.clear_screen()
            print("*******")
            print("  |  ".join(raw))
            print("*******")

        def get_payout(raw, bet):
            if raw[0] == raw[1] == raw[2]:
                if raw[0] == "🏅":
                    print(f"You won +${bet * 3}!!")
                    return bet * 3
                elif raw[0] == "🌟":
                    print(f"You won +${bet * 5}!!")
                    return bet * 5
                elif raw[0] == "👑":
                    print(f"You won +${bet * 7}!!")
                    return bet * 7
            return 0

        while balance > 0:
            self.clear_screen()
            print(f"Current Balance: ${balance}")
            bet = input("How much is your bet?: ")
            if not bet.isdigit() or int(bet) > balance or int(bet) <= 0:
                print("Invalid bet!")
                continue
            bet = int(bet)
            balance -= bet
            raw = spin_raw()
            print("Spinning...\n")
            time.sleep(1)
            print_raw(raw)

            payout = get_payout(raw, bet)
            balance += payout

            if balance > 0:
                play_request = input("Do you want to spin again (N/Y)? ").upper()
                if play_request == "N":
                    break
            else:
                print("You are out of money!")
                break
        print(f"Your final balance is ${balance}")
    
    def store(self, balance):
        while True:
            self.clear_screen()
            print("Store Items:")
            print("1. More Time = $50")
            print("2. MysteryBox = $20")
            print("3. More SlotMachine Luck = $300")
            print("4. Back")
            choice = input("Choose (1-4): ")
            if choice == "1":
                self.diamonds += 1
                print("You bought More Time!")
                time.sleep(20)
            elif choice == "2":
                box = [10, 20, "Nothing", 40, "1 Diamond", "Nothing"]
                result = random.choice(box)
                if isinstance(result, int):
                    balance += result
                    print(f"You got ${result}!")
                elif result == "1 Diamond":
                    self.diamonds += 1
                    print("You got 1 Diamond!")
                else:
                    print("You got NOTHING!")
            elif choice == "3":
                print("You bought More Luck for the Slot Machine!")
            elif choice == "4":
                break
            else:
                print("Invalid choice.")
        return balance

if __name__ == "__main__":
    game = Game()
    game.gambling()
