<template>
  <div id="topFive">
      <div id="viewOptions">
      <a href="#" @click.prevent="viewAmount = 0">Your Starting 5</a>
      <a href="#" @click.prevent="viewAmount = 5">$5 Players</a>
      <a href="#" @click.prevent="viewAmount = 4">$4 Players</a>
      <a href="#" @click.prevent="viewAmount = 3">$3 Players</a>
      <a href="#" @click.prevent="viewAmount = 2">$2 Players</a>
      <a href="#" @click.prevent="viewAmount = 1">$1 Players</a>
      </div>
      <h2 :class="{red : total > 15}">Current Roster Cost: ${{total}}</h2>
      <div id="current5">
        <div class="player" v-for="player in playersToDisplay" :key="player.name" @click="addToRoster($event, player)">
            <img :src="'@/assets/' + player.img"/>
            <h4>{{player.name}}</h4>
            <p>{{player.position}}</p>
            <p v-if="viewAmount === 0">Cost: ${{player.cost}}</p>
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
                    position:'PG',
                    img: 'magicjohnson.jpg'
                }, {name: 'Oscar Robertson',
                    cost:4,
                    position:'PG',
                    img: 'oscarrobertson.jpg'
                },{ name: 'Isiah Thomas',
                    cost:3,
                    position:'PG',
                    img: 'isiahthomas.jpg'
                },{ name: 'John Stockton',
                    cost:2,
                    position:'PG',
                    img: 'johnstockton.jpg'
                },{ name:'Walt Frazier',
                    cost:1,
                    position:'PG',
                    img: 'waltfrazier.jpg'
                },{ name:'Michael Jordan',
                    cost:5,
                    position:'SG',
                    img: 'michaeljordan.jpg'
                },{ name: 'Kobe Bryant',
                    cost:4,
                    position:'SG',
                    img: 'kobebryant.jpg'
                },{ name: 'Jerry West',
                    cost:3,
                    position:'SG',
                    img: 'jerrywest.jpg'
                },{ name: 'Clyde Drexler',
                    cost:2,
                    position:'SG',
                    img: 'clydedrexler.jpg'
                },{ name:'Dwyane Wade',
                    cost:1,
                    position:'SG',
                    img: 'dwyanewade.jpg'
                },{ name:'Lebron James',
                    cost:5,
                    position:'SF',
                    img: 'lebronjames.jpg'
                },{ name: 'Larry Bird',
                    cost:4,
                    position:'SF',
                    img: 'larrybird.jpg'
                },{ name: 'Julius Erving',
                    cost:3,
                    position:'SF',
                    img: 'juliuserving.jpg'
                },{ name: 'Kevin Durant',
                    cost:2,
                    position:'SF',
                    img: 'kevindurant.jpg'
                },{ name:'Scottie Pippen',
                    cost:1,
                    position:'SF',
                    img: 'scottiepippen.jpg'
                },{ name:'Karl Malone',
                    cost:5,
                    position:'PF',
                    img: 'karlmalone.jpg'
                },{ name: 'Charles Barkley',
                    cost:4,
                    position:'PF',
                    img: 'charlesbarkley.jpg'
                },{ name: 'Tim Duncan',
                    cost:3,
                    position:'PF',
                    img: 'timduncan.jpg'
                },{ name: 'Dirk Nowitzki',
                    cost:2,
                    position:'PF',
                    img: 'dirknowitzki.jpg'
                },{ name:'Kevin Garnett',
                    cost:1,
                    position:'C',
                    img: 'kevingarnett.jpg'
                },{ name:'Kareem Abdul-Jabbar',
                    cost:5,
                    position:'C',
                    img: 'kareemabduljabbar.jpg'
                },{ name: 'Bill Russell',
                    cost:4,
                    position:'C',
                    img: 'billrussell.jpg'
                },{ name: 'Wilt Chamberlain',
                    cost:3,
                    position:'C',
                    img: 'wiltchamberlain.jpg'
                },{ name: 'Shaquille O\'Neal',
                    cost:2,
                    position:'C',
                    img: 'shaquilleoneal.jpg'
                },{ name:'Hakeem Olajuwon',
                    cost:1,
                    position:'C',
                    img: 'hakeemolajuwon.jpg'
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
    }, methods: {
        addToRoster(event, player){
            if(this.startingFive.includes(player)){
                this.startingFive = this.startingFive.filter(starter => starter !== player);
                this.total -= player.cost;
            }else if(this.startingFive.length < 6){
            this.startingFive.push(player);
            this.total += player.cost;}
        }
    }, playerImage(imageName){
        return require('../assets/' + imageName)
    }
}
</script>

<style>

#current5 {
    display: flex;
    width: 70%;
    margin: auto;
    justify-content: space-evenly;
    padding-top: 20px;
}

#viewOptions{
    display: flex;
    width: 70%;
    margin: auto;
    justify-content: space-evenly;
}

.player{
    width:17%;
    background-color: whitesmoke;
    padding-top: 10px;
    border-radius: 10px;
}

.clickable{
    cursor: pointer;
}

a{
    text-decoration: none;
    color: whitesmoke;
}

h2{
    color: whitesmoke;
}

.red {
    color: red;
    font-size: 2em;
    text-shadow: -1px 0 white, 0 1px white, 1px 0 white, 0 -1px white;
}

</style>