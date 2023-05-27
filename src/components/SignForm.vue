<template>
  <div class="form-body">
    <p class="try-btn">
      <strong>Try it free 7 days </strong>then $20/mo. thereafter
    </p>
    <form class="form">
      <input
        class="form-input"
        type="text"
        id="fname"
        name="fname"
        :placeholder="input.firstName.placeholder"
        v-model="input.firstName.value"
        :class="[input.firstName.classError ? 'error' : '']"
      />
      <img
        src="../assets/icon-error.svg"
        class="invalid-icon"
        data-for="fname"
        alt="error icon"
        v-show="input.firstName.invalidIcon"
      />
      <p
        class="invalid-p"
        data-for="fname"
        v-show="input.firstName.invalidParagraph"
      >
        {{ input.firstName.text }}
      </p>
      <br />
      <input
        class="form-input"
        type="text"
        id="lname"
        name="lname"
        :placeholder="input.lastName.placeholder"
        v-model="input.lastName.value"
        :class="[input.lastName.classError ? 'error' : '']"
      />
      <img
        src="../assets/icon-error.svg"
        class="invalid-icon"
        data-for="lname"
        alt="error icon"
        v-show="input.lastName.invalidIcon"
      />
      <p
        class="invalid-p"
        data-for="lname"
        v-show="input.lastName.invalidParagraph"
      >
        {{ input.lastName.text }}
      </p>
      <br />
      <input
        class="form-input"
        type="email"
        id="email"
        name="email"
        :placeholder="input.email.placeholder"
        v-model="input.email.value"
        :class="[input.email.classError ? 'error' : '']"
      />
      <img
        src="../assets/icon-error.svg"
        class="invalid-icon-email"
        data-for="email"
        alt="error icon"
        v-show="input.email.invalidIcon"
      />
      <p
        class="invalid-p-email"
        data-for="email"
        v-if="this.input.email.classErrorInvalid"
      >
        Looks like this is not an email
      </p>

      <p
        class="invalid-p-email"
        data-for="email"
        v-show="input.email.invalidParagraph"
        v-else
      >
        {{ input.email.text }}
      </p>

      <br />
      <input
        class="form-input"
        type="password"
        id="password"
        name="password"
        :placeholder="input.password.placeholder"
        v-model="input.password.value"
        :class="[input.password.classError ? 'error' : '']"
      />
      <img
        src="../assets/icon-error.svg"
        class="invalid-icon"
        data-for="password"
        alt="error icon"
        v-show="input.password.invalidIcon"
      />
      <p
        class="invalid-p"
        data-for="password"
        v-show="input.password.invalidParagraph"
      >
        {{ input.password.text }}
      </p>
      <br />
      <button class="claim-btn" type="submit" form="form" @click="formSubmit">
        CLAIM YOUR FREE TRIAL
      </button>

      <p class="disclaimer">
        By clicking the button, you are agreeing to our
        <strong
          ><span class="tos"><a href="#">Terms and Services</a></span></strong
        >
      </p>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: {
        firstName: {
          placeholder: "First Name",
          text: "First Name cannot be empty",
          value: "",
          invalidIcon: false,
          invalidParagraph: false,
          classError: false,
        },
        lastName: {
          placeholder: "Last Name",
          text: "Last Name cannot be empty",
          value: "",
          invalidIcon: false,
          invalidParagraph: false,
          classError: false,
        },
        email: {
          placeholder: "Email Address",
          text: "Email Address cannot be empty",
          value: "",
          invalidIcon: false,
          invalidParagraph: false,
          classError: false,
          emailRegex: /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/,
          classErrorInvalid: false,
        },
        password: {
          placeholder: "Password",
          text: "Password cannot be empty",
          value: "",
          invalidIcon: false,
          invalidParagraph: false,
          classError: false,
        },
      },
    };
  },
  computed: {
    isValidEmail() {
      return this.input.email.emailRegex.test(this.input.email.value);
    },
  },
  methods: {
    formSubmit() {
      const inputFields = ["firstName", "lastName", "email", "password"];

      inputFields.forEach((field) => {
        if (!this.input[field].value) {
          this.input[field].placeholder = "";
          this.input[field].invalidIcon = true;
          this.input[field].invalidParagraph = true;
          this.input[field].classError = true;
        }
      });
      if (!this.isValidEmail && this.input.email.value) {
        this.input.email.classErrorInvalid = true;
        this.input.email.classError = true;
        this.input.email.invalidIcon = true;
      } else {
        this.input.email.classErrorInvalid = false;
      }
    },
  },
};
</script>

<style>
.form {
  border-radius: 10px;
  background-color: hsl(0, 100%, 100%);
  box-shadow: 0px 10px 10px rgba(0, 0, 0, 0.3);
  text-align: center;
  position: relative;
  z-index: 0;
}

.form-body {
  position: relative;
  padding-left: 20px;
  min-height: 500px;
}

.try-btn {
  border-radius: 10px;
  background-color: hsl(248, 32%, 49%);
  color: hsl(0, 100%, 100%);
  padding: 20px;
  text-align: center;
  box-shadow: 0px 10px 10px rgba(0, 0, 0, 0.3);
}

.claim-btn {
  border-radius: 5px;
  background-color: hsl(154, 59%, 51%);
  color: hsl(0, 100%, 100%);
  padding: 10px 50px;
  border: none;
  width: 85%;
  height: 50px;
  font-weight: 600;
  cursor: pointer;
  box-shadow: 0 0.2em rgba(18, 166, 102);
  font-size: 15px;
}

.claim-btn:hover {
  background-color: rgba(56, 204, 140, 0.7);
}

.disclaimer {
  font-size: 10px;
  color: hsl(246, 25%, 77%);
  padding-bottom: 40px;
  font-weight: 500;
}

.tos a {
  color: hsl(0, 100%, 74%);
  text-decoration: none;
}

input {
  border: 1px solid hsl(246, 25%, 77%);
  border-radius: 5px;
  width: 80%;
  height: 40px;
  margin-bottom: 20px;
  padding-left: 20px;
  font-weight: 600;
  padding-top: 10px;
  padding-bottom: 10px;
}

input:first-of-type {
  margin-top: 40px;
}

input:focus {
  outline: 1px solid;
}

#fname.error::placeholder {
  color: transparent;
}

.error-icon {
  position: absolute;
}

.invalid-icon,
.invalid-icon-email {
  display: block;
  position: relative;
  z-index: 1;
  bottom: 65px;
  left: 500px;
}

.invalid-p,
.invalid-p-email {
  display: flex;
  font-size: 11px;
  font-style: italic;
  color: hsl(0, 100%, 74%);
  font-weight: 500;
  margin-top: -35px;
  margin-bottom: 0;
  justify-content: flex-end;
  padding-right: 55px;
}

input.error {
  border: 2px solid hsl(0, 100%, 74%);
}

.invalid-email {
  display: none;
  color: hsl(0, 100%, 74%);
  font-weight: 600;
}

input#email.form-input.error {
  color: hsl(0, 100%, 74%);
  font-weight: 700;
}

/* Mobile design */

@media only screen and (max-width: 350px) {
  .form-body {
    padding: 10px 10px 5px 10px;
  }

  .claim-btn {
    padding: 0;
    width: 90%;
  }

  .disclaimer {
    padding: 8px 40px 20px 40px;
  }

  .invalid-icon,
  .invalid-icon-email {
    position: relative;
    z-index: 1;
    bottom: 65px;
    left: 80%;
  }

  .invalid-p,
  .invalid-p-email {
    justify-content: flex-end;
    padding-right: 20px;
  }
}

@media only screen and (min-width: 351px) and (max-width: 1024px) {
  .form-body {
    padding: 10px 20px 5px 20px;
  }

  .claim-btn {
    padding: 0;
    width: 87%;
  }

  .disclaimer {
    padding: 8px 50px 20px 50px;
  }

  .invalid-icon,
  .invalid-icon-email {
    position: relative;
    z-index: 1;
    bottom: 65px;
    left: 80%;
  }
}
</style>