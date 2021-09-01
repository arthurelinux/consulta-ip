<template>
  <div id="app">
    <nav class="navbar navbar-expand-md navbar-dark shadow-sm">
            <div class="container">
                <a class="navbar-brand" href="/home"> <img src="https://acessodesign.com.br/src/img/logobranca.png" width="150" >
                </a>
                <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" >
                    <span class="navbar-toggler-icon"></span>
                </button>

                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                    <!-- Left Side Of Navbar -->
                    <ul class="navbar-nav mr-auto">

                    </ul>

                    <!-- Right Side Of Navbar -->
                    <ul class="navbar-nav ml-auto">
                        <!-- Authentication Links -->
                       
                                <li class="nav-item">
                                    <a class="nav-link" href="#">Login</a>
                                </li>
                    </ul>
                </div>
            </div>
        </nav>

    <div class="container">
        <input type="text" v-model="ip" placeholder="IP">
    <button v-on:click="popular">Consultar</button>

    <table>
      <tbody>
        <tr>
          <td> <strong>IP</strong></td>
          <td>{{query}}</td>
        </tr>
        <tr>
          <td> <strong>Status</strong> </td>
          <td>{{status}}</td>
        </tr>
        <tr>
          <td> <strong>País</strong> </td>
          <td>{{country}}</td>
        </tr>
        <tr>
          <td> <strong>Código do País</strong> </td>
          <td>{{countryCode}}</td>
        </tr>
        <tr>
          <td> <strong>Região</strong> </td>
          <td>{{region}}</td>
        </tr>
        <tr>
          <td> <strong>Nome da região</strong> </td>
          <td>{{regionName}}</td>
        </tr>
        <tr>
          <td> <strong>Cidade</strong> </td>
          <td>{{city}}</td>
        </tr>
        <tr>
          <td> <strong>País</strong> </td>
          <td>{{zip}}</td>
        </tr>
        <tr>
          <td> <strong>Latitude</strong> </td>
          <td>{{lat}}</td>
        </tr>
         <tr>
          <td> <strong>Logitude</strong> </td>
          <td>{{lon}}</td>
        </tr>
         <tr>
          <td> <strong>timezone</strong> </td>
          <td>{{timezone}}</td>
        </tr>
         <tr>
          <td> <strong>isp</strong> </td>
          <td>{{isp}}</td>
        </tr>
        <tr>
          <td> <strong>org</strong> </td>
          <td>{{org}}</td>
        </tr>
        <tr>
          <td> <strong>As</strong> </td>
          <td>{{as}}</td>
        </tr>
        
      </tbody>

    </table>
    </div>
  </div>
</template>

<script>
import api from "@/services/api.js"
import "./assets/style.css"
import Vue from 'vue'
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'

// Import Bootstrap an BootstrapVue CSS files (order is important)
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

// Make BootstrapVue available throughout your project
Vue.use(BootstrapVue)
// Optionally install the BootstrapVue icon components plugin
Vue.use(IconsPlugin)
export default {
  name: 'App',
   data(){
        return{
              ip: '',
              query: "",
              status: "",
              country: "",
              countryCode: "",
              region: "",
              regionName: "",
              city: "",
              zip: "",
              lat: 0,
              lon: 0,
              timezone: "",
              isp: "",
              org: "",
              as: ""
        }
    },
  components: {
   
  },
  methods:{
    popular(){
        api.get(''+this.ip).then(Response =>  {
            this.query = Response.data.query;      
              this.status = Response.data.status,
              this.country= Response.data.country,
              this.countryCode= Response.data.countryCode,
              this.region= Response.data.region,
              this.regionName= Response.data.regionName,
              this.city= Response.data.city,
              this.zip= Response.data.zip,
              this.lat= Response.data.lat,
              this.lon= Response.data.lon,
              this.timezone= Response.data.timezone,
              this.isp= Response.data.isp,
              this.org= Response.data.org,
              this.as= Response.data.as

              console.log(Response)
        })
    }
  }
}
</script>

<style>
#app {

}
</style>
