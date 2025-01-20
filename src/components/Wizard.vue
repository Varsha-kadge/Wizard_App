<template>
  <div>
    <div class="nav-bar">
      <img alt="banner" class="banner-img" src="../assets/banner.png">
    </div>
    <div class="body-container">
      <div class="chlng-txt">
      <h2>What is WizFit Challenge?</h2>
      <button class="video-btn"><span>Watch Video</span></button>
    </div>
    <div>
      <img alt="banner" class="banner-img" src="../assets/Player.png">
    </div>
    <div class="form">
      <h1>Are you ready to take the challenge? </h1>
      <h4>Download Harlem Wizards App</h4>
      <div>
        <img alt="banner" class="apple-img" src="../assets/apple-store.png">
        <img alt="banner" class="google-img" src="../assets/goolge-store.png">
      </div>
      <div class="hr-div">
      <h5 class="hr-lines">Or you can sign up right now</h5>
    </div>
      <input class="input-box" type="search" v-model="searchQuery" placeholder="Search Campaign Here...">
      <div class="school-list" v-if="schoolData">
        <ul v-for="items in resultQuery" :key="items.id">
          <li>{{ items.school_name }}</li><button class="btn">Join Campaign</button>
        </ul>
      </div>
      <div v-else>
        <p>{{ errorMsg }}</p>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'Wizard-App',
  props: {
  },
  data: () => ({
    schoolData: [],
    searchQuery: "",
    errorMsg:""
  }),
  mounted() {
    try {
      axios.get('https://api.devharlemwizardsinabox.com/campaign/campaign_school_list/?').then((response) => {
        this.schoolData = response.data.school_list;
      })
    }
    catch (error) {
      this.errorMsg = error, 'API is failed to load';
      console.log(error,'API is failed to load');
    }
  },
  computed: {
    resultQuery() {
      if (this.searchQuery) {
        return this.schoolData.filter((item) => {
          return this.searchQuery.toLowerCase().split(' ').every(v => item.school_name.toLowerCase().includes(v))
        })
      } else {
        return this.schoolData;
      }
    }
  }
}

</script>

