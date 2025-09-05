from http.client import responses

import requests

def get_weather(city, api_key):
    url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"
    response = requests.get(url)
    if response.ok:
        data = response.json()
        temperature = data['main']['temp']
        pressure = data['main']['pressure']
        humidity = data['main']['humidity']
        weather_description = data['weather'][0]['description']
        print(f"погода в {city}:{temperature}°C, {pressure} гПа, {humidity}%, {weather_description.capitalize()}")
    else:
        print("ошибка", response.status_code)
    if __name__ == "__main__":
        city = "Тверь"
        api_key = "КЛЮЧ" 
        get_weather(city, api_key)
