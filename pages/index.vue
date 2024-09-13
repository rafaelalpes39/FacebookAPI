<script setup lang="ts">
import { ref } from "vue";

const headers = [
  {
    key: "date",
    title: "Date",
    align: "center",
    sortable: true,
    width: "120px",
  },
  { key: "app", title: "App", align: "center", width: "100px" },
  {
    key: "serviceFeeConsumption",
    title: "Service fee Consumption",
    align: "center",
  },
  { key: "consumption", title: "Consumption", align: "center" },
  { key: "refluxConsumption", title: "Reflux consumption", align: "center" },
  { key: "register", title: "Register", align: "center" },
  { key: "registrationCosts", title: "Registration Costs", align: "center" },
  {
    key: "firstChargeQuantity",
    title: "First charge quantity",
    align: "center",
  },
  { key: "firstChargeCost", title: "First charge cost", align: "center" },
  { key: "actualRegistration", title: "Actual registration", align: "center" },
  {
    key: "actualRegistrationCost",
    title: "Actual registration cost",
    align: "center",
  },
  {
    key: "actualFirstChargeQuantity",
    title: "Actual first charge quantity",
    align: "center",
  },
  {
    key: "actualFirstChargeCost",
    title: "Actual first charge cost ($)",
    align: "center",
  },
];

const dialog = ref(false);
// Define data for the data table
const Datafetch = ref([
  {
    date: "2024-09-02",
    serviceFeeConsumption: 60,
    app: "https://example.com/app2/overvieasdfasdfasdfasdfkasdfl;aksdfal;kdflasdf;lasdf;aksdjfklajsdfkjasdklfjas;ldkfjalsdkjfw",
    consumption: 110,
    refluxConsumption: 15,
    register: 6,
    registrationCosts: 25,
    firstChargeQuantity: 3,
    firstChargeCost: 35,
    actualRegistration: 5,
    actualRegistrationCost: 20,
    actualFirstChargeQuantity: 2,
    actualFirstChargeCost: 30,
  },
  {
    date: "2024-09-03",
    app: "https://anotherdomain.org/app1/dashboard",
    serviceFeeConsumption: 75,
    consumption: 130,
    refluxConsumption: 20,
    register: 7,
    registrationCosts: 30,
    firstChargeQuantity: 4,
    firstChargeCost: 40,
    actualRegistration: 6,
    actualRegistrationCost: 25,
    actualFirstChargeQuantity: 3,
    actualFirstChargeCost: 35,
  },
  {
    date: "2024-09-04",
    app: "https://myappsite.net/app3/details",
    serviceFeeConsumption: 50,
    consumption: 100,
    refluxConsumption: 10,
    register: 5,
    registrationCosts: 20,
    firstChargeQuantity: 2,
    firstChargeCost: 30,
    actualRegistration: 4,
    actualRegistrationCost: 15,
    actualFirstChargeQuantity: 1,
    actualFirstChargeCost: 25,
  },
  {
    date: "2024-09-05",
    app: "https://services.example.com/app4/info",
    serviceFeeConsumption: 65,
    consumption: 120,
    refluxConsumption: 18,
    register: 8,
    registrationCosts: 28,
    firstChargeQuantity: 5,
    firstChargeCost: 45,
    actualRegistration: 7,
    actualRegistrationCost: 22,
    actualFirstChargeQuantity: 4,
    actualFirstChargeCost: 40,
  },
  {
    date: "2024-09-06",
    app: "https://coolapps.org/app5/statistics",
    serviceFeeConsumption: 55,
    consumption: 115,
    refluxConsumption: 12,
    register: 6,
    registrationCosts: 26,
    firstChargeQuantity: 3,
    firstChargeCost: 32,
    actualRegistration: 6,
    actualRegistrationCost: 18,
    actualFirstChargeQuantity: 3,
    actualFirstChargeCost: 28,
  },
]);
</script>

<template>
  <fieldset class="fieldset-container">
    <legend class="fieldset-title">Filter by condition</legend>
    <v-form>
      <v-container>
        <v-row>
          <v-col cols="12" md="2">
            <span class="text-xs">Date</span>
            <input
              type="date"
              class="w-full rounded-lg px-6 py-2 border border-gray-300 text-gray-700 focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-200"
            />
          </v-col>
          <v-col cols="12" md="2">
            <span class="text-xs">Date</span>
            <input
              type="date"
              class="w-full rounded-lg px-6 py-2 border border-gray-300 text-gray-700 focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-200"
            />
          </v-col>

          <v-col cols="12" md="3">
            <span class="text-xs">App</span>
            <v-select
              density="compact"
              variant="outlined"
              :items="[
                'California',
                'Colorado',
                'Florida',
                'Georgia',
                'Texas',
                'Wyoming',
              ]"
            ></v-select>
          </v-col>

          <v-col cols="12" md="3">
            <span class="text-xs">Promotion Method</span>
            <v-select
              density="compact"
              variant="outlined"
              :items="[
                'California',
                'Colorado',
                'Florida',
                'Georgia',
                'Texas',
                'Wyoming',
              ]"
            ></v-select>
          </v-col>

          <v-col cols="12" md="1">
            <div class="flex pt-6 gap-5">
              <div>
                <v-btn class="flex-1" variant="elevated" color="primary">
                  Query
                </v-btn>
              </div>
              <div>
                <v-btn class="flex-1" variant="outlined">Reset</v-btn>
              </div>
            </div>
          </v-col>
        </v-row>
      </v-container>
    </v-form>
  </fieldset>

  <div class="pa-4">
    <v-table density="compact" class="v-table-border">
      <thead>
        <tr>
          <th class="text-center">Consumption</th>
          <th class="text-center">Balance</th>
          <th class="text-center">Service Fee</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="text-center">$50</td>
          <td class="text-center">$200</td>
          <td class="text-center">$30</td>
        </tr>
      </tbody>
    </v-table>
  </div>

  <div class="pa-4">
    <v-data-table
      :headers="headers"
      :items="Datafetch"
      height="500px"
      fixed-header
    >
      <template v-slot:item="{ item, index }">
        <tr class="text-center">
          <td>
            {{ item.date }}
          </td>
          <td class="cursor-pointer">
            <modal :status="dialog" :item.app />
          </td>
          <td>{{ item.serviceFeeConsumption }}</td>
          <td>{{ item.consumption }}</td>
          <td>{{ item.refluxConsumption }}</td>
          <td>{{ item.register }}</td>
          <td>{{ item.registrationCosts }}</td>
          <td>{{ item.firstChargeQuantity }}</td>
          <td>{{ item.firstChargeCost }}</td>
          <td>{{ item.actualRegistration }}</td>
          <td>{{ item.actualRegistrationCost }}</td>
          <td>{{ item.actualFirstChargeQuantity }}</td>
          <td>{{ item.actualFirstChargeCost }}</td>
        </tr>
      </template>
    </v-data-table>
  </div>
</template>

<style scoped>
.fieldset-container {
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 10px;
  margin: 16px;
}

.fieldset-title {
  font-size: 1.25em;
  font-weight: bold;
  margin-bottom: 12px;
  color: #212121; /* Changed to gray color */
}
.v-table-border th,
.v-table-border td {
  border: 1px solid #ddd; /* Light gray border */
}
</style>
