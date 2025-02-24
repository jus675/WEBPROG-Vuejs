<template>
  <ul>
    <li v-for="country in countries" :key="country.id">{{ country.name }}</li>
  </ul>
    
  <h1>Food</h1>
  <personal-profile/> <br>
  <country>
  <food-item/> 
  <food-item2/> 
  <food-item/>  
  <comment-form/>
  <comment/>
  <rest-api/>

  </country>
  <comment-form/>
  <comment/>
</template>


<script setup>
import { ref, onMounted } from 'vue'
import { supabase } from './lib/supabaseClient'

const countries = ref([])

async function getCountries() {
  const { data } = await supabase.from('countries').select()
  countries.value = data
}

onMounted(() => {
  getCountries()
})

</script>