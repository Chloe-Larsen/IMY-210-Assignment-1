<!-- Chloe Larsen u25004141 -->
<script setup>
  
</script>

<template>
  <div>    
    <nav class="nav">
      <NuxtLink to="/" class="nav-link active">Home</NuxtLink>
      <NuxtLink to="/projects" class="nav-link">Projects</NuxtLink>
      <NuxtLink to="/contact" class="nav-link">Contact</NuxtLink>
      <NuxtLink to="/apis" class="nav-link">API Link</NuxtLink>
    </nav>

    <section class="hero">
      <h1>Chloe Larsen</h1>
      <img src="/Images/profile.jpg" alt="Your Name" class="profile-img">
      <p>Chloe is a second year BSc IT IKS student at the university of Pretoria. She was born and raised in Johannesburg, Gauteng. She has won the uber gloabal hackathon for her reigen of Africa, Middle East and Russia. She excells in Math and IT and has played the trumpet for 14 years </p>
    </section>   
    
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

.hero {
  text-align: center;
  padding: 4rem 2rem;
  background: #764ba2;
  color: white;
}

.hero h1 {
  font-size: 50px;  
}

.hero p {
  max-width: 800px;
  margin: 0 auto;
  font-size: 25px;  
}

.profile-img {
  width: 300px;
  height: 300px;
  border-radius: 50%;
  object-fit: cover;
  border: 4px solid white;
  margin: 2rem auto;
  display: block;
}

@media (max-width: 768px) {
  .hero {
    padding: 2rem 1rem;
  }
  
  .profile-img {
    width: 200px;
    height: 200px;
  }
  
  .preview {
    padding: 2rem 1rem;
  }
}
</style>