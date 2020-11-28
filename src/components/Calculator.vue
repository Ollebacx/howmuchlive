<template>
  <v-container class="max">
    <v-row class="text-center">
      <v-col cols="12">
        <!-- <v-text-field
                  label="Amount"
                  solo
                  prepend-inner-icon="mdi-wallet-travel"
                  hint="10.00"
                  persistent-hint
                  clearable
                  @keypress="validate(event)"
                ></v-text-field> -->
                <p>How much money does it cost?</p>
      <vuetify-money
        class="text-right"
        v-model="amount"
        :options="options"
        :properties="propertiesAmount"
        :clearable="clearable"
        placeholder="1200"
        autofocus=true
       />
      </v-col>

        <v-col cols="12" class="mb-0 pb-0">
          <p>How much is your income?</p>
        <vuetify-money
          class="text-right mb-0 pb-0"
          v-model="salary"
          :options="options"
          :properties="propertiesSalary"
          :clearable="clearable"
          :placeholder="placeholder"
        />
        <v-select
          id="textComputer"
          class="purple darken-2 px-3 mt-0 pt-0"
          :items="items"
          v-model="salarySelection"
        ></v-select>
        </v-col>

        <v-col cols="12" class="mb-0 pb-0">
          <p>How many hours you work?
</p>
        <vuetify-money
          class="text-right mb-0 pb-0"
          v-model="salary"
          :options="options"
          :properties="propertiesSalary"
          :clearable="clearable"
          :placeholder="placeholder"
        />
        <v-select
          id="textComputer"
          class="purple darken-2 px-3 mt-0 pt-0"
          :items="items"
          v-model="salarySelection"
        ></v-select>
        </v-col>

  </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Calculator",
  data: () => ({
    amount: "",
    salary:"",
    salarySelection: "monthly",
    items: ["yearly","monthly","daily", "hourly"],
    placeholder: "",
    readonly: false,
    disabled: false,
    outlined: true,
    clearable: true,
    valueWhenIsEmpty: "",
    options: {
      locale: "fr-FR",
      prefix: "",
      suffix: "",
      length: 9,
      precision: 0
    },
    propertiesAmount: {
      // hint: "How much money does it cost?",
      // "persistent-hint":true,
      "append-icon": "mdi-currency-eur",
      // solo: true
      // You can add other v-text-field properties, here.
    },
    propertiesSalary: {
      "append-icon": "mdi-arrow-down-bold-box",
      // You can add other v-text-field properties, here.
    },
  }),
  methods: {
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
.max{
  max-width: 400px;
}
.text-right {
  direction: rtl;
}
#textComputer {
  font-size: 24px !important;
}
</style>