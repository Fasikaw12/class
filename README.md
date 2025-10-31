# Parent Class
class Device:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    def device_info(self):
        return f"Device: {self.brand} {self.model}"


# Child Class (inherits from Device)
class Smartphone(Device):
    def __init__(self, brand, model, battery_life, storage):
        # Call the parent constructor
        super().__init__(brand, model)
        self.__battery_life = battery_life  # Private attribute (Encapsulation)
        self.storage = storage

    # Method to make a call
    def make_call(self, contact_name):
        print(f"📞 Calling {contact_name} from {self.brand} {self.model}...")

    # Getter method for encapsulated attribute
    def get_battery_life(self):
        return self.__battery_life

    # Setter method for encapsulated attribute
    def set_battery_life(self, new_battery_life):
        if new_battery_life > 0:
            self.__battery_life = new_battery_life
        else:
            print("❌ Battery life must be positive!")

    def device_info(self):
        # Overriding parent method (Polymorphism)
        return f"Smartphone: {self.brand} {self.model} | Battery: {self.__battery_life} hrs | Storage: {self.storage} GB"


# Create objects
phone1 = Smartphone("Samsung", "Galaxy S24", 24, 256)
phone2 = Smartphone("Apple", "iPhone 15", 20, 512)

# Display info
print(phone1.device_info())
print(phone2.device_info())

# Call methods
phone1.make_call("Alice")

# Access encapsulated data safely
print("Battery life:", phone1.get_battery_life())
phone1.set_battery_life(30)
print("Updated battery life:", phone1.get_battery_life())
