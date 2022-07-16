<template>
    <input type="text" class="search" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)">
</template>

<script>
export default {
    name: 'SearchInput',
    props: {
        modelValue: {
            type: String,
            default: ''
        }
    },
}
</script>

<style scoped>
.search {
    margin: 15px 0;
}
</style>