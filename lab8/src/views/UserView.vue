<template>
    <div>
      <button @click="loadUser()">Maejo University</button> <br />
  
      <!------ //<div>{{ typeof(userData) }}</div>// ----->
      <div class="row">
        <div v-for="user in userData" :key="user.id" class="col-4">
          <div class="row container text-center">
            <div class="card" style="width: 18rem">
              <div class="card-body">
                <h5 class="card-title">University of United States</h5>
                <p class="card-text">
                  ประเทศ:{{ user.country }} <br />
                  ตัวย่อชื่อประเทศ:{{ user.alpha_two_code }} <br />
                  เว็บมหาวิทยาลัย:{{ user.web_pages }} <br />
                  ชื่อมหาวิทยาลัย:{{ user.name }}
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  <script setup>
  import axios from "axios";
  import { ref } from "vue";
  const userData = ref([]);
  const url = ref("http://universities.hipolabs.com/search?country=United+States");
  function loadUser() {
    axios
      .get(url.value)
      .then((response) => {
        userData.value = response.data;
      })
      .catch((err) => {
        console.log(err);
      });
  }
  </script>
  <style>
  .card {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
  }
  </style>