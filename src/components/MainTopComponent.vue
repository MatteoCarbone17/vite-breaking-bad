
<script>
export default {
    name:'MainTopComponent',
    data() {
        return {
            value : 1 
        }
    },
    
}
</script>

<template>
   <div>
    <select v-model="value" @input="$emit('selectTypeArch', value)">
        <option :value="null"> Select a ... </option>
        <option v-for="option in options" :value="option.slug"> </option>
    </select> 
   </div>
</template>

<style lang="scss" scoped>
    div{
        width: 100%;
        background-color: rgb(212, 143, 56);
        display: flex;
        justify-content: center;
        select{
            margin-top: 50px;
        }
      
    }
</style>