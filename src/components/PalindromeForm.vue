<template>
  <div>
    <p>Please enter text to check for a palindrome.</p>
    <input v-model="userText" type="text" @input="onUserInput" />
    <button :disabled="!hasUserText" v-if="!autoCheck" @click="checkUserText">
      Check
    </button>
    <p :class="resultsClass">{{ resultsText }}</p>
  </div>
</template>

<script>
export default {
  name: "PalindromeForm",
  props: {
    autoCheck: Boolean,
  },
  data() {
    return {
      isPalindrome: undefined,
      userText: "",
    };
  },
  computed: {
    hasUserText() {
      return this.userText.trim() !== "";
    },
    resultsClass() {
      return this.isPalindrome ? "successText" : "failureText";
    },
    resultsText() {
      if (this.isPalindrome === undefined) {
        return "";
      }
      return this.isPalindrome ? "Is a palindrome!" : "Is not a palindrome.";
    },
  },
  methods: {
    onUserInput() {
      this.isPalindrome = undefined;
      if (this.autoCheck) {
        this.checkUserText();
      }
    },
    checkUserText() {
      if (this.hasUserText) {
        let reversedUserText = this.userText.split("").reverse().join("");
        this.isPalindrome = this.userText === reversedUserText;
      } else {
        this.isPalindrome = undefined;
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.successText {
  color: green;
}
.failureText {
  color: red;
}
</style>
