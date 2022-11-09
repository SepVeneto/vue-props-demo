<template>
  <section>
    <p>
      <input-vue v-model="formData.name" />
      <!-- <input-vue :value="formData.name" @input="onInput" /> -->
    </p>
    <p>
      <input-vue v-model="formData.age" />
    </p>
    <pre>{{ formData }}</pre>
  </section>
</template>

<script>
import inputVue from '../components/input.vue';
export default {
  components: {
    inputVue,
  },
  data() {
    return {
      formData: {
        name: '',
        obj: {
          name: '',
        }
      }
    }
  },
  created() {
    console.log(this.formData)
  },
  methods: {
    onInput(val) {
      debugger;
      this.formData.name = val
    }
  }
}
</script>
