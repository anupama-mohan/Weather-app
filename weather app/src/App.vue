<script setup>
import {ref} from 'vue'
import Searchinput from "./components/Searchinput.vue";
import WeatherCard from "./components/WeatherCard.vue";
const places = ref([])
const addPlace = (data) => {
places.value.push(data)
}
const deletePlace = (name) => {
  if (confirm('Are you Sure')){
    
  }
places.value = places.value.filter((p)=> p.location.name !== name)}

</script>
<template>
  <main>
    <!-- Date -->
    <div class="text-center mb-6">
      {{
        new Date().toLocaleDateString('en-us', {
          weekday: 'long',
          year: 'numeric',
          month: 'long',
          day: 'numeric'
        })
      }}
    </div>


    <!-- Search -->
    <div>
      <Searchinput @place-data="addPlace"/>
    </div>

    <!-- Weather cards -->
    <div class="grid grid-cols-2 gap-4">
      <div v-for="(place,idx) in places" :key="idx">
        <WeatherCard :place="place" @delete-place="deletePlace"/>
      </div>
      
    </div>
  </main>
</template>