<template>
    <div id="app" :class="typeof weather.main != 'undefined' && weather.main.temp > 15  ? 'hot' : ''  ">
        <main>
            <div class="search">
              <input tupe="text" class="serch-bar" placeholder="Search..." v-model="query"  @keypress="fetchWeather" />
            </div>
            <div v-if="typeof weather.main != 'undefined'">
                  <div class="weather">
                <div class="location">
                     {{weather.name}},{{weather.sys.country}}
                </div>
                <!-- <div class="date">
                    Monday 20 March 2022
                </div> -->
                <div class="temp">
                    {{Math.round(weather.main.temp)}}°c
                </div>
                <div class="weather-status">{{weather.weather[0].main}}</div>
            </div>
            </div>
        </main>
    </div>
</template>

<script>
  export default{
     name: 'App',
      data(){
          return{
            api_key: '07458d33e7c7f44cfb1b539d087a2efe',
            url: `https://api.openweathermap.org/data/2.5/`,
            query:'',
            weather:{}
        }
      },
      methods:{
          fetchWeather(e){
              if(e.key == 'Enter'){
                  fetch(`${this.url}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
                  .then(res =>{
                      return res.json();
                  }).then(this.setResult);
              }
          },
          setResult(result){
              this.weather = result;
              this.query = ''
          }
      }
  }
</script>

<style>
*{
  margin: 0px;
  padding: 0px;
}
#app {
  background-image: url('./assets/freeze.jpg');
  background-size: cover;
  background-position: center;
  transition: 0.4s;
  
}

#app.hot{
  background-image: url('./assets/warm.jpg');
}



main{
  height: 100vh;
  background-image: linear-gradient(to bottom,rgba(0,0,0,0.25),rgba(0,0,0,0.75));
  padding-left: 500px;
}
.search{
  padding: 50px;
}
input{
  max-width: 500px;
  padding: 25px;
  font-size: 30px;
  display: block;
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 0px 20px 0px 20px;
  transition: 0.5s;
  box-shadow: 5px 5px 5px rgb(167, 140, 140);
}

input:focus{
      border-radius: 20px 0px 20px 0px;
      box-shadow: 10px 10px 10px rgb(206, 192, 192);

}

.location{
  color: white;
  font-size: 70px;
  font-weight: 500px;
  text-align: center;
  max-width: 500px;
  text-shadow:
  1px 1px 1px grey,
  1px 2px 1px grey,
  1px 3px 1px grey,
  1px 4px 1px grey,
  1px 5px 1px grey,
  1px 6px 1px grey,
  1px 7px 1px grey,
  1px 8px 1px grey,
  1px 9px 1px grey,
  1px 10px 1px grey,
  1px 16px 6px rgba(16, 16, 16, 0.4),
  1px 22px 10px rgba(16, 16, 16, 0.2),
  1px 25px 40px rgba(16, 16, 16, 0.2),
  1px 30px 60px rgba(126, 95, 95, 0.4);
}
.date{
  color: white;
  font-size: 30px;
  font-weight: 500px;
  text-align: center;
  margin-top: 10px;
  max-width: 500px;
  text-shadow:
  1px 1px 1px grey,
  1px 2px 1px grey,
  1px 3px 1px grey,
  1px 4px 1px grey,
  1px 5px 1px grey,
  1px 6px 1px grey,
  1px 7px 1px grey,
  1px 8px 1px grey,
  1px 9px 1px grey,
  1px 10px 1px grey,
  1px 16px 6px rgba(16, 16, 16, 0.4),
  1px 22px 10px rgba(16, 16, 16, 0.2),
  1px 25px 40px rgba(16, 16, 16, 0.2),
  1px 30px 60px rgba(126, 95, 95, 0.4);
}
.weather .temp{
  color: white;
  font-size: 130px;
  font-weight: 500px;
  text-align: center;
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 30px;
  max-width: 500px;
  margin-top: 20px;
  padding: 10px;
  text-shadow:
  1px 1px 1px grey,
  1px 2px 1px grey,
  1px 3px 1px grey,
  1px 4px 1px grey,
  1px 5px 1px grey,
  1px 6px 1px grey,
  1px 7px 1px grey,
  1px 8px 1px grey,
  1px 9px 1px grey,
  1px 10px 1px grey,
  1px 16px 6px rgba(16, 16, 16, 0.4),
  1px 22px 10px rgba(16, 16, 16, 0.2),
  1px 25px 40px rgba(16, 16, 16, 0.2),
  1px 30px 60px rgba(126, 95, 95, 0.4);
  box-shadow: 1px 1px 1px grey,
  1px 2px 1px grey,
  1px 3px 1px grey,
  1px 4px 1px grey,
  1px 5px 1px grey,
  1px 6px 1px grey,
  1px 7px 1px grey,
  1px 8px 1px grey,
  1px 9px 1px grey,
  1px 10px 1px grey,
  1px 16px 6px rgba(16, 16, 16, 0.4),
  1px 22px 10px rgba(16, 16, 16, 0.2),
  1px 25px 40px rgba(16, 16, 16, 0.2),
  1px 30px 60px rgba(126, 95, 95, 0.4);;
}
.weather-status{
  color: white;
  font-size: 90px;
  font-weight: 500px;
  text-align: center;
  max-width: 500px;
  text-shadow:
  1px 1px 1px grey,
  1px 2px 1px grey,
  1px 3px 1px grey,
  1px 4px 1px grey,
  1px 5px 1px grey,
  1px 6px 1px grey,
  1px 7px 1px grey,
  1px 8px 1px grey,
  1px 9px 1px grey,
  1px 10px 1px grey,
  1px 16px 6px rgba(16, 16, 16, 0.4),
  1px 22px 10px rgba(16, 16, 16, 0.2),
  1px 25px 40px rgba(16, 16, 16, 0.2),
  1px 30px 60px rgba(126, 95, 95, 0.4);
}
</style>
