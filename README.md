# Flight Management System

class Flight:
    
    # Constructor
    def __init__(self, flight_no, source, destination, base_fare):
        self.flight_no = flight_no
        self.source = source
        self.destination = destination
        self.base_fare = base_fare

    # flight information
    def get_flight_info(self):
        return f"Flight No: {self.flight_no}, Source: {self.source}, Destination: {self.destination}"

    # Method to calculate fare
    def calculate_fare(self, passenger_count, discount_percent=0):
        total_fare = self.base_fare * passenger_count
        
        if discount_percent > 0:
            total_fare = total_fare - (total_fare * discount_percent / 100)
        
        return total_fare

    # e) route information
    # If only destination is given → update destination
    # If both source and destination are given → update both
    def update_route(self, source=None, destination=None):
        if source is not None and destination is not None:
            self.source = source
            self.destination = destination
        elif destination is not None:
            self.destination = destination


# Flight object
flight1 = Flight("AI203", "Bangalore", "Delhi", 4500)

# Display flight info
print("Original Flight Info:")
print(flight1.get_flight_info())

# Calculate fare without discount
fare1 = flight1.calculate_fare(3)
print("Total Fare (No Discount):", fare1)

# Calculate fare with discount
fare2 = flight1.calculate_fare(3, 10)
print("Total Fare (With 10% Discount):", fare2)

# Update only destination
flight1.update_route(destination="Mumbai")
print("\nAfter Updating Only Destination:")
print(flight1.get_flight_info())

# Update both source and destination
flight1.update_route("Chennai", "Kolkata")
print("\nAfter Updating Source and Destination:")
print(flight1.get_flight_info())
