<template>
  <form @submit.prevent="register">
    <div class="container">
      <div class="input__group">
        <label for="email">Email</label>
        <input
          v-model.trim="email.val"
          :class="{ invalid: !email.isValid }"
          @blur="clearValidity('email')"
          type="text"
        />
        <p v-if="!email.isValid">Wpisz Email.</p>
      </div>
      <div class="input__group">
        <label for="email">Card information</label>
        <div class="card__group">
          <input
            :class="{ invalid: !cardInfo.isValid }"
            @blur="clearValidity('cardInfo')"
            placeholder="1234 1234 1234 1234"
            type="text"
            class="number"
            v-model.trim="cardInfo.val"
          />
          <input placeholder="MM / YY" type="text" class="expired" />
          <input placeholder="CVC" type="text" class="cvc" />
        </div>
        <p v-if="!cardInfo.isValid">Wrong Card info</p>
      </div>
      <div class="input__group">
        <label for="name">Name on card</label>
        <input
          v-model.trim="name.val"
          :class="{ invalid: !name.isValid }"
          @blur="clearValidity('name')"
          type="text"
        />
        <p v-if="!name.isValid">wrong Name</p>
      </div>
      <div class="input__group">
        <label for="email">Country or region</label>
        <select
          v-model.trim="country.val"
          :class="{ invalid: !country.isValid }"
          @blur="clearValidity('country')"
          name="country__select"
          id="country__select"
        >
          <option value="Poland">Poland</option>
          <option value="Germany">Germany</option>
          <option value="United States">United States</option>
          <option value="Ukraine">Ukraine</option>
          <option value="Czech Rebublic">Czech Rebublic</option>
        </select>
        <p v-if="!email.isValid">Choose country</p>
      </div>
      <button>Pay</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      name: {
        val: '',
        isValid: true,
      },
      email: {
        val: '',
        isValid: true,
      },
      cardInfo: {
        val: '',
        isValid: true,
      },
      country: {
        val: '',
        isValid: true,
      },
      formIsValid: true,
    };
  },
  methods: {
    clearValidity(input) {
      this[input].isValid = true;
    },
    register() {
      this.validateForm();
    },
    showModal() {
      if (!this.formIsValid) {
        alert('form is invalid');
      } else {
        alert('form is valid');
      }
    },
    validateForm() {
      this.formIsValid = true;
      if (this.name.val === '') {
        this.name.isValid = false;
        this.formIsValid = false;
      }
      if (this.cardInfo.val === '' || this.cardInfo.val.length !== 16) {
        this.cardInfo.isValid = false;
        this.formIsValid = false;
      }
      if (this.email.val === '' || !this.email.val.includes('@')) {
        this.email.isValid = false;
        this.formIsValid = false;
      }
      if (this.country.val === '') {
        this.country.isValid = false;
        this.formIsValid = false;
      }
      this.showModal();
    },
  },
};
</script>

<style scoped>
.temp {
  width: 100%;
  display: flex;
  align-items: flex-start;
}
.container {
  position: relative;
  min-width: 400px;
  min-height: 700px;
  padding-inline: 1rem 2rem;
  height: auto;
  background-color: rgba(255, 255, 255, 1);
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
  flex-direction: column;
  padding: 1rem;
  gap: 30px;
  box-shadow: 4px 4px 10px rgba(0, 0, 0, 0.25);
  border-radius: 4px;
  z-index: 20;
}
.input__group {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 2px;
  width: 100%;
}
.card__group {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: repeat(2, 1fr);
  grid-column-gap: 0px;
  grid-row-gap: 0px;
}
label {
  font-weight: 400;
}
.number {
  grid-area: 1 / 1 / 2 / 3;
}
.expired {
  grid-area: 2 / 1 / 3 / 2;
}
.cvc {
  grid-area: 2 / 2 / 3 / 3;
}
input {
  font-family: 'Poppins', sans-serif !important;
  font-size: 1rem;
  outline: none !important;
  border: 1px rgb(185, 184, 184) solid;
  background-color: transparent;
  padding: 0.6rem;
  color: rgb(185, 184, 184);
}
option,
select {
  font-family: 'Poppins', sans-serif !important;
  font-size: 1rem;
  outline: none !important;
  border: 1px rgb(185, 184, 184) solid;
  background-color: transparent;
  padding: 0.6rem;
  color: rgb(185, 184, 184);
  width: 100%;
}
input,
option,
select {
}
button {
  margin-top: 120px;
  bottom: 16%;
  width: 100%;
  left: 1rem;
  padding: 0.7rem;
  border: none;
  background-color: #1e1d5c;
  color: white;
  font-size: 1rem;
  border-radius: 6px;
  cursor: pointer;
  transition: 0.3s all;
  box-shadow: 4px 4px 10px rgba(0, 0, 0, 0.25);
}
button:hover {
  box-shadow: none;
}
p {
  width: 100%;
  color: rgba(179, 23, 23, 0.486) !important;
  font-size: 0.7rem;
}
.invalid {
  color: rgba(179, 23, 23, 0.486) !important;
  border: 1px solid rgba(179, 23, 23, 0.486) !important;
}
</style>
