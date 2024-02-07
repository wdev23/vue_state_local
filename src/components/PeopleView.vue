<template>
  <div class="people_container">

    <div class="no-items" v-if="store.people.length === 0">No items</div>
    <div class="people-view" v-if="store.people.length > 0">

      <div class="header_container">
        <div class="header_content">
          <Label title="Total + Tip: " :value="getGrandTotal"/>
          <h3>{{ getGrandTotal() }}</h3>
        </div>
        <div class="header_content">
          <Label title="Remaining: " :value="store.params.remaining"/>
        </div>
      </div>

      <div class="people-content">
        <div>
          <Person 
          v-for="person in store.people" :key="person.id"
          :id="person.id" :number-of-person="person.numberOfPerson" :total-per-person="person.totalPerPerson" :paid="person.paid"/>
        </div>
      </div>

    </div>
  </div>
</template>

<script setup>
  import { store, getGrandTotal } from '@/store/store';  
  import Label from './Label.vue';
import Person from './Person.vue';
</script>

<style scoped>

  .people_container{
    color: #fff;
    font-size: 1.6rem;
  }
  .h3 {
    color: inherit;
  }
</style>
