<template>
  <div class="NuxtLogo" >
    <div style="border-radius: 100%; width: auto; height: 20vw; margin: auto;">
      <img loading="lazy" src="../assets/me.jpg" class="image" alt="image">
    </div>
  </div>
</template>

<style>
.NuxtLogo {
  animation: 1s appear;
  margin: auto;
  padding: 25px;

}

.image{
  object-fit: scale-down;
  border-radius: 100%;
  height: 20vw;
  /* width: 50%; */ 
}

@keyframes appear {
  0% {
    opacity: 0;
  }
}
</style>
