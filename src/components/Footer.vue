<template>
  <v-container fluid fill-height class="homefone" style="position: relative; margin-bottom: -10px; margin-top: 50px;">
    <FooterFone :footerHeight="footerHeight" />
    <v-container fluid class="footer--top-content" :style="{ top: topContentTop }">
      <v-row align="start" justify="center" style="position: absolute; top: 0; left: 0; width: 100%">
        <v-card-title>
          <h2 class="white-text centered">{{ footer.topHead }}</h2>
        </v-card-title>
        <v-card-text max-width="100%">
          <h4 class="white-text centered">
              {{ footer.topText }}
          </h4>
        </v-card-text>
        <v-row class="mx-auto">
          <v-col cols="12" class="mx-auto">
            <v-row align="center" justify="center">
              <v-card flat class="transparent mx-1 my-1" v-if="viewportWidth > 420">
                <v-text-field
                      height="53"
                      class="input-field rounded transparent"
                      label="Name"
                      hide-details
                      rounded
                      outlined
                      dark
                      color="#fff"
                      v-model="name"
                ></v-text-field>
              </v-card>
              <v-card flat class="transparent mx-1 my-1" v-if="viewportWidth > 420">
                <v-text-field
                      height="53"
                      class="input-field rounded transparent"
                      label="Email"
                      hide-details
                      rounded
                      outlined
                      dark
                      color="#fff"
                      v-model="email"
                ></v-text-field>
              </v-card>
              <v-card flat class="transparent mx-1 my-1" v-if="viewportWidth > 420">
                <v-text-field
                      height="53"
                      class="input-field rounded transparent"
                      label="Phone"
                      hide-details
                      rounded
                      outlined
                      dark
                      color="#fff"
                      v-model="phone"
                      style="font-size: 16px"
                      background-color="transparent"
                ></v-text-field>
              </v-card>
              <v-card flat class="transparent mx-1 my-0">
                <v-btn
                    height="53"
                    max-width="280"
                    min-width="280"
                    label="Phone"
                    dense
                    hide-details
                    rounded
                    light
                    @click="submit"
                    style="color: #20731C"
                >Get started</v-btn>
              </v-card>
            </v-row>
          </v-col>
        </v-row>
      </v-row>
    </v-container>

    <FooterBottomContent v-if="viewportWidth >= 770" />
    <FooterBottomContentSmall  v-if="viewportWidth < 770" class="footer--bottom-content-small"/>
  </v-container>
</template>

<style>

.footer--top-content {
  position: absolute;
  width: 100%;
}

.footer--bottom-content-small {
  position: absolute;
  bottom: 40px;
  left: 0;
}

.title {
  margin-top: 198px;
}

.rounded {
  border-radius: 40px!important;
}

.white-text {
  color: #fff;
}

.centered {
  text-align: center;
}
.icon {
  display: inline-block;
  width: 10px;
  margin-right: 10px;
}

.left-16 {
  font-size: 16px;
  font-weight: 900;
  text-align: left;
  color: #fff;
}
.left-14 {
  font-size: 14px;
  font-weight: normal;
  text-align: left;
  color: #fff;
}

.ref {
  text-decoration: none;
  cursor: pointer;
}
.ref:hover {
  color: #E5FDD7;
}

.input-field {
  width: 280px;
}

</style>

<script>

import { mapState } from 'vuex'

import FooterFone from '@/components/footer/FooterFone.vue'
import FooterBottomContent from '@/components/footer/BottomContent.vue'
import FooterBottomContentSmall from '@/components/footer/BottomContentSmall.vue'

export default {
  name: 'Footer',
  components: {
    FooterFone,
    FooterBottomContentSmall,
    FooterBottomContent
  },
  props: {
    user: Object,
    page: Number
  },
  data () {
    return {
      name: '',
      email: '',
      phone: '',
      send: false
    }
  },
  computed: {
    ...mapState(['viewportWidth']),
    ...mapState('content', ['footer']),
    topContentTop () {
      return this.viewportWidth < 420 ? '80px' : this.viewportWidth > 1904 ? '288px' : '198px'
    },
    topContentFont () {
      return this.viewportWidth < 420 ? '80px' : this.viewportWidth > 1904 ? '288px' : '198px'
    },
    footerHeight () {
      return this.viewportWidth < 420 ? 680 : this.viewportWidth > 1904 ? 980 : 860
    }
  },
  methods: {
    submit () {
      if (!this.name || !this.phone) return
      this.$emit('update:user', {
        name: this.name,
        email: this.email,
        phone: this.phone
      })
    }
  }
}
</script>
