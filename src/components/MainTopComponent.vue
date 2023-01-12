
<script>
export default {
    name:'MainTopComponent',
    data() {
        return {
            value: null,
          
        }
    },
    
}
</script>

<template>
   <div>
    <select v-model="value" @change="$emit('selectTypeArch', value)">
        <option> Select a </option>
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