<template>
    <h3>History</h3>
    <ul id="list" class="list" :class="transactions.length > 3 ? 'overflow' : null">
        <li v-for="transaction in transactions" :key="transaction.id" :class="transaction.amount < 0 ? 'minus' : 'plus'">
            {{
                transaction.text }} <span>₱{{ Intl.NumberFormat().format(transaction.amount)
    }}</span><button @click="deleteTransaction(transaction.id)" class="delete-btn">x</button></li>
    </ul>
</template>

<script setup>
import { defineProps } from 'vue';

const emit = defineEmits(['transactionDeleted'])

const props = defineProps({
    transactions: {
        type: Array,
        required: true
    }
})

const deleteTransaction = (id) => {
    emit('transactionDeleted', id)
}

</script>

<style lang="scss" scoped></style>