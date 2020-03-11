<template>
    <table class="table table-striped">
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Strength</th>
            <th>Health</th>
            <th>Special</th>
            <th>
                Actions
            </th>
        </tr>
        <monster
                v-for="(monster, index) in monsters"
                v-bind:key="index"
                v-bind:monster="monster"
                @delete-monster="onDeleteMonster(index)"
        ></monster>
    </table>
</template>

<script>
    import Monster from "./Monster";
    export default {
        name: "Monsters",
        components:{
            Monster
        },
        props:['monsters'],
        methods:{
            onDeleteMonster: function(index){
                this.monsters.splice(index, 1);
            }
        }
    }
</script>

<style scoped lang="scss">

</style>