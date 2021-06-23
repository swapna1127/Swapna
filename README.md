import requests
from datetime import datetime
 
api_key='82f01708b25fb77331b56f4d607ff6ae'
location=input("Enter the city name:")
 
complete_api_link='http://api.openweathermap.org/data/2.5/weather?q=guntur&appid=82f01708b25fb77331b56f4d607ff6ae'
api_link=requests.get(complete_api_link)
api_data=api_link.json()
 
 
temp_city=((api_data['main']['temp'])-273.15)
weather_desc=api_data['weather'][0]['description']
hmdt=api_data['main']['humidity']
wind_speed=api_data['wind']['speed']
datetime=datetime.now().strftime("%d %b %Y | %I:%M:%S %p")
 
print("------------------------------------------------------------------")
print("weather stats for -{} || {} ".format(location.upper(),datetime))
print("-------------------------------------------------------------------")
print("current temperature is:{:.2f} deg C".format(temp_city))
print("current weather desc:", weather_desc)
print("current humidity: ",hmdt,'%')
print("current wind speed:",wind_speed,'kmph')
