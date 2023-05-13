<template>
  <main id="signup-form">
    <div id="signup-body">
      <div class="main-text">
        <h1>Learn to code by watching others</h1>
        <p>
          See how experienced developers solve problems in real-time. Watching
          scripted tutorials is great, but understanding how developers think is
          invaluable.
        </p>
      </div>
      <SignForm />
    </div>
  </main>
</template>

<script>
import SignForm from "./components/SignForm.vue";
export default {
  name: "App",
  components: {
    SignForm: SignForm,
  },
};
</script>

<style>
* {
  font-family: "Poppins", sans-serif;
}

body {
  background-image: url("/src/assets/bg-intro-desktop.png");
  background-color: hsl(0, 100%, 74%);
  font-size: 16px;
}

#signup-form {
  display: flex;
  height: 100vh;
  justify-content: center;
  align-items: center;
}

#signup-body {
  display: grid;
  grid-template-columns: 500px 600px;
}

.main-text {
  display: flex;
  flex-direction: column;
  color: hsl(0, 100%, 100%);
  justify-content: center;
}

.main-text h1 {
  position: relative;
  right: 60px;
  font-size: 40px;
  margin-bottom: 8px;
}

.main-text p {
  position: relative;
  right: 60px;
}

/* Mobile design */

@media only screen and (max-width: 350px) {
  body {
    background-image: url("/src/assets/bg-intro-mobile.png");
  }

  #signup-form {
    height: 1000px;
  }

  #signup-body {
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .main-text h1 {
    right: 0px;
    font-size: 22px;
    margin-bottom: 0px;
    text-align: center;
  }

  .main-text p {
    text-align: center;
    right: 0;
  }
}

@media only screen and (min-width: 351px) and (max-width: 1024px) {
  body {
    background-image: url("/src/assets/bg-intro-mobile.png");
  }

  #signup-form {
    height: 1000px;
  }

  #signup-body {
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .main-text h1 {
    right: 0px;
    font-size: 22px;
    margin-bottom: 0px;
    text-align: center;
  }

  .main-text p {
    text-align: center;
    right: 0;
  }
}
</style>
