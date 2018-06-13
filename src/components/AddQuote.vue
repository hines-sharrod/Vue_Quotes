<template>
  <div class="row">
      <form>
        <div class="colsm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
            <label>Quote</label>
            <textarea rows="3" class="form-control" v-model="quote"></textarea>
        </div>
        <div class="colsm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
            <button class="btn btn-primary" @click.prevent="addQuote">Add Quote</button>
        </div>
      </form>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      quote: ""
    };
  },
  methods: {
    addQuote() {
      this.$emit("quoteAdded", this.quote);
      this.quote = "";
    }
  }
};
</script>

<style scoped>
button {
  display: block;
  margin: 0 auto;
}
</style>
