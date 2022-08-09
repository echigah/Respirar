<template>
  <div class="hello">
    <h1>Sensores</h1>
    <pre v-for="sensor in sensors" :key="sensor.id">{{ sensor }}</pre>
  </div>
</template>

<script>
import axios from 'axios'

const url = 'http://localhost:8080/v2/entities'
const headers = { 
  "Access-Control-Allow-Origin": "*",
  'fiware-service': 'mdp', 
  'fiware-servicepath': '/'
}
const config = {
  headers: headers
}

export default {
  name: 'Mapa',
  data () {
    return {
      sensors: []
    }
  },
  mounted () {   
    axios
      .get(url, config)
      .then(response => (this.sensors = response.data))
      .catch(error => console.log(error))
  }
}
</script>


