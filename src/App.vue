<script setup>
import { ref, computed } from "vue";
import contacts from "./contacts.json";

const contactsList = ref(contacts);
//console.log(contactsList);

//para solo mostrar 5
const fiveContacts = computed(() => {
  return contactsList.value.slice(0, 5);
});
console.log(fiveContacts);
</script>

<template>
  <section>
    <h1>Iron-Contacts</h1>
    <table class="table">
      <tr>
        <th>Picture</th>
        <th>Name</th>
        <th>Popularity</th>
        <th>Won an Oscar</th>
        <th>Won an Emmy</th>
      </tr>
      <tr v-for="contact in fiveContacts">
        <!-- otra forma <tr v-for="(contact, index) in contactsList" :key="index" v-if="index < 5"> -->
        <td><img :src="contact.pictureUrl" /></td>
        <td>{{ contact.name }}</td>
        <td>{{ contact.popularity }}</td>
        <td>{{ contact.wonOscar ? "🏆" : "" }}</td>
        <td>{{ contact.wonEmmy ? "🏆" : "" }}</td>
      </tr>
    </table>
  </section>
</template>

<style scoped>
section {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.table {
  border-collapse: collapse;
  width: 70%;
  margin: 20px;
}
th,
td {
  padding: 10px;
  border: 1px solid #ddd;
  text-align: center;
}
.table img {
  width: 100px;
  height: auto;
}
</style>
