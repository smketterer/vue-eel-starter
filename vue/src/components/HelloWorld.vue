<template>
  <div class="hello">
    <h1>{{ this.message }}</h1>
    <input type="text" v-model="inputValue" />
    <button @click="onClick">Send</button>
    <div>
      {{ response }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: function() {
    return {
      message: "",
      inputValue: "",
      response: ""
    }
  },
  mounted: function() {
    eel.hello_world()((val) => {
      // Receiving a value from Python
      this.message = val
    })
  },
  methods: {
    onClick() {
      // Passing values to Python
      eel.print_string(this.inputValue)((val) => {
        // Return response from Python
        this.response = val
      })
    }
  }
}
</script>
