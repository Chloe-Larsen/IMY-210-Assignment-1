<!-- Chloe Larsen u25004141 -->
<script setup>
import { ref } from 'vue'

const formData = ref({
  name: '',
  email: '',
  message: ''
})

const submitting = ref(false)
const submitted = ref(false)

const handleSubmit = async () => {
  submitting.value = true
  
  // Create form data object
  const data = new FormData()
  data.append('form-name', 'contact')
  data.append('name', formData.value.name)
  data.append('email', formData.value.email)
  data.append('message', formData.value.message)

  try {
    // Send to Netlify
    const response = await fetch('/', {
      method: 'POST',
      body: data
    })
    
    if (response.ok) {
      submitted.value = true
      formData.value = { name: '', email: '', message: '' }
      
      // Hide success message after 5 seconds
      setTimeout(() => {
        submitted.value = false
      }, 5000)
    }
  } catch (error) {
    console.error('Form submission error:', error)
    alert('Something went wrong. Please try again.')
  } finally {
    submitting.value = false
  }
}
</script>

<template>
  <section id="contact" class="contact-section">
    <nav class="nav">
      <NuxtLink to="/" class="nav-link">Home</NuxtLink>
      <NuxtLink to="/projects" class="nav-link">Projects</NuxtLink>
      <NuxtLink to="/contact" class="nav-link active">Contact</NuxtLink>
      <NuxtLink to="/apis" class="nav-link">API Link</NuxtLink>
    </nav>

    <div class="content">
        <h2>Contact Me</h2>
        <form 
        name="contact" 
        method="POST" 
        data-netlify="true" 
        netlify-honeypot="bot-field"
        @submit.prevent="handleSubmit"
        >          
        <div class="form-group">
            <label for="name">Name:</label>
            <input 
              type="text" 
            id="name" 
            name="name" 
            required 
            v-model="formData.name"
            />
          </div>

          <div class="form-group">
            <label for="email">Email:</label>
            <input 
                type="email" 
                id="email" 
                name="email" 
                required 
                v-model="formData.email"
            />
        </div>

        <div class="form-group">
            <label for="message">Message:</label>
            <textarea 
                id="message" 
                name="message" 
                rows="5" 
                required 
                v-model="formData.message"
            ></textarea>
        </div>

        <button type="submit" :disabled="submitting">
            {{ submitting ? 'Sending...' : 'Send Message' }}
        </button>
        
        <div v-if="submitted" class="success-message">
            Thank you! Your message has been sent.
        </div>
        </form>
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
  font-size: 25px;
}

.form-group {
    margin-bottom: 1.5rem;
}

label {
    display: block;
     margin-bottom: 0.5rem;
    font-weight: bold;
}

input, textarea {
    width: 90%;
    padding: 0.75rem;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-family: inherit;
}

button {
    background-color: #935ec9;
    color: white;
    padding: 0.75rem 1.5rem;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 25px;
}

button:hover {
    background-color: #d7d7d7;
}

button:disabled {
    background-color: #cccccc;
    cursor: not-allowed;
}

.success-message {
    margin-top: 1rem;
    padding: 1rem;
    background-color: #d4edda;
    color: #155724;
    border-radius: 4px;
}
</style>