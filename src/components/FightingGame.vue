<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <monsters></monsters>
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
            console.log(this.monsters)
        },
        methods: {
            resetTable() {
                for (var i = 0; i < this.monsterConfig.count; i++) {
                    var monsterType = this.monsterConfig.types[Math.floor(Math.random() * this.monsterConfig.types.length)];
                    this.monsters.push(this.generateMonster(monsterType));
                }
            },
            generateMonster(monsterType) {
                return {
                    'name': 'A name',
                    'type': monsterType.name,
                    'health': this.generateValue(monsterType.health.min, monsterType.health.max),
                    'strength': this.generateValue(monsterType.strength.min, monsterType.strength.max),
                }
            },
            generateValue(min, max) {
                return min + Math.floor(Math.random() * (max - min));
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
