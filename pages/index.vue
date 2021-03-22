<template>
  <div class="container" fluid="lg">
    <div>
      <Logo />
      <h1 class="title">
        Sukhvinder Singh
      </h1>
      <div class="links">
        <a
          href="/projects"
          rel="noopener noreferrer"
          class="button--green"
        >
          Past Projects
        </a>
        <a
          href="/collaborate"
          rel="noopener noreferrer"
          class="button--grey"
        >
          Collaborate
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  /* background-image: url('../assets/background.jpg'); */
  
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

@media (max-width: 600px){
  .title {
      font-size: 60px;
      line-height: 90px;
  }
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
