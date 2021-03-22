<template>
  <b-container fluid>
      <b-row>
          <b-col cols="12" lg="2" sm="2" class="optionSection">col1</b-col>
          <b-col cols="12" lg="10" sm="12" class="optionDetails">
              <b-row>
                  <b-col cols="4">Content1</b-col>
                  <b-col cols="4">Content2</b-col>
                  <b-col cols="4">Content3</b-col>
              </b-row>
              <b-row class="m-2">
                  <Card/>
              </b-row>
          </b-col>
      </b-row>
  </b-container>
</template>

<script>
export default {

}
</script>

<style scoped>
.container-fluid{
    height: 100vh;
}
.optionSection{
    background-color: red;
    height: 100vh;
}
.optionDetails{
    padding-left: 25px;
    height: 100vh;
}

</style>