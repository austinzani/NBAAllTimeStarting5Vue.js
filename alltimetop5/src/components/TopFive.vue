<template>
  <div id="topFive">
      <div id="viewOptions">
      <a href="#" @click.prevent="viewAmount = 0" class="starting5">Your Starting 5</a>
      <div id="sortByDollar">
      <a href="#" @click.prevent="viewAmount = 5">$5</a>
      <a href="#" @click.prevent="viewAmount = 4">$4</a>
      <a href="#" @click.prevent="viewAmount = 3">$3</a>
      <a href="#" @click.prevent="viewAmount = 2">$2</a>
      <a href="#" @click.prevent="viewAmount = 1">$1</a>
      </div>
      <div id="sortByPosition">
      <a href="#" @click.prevent="viewAmount = 'PG'">PG</a>
      <a href="#" @click.prevent="viewAmount = 'SG'">SG</a>
      <a href="#" @click.prevent="viewAmount = 'SF'">SF</a>
      <a href="#" @click.prevent="viewAmount = 'PF'">PF</a>
      <a href="#" @click.prevent="viewAmount = 'C'">C</a>
      </div>
      </div>
      <h2 :class="{red : total > 15}">Current Cost: ${{total}}</h2>
      <h1 v-if="viewAmount > 0">${{viewAmount}} Players</h1>
      <h1 v-if="viewAmount === 0">Your Starting Lineup</h1>
      <h1 v-if="typeof viewAmount === 'string'">{{viewAmount}}'s</h1>
      
      <div id="current5">
        <div class="player" :class="{border: player.inRoster}" v-for="player in playersToDisplay" :key="player.name" @click="addToRoster($event, player)">
            <img :src="playerImage(player.img)">
            <h4>{{player.name}}</h4>
            <p>{{player.position}}</p>
            <p>Cost: ${{player.cost}}</p>
        </div>
      </div>
      <p class="white">Click to add or remove from your roster</p>
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
                    img: 'magicjohnson.jpg',
                    inRoster: false
                }, {name: 'Oscar Robertson',
                    cost:4,
                    position:'PG',
                    img: 'oscarrobertson.jpg',
                    inRoster: false
                },{ name: 'Isiah Thomas',
                    cost:3,
                    position:'PG',
                    img: 'isiahthomas.jpg',
                    inRoster: false
                },{ name: 'John Stockton',
                    cost:2,
                    position:'PG',
                    img: 'johnstockton.jpg',
                    inRoster: false
                },{ name:'Walt Frazier',
                    cost:1,
                    position:'PG',
                    img: 'waltfrazier.jpg',
                    inRoster: false
                },{ name:'Michael Jordan',
                    cost:5,
                    position:'SG',
                    img: 'michaeljordan.jpg',
                    inRoster: false
                },{ name: 'Kobe Bryant',
                    cost:4,
                    position:'SG',
                    img: 'kobebryant.jpg',
                    inRoster: false
                },{ name: 'Jerry West',
                    cost:3,
                    position:'SG',
                    img: 'jerrywest.jpg',
                    inRoster: false
                },{ name: 'Clyde Drexler',
                    cost:2,
                    position:'SG',
                    img: 'clydedrexler.jpg',
                    inRoster: false
                },{ name:'Dwyane Wade',
                    cost:1,
                    position:'SG',
                    img: 'dwyanewade.jpg',
                    inRoster: false
                },{ name:'Lebron James',
                    cost:5,
                    position:'SF',
                    img: 'lebronjames.jpg',
                    inRoster: false
                },{ name: 'Larry Bird',
                    cost:4,
                    position:'SF',
                    img: 'larrybird.jpg',
                    inRoster: false
                },{ name: 'Julius Erving',
                    cost:3,
                    position:'SF',
                    img: 'juliuserving.jpg',
                    inRoster: false
                },{ name: 'Kevin Durant',
                    cost:2,
                    position:'SF',
                    img: 'kevindurant.jpg',
                    inRoster: false
                },{ name:'Scottie Pippen',
                    cost:1,
                    position:'SF',
                    img: 'scottiepippen.jpg',
                    inRoster: false
                },{ name:'Karl Malone',
                    cost:5,
                    position:'PF',
                    img: 'karlmalone.jpg',
                    inRoster: false
                },{ name: 'Charles Barkley',
                    cost:4,
                    position:'PF',
                    img: 'charlesbarkley.jpg',
                    inRoster: false
                },{ name: 'Tim Duncan',
                    cost:3,
                    position:'PF',
                    img: 'timduncan.jpg',
                    inRoster: false
                },{ name: 'Dirk Nowitzki',
                    cost:2,
                    position:'PF',
                    img: 'dirknowitzki.jpg',
                    inRoster: false
                },{ name:'Kevin Garnett',
                    cost:1,
                    position:'PF',
                    img: 'kevingarnett.jpg',
                    inRoster: false
                },{ name:'Kareem Abdul-Jabbar',
                    cost:5,
                    position:'C',
                    img: 'kareemabduljabbar.jpg',
                    inRoster: false
                },{ name: 'Bill Russell',
                    cost:4,
                    position:'C',
                    img: 'billrussell.jpg',
                    inRoster: false
                },{ name: 'Wilt Chamberlain',
                    cost:3,
                    position:'C',
                    img: 'wiltchamberlain.jpg',
                    inRoster: false
                },{ name: 'Shaquille O\'Neal',
                    cost:2,
                    position:'C',
                    img: 'shaquilleoneal.jpg',
                    inRoster: false
                },{ name:'Hakeem Olajuwon',
                    cost:1,
                    position:'C',
                    img: 'hakeemolajuwon.jpg',
                    inRoster: false
                },
            ], total: 0,
            viewAmount: 5,
            startingFive:[]
        }
    }, computed: {
        sortedStarting5(){
            let sortedStarting5 = [];
            this.startingFive.forEach(player =>{
                if (player.position === "PG") sortedStarting5.push(player);
            });
            this.startingFive.forEach(player =>{
                if (player.position === "SG") sortedStarting5.push(player);
            });
            this.startingFive.forEach(player =>{
                if (player.position === "SF") sortedStarting5.push(player);
            });
            this.startingFive.forEach(player =>{
                if (player.position === "PF") sortedStarting5.push(player);
            });
            this.startingFive.forEach(player =>{
                if (player.position === "C") sortedStarting5.push(player);
            });
            
            return sortedStarting5;
        }, playersToDisplay(){
            if(this.viewAmount === 0){
                return this.sortedStarting5;
            } else if(typeof this.viewAmount === "number") {
                return this.players.filter(player => player.cost === this.viewAmount)
            } else {
                return this.players.filter(player => player.position === this.viewAmount)
            }
        }
    }, methods: {
        addToRoster(event, player){
            if(this.startingFive.includes(player)){
                this.startingFive = this.startingFive.filter(starter => starter !== player);
                this.total -= player.cost;
                player.inRoster = false;
            }else if(this.startingFive.length < 5){
            this.startingFive.push(player);
            this.total += player.cost;
            player.inRoster = true;
            }
        },
        playerImage(image){
            return require('../assets/' + image);
        }
    }, 
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
    flex-direction: column;
}

#viewoptions:nth-child(1){
    width: 20%;
}

#sortByDollar {
    display: flex;
    width: 70%;
    margin: auto;
    justify-content: space-evenly;
    padding-top: 20px;
}

#sortByPosition {
    display: flex;
    width: 70%;
    margin: auto;
    justify-content: space-evenly;
    padding-top: 20px;
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
    color: blue;
    padding: 5px;
    border-radius: 5px;
    background-color: whitesmoke;
    width: 12%;
}

.starting5 {
    width: 30%;
    margin: auto;
}

h2{
    color: whitesmoke;
}

.red {
    color: red;
    font-size: 2em;
    text-shadow: -1px 0 white, 0 1px white, 1px 0 white, 0 -1px white;
}

.white{
    color: whitesmoke;
}

.border{
    border-style: solid;
    border-color: goldenrod;
    border-width: thick;
}

img{
    width: 90%;
    height: auto;
}

@media only screen and (max-width: 420px) {
   .player{
       width: 45%;
       margin-top: 15px;
   } 
   #current5 {
    display: flex;
    width: 95%;
    margin: auto;
    flex-wrap: wrap;
    justify-content: space-evenly;
    padding-top: 20px;
    }
    #viewOptions{
        width: 95%;
    }
    #sortByDollar {
        width: 100%;
    }
    #sortByPosition{
        width: 100%;
    }
}

</style>