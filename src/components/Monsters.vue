<template>
    <table class="table table-striped table-hover" v-bind:class="{ 'table-dark': isDark }">
        <thead>
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
        </thead>
        <tbody>
        <monster
                v-for="(monster, index) in monsters"
                v-bind:key="index"
                v-bind:monster="monster"
                @delete-monster="onDeleteMonster(index)"
        ></monster>
        </tbody>
    </table>
</template>

<script>
    import Monster from "./Monster";
    export default {
        name: "Monsters",
        components:{
            Monster
        },
        props:['monsters','isDark'],
        methods:{
            onDeleteMonster: function(index){
                this.monsters.splice(index, 1);
            }
        }
    }
</script>

<style lang="scss">

</style>