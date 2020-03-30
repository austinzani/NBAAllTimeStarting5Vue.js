<template>
  <div id="topFive">
      <select v-model="viewAmount">
        <option v-for="(amount, index) in 6" :key="amount" :value="index">{{index>0? '$'+ index + ' Players': 'Starting Lineup'}}</option>
      </select>
      <div id="current5">
        <div class="player" v-for="player in playersToDisplay" :key="player.name">
            <p>{{player.name}}</p>
        </div>
      </div>
  </div>
</template>

<script>
export default {
    data(){
        return{
            players: [
                {   name:'Magic Johnson',
                    cost:5,
                    position:'PG'
                }, {name: 'Oscar Robertson',
                    cost:4,
                    position:'PG',
                },{ name: 'Isiah Thomas',
                    cost:3,
                    position:'PG'
                },{ name: 'John Stockton',
                    cost:2,
                    position:'PG'
                },{ name:'Walt Frazier',
                    cost:1,
                    position:'PG'
                },{ name:'Michael Jordan',
                    cost:5,
                    position:'SG'
                },{ name: 'Kobe Bryant',
                    cost:4,
                    position:'SG'
                },{ name: 'Jerry West',
                    cost:3,
                    position:'SG'
                },{ name: 'Clyde Drexler',
                    cost:2,
                    position:'SG'
                },{ name:'Dwyane Wade',
                    cost:1,
                    position:'SG'
                },{ name:'Lebron James',
                    cost:5,
                    position:'SF'
                },{ name: 'Larry Bird',
                    cost:4,
                    position:'SF'
                },{ name: 'Julius Erving',
                    cost:3,
                    position:'SF'
                },{ name: 'Kevin Durant',
                    cost:2,
                    position:'SF'
                },{ name:'Scottie Pippen',
                    cost:1,
                    position:'SF'
                },{ name:'Karl Malone',
                    cost:5,
                    position:'PF'
                },{ name: 'Charles Barkley',
                    cost:4,
                    position:'PF'
                },{ name: 'Tim Duncan',
                    cost:3,
                    position:'PF'
                },{ name: 'Dirk Nowitzki',
                    cost:2,
                    position:'PF'
                },{ name:'Kevin Garnett',
                    cost:1,
                    position:'C'
                },{ name:'Kareem Abdul-Jabbar',
                    cost:5,
                    position:'C'
                },{ name: 'Bill Russell',
                    cost:4,
                    position:'C'
                },{ name: 'Wilt Chamberlain',
                    cost:3,
                    position:'C'
                },{ name: 'Shaquiel O\'Neal',
                    cost:2,
                    position:'C'
                },{ name:'Hakeem Olajuwan',
                    cost:1,
                    position:'C'
                },
            ], total: 0,
            viewAmount: 0,
            startingFive:[]
        }
    }, computed: {
        playersToDisplay(){
            if(this.viewAmount === 0){
                return this.startingFive
            } else {
                return this.players.filter(player => player.cost === this.viewAmount)
            }
        }
    }
}
</script>

<style>

</style>