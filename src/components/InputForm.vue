<template>
  <div>
    <form action="" @submit.prevent="handleSubmit">
        <div class="form-container">
            <div class="form-content">
                <label for="total">Total</label>
                <input type="number" id="total" required v-model="total" />
            </div>

            <div class="form-content">
                <label for="tip">Tip %</label>
                <input type="number" id="tip" required v-model="tip" />
            </div>

            <div class="form-content">
                <label for="people">People</label>
                <input type="number" id="people" required v-model="people" />
            </div>

            <div class="btn_submit">
                <input type="submit" value="Calculate">
            </div>
        </div>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { store } from '@/store/store';

const total = ref('')
const tip = ref('')
const people = ref('')

const handleSubmit = () => {
    store.params.total = total
    store.params.tip = tip
}

</script>

<style scoped>

</style>