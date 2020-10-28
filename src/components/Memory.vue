<template>
  <div id="memory-wrapper" :class="wrapperClass()">
    <div class="time">Time: {{ time }}</div>
    <button class="restart" @click="restartGame()">Restart</button>
    <button class="next" v-if="nextButton" @click="nextLevel()">Next</button>
      <div class="memory-container">
        <div :class="['item', itemClass()]" v-for="(image, index) in limitObj" :key="index">
          <div class="switched" @click="getPoint(index, image.id)">
            <div class="card front-side"></div>
            <div class="card back-side" :style="{backgroundImage: 'url(' + image.img + ')'}"></div>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
//import Velocity from 'velocity-animate'
export default {
  name: 'Memory',
  props: {
    images: Array
  },
  data() {
    return {
      limitObj: [],
      match: [],
      item: Object,
      point: [],
      time: 0,
      end: false,
      start: true,
      restart: false,
      counting: true,
      nextButton: false,
      level: 23,
      levelIndex: 0
    }
  },
  methods: {
    randImage: function() {
      var int = setInterval(function() {
        if(this.limitObj.length > this.level) {
        clearInterval(int)
      }
      var item = this.randItem()
      if(this.limitObj.length) {
        for(var i = 0; i < this.limitObj.length; ++i) {

          
          if((this.limitObj[i].id === item.id)) {
            
            this.match.push(item)
      
          }
        }

          if(this.match.length < 2) {
            this.limitObj.push(item)
          }

          this.match = []
        
        }
      else {
        this.limitObj.push(item)
      }
      }.bind(this), 1)
      
    },
    randItem() {
      return this.images[this.levelIndex][Math.floor(Math.random()*this.images[this.levelIndex].length)]
    },
    switchSide(index) {
      document.querySelectorAll('.switched').item(index).classList.toggle('is-flipped')
      if(!document.querySelectorAll('.switched').item(index).classList.contains('is-flipped')) {
        document.querySelectorAll('.switched').item(index).classList.add('is-flipped')
        document.querySelectorAll('.is-flipped').forEach(function(el) {
          if(!el.classList.contains('matched')) {
            el.classList.remove('is-flipped')
          }
        })
        document.querySelectorAll('.switched').item(index).classList.add('is-flipped')
      }
    
    },


    getPoint(index, id) {
      if(this.counting) {
        this.startGame()
      }
      this.counting = false
      if(!this.start) {
          if(!document.querySelectorAll('.switched').item(index).classList.contains('matched')) {
            this.switchSide(index, id)
            if(document.querySelectorAll('.is-flipped').length === 1) {
              this.point = []
              this.point.push(id)
            }
            else if(document.querySelectorAll('.is-flipped').length === 2) {
              this.point.push(id)
              if(this.point[0] === this.point[1]) {
                document.querySelectorAll('.is-flipped').forEach(function(el) {
                  el.classList.add('matched')
                  el.classList.remove('is-flipped')
                }) 
              }
            }
            else if(document.querySelectorAll('.is-flipped').length === 3) {
              this.point = []
              this.point.push(id)
              document.querySelectorAll('.is-flipped').forEach(function(el) {
              if(!el.classList.contains('matched')) {
                el.classList.remove('is-flipped')
              }
              })
              document.querySelectorAll('.switched').item(index).classList.toggle('is-flipped')
            }
      }

          if(document.querySelectorAll('.matched').length === (this.level + 1)) {
                this.end = true
                if(document.querySelectorAll('.matched').length < 32) {
                  this.nextButton = true
                }
              }

      }
    },

    startGame() {
        this.end = false
        this.restart = true
        this.start = false
        var int = setInterval(function() {
          if(this.end) {
            clearInterval(int)
          }
          else {
            this.time++
          }
        }.bind(this), 1000)
      },

    restartGame() {
        this.nextButton = false
        this.end = true
        this.restart = false
        this.start = true
        this.time = 0
        this.counting = true
       document.querySelectorAll('.switched').forEach(function(el) {
         el.classList.remove('is-flipped')
         el.classList.remove('matched')
       })
       this.limitObj = []
       this.randImage()
      },

      nextLevel() {
        this.levelIndex++
        this.level += 4
        this.restartGame()
      },

      wrapperClass() {
        var wrappClass = ''
        if(this.levelIndex === 0) {
          wrappClass = 'wrapper-level-1'
        }
        else if(this.levelIndex === 1) {
          wrappClass = 'wrapper-level-2'
        }
        else if(this.levelIndex === 2) {
          wrappClass = 'wrapper-level-3'
        }
        return wrappClass
      },

      itemClass() {
        var itemClass = ''
        if(this.levelIndex === 0) {
          itemClass = 'level-1'
        }
        else if(this.levelIndex === 1) {
          itemClass = 'level-2'
        }
        else if(this.levelIndex === 2) {
          itemClass = 'level-3'
        }
        return itemClass
      }
      

  },
  created() {
    this.randImage()
    this.wrapperClass()
    this.itemClass()
  }
}



/* */
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#memory-wrapper {
  height: 600px;
  margin: auto;
}
.wrapper-level-1 {
  width: 70%;
}
.wrapper-level-2 {
  width: 80%;
}
.wrapper-level-3 {
  width: 87%;
}
  .memory-container {
    width: 100%;
    height: 100%;
    overflow: hidden;
    display: flex;
    flex-wrap: wrap;
  }
  .item {
    perspective: 600px;
    padding: 10px;
    box-sizing: border-box;
    height: 25%;
  }
  .level-1 {
    width: 16.66%;
  }
  .level-2 {
    width: 14.28%;
  }
  .level-3 {
    width: 12.5%;
  }
  .switched {
    width: 100%;
    height: 100%;
    transition: transform .5s;
    position: relative;
    transform-style: preserve-3d;
  }
  .card {
    position: absolute;
    width: 100%;
    height: 100%;
    line-height: 260px;
    backface-visibility: hidden;
  }
  .front-side {
    background-image: url('https://store-images.s-microsoft.com/image/apps.54588.14352762657499021.bcf94466-da7b-4b88-bb7e-60467547a219.80c0934e-f2b4-4618-ba4f-913c326019f6?mode=scale&q=90&h=1080&w=1920');
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
  }
  .back-side {
    transform: rotateY(180deg);
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
  }
  .is-flipped {
    transform: rotateY(180deg);
  }
  .matched {
    transform: rotateY(180deg);
  }
  .start {
    position: fixed;
    left: 20px;
    top: 20px;
  }
  .restart {
    position: fixed;
    left: 20px;
    top: 20px;
  }
  .time {
    position: fixed;
    top: 50px;
    left: 20px;
  }
  .next {
    position: fixed;
    left: 20px;
    top: 80px;
  }
</style>
