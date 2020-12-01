<template>
  <v-container class="max mt-n9">
    <!-- elevation-18 -->
    <!-- <v-app-bar
      flat
      class="mb-5 navbar"
      color="transparent"
    >
      <h1 class="name"><b>LifePay</b><span class="light">Calculator</span></h1>
    </v-app-bar> -->
    <v-row class="mb-n8 pa-3">
      <v-col cols="12" class="mb-n8">
        <!-- <v-text-field
                  label="Amount"
                  solo
                  prepend-inner-icon="mdi-wallet-travel"
                  hint="10.00"
                  persistent-hint
                  clearable
                  @keypress="validate(event)"
                ></v-text-field> -->
        <p>Total price</p>
      </v-col>
      <v-col cols="12">
        <vuetify-money
          class="inputMoney first"
          v-model="amount"
          :options="options"
          :properties="propertiesAmount"
          placeholder="e.g. 800"
          outlined
        />
      </v-col>
    </v-row>
    <v-row class="pa-3">
      <v-col cols="12" class="mb-n8">
        <p>Your salary</p>
      </v-col>
      <v-col cols="12">
        <vuetify-money
          class="inputMoney mb-n6"
          v-model="salary"
          :options="options"
          :properties="propertiesSalary"
          :clearable="clearable"
          placeholder="e.g. 20"
          outlined
        />
        <v-chip-group
          active-class="primary--text elevation-8"
          column
          center-active
          mandatory
          v-model="salaryOption"
          class="visible"
        >
          <v-chip v-for="(item, idx) in itemsSalary" :key="idx" filter outlined>
            {{ item }}
          </v-chip>
        </v-chip-group>
      </v-col>
    </v-row>
    <v-row class="pa-3">
      <v-col cols="12" class="mb-n8">
        <p>Hours you work</p>
      </v-col>

      <v-col cols="12">
        <vuetify-money
          class="inputMoney mb-n6"
          v-model="hours"
          :options="options"
          :properties="propertiesHours"
          :clearable="clearable"
          placeholder="e.g. 8"
          outlined
          rounded
        />
        <!-- <v-select
          :items="items"
          v-model="salarySelection"
          dense
          rounded
          outlined
          chips
          tags
        ></v-select> -->
        <v-chip-group
          active-class="primary--text elevation-8"
          column
          mandatory
          v-model="hourOption"
          class="visible"
        >
          <v-chip v-for="(item, idx) in itemsHours" :key="idx" filter outlined>
            {{ item }}
          </v-chip>
        </v-chip-group>
      </v-col>
    </v-row>
    <v-btn
      class="btn py-6 mb-3 elevation-12"
      rounded
      dark
      block
      x-large
      @click="calculate()"
      >Calculate</v-btn
    >
  </v-container>
</template>

<script>
export default {
  name: "Calculator",
  data: () => ({
    amount: "",
    salary: "",
    itemsSalary: ["hourly", "daily", "monthly", "yearly"],
    salaryOption: "",
    hours: "",
    itemsHours: ["daily", "weekly", "monthly"],
    hourOption: "",
    salaryPerHour: "",
    dailyHours:"",
    clearable: true,
    options: {
      locale: "fr-FR",
      prefix: "",
      suffix: "",
      length: 9,
      precision: 0,
    },
    propertiesAmount: {
      autofocus: true,
    },
    propertiesSalary: {
      "prepend-inner-icon": "mdi-cash",
      rounded: true,
    },
    propertiesHours: {
      "prepend-inner-icon": "mdi-clock",
      rounded: true,
    },
  }),
  methods: {
    calculate() {
      console.log(
        this.amount,
        this.salary,
        this.itemsSalary[this.salaryOption],
        this.hours,
        this.itemsHours[this.hourOption]
      );
      if (this.salary) {
        if (
          (this.itemsSalary[this.salaryOption] === this.itemsSalary[0]) ===
          "hourly"
        ) {
          this.salaryPerHour = this.salary;
        } else if (
          (this.itemsSalary[this.salaryOption] === this.itemsSalary[1]) ===
          "daily"
        ) {
          this.salaryPerHour = this.salary / this.dailyHours;
        } else if (
          (this.itemsSalary[this.salaryOption] === this.itemsSalary[1]) ===
          "monthly"
        ) {
          this.salaryPerHour = (this.salary / 22) / this.dailyHours;
        }
      }
    },
    // validate(content) {
    //   var theEvent = content || window.event;
    //   // Handle paste
    //   if (theEvent.type === 'paste') {
    //       key = event.clipboardData.getData('text/plain');
    //   } else {
    //   // Handle key press
    //       var key = theEvent.keyCode || theEvent.which;
    //       key = String.fromCharCode(key);
    //   }
    //   var regex = /[0-9]|\./;
    //   if( !regex.test(key) ) {
    //     theEvent.returnValue = false;
    //     if(theEvent.preventDefault) theEvent.preventDefault();
    //   }
    // }
  },
};
</script>

<style scoped>
.max {
  max-width: 450px;
  width: 100vw;
  background-color: #e9edf1f8;
  /* border-radius: 30px; */
  padding: 3vh 1vw;
  /* margin: 4vh; */
  /* border: 1px solid blue; */
}
.navbar {
  height: 50px !important;
  justify-content: center;
  align-items: flex-end;
  text-align: center;
}
.name {
  font-size: 2.8em;
  /* background-color: blue; */
  width: 400px;
  color:blue;
  font-weight: 800;
}
.light {
  font-weight: 400;
  color:blue;
  /* color: rgb(31, 31, 31); */
}
p {
  font-size: 1.2em;
  font-weight: 400;
}
.inputMoney >>> input {
  /* font-family: "Teko", sans-serif; */
  font-size: 1.6em;
  color: blue !important;
  font-weight: 400;
  padding: 15px;
}
.first >>> input {
  /* font-family: "Teko", sans-serif; */
  font-size: 3.6em;
  color: blue !important;
  font-weight: 500;
  min-height: 80px !important;
  text-align: right;
  padding: 20px;
}
.visible {
  /* background-color: red; */
  height: 70px;
  width: 100%;
}
.v-chip.v-chip--outlined.v-chip.v-chip {
  padding: 20px;
  margin: 0px 10px 0px 0px !important;
  border-radius: 50px !important;
  opacity: 0.5;
  background-color: blue !important;
  color: white !important;
}
.primary--text {
  opacity: 1 !important;
}
.btn {
  /* background-image: linear-gradient( 170deg, rgb(190, 1, 190) 10%, blue 100%); */
  background-color: blue !important;
  color: white;
  font-weight: 900 !important;
}
.btn:active {
  box-shadow: none !important;
}
</style>
