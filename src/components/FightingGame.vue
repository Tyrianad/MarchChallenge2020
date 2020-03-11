<template>
    <div class="container">
        <div class="row">
            <div class="col-12 pt-4">
                <h3 class="text-center">
                    Fighting Game!
                </h3>
                    <div class="text-right py-4">
                        <button class="btn btn-success mr-2" @click="rollDice()"><i class="fas fa-dice"></i> Roll the Dice</button>
                        <button class="btn btn-warning" @click="askReset()"><i class="fas fa-recycle"></i> Reset Table</button>
                    </div>
            </div>
            <div class="col-12 pt-4">
                <monsters v-bind:monsters="monsters"></monsters>
            </div>
        </div>
    </div>
</template>

<script>
    import Monsters from "./Monsters";

    export default {
        name: 'FightingGame',
        data: function () {
            return {
                monsterConfig:
                    {
                        count: 100,
                        types:
                            [
                                {
                                    'name': 'Witch',
                                    'strength': {'min': 60, 'max': 80},
                                    'health': {'min': 60, 'max': 80}
                                },
                                {
                                    'name': 'Dragon',
                                    'strength': {'min': 80, 'max': 90},
                                    'health': {'min': 80, 'max': 90}
                                },
                                {
                                    'name': 'Snake',
                                    'strength': {'min': 30, 'max': 60},
                                    'health': {'min': 30, 'max': 90}
                                },
                                {
                                    'name': 'River Troll',
                                    'strength': {'min': 22, 'max': 65},
                                    'health': {'min': 60, 'max': 92}
                                }
                            ]
                    },
                monsters: []
            };
        },
        components: {
            Monsters
        },
        mounted() {
            this.resetTable();
        },
        methods: {
            resetTable() {
                this.monsters = [];
                for (var i = 1; i <= this.monsterConfig.count; i++) {
                    var monsterType = this.monsterConfig.types[Math.floor(Math.random() * this.monsterConfig.types.length)];
                    this.monsters.push(this.generateMonster(monsterType,i));
                }
            },
            generateMonster(monsterType,id) {
                return {
                    id:id,
                    name: 'A name',
                    type: monsterType.name,
                    health: {
                     current:this.generateValue(monsterType.health.min, monsterType.health.max),
                     max:monsterType.health.max
                    },
                    strength: this.generateValue(monsterType.strength.min, monsterType.strength.max),
                }
            },
            generateValue(min, max) {
                return min + Math.floor(Math.random() * (max - min));
            },
            askReset(){
                if(confirm("Do you really want to reset the table?")){
                    this.resetTable();
                }
            },
            rollDice(){
                alert('About to fight');
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
    .table{
        td,th{
            vertical-align: middle !important;
            text-align: center;
        }
    }
</style>
