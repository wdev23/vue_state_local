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

      <div>
        <div class="people-content">
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

.people_container {
  font-size: 1.6rem;
}
.no-items {
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
}

.people-view {
  margin: 0;
  display: flex;
  align-items: center;
  flex-direction: column;
}

.people-content {
  width: 800px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: auto;
}

.header {
  color: #fff;
  font-weight: bolder;
  padding: 20px 0;
  font-size: 2.8rem;
  display: flex;
  justify-content: space-between;
  gap: 10px;
  flex-direction: column;
}
</style>
