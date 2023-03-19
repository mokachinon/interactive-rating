<template>
  <div>
    <div class="body">
      <div class="container" v-if="!ratingModal">

        <!-- Rating state start -->
        <div class="round">
          <img src="~/static/images/icon-star.svg" alt="icon-star" class="icon-star" />
        </div>
        <h2 class="title">How did we do?</h2>
        <p>
          Please let us know how we did with your support request. All feedback is appreciated
          to help us improve our offering!
        </p>
        <div class="btn-flex">
          <div class="btn-review" v-for="number in 5" :key="number" :class="{ 'btn-active': activeButton === number }">
            <input type="button" :value="number" @click="handleClick(number)" />
          </div>
        </div>
        <div class="btn-submit" @click="submitRating">
          <button>Submit</button>
        </div>
      </div>
      <div class="pop-up" v-if="ratingModal">
        <img src="~static/images/illustration-thank-you.svg" alt="thankyou" class="img-popup">
        <div class="text-content">
          <p class="text orange">You selected {{ activeButton }} out of 5</p>
        </div>
        <h2 class="title">Thank You!</h2>
        <p class="text grey">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Nemo, doloremque deleniti! Dolor,
          deleniti.
          Laudantium modi et cum consequuntur, harum sit veritatis eos ea hic natus.</p>
      </div>
    </div>
    <attribution />
  </div>
</template>
<script>
export default {
  data() {
    return {
      activeButton: null,
      ratingModal: false
    };
  },
  methods: {
    handleClick(number) {
      if (this.activeButton === number) {
        this.activeButton = null;
      } else {
        this.activeButton = number;
      }
    },
    submitRating() {
      if (this.activeButton) {
        this.ratingModal = true;
      } else {
        alert("Please Choose a Number")
      }
    }
  }
};
</script>
<style scoped>
.body {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 50px;
}

.container {
  box-shadow: 0px 151px 60px rgba(0, 0, 0, 0.01), 0px 85px 51px rgba(0, 0, 0, 0.05), 0px 38px 38px rgba(0, 0, 0, 0.09), 0px 9px 21px rgba(0, 0, 0, 0.1), 0px 0px 0px rgba(0, 0, 0, 0.1);
  background: radial-gradient(150.12% 150.12% at 50% -50.12%, rgba(34, 41, 50, 0.9) 1.73%, #171E28 79.84%), #FFFFFF;
  max-width: 412px;
  max-height: 415px;
  width: 100%;
  height: 100%;
  border-radius: 10px;
  padding: 32px;
  gap: 34px;
  display: flex;
  flex-direction: column;
}

.pop-up {
  box-shadow: 0px 151px 60px rgba(0, 0, 0, 0.01), 0px 85px 51px rgba(0, 0, 0, 0.05), 0px 38px 38px rgba(0, 0, 0, 0.09), 0px 9px 21px rgba(0, 0, 0, 0.1), 0px 0px 0px rgba(0, 0, 0, 0.1);
  background: radial-gradient(150.12% 150.12% at 50% -50.12%, rgba(34, 41, 50, 0.9) 1.73%, #171E28 79.84%), #FFFFFF;
  max-width: 412px;
  max-height: 415px;
  width: 100%;
  height: 100%;
  border-radius: 10px;
  padding: 32px;
  gap: 34px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.round {
  width: 51px;
  height: 51px;
  border-radius: 50%;
  background-color: var(--mediumGrey);
  display: flex;
  justify-content: center;
  align-items: center;
}

.title {
  font-weight: var(--fwBold);
  color: var(--white);
}

p,
span,
button {
  font-size: var(--forParagraph);
  color: var(--lightGrey)
}

.btn-flex {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
}

.btn-submit {
  width: 100%;
  max-width: 341px;
  max-height: 44px;
  height: 100%;
  border-radius: 30px;
  background-color: var(--orange);
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn-submit button {
  color: var(--white);
  background: none;
  border: none;
  padding: 44px;
}

.btn-submit:hover {
  background-color: var(--orange2);
  cursor: pointer;

}

.text {
  color: var(--pureGrey)
}

.btn-review {
  width: 51px;
  height: 51px;
  border-radius: 50%;
  background: var(--veryDarkBlueOpt);
  display: flex;
  justify-content: center;
  align-items: center;
}


.btn-review:hover {
  background-color: var(--mediumGrey);
  cursor: pointer;
}

.btn-active {
  background-color: var(--orange);
}

.btn-active:hover {
  cursor: pointer;
  background-color: var(--orange2);
}

.orange {
  color: var(--orange);
}

.btn-review input {
  border: none;
  background: none;
  width: 51px;
  height: 51px;
  color: var(--white);
}

.img-popup {
  margin-bottom: -20px;
  width: 50%;
}

.text-content {
  padding: 10px;
  background-color: var(--darkBlue);
  border-radius: 100px;
  width: 193px;
}

.grey {
  color: var(--mediumGrey);
  margin-top: -20px;
}

@media screen and (max-width: 375px) {
  .body {
    box-sizing: border-box;
  }

  .container {
    width: 327px;
    height: 360px;
    gap: 22px;
    padding: 24px;
  }

  .round {
    width: 42px;
    height: 42px;
  }

  .btn-review button {
    width: 42px;
    height: 42px;
  }

  .btn-submit {
    width: 279px;
    height: 45px;
  }
}
</style>


