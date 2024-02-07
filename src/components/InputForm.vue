<template>
  <div class="input-form-container">
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
import { store, calculate } from '@/store/store';

const total = ref(0)
const tip = ref(0)
const people = ref(0)

const handleSubmit = () => {
    store.params.total = total
    store.params.tip = tip
    store.params.people = people
    calculate()
}

</script>

<style scoped>
    .input-form-container {
        color: #fff;
        font-size: 1.6rem;
    }

    input {
        margin: 0 .4rem .7rem .8rem;
    }

    .form-content {
        display: flex;
        align-items: center;
        justify-content: right;
    }

    
</style>