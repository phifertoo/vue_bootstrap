<template>
  <div id="app">
    <b-container class="bv-example-row">
      <TheNavbar />
      <b-row>
        <!-- md means columns and stack at mid-screen -->
        <b-col md="4"
          >Lorem ipsum dolor sit amet consectetur adipisicing elit. Perferendis
          temporibus quidem impedit, voluptates sit ratione. Asperiores
          reprehenderit distinctio modi non.</b-col
        >
        <b-col md="6"
          >Lorem ipsum dolor sit amet consectetur adipisicing elit. Perferendis
          temporibus quidem impedit, voluptates sit ratione. Asperiores
          reprehenderit distinctio modi non.</b-col
        >
        <b-col md="2"
          >Lorem ipsum dolor sit amet consectetur adipisicing elit. Perferendis
          temporibus quidem impedit, voluptates sit ratione. Asperiores
          reprehenderit distinctio modi non.</b-col
        >
      </b-row>
      <!-- vertical alignment: align-v -->
      <b-row align-v="center" class="height">
        <b-col>1 of 3</b-col>
        <b-col>2 of 3</b-col>
        <b-col>3 of 3</b-col>
      </b-row>
      <!-- horizontal alignment: align-h -->
      <b-row align-h="center">
        <b-col cols="4"
          ><b-button size="lg" variant="success" @click="handleClick">
            Large Button</b-button
          ></b-col
        >
        <b-col cols="4">
          <b-alert v-model="showDismissibleAlert" variant="danger" dismissible>
            Dismissible Alert!
          </b-alert></b-col
        >
      </b-row>

      <b-row>
        <div>
          <b-form @submit="onSubmit" @reset="onReset" v-if="show">
            <b-form-group
              id="input-group-1"
              label="Email address:"
              label-for="input-1"
              description="We'll never share your email with anyone else."
            >
              <b-form-input
                id="input-1"
                v-model="form.email"
                type="email"
                required
                placeholder="Enter email"
              ></b-form-input>
            </b-form-group>

            <b-form-group
              id="input-group-2"
              label="Your Name:"
              label-for="input-2"
            >
              <b-form-input
                id="input-2"
                v-model="form.name"
                required
                placeholder="Enter name"
              ></b-form-input>
            </b-form-group>

            <b-form-group id="input-group-3" label="Food:" label-for="input-3">
              <b-form-select
                id="input-3"
                v-model="form.food"
                :options="foods"
                required
              ></b-form-select>
            </b-form-group>

            <b-form-group id="input-group-4">
              <b-form-checkbox-group v-model="form.checked" id="checkboxes-4">
                <b-form-checkbox value="me">Check me out</b-form-checkbox>
                <b-form-checkbox value="that">Check that out</b-form-checkbox>
              </b-form-checkbox-group>
            </b-form-group>

            <b-button type="submit" variant="primary">Submit</b-button>
            <b-button type="reset" variant="danger">Reset</b-button>
          </b-form>
          <b-card class="mt-3" header="Form Data Result">
            <pre class="m-0">{{ form }}</pre>
          </b-card>
        </div>
      </b-row>

      <b-row>
        <b-button v-b-modal.modal-1>Launch demo modal</b-button>
        <b-button
          v-b-popover.hover.top="'I am popover directive content!'"
          title="Popover Title"
        >
          Hover Me
        </b-button>
      </b-row>

      <b-row>
        <b-table striped hover :items="items"></b-table>
      </b-row>
    </b-container>

    <b-modal id="modal-1" title="BootstrapVue">
      <p class="my-4">Hello from modal!</p>
    </b-modal>
    <TheCard />
    <div class="container">
      <div class="row">
        <div class="col">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic maxime
          quo aperiam magni! Repellat, consectetur voluptatem rem quasi
          voluptatum in!
        </div>
        <div class="col">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic maxime
          quo aperiam magni! Repellat, consectetur voluptatem rem quasi
          voluptatum in!
        </div>
        <div class="col">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic maxime
          quo aperiam magni! Repellat, consectetur voluptatem rem quasi
          voluptatum in!
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TheNavbar from "./components/TheNavbar";
import TheCard from "./components/TheCard";

export default {
  name: "app",
  components: {
    TheNavbar,
    TheCard,
  },
  data() {
    return {
      showDismissibleAlert: false,
      form: {
        email: "",
        name: "",
        food: null,
        checked: [],
      },
      foods: [
        { text: "Select One", value: null },
        "Carrots",
        "Beans",
        "Tomatoes",
        "Corn",
      ],
      show: true,
      items: [
        { age: 40, first_name: "Dickerson", last_name: "Macdonald" },
        { age: 21, first_name: "Larsen", last_name: "Shaw" },
        { age: 89, first_name: "Geneva", last_name: "Wilson" },
        { age: 38, first_name: "Jami", last_name: "Carney" },
      ],
    };
  },
  methods: {
    handleClick() {
      console.log("handling");
      this.showDismissibleAlert = true;
    },
    onSubmit(evt) {
      evt.preventDefault();
      alert(JSON.stringify(this.form));
    },
    onReset(evt) {
      evt.preventDefault();
      // Reset our form values
      this.form.email = "";
      this.form.name = "";
      this.form.food = null;
      this.form.checked = [];
      // Trick to reset/clear native browser form validation state
      this.show = false;
      this.$nextTick(() => {
        this.show = true;
      });
    },
  },
};
</script>

<style lang="scss">
.height {
  min-height: 10rem;
  background: grey;
}
</style>
