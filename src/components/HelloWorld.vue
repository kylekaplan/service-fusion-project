<template>
  <v-card>
    <v-card-title>
      Nutrition
      <v-spacer></v-spacer>
      <v-text-field
        v-model="search"
        append-icon="search"
        label="Search"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>
    <v-data-table
      :headers="headers"
      :items="contacts"
      :search="search"
    ></v-data-table>
  </v-card>
</template>

<script>
  import { db } from '../main'
  export default {
    data () {
      return {
        search: '',
        headers: [
          {
            text: 'First Name',
            align: 'left',
            sortable: false,
            value: 'firstName',
          },
          { text: 'Last Name', value: 'lastName' },
          { text: 'Date of Birth', value: 'dob' },
          { text: 'Addresses', value: 'addresses' },
          { text: 'Phone Numbers', value: 'phoneNumbers' },
          { text: 'Emails', value: 'emails' },
        ],
        contacts: [],
      }
    },
    firestore () {
      return {
        contacts: db.collection('contacts')
      }
    }
  }
</script>
