<template>
    <tr>
        <td>{{this.monster.name}}</td>
        <td>{{this.monster.icon}} {{this.monster.type}}</td>
        <td>{{this.monster.strength}}</td>
        <td>{{this.monster.health.current}}</td>
        <td>{{this.monster.special}}</td>
        <td>
            <div class="d-flex justify-content-around">
                <button class="btn btn-outline-success" @click="increaseHealth"><i class="fas fa-long-arrow-alt-up"></i> <i class="fas fa-medkit"></i></button>
                <button class="btn btn-outline-warning" @click="decreaseHealth"><i class="fas fa-long-arrow-alt-down"></i> <i class="fas fa-medkit"></i></button>
                <button class="btn btn-outline-danger" @click="deleteMonster"><i class="far fa-trash-alt"></i></button>
            </div>
        </td>
    </tr>
</template>

<script>
    export default {
        name: "Monster",
        props:['monster'],
        methods:{
            increaseHealth(){
                if(this.monster.health.current<this.monster.health.max) {
                    this.monster.health.current++;
                    alert('Increased health');
                }
                else
                {
                    alert('Health is already at max');
                }
            },
            decreaseHealth(){
                if(this.monster.health.current>1) {
                    this.monster.health.current--;
                    alert('Decreased health');
                }
                else
                {
                    if(confirm('Do you want to kill the monster?'))
                    {
                        this.$emit('delete-monster',this.monster.id);
                    }
                }
            },
            deleteMonster(){
                alert('Delete: '+this.monster.name);
                this.$emit('delete-monster');
            }
        }
    }
</script>

<style scoped lang="scss">

</style>