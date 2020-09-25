<template>
  <div>
    <div>
      <div v-bind="searchData()"></div>
      <h1>รายงานสถานการณ์ โควิด-19</h1>

      <b-card-group deck class="mb-2 ">
        <b-card
          bg-variant="primary"
          text-variant="white"
          title="ติดเชื้อสะสม"
          class="text-center"
        >
          <b-card-title >
            {{ playlist.Confirmed }}
          </b-card-title>
        </b-card>

        <b-card
          bg-variant="secondary"
          text-variant="white"
          title="ผู้ติดเชื้อรายใหม่"
          class="text-center "
        >
          <b-card-title >
            {{ playlist.NewConfirmed }}</b-card-title>
        </b-card>

        <b-card
          bg-variant="success"
          text-variant="white"
          title="รักษาหายแล้ว"
          class="text-center"
        >
          <b-card-title >
            {{ playlist.Recovered }}</b-card-title>
        </b-card>
      </b-card-group>

      <div class="mt-3 ">
        <b-card-group deck>
          <b-card
            bg-variant="info"
            text-variant="white"
            title="รักษาอยู่ในโรงพยาบาล "
            class="text-center"
          >
            <b-card-title >
              {{ playlist.Hospitalized }}</b-card-title>
          </b-card>

          <b-card
            bg-variant="warning"
            text-variant="white"
            title="ออกจากโรงพยาบาล"
            class="text-center"
          >
            <b-card-title>{{ playlist.NewHospitalized }}</b-card-title>
          </b-card>

          <b-card
            bg-variant="danger"
            text-variant="white"
            title="เสียชีวิต"
            class="text-center"
          >
            <b-card-title>{{ playlist.Deaths }}</b-card-title>
          </b-card>
        </b-card-group>
      </div>

      <div class="mt-3">
        <b-card-group deck>
          <b-card 
          bg-variant="light" 
          title="อัพเดทข้อมูลล่าสุด" 
          class="text-center">
            <b-card-title>{{ playlist.UpdateDate }}</b-card-title>
          </b-card>

          <b-card
            bg-variant="dark"
            title="เสียชีวิตเพิ่ม"
            text-variant="white"
            class="text-center"
          >
            <b-card-title>{{ playlist.NewDeaths }}</b-card-title>
          </b-card>

          <b-card 
          title="รักษาหายเพิ่ม" 
          class="text-center">
            <b-card-title>{{ playlist.NewRecovered }}</b-card-title>
          </b-card>
        </b-card-group>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      playlist: "",
    };
  },

  methods: {
    searchData() {
      axios
        .get("https://covid19.th-stat.com/api/open/today")
        .then((Response) => {
          this.playlist = Response.data;
        })
        .catch((err) => {
          console.log(err);
          this.err = true;
        });
    },
  },
};
</script>

<style>
.card{
  font-family: 'Mitr', sans-serif;
  margin-top: 10px;
}
</style>
