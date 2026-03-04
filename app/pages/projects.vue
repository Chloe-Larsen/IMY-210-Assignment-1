<!-- Chloe Larsen u25004141 -->
<script>

</script>

<template>
  <section class="projects-section">
    <nav class="nav">
      <NuxtLink to="/" class="nav-link">Home</NuxtLink>
      <NuxtLink to="/projects" class="nav-link active">Projects</NuxtLink>
      <NuxtLink to="/contact" class="nav-link">Contact</NuxtLink>
      <NuxtLink to="/apis" class="nav-link">API Link</NuxtLink>

    </nav>

    <div class="content">
      <h2>My Projects</h2>
      
      <div class="projects-grid">
        <div class="project-card">
          <h3>Animal Adoption Programs</h3>
          <p>Project for to help make the animal adoption process easier. Created using java GUIs and access databases</p>
          <span class="tech-tag">Java and SQL</span>
        </div>

        <div class="project-card">
          <h3>Carbon Calculator</h3>
          <p>Project that won the reigon of Africa, Middle East and Russia for the International Uber Hackathon. A carbon calculator for uber's app make using Java and access databse.</p>
          <span class="tech-tag">Java and SQL</span>
        </div>

        <div class="project-card">
          <h3>Soap Shop</h3>
          <p>HTML, Javascript and CSS project for INF164. A website for the sale of different soaps.</p>
          <span class="tech-tag">HTML, Javascript, CSS</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style>
.nav {
  display: flex;
  justify-content: center;
  gap: 2rem;
  padding: 1rem;
  background-color: #764ba296;
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

.content {
  text-align: center;
  padding: 4rem 2rem;
  background: #764ba2;
  color: white;
  min-height: 100vh;
}

.content h2 {
  margin-bottom: 3rem;
  font-size: 35px;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.project-card {
  background: white;
  color: #333;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  transition: transform 0.3s, box-shadow 0.3s;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 12px rgba(0,0,0,0.15);
}

.project-card h3 {
  margin-bottom: 1rem;
  color: #764ba2;
}

.project-card p {
  margin-bottom: 1.5rem;
  line-height: 1.6;
}

.tech-tag {
  display: inline-block;
  background: #764ba2;
  color: white;
  padding: 0.25rem 0.75rem;
  border-radius: 20px;
  font-size: 20px;
}

@media (max-width: 768px) {
  .content {
    padding: 2rem 1rem;
  }
  
  .projects-grid {
    grid-template-columns: 1fr;
  }
}
</style>