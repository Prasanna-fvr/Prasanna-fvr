import requests
import json

OpenWeatherMap API endpoint
API_ENDPOINT = "(link unavailable)"

Your OpenWeatherMap API key
API_KEY = "YOUR_API_KEY_HERE"

def get_weather(city):
    # Set API parameters
    params = {
        "q": city,
        "units": "metric",
        "appid": API_KEY
    }

    # Send GET request to API
    response = requests.get(API_ENDPOINT, params=params)

    # Check if response was successful
    if response.status_code == 200:
        # Parse JSON response
        weather_data = response.json()

        # Extract relevant weather data
        temperature = weather_data["main"]["temp"]
        humidity = weather_data["main"]["humidity"]
        weather_description = weather_data["weather"][0]["description"]

        # Print weather data
        print(f"Weather in {city}:")
        print(f"Temperature: {temperature}°C")
        print(f"Humidity: {humidity}%")
        print(f"Description: {weather_description}")
    else:
        print(f"Error: {response.status_code}")

def main():
    city = input("Enter city name: ")
    get_weather(city)

if __name__ == "__main__":
    main()
```
