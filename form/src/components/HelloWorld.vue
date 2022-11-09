<template>
  <div>
    <el-form :model="form">
      <el-form-item label="name">
        <el-input v-model="formData.name" />
      </el-form-item>
    </el-form>
    <pre>{{ form }}</pre>
  </div>
</template>

<script>
import { Form, FormItem, Input } from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'
export default {
  name: 'HelloWorld',
  components: {
    [Form.name]: Form,
    [FormItem.name]: FormItem,
    [Input.name]: Input
  },
  props: {
    form: Object,
  },
  data() {
    return {
      formData: this.form
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
