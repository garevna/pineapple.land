<template>
<v-container fluid class="footer--bottom-content">
  <v-row width="100%" justify="center" class="mx-auto">
    <v-col style="min-width: 340px; max-width: 340px">
      <v-card flat class="transparent mx-auto">
        <v-card-title>
          <p class="left-16">ABOUT PINEAPPLE NET</p>
        </v-card-title>
        <v-card-text>
          <p class="left-14">{{ about }}</p>
          <p></p>
          <p class="left-14">{{ officeAddress }}</p>
          <p class="left-14">
            <span width="10" height="10" class="mr-2" style="display: inline-block;">
              <v-img src="@/assets/home/icons/system-bar-call-answer.png" width="10" height="10" contain style="display: inline-block; vertical-align: middle"></v-img>
            </span>
            <span style="color: #fff">{{ officePhone }}</span>
          </p>
          <p class="left-14">{{ officeEmail }}</p>
          <p class="left-14">ABN: {{ officeABN }}</p>
        </v-card-text>
      </v-card>
    </v-col>
    <v-col style="max-width: 180px">
      <v-card flat class="transparent mx-auto">
        <v-card-title>
          <p class="left-16">COMPANY</p>
        </v-card-title>
        <v-card-text>
          <p class="left-14 ref" @click="$emit('update:page', 0)">Home</p>
          <p class="left-14 ref" @click="$emit('update:page', 1)">About</p>
          <p class="left-14 ref" @click="$emit('update:page', 2)">Residential</p>
          <p class="left-14 ref" @click="$emit('update:page', 3)">Business</p>
          <p class="left-14 ref" @click="$emit('update:page', 4)">Connect</p>
          <p class="left-14 ref" @click="$emit('update:page', 5)">Contact Us</p>
        </v-card-text>
      </v-card>
    </v-col>
    <v-col style="max-width: 180px">
      <v-card flat class="transparent mx-auto">
        <v-card-title>
          <p class="left-16">PRODUCTS</p>
        </v-card-title>
        <v-card-text>
          <p class="left-14 ref">Residential Internet</p>
          <p class="left-14 ref">Business Internet</p>
        </v-card-text>
      </v-card>
    </v-col>
    <v-col style="max-width: 180px">
      <v-card flat class="transparent mx-auto">
        <v-card-title>
          <p class="left-16">CONNECT</p>
        </v-card-title>
        <v-card-text>
          <a :href="faceBook" target="_blank" class="ref">
            <p class="left-14 ref">
              <v-img src="@/assets/home/icons/system-bar-facebook.png" class="icon"></v-img>Facebook
            </p>
          </a>
          <a :href="linkedIn" target="_blank" class="ref">
            <p class="left-14 ref">
              <v-img src="@/assets/home/icons/system-bar-linkedin.png" class="icon"></v-img> Linkedin
            </p>
          </a>
          <br>
          <br>
          <br>
          <p class="left-14 ref">FAQs & Support</p>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</v-container>
</template>

<style scoped>
.footer--bottom-content {
  position: absolute;
  left: 0;
  /* overflow: hidden; */
  margin-bottom: -4px;
  bottom: 10px;
}
</style>

<script>

import { mapState } from 'vuex'

export default {
  name: 'FooterBottomContent',
  computed: {
    ...mapState(['officePhone', 'officeAddress', 'officeEmail', 'officeABN', 'linkedIn', 'faceBook']),
    ...mapState('content', ['about', 'copyright'])
  }
}
</script>
