Here’s a basic Car Showroom Management System in Python, perfect to upload on GitHub as a beginner/intermediate project.

This project includes:

Adding cars to showroom inventory

Viewing available cars

Selling a car

Showing sold cars



---

Car Showroom – Python Code

# car_showroom.py

class Car:
    def __init__(self, car_id, brand, model, price):
        self.car_id = car_id
        self.brand = brand
        self.model = model
        self.price = price
        self.sold = False

    def display(self):
        status = "Sold" if self.sold else "Available"
        print(f"[{self.car_id}] {self.brand} {self.model} - ${self.price} ({status})")


class CarShowroom:
    def __init__(self):
        self.cars = []

    def add_car(self):
        car_id = input("Enter Car ID: ")
        brand = input("Enter Brand: ")
        model = input("Enter Model: ")
        price = float(input("Enter Price: "))
        car = Car(car_id, brand, model, price)
        self.cars.append(car)
        print("Car added to showroom.")

    def view_cars(self, sold=False):
        filtered = [c for c in self.cars if c.sold == sold]
        if not filtered:
            print("No cars to display.")
            return
        for car in filtered:
            car.display()

    def sell_car(self):
        car_id = input("Enter Car ID to sell: ")
        for car in self.cars:
            if car.car_id == car_id and not car.sold:
                car.sold = True
                print(f"{car.brand} {car.model} sold successfully!")
                return
        print("Car not found or already sold.")

    def run(self):
        while True:
            print("\n--- Car Showroom Management ---")
            print("1. Add Car")
            print("2. View Available Cars")
            print("3. Sell Car")
            print("4. View Sold Cars")
            print("5. Exit")
            choice = input("Select an option: ")

            if choice == '1':
                self.add_car()
            elif choice == '2':
                self.view_cars(sold=False)
            elif choice == '3':
                self.sell_car()
            elif choice == '4':
                self.view_cars(sold=True)
            elif choice == '5':
                print("Exiting system.")
                break
            else:
                print("Invalid choice.")


if __name__ == "__main__":
    showroom = CarShowroom()
    showroom.run()
