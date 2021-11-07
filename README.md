const description= document.querySelectorAll(".temperature-description p")
const temperature= document.querySelectorAll(".temperature-value p")
const locationElement= document.querySelectorAll(".location p")

const weather={
   temperature: {
       value:28,
       unit:"Celsius",
   },

   description:"Sunny",
   city:"London",
   country:"GB"
};

temperature.innerHTML='${weather.temperature.value}'

description.innerHTML= weather.description;

location.innerHTML='${weather.city},${weather.country}'

if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(setPosition);
  } else {
    x.innerHTML = "Geolocation is not supported by this browser.";
  }

function setPosition(position){
    let latitude=position.coords.latitude;
    let longitude=position.coords.longitude;
    getWeather(latitude,longitude);
}
const KELVIN=273;
const KEY = "ed735048eebb35ae81fada4ac3232104";

function getWeather(latitude, longitude){
    let api ='http://api.openweathermap.org/data/2.5/weather?lat={latitude}&lon={longitude}&appid={ed735048eebb35ae81fada4ac3232104}';
}

fetch('http://api.openweathermap.org/data/2.5/weather?lat={latitude}&lon={longitude}&appid={ed735048eebb35ae81fada4ac3232104}')
.then(function(response)
{
    let data= response.json();
    return data;
})
.then(function(data){
    weather.temperature=data.temperature;
    weather.description= data.weather.description;
    weather.city=data.name;
    weather.country=data.country;
}).then(function(){
    displayWeather();
});

function displayWeather()
    {
        temperature.innerHTML='${weather.temperature.value}'
        description.innerHTML=weather.description;
        location.innerHTML='${weather.city},${weather.country}'
    };

