<template>
  <v-app>
    <nav class="bg-dark navbar">
      <div class="py-3">
        <span class="text-white mr-5 h5 activeLink" @click="$router.push('/')">HOME</span>
        <span class="text-white h5 activeLink" @click="$router.push('form')">FORM</span>
      </div>
    </nav>
    <div style="position: relative; min-height: 100vh;">
      <div style=" padding-bottom: 125px;">
        <Nuxt/>
      </div>
      <footer id="footer" class="bg-dark">
        <div class="text-center pt-3">
          <span class="text-white-50">Marijo Kiš</span>
        </div>
        <div>
          <b-icon-envelope font-scale="1.5" style="color: white"></b-icon-envelope>
          <span><a href="mailto:mymail@mail.com">Email Us</a></span>
        </div>
        <div class="mt-2">
          <b-icon-watch font-scale="1.5" style="color: white"></b-icon-watch>
          <span style="color: white">8:00 am - 4:00 pm</span>
        </div>
      </footer>
    </div>


  </v-app>
</template>

<script>
    import {BIconEnvelope, BIconWatch, BIconDisplay} from 'bootstrap-vue'

    export default {
        components: {
            BIconEnvelope,
            BIconWatch,
            BIconDisplay
        }
    }
</script>

<style>
  .activeLink:hover {
    color: #0275D8 !important;
    cursor: pointer;
  }

  #footer {
    position: absolute;
    bottom: 0;
    width: 100%;
    height: 125px;
  }
</style>
