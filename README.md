# -AI-
スマートホームは、エッジAIを活用して家電機器をインテリジェントに制御し、ユーザーの生活パターンに合わせて自動的に動作を最適化することで、利便性の向上と省エネを実現します。
import random
import time

class SmartHome:
    def __init__(self):
        self.temperature = 20  # Initial temperature in Celsius
        self.lights_on = False
        self.user_active = True  # User is active in the house
    
    def simulate_sensor_data(self):
        """Simulate changes in environment and user activity."""
        self.temperature += random.uniform(-0.5, 0.5)  # Simulate natural temperature fluctuation
        self.user_active = random.choice([True, False])  # Simulate user activity

    def adjust_temperature(self):
        """Adjust temperature to save energy and maintain comfort."""
        if self.user_active and self.temperature < 19:
            print("Heating on to increase temperature for comfort.")
            self.temperature += 1
        elif not self.user_active and self.temperature > 22:
            print("Cooling on to reduce temperature for energy saving.")
            self.temperature -= 1

    def adjust_lights(self):
        """Automatically turn lights on/off based on user activity."""
        if self.user_active and not self.lights_on:
            print("Turning lights on as user is active.")
            self.lights_on = True
        elif not self.user_active and self.lights_on:
            print("Turning lights off to save energy as user is inactive.")
            self.lights_on = False

    def run_simulation(self, duration=10):
        """Run the smart home simulation for a specified duration in seconds."""
        for _ in range(duration):
            self.simulate_sensor_data()
            self.adjust_temperature()
            self.adjust_lights()
            time.sleep(1)  # Simulate one second of real time

if __name__ == "__main__":
    smart_home = SmartHome()
    print("Starting Smart Home Simulation...")
    smart_home.run_simulation(duration=10)
    print("Simulation ended.")
