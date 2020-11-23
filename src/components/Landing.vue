<template>
  <section>
    <div class="hero">
      <form>
        <div class="col-md-8 mb-3 ml-auto mr-auto">
          <div class="input-group">
            <div class="input-group-prepend">
              <span class="input-group-text bg-white hero-search"><i class="fa fa-search" aria-hidden="true"></i></span>
            </div>
            <input type="text" class="form-control" placeholder="Search for photo" aria-describedby="search" required>
          </div>
        </div>
      </form>
    </div>
  </section>
</template>

<script>
  export default {
    name: 'HelloWorld',
    props: {
      msg: String
    }
  }
</script>

<!--limits CSS to this component only -->
<style lang="scss">
  .hero {
    background-color: #F7F7F8;
    height: 18rem;
    padding: 7.5rem 0;
  }

  input[type="text"] {
    outline: none;
    box-shadow: none !important;
    border: 0;
    height: 3rem;
  }

  .input-group-text {
    border: 0 !important;
    height: 3rem;
  }
</style>