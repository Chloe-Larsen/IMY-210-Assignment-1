<!--Chloe Larsen u25004141-->
<script setup>
    import WeatherWidget from './weather.vue'  
    import CatFacts from './catFacts.vue';
</script>

<template>
    <div>
        <nav class="nav">
            <NuxtLink to="/" class="nav-link">Home</NuxtLink>
            <NuxtLink to="/projects" class="nav-link">Projects</NuxtLink>
            <NuxtLink to="/contact" class="nav-link">Contact</NuxtLink>
              <NuxtLink to="/apis" class="nav-link active">API Link</NuxtLink>
        </nav>
        <WeatherWidget /> 
        <CatFacts />
    </div>
</template>

<style>
.nav {
  display: flex;
  justify-content: center;
  gap: 2rem;
  padding: 1rem;
  background-color: #764ba296;
  font-size: 25px;
}

.nav-link {
  color: rgb(0, 0, 0);
  text-decoration: none;
  padding: 0.5rem 1rem;  
}

.nav-link:hover {
  color: #764ba2;
}

.nav-link.active {
  color: #764ba2;
  font-weight: bold;
  border-bottom: 2px solid #764ba2;
}
</style>