<template>
  <div style="width: 100vw; height: 100vh; display: flex; justify-content: center; padding: 32px 16px;">
    <div style="width: 290px">

      <label>Dark Mode <input type="checkbox" v-model="dark"></label>

      <br>
      <hr>
      <br>

      <h3>Date value: <pre>{{ date }}</pre></h3>

      <label>Disabled <input type="checkbox" v-model="disabled"></label>

      <label>Enable Time <input type="checkbox" v-model="enableTime"></label>
      <label>Use 24-Hour Format <input type="checkbox" v-model="use24"></label>
      <label>Include Seconds <input type="checkbox" v-model="enableSeconds"></label>

      <br>
      <hr>
      <br>

      <div class="label type-label disabled" data-v-792c5ca7 data-v-5157b788>
        <span class="field-name" data-v-792c5ca7>Date</span>
      </div>
      <div class="interface" data-v-175a2f1a data-v-5157b788>
        <DatePicker :disabled="disabled" :enable-time="enableTime" :use24="use24" :enable-seconds="enableSeconds" :value="date" @input="v => date = v"></DatePicker>
      </div>
    </div>
  </div>
</template>

<script>
import DatePicker from "../interface.vue";
import './directus_styles.css'

export default {
  name: "wrapper.vue",
  components: {DatePicker},
  data () {
    return {
      date: new Date().toISOString(),
      disabled: false,
      enableTime: false,
      use24: false,
      enableSeconds: false,
      dark: false,
    }
  },
  watch: {
    dark: {
      immediate: true,
      handler (dark) {
        window.document.body.classList.remove('auto', 'dark', 'light')

        window.document.body.classList.add(dark ? 'dark' : 'light')
      }
    }
  }
}
</script>