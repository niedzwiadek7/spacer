<template>
  <div class="searchWrapper">
    <input id="search"
           class="search"
           autocomplete="off"
           :value="value"
           @input="handleChange"
    >
  </div>
</template>

<script>

export default {
  name: 'SearchInput',
  props: {
    value: {
      type: String,
      required: true,
    },
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
  .searchWrapper {
    display: flex;
    flex-direction: column;
    width: 300px;
    margin-top: 50px;
  }

  label {
    font-family: Montserrat, sans-serif;
  }

  input {
    height: 30px;
    border: 0;
    font-size: 18px;
    color: white;
    text-align: center;
    border-bottom: 1px solid white;
    background: none;
    transition: box-shadow .3s ease-out;

    @media (min-width: 1024px) {
      font-weight: 400;
    }
  }

  input:focus {
    outline: none;
    box-shadow: 0 10px 20px -8px rgba(255, 255, 255, .3);
  }
</style>
