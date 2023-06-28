<template>
  <div class="wather-info">
    <div class="button">
      <button @click="infoDay">день</button>
      <button @click="infoSunday">тиждень</button>
    </div>
    <div class="info-button">
      <div class="info_day_content">
        <div class="info-day" v-show="isOpenDay">
          <p>
            {{ date.getDate() }} {{ months[date.getMonth()] }}
            {{ day[date.getDay()] }}
          </p>
          <p>
            Температура в даний час {{ weatherInfo.data?.current.temp
            }}<sup>o</sup>C
          </p>
          <p>
            Ранок - {{ weatherInfo.data?.daily[0].temp.morn }} <sup>o</sup>C
          </p>
          <p>День - {{ weatherInfo.data?.daily[0].temp.day }} <sup>o</sup>C</p>
          <p>Вечір - {{ weatherInfo.data?.daily[0].temp.eve }} <sup>o</sup>C</p>
          <p>Ніч - {{ weatherInfo.data?.daily[0].temp.night }} <sup>o</sup>C</p>
          <!-- <p>{{weatherInfo.data?.current?.weather[0].icon}}</p> -->
          <!-- <p>{{weatherInfo.data?.daily[0].weather[0].icon}}</p>
        <p>{{weatherInfo.data?.daily[6].weather}}</p> -->
        </div>
      </div>
      <!-- <p>{{ weatherInfo.data?.daily }}</p> -->
      <div class="info-Sunday" v-show="isOpenSunday">
        <div class="sunday-content">
          <p>
            {{
              new Date(
                weatherInfo.data?.daily[0].dt * 1000 -
                  weatherInfo.data?.timezone_offset
              ).getDate()
            }}
          </p>
          <p>
            {{
              months[
                date.getMonth(
                  weatherInfo.data?.daily[0].dt * 1000 -
                    weatherInfo.data?.timezone_offset
                )
              ]
            }}
          </p>
          <p>
            {{
              day[
                new Date(
                  weatherInfo.data?.daily[0].dt * 1000 -
                    weatherInfo.data?.timezone_offset
                ).getDay()
              ]
            }}
          </p>
          <img
            :src="`https://openweathermap.org/img/wn/${weatherInfo.data?.daily[0].weather[0].icon}@2x.png`"
            alt=""
          />
          <div>
            <div>
              <p>мін. {{ weatherInfo.data?.daily[0].temp.min }}</p>
            </div>
            <div>
              <p>макс. {{ weatherInfo.data?.daily[0].temp.max }}</p>
            </div>
          </div>
        </div>
        <div class="sunday-content">
          <p>
            {{
              new Date(
                weatherInfo.data?.daily[1].dt * 1000 -
                  weatherInfo.data?.timezone_offset
              ).getDate()
            }}
          </p>
          <p>
            {{
              months[
                date.getMonth(
                  weatherInfo.data?.daily[1].dt * 1000 -
                    weatherInfo.data?.timezone_offset
                )
              ]
            }}
          </p>
          <p>
            {{
              day[
                new Date(
                  weatherInfo.data?.daily[1].dt * 1000 -
                    weatherInfo.data?.timezone_offset
                ).getDay()
              ]
            }}
          </p>
          <img
            :src="`https://openweathermap.org/img/wn/${weatherInfo.data?.daily[1].weather[0].icon}@2x.png`"
            alt=""
          />
          <v-imgUrl></v-imgUrl>
          <div>
            <div>
              <p>мін. {{ weatherInfo.data?.daily[1].temp.min }}</p>
            </div>
            <div>
              <p>макс. {{ weatherInfo.data?.daily[1].temp.max }}</p>
            </div>
          </div>
        </div>
        <div class="sunday-content">
          <p>
            {{
              new Date(
                weatherInfo.data?.daily[2].dt * 1000 -
                  weatherInfo.data?.timezone_offset
              ).getDate()
            }}
          </p>
          <p>
            {{
              months[
                date.getMonth(
                  weatherInfo.data?.daily[2].dt * 1000 -
                    weatherInfo.data?.timezone_offset
                )
              ]
            }}
          </p>
          <p>
            {{
              day[
                new Date(
                  weatherInfo.data?.daily[2].dt * 1000 -
                    weatherInfo.data?.timezone_offset
                ).getDay()
              ]
            }}
          </p>
          <img
            :src="`https://openweathermap.org/img/wn/${weatherInfo.data?.daily[2].weather[0].icon}@2x.png`"
            alt=""
          />
          <div>
            <div>
              <p>мін. {{ weatherInfo.data?.daily[2].temp.min }}</p>
            </div>
            <div>
              <p>макс. {{ weatherInfo.data?.daily[2].temp.max }}</p>
            </div>
          </div>
        </div>
        <div class="sunday-content">
          <p>
            {{
              new Date(
                weatherInfo.data?.daily[3].dt * 1000 -
                  weatherInfo.data?.timezone_offset
              ).getDate()
            }}
          </p>
          <p>
            {{
              months[
                date.getMonth(
                  weatherInfo.data?.daily[3].dt * 1000 -
                    weatherInfo.data?.timezone_offset
                )
              ]
            }}
          </p>
          <p>
            {{
              day[
                new Date(
                  weatherInfo.data?.daily[3].dt * 1000 -
                    weatherInfo.data?.timezone_offset
                ).getDay()
              ]
            }}
          </p>
          <img
            :src="`https://openweathermap.org/img/wn/${weatherInfo.data?.daily[3].weather[0].icon}@2x.png`"
            alt=""
          />
          <div>
            <div>
              <p>мін. {{ weatherInfo.data?.daily[3].temp.min }}</p>
            </div>
            <div>
              <p>макс. {{ weatherInfo.data?.daily[3].temp.max }}</p>
            </div>
          </div>
        </div>
        <div class="sunday-content">
          <p>
            {{
              new Date(
                weatherInfo.data?.daily[4].dt * 1000 -
                  weatherInfo.data?.timezone_offset
              ).getDate()
            }}
          </p>
          <p>
            {{
              months[
                date.getMonth(
                  weatherInfo.data?.daily[4].dt * 1000 -
                    weatherInfo.data?.timezone_offset
                )
              ]
            }}
          </p>
          <p>
            {{
              day[
                new Date(
                  weatherInfo.data?.daily[4].dt * 1000 -
                    weatherInfo.data?.timezone_offset
                ).getDay()
              ]
            }}
          </p>
          <img
            :src="`https://openweathermap.org/img/wn/${weatherInfo.data?.daily[4].weather[0].icon}@2x.png`"
            alt=""
          />
          <div>
            <div>
              <p>мін. {{ weatherInfo.data?.daily[4].temp.min }}</p>
            </div>
            <div>
              <p>макс. {{ weatherInfo.data?.daily[4].temp.max }}</p>
            </div>
          </div>
        </div>
        <div class="sunday-content">
          <p>
            {{
              new Date(
                weatherInfo.data?.daily[5].dt * 1000 -
                  weatherInfo.data?.timezone_offset
              ).getDate()
            }}
          </p>
          <p>
            {{
              months[
                date.getMonth(
                  weatherInfo.data?.daily[5].dt * 1000 -
                    weatherInfo.data?.timezone_offset
                )
              ]
            }}
          </p>
          <p>
            {{
              day[
                new Date(
                  weatherInfo.data?.daily[5].dt * 1000 -
                    weatherInfo.data?.timezone_offset
                ).getDay()
              ]
            }}
          </p>
          <img
            :src="`https://openweathermap.org/img/wn/${weatherInfo.data?.daily[5].weather[0].icon}@2x.png`"
            alt=""
          />
          <div>
            <div>
              <p>мін. {{ weatherInfo.data?.daily[5].temp.min }}</p>
            </div>
            <div>
              <p>макс. {{ weatherInfo.data?.daily[5].temp.max }}</p>
            </div>
          </div>
        </div>
        <div class="sunday-content">
          <p>
            {{
              new Date(
                weatherInfo.data?.daily[6].dt * 1000 -
                  weatherInfo.data?.timezone_offset
              ).getDate()
            }}
          </p>
          <p>
            {{
              months[
                date.getMonth(
                  weatherInfo.data?.daily[6].dt * 1000 -
                    weatherInfo.data?.timezone_offset
                )
              ]
            }}
          </p>
          <p>
            {{
              day[
                new Date(
                  weatherInfo.data?.daily[6].dt * 1000 -
                    weatherInfo.data?.timezone_offset
                ).getDay()
              ]
            }}
          </p>
          <img
            :src="`https://openweathermap.org/img/wn/${weatherInfo.data?.daily[6].weather[0].icon}@2x.png`"
            alt=""
          />
          <div>
            <div>
              <p>мін. {{ weatherInfo.data?.daily[6].temp.min }}</p>
            </div>
            <div>
              <p>макс. {{ weatherInfo.data?.daily[6].temp.max }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="chart">
      <v-chart :weatherChart="weatherInfo"></v-chart>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import vChart from "./v-chart.vue"
export default {
  name: "v-infoWeather",
  components: {vChart},
  props: { weatherInfo: Object },
  setup() {
    const date = new Date();
    const day = [
      "Неділя",
      "Понеділок",
      "Вівторок",
      "Середа",
      "Четверг",
      "Пятниця",
      "Субота",
    ];
    const months = [
      "Січня",
      "Лютого",
      "Березня",
      "Квітня",
      "Травня",
      "Червня",
      "Липня",
      "Серпня",
      "Вересня",
      "Жовтня",
      "Листопада",
      "Грудня",
    ];
    const imgUrl = "";
    const isOpenDay = ref(true);
    const isOpenSunday = ref(false);
    const dataUrl = ref("");

    function infoDay() {
      isOpenDay.value = true;
      isOpenSunday.value = false;
    }

    function infoSunday() {
      isOpenDay.value = false;
      isOpenSunday.value = true;
    }

    return {
      date,
      day,
      months,
      imgUrl,
      isOpenDay,
      isOpenSunday,
      infoDay,
      infoSunday,
      dataUrl,
    };
  },
};
</script>

<style scoped>
.info-Sunday {
  display: flex;
  justify-content: center;
}
.sunday-content {
  border: 2px solid green;
  background: rgb(80, 137, 250);
  padding: 5px;
  margin: 5px;
}
.button button {
  width: 70px;
  height: 25px;
  margin: 20px;
}
.info-day {
  border: 2px solid black;
  margin: 20px;
  padding: 20px;
}
.info_day_content{
  display: flex;
  justify-content: center;
}
</style>
