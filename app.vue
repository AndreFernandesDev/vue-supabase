<script setup>
import { createClient } from "@supabase/supabase-js";
const supabase = createClient(
  "https://yfslejowqsnlgoqdtmlo.supabase.co",
  "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Inlmc2xlam93cXNubGdvcWR0bWxvIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MzQ5MDY0NzIsImV4cCI6MjA1MDQ4MjQ3Mn0.9HroT7T2BZ1mK45tKCW2lh1niIRwoez2_WZM8JM651o"
);
const countries = ref([]);

async function getCountries() {
  const { data } = await supabase.from("countries").select();
  countries.value = data;
}

onMounted(() => {
  getCountries();
});
</script>

<template>
  My website
  <ul>
    <li v-for="country in countries" :key="country.id">{{ country.name }}</li>
  </ul>
</template>
