<!-- Chloe Larsen u25004141 -->
<script setup>
import { ref, onMounted } from 'vue'

// Replace with your actual API key
const API_KEY = 'e3308efd7b19fcf326ff8aae192fa0f5'
const weatherData = ref(null)
const loading = ref(true)
const error = ref(null)
const city = ref('Pretoria')

const fetchWeather = async () => {
  loading.value = true
  error.value = null
  
  try {
    const response = await fetch(
      `http://api.weatherstack.com/current?access_key=${API_KEY}&query=${city.value}&units=m`
    )
    
    const data = await response.json()
    
    // Check for errors
    if (data.error) {
      throw new Error(data.error.info || 'Weather data not available')
    }
    
    if (data.success === false) {
      throw new Error('Failed to fetch weather data')
    }
    
    weatherData.value = data
  } catch (err) {
    console.error('Weather fetch error:', err)
    error.value = err.message || 'Failed to load weather data'
  } finally {
    loading.value = false
  }
}

onMounted(() => {
  fetchWeather()
})
</script>

<template>
  <div class="weather-widget">
    <div class="weather-header">
      <h3>🌤️ Current Weather</h3>
      <div class="city-selector">
        <input 
          v-model="city" 
          @keyup.enter="fetchWeather"
          placeholder="Enter city"
          class="city-input"
        />
        <button @click="fetchWeather" class="search-btn">Search</button>
      </div>
    </div>

    <div v-if="loading" class="weather-loading">
      Loading weather...
    </div>

    <div v-else-if="error" class="weather-error">
      {{ error }}
    </div>

    <div v-else-if="weatherData && weatherData.current" class="weather-content">
      <!-- Location Info -->
      <div class="weather-location">
        <strong>{{ weatherData.location.name }}, {{ weatherData.location.country }}</strong>
        <span class="localtime">{{ weatherData.location.localtime }}</span>
      </div>
      
      <div class="weather-main">
        <div class="weather-icon">
          <img :src="weatherData.current.weather_icons[0]" :alt="weatherData.current.weather_descriptions[0]">
        </div>
        <div class="weather-temp">
          {{ weatherData.current.temperature }}°C
        </div>
      </div>
      
      <div class="weather-desc">
        {{ weatherData.current.weather_descriptions[0] }}
      </div>
      
      <div class="weather-details">
        <div class="detail">
          <span class="detail-label">Feels like</span>
          <span class="detail-value">{{ weatherData.current.feelslike }}°C</span>
        </div>
        <div class="detail">
          <span class="detail-label">Humidity</span>
          <span class="detail-value">{{ weatherData.current.humidity }}%</span>
        </div>
        <div class="detail">
          <span class="detail-label">Wind</span>
          <span class="detail-value">{{ weatherData.current.wind_speed }} km/h</span>
        </div>
        <div class="detail">
          <span class="detail-label">Wind Direction</span>
          <span class="detail-value">{{ weatherData.current.wind_dir }}</span>
        </div>
        <div class="detail">
          <span class="detail-label">Pressure</span>
          <span class="detail-value">{{ weatherData.current.pressure }} mb</span>
        </div>
        <div class="detail">
          <span class="detail-label">UV Index</span>
          <span class="detail-value">{{ weatherData.current.uv_index }}</span>
        </div>
      </div>
      
      <div class="weather-visibility">
        Visibility: {{ weatherData.current.visibility }} km
      </div>
    </div>

    <div v-else class="weather-error">
      No weather data available
    </div>
  </div>
</template>

<style scoped>
.weather-widget {
  background: #764ba2;
  border-radius: 12px;
  padding: 1.5rem;
  color: white;
  margin: 1rem 0;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}

.weather-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
  flex-wrap: wrap;
  gap: 1rem;
}

.weather-header h3 {
  margin: 0;
  font-size: 1.3rem;
}

.city-selector {
  display: flex;
  gap: 0.5rem;
}

.city-input {
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
  font-size: 0.9rem;
  min-width: 150px;
}

.search-btn, .location-btn {
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
  background: rgba(255,255,255,0.2);
  color: white;
  cursor: pointer;
  transition: background 0.3s;
  font-size: 0.9rem;
}

.search-btn:hover, .location-btn:hover {
  background: rgba(255,255,255,0.3);
}

.weather-content {
  text-align: center;
}

.weather-location {
  margin-bottom: 1rem;
  font-size: 1.1rem;
}

.localtime {
  display: block;
  font-size: 0.9rem;
  opacity: 0.8;
  margin-top: 0.25rem;
}

.weather-main {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1.5rem;
  margin-bottom: 0.5rem;
}

.weather-icon img {
  width: 60px;
  height: 60px;
}

.weather-temp {
  font-size: 3rem;
  font-weight: bold;
}

.weather-desc {
  font-size: 1.2rem;
  margin-bottom: 1.5rem;
  text-transform: capitalize;
}

.weather-details {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 1rem;
  margin: 1.5rem 0;
  padding: 1rem 0;
  border-top: 1px solid rgba(255,255,255,0.2);
  border-bottom: 1px solid rgba(255,255,255,0.2);
}

.detail {
  display: flex;
  flex-direction: column;
}

.detail-label {
  font-size: 0.8rem;
  opacity: 0.8;
  margin-bottom: 0.25rem;
}

.detail-value {
  font-size: 1.1rem;
  font-weight: bold;
}

.weather-visibility {
  font-size: 0.95rem;
  opacity: 0.9;
}

.weather-loading, .weather-error {
  text-align: center;
  padding: 2rem;
  opacity: 0.8;
}

.weather-error {
  color: #ff6b6b;
}

@media (max-width: 768px) {
  .weather-header {
    flex-direction: column;
    align-items: stretch;
  }
  
  .city-selector {
    width: 100%;
  }
  
  .city-input {
    flex: 1;
  }
  
  .weather-details {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>