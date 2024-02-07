<template>
    <div :class="['person', props.paid ? 'person-paid' : 'person-no-paid']">
        <div class="person-number">
            Person {{ props.numberOfPerson }}
        </div>
        <div class="peson-to-pay">
            {{
                new Intl.NumberFormat('en-US', {
                    style: 'currency',
                    currency: 'USD',
                }).format(props.totalPerPerson)
            }}
        </div>
        <div class="paid">
            <input type="checkbox" name="" id="" @change="handleChange" /> Paid
        </div>
    </div>
</template>

<script setup>
import { defineProps, ref } from 'vue';
import { pay } from '@/store/store';

const props = defineProps(['id', 'numberOfPerson', 'totalPerPerson', 'paid'])
let paid = ref(false)

const handleChange = (e) => {
    paid = e.target.checked

    pay(props.id, paid)
}

</script>

<style scoped>
.person {
    height: 200px;
    border-radius: 5px;
    font-size: 2rem;
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    justify-content: space-between;
    overflow: hidden;
}

.person-paid {
    border: solid 3px yellowgreen;
}

.person-no-paid {
    border: solid 3px #ccc;
}
</style>