<template>
  <div class="flex flex-col justify-center justify-items-center">
    <input
      placeholder=" Define your First and Secod name please. ? "
      class="InputName"
      name="name"
      id="name"
      v-model="name"
    />
    <button
      @click="checkName"
      class="button p-1 mt-1 rounded hover:bg-white hover:text-orange-500 bg-orange-500 text-white"
    >
      Continue
    </button>
    <p v-show="show" class="text-white p-2 bg-indigo-500 rounded mt-2 p-1">
      {{ `${CheckedName}` }}
      <button
        v-show="isValidName"
        @click="$emit('valid')"
        class="button p-1 mt-1 rounded hover:bg-white hover:text-red-500 bg-red-500 text-white"
      >
        Next step
      </button>
    </p>
  </div>
</template>

<script>
export default {
  data: function () {
    name: "Question1";

    return {
      name: "",
      show: false,
      CheckedName: "",
      isValidName: false,
    };
  },
  methods: {
    checkName() {
      const name = this.name.toUpperCase();
      if (name != "LARA GRAZIELA") {
        this.CheckedName =
          "Access denied. These name is invalid for users system";
        this.show = true;
        this.isValidName = false;
      }
      if (name == "LARA GRAZIELA") {
        this.feedBackStyle = "text-white p-2 red-600 rounded mt-2 p-1";
        this.CheckedName =
          "Woooool! You here baby ? Welcome to the little love machine online hehehe";
        this.show = true;
        this.isValidName = true;
      }
      if (name == "NATAN MARTINS") {
        this.CheckedName =
          "Hello Natan. Thank you for create me! But let another user enter in the system!";
        this.show = true;
        this.isValidName = false;
      }

      setTimeout(() => {
        console.log("this is the first message");
      }, 5000);
      return this.CheckedName;
    },
  },
};
</script>

<style>
.button {
  width: 100px;
}
.InputName {
  width: 400px;
}
</style>