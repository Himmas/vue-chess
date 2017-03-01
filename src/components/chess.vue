<template>
  <div class="bg-board">
    <div class="btn-back" @click="back">返回上一步</div>
    <div class="chess-board-box">
      <div class="chess-board">
        <div class="row">
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td">
            <div class="diagonal t no-t"></div>
          </div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
        </div>
        <div class="row">
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td">
            <div class="diagonal b no-b"></div>
          </div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
        </div>
        <div class="row">
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
        </div>
        <div class="row">
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
        </div>
        <div class="row cross"></div>
        <div class="row">
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
        </div>
        <div class="row">
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
        </div>
        <div class="row">
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td">
            <div class="diagonal t no-t"></div>
          </div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
        </div>
        <div class="row">
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td">
            <div class="diagonal b no-b"></div>
          </div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
          <div class="td"></div>
        </div>
      </div>
      <div class="piece-box">
        <div class="piece black" v-for="piece in pieceList.black"
             :style="{top:piece.pos[piece.pos.length-1].y*lattice_size+'px',left:piece.pos[piece.pos.length-1].x*lattice_size+'px'}">{{piece.name}}
        </div>
      </div>
      <div class="piece-box inversion">
        <div class="piece red" v-for="piece in pieceList.red"
             :style="{top:piece.pos[piece.pos.length-1].y*lattice_size+'px',left:piece.pos[piece.pos.length-1].x*lattice_size+'px'}">{{piece.name}}
        </div>
      </div>
    </div>
    <div class="key-board-box">
      <div class="key-board">
        <span @click="stepTo(key)" v-for="key in keyBoard[step]">{{key.name}}</span>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'chess',
    data () {
      return {
        lattice_size: 40,
        pieceList: {
          red: [{
            name: '车',
            pos: [{
              x: 0,
              y: 0
            }]
          }, {
            name: '马',
            pos: [{
              x: 1,
              y: 0
            }]
          }, {
            name: '象',
            pos: [{
              x: 2,
              y: 0
            }]
          }, {
            name: '士',
            pos: [{
              x: 3,
              y: 0
            }]
          }, {
            name: '将',
            pos: [{
              x: 4,
              y: 0
            }]
          }, {
            name: '士',
            pos: [{
              x: 5,
              y: 0
            }]
          }, {
            name: '象',
            pos: [{
              x: 6,
              y: 0
            }]
          }, {
            name: '马',
            pos: [{
              x: 7,
              y: 0
            }]
          }, {
            name: '车',
            pos: [{
              x: 8,
              y: 0
            }]
          }, {
            name: '炮',
            pos: [{
              x: 1,
              y: 2
            }]
          }, {
            name: '炮',
            pos: [{
              x: 7,
              y: 2
            }]
          }, {
            name: '卒',
            pos: [{
              x: 0,
              y: 3
            }]
          }, {
            name: '卒',
            pos: [{
              x: 2,
              y: 3
            }]
          }, {
            name: '卒',
            pos: [{
              x: 4,
              y: 3
            }]
          }, {
            name: '卒',
            pos: [{
              x: 6,
              y: 3
            }]
          }, {
            name: '卒',
            pos: [{
              x: 8,
              y: 3
            }]
          }],
          black: [{
            name: '车',
            pos: [{
              x: 0,
              y: 0
            }]
          }, {
            name: '马',
            pos: [{
              x: 1,
              y: 0
            }]
          }, {
            name: '相',
            pos: [{
              x: 2,
              y: 0
            }]
          }, {
            name: '仕',
            pos: [{
              x: 3,
              y: 0
            }]
          }, {
            name: '帅',
            pos: [{
              x: 4,
              y: 0
            }]
          }, {
            name: '仕',
            pos: [{
              x: 5,
              y: 0
            }]
          }, {
            name: '相',
            pos: [{
              x: 6,
              y: 0
            }]
          }, {
            name: '马',
            pos: [{
              x: 7,
              y: 0
            }]
          }, {
            name: '车',
            pos: [{
              x: 8,
              y: 0
            }]
          }, {
            name: '砲',
            pos: [{
              x: 1,
              y: 2
            }]
          }, {
            name: '砲',
            pos: [{
              x: 7,
              y: 2
            }]
          }, {
            name: '兵',
            pos: [{
              x: 0,
              y: 3
            }]
          }, {
            name: '兵',
            pos: [{
              x: 2,
              y: 3
            }]
          }, {
            name: '兵',
            pos: [{
              x: 4,
              y: 3
            }]
          }, {
            name: '兵',
            pos: [{
              x: 6,
              y: 3
            }]
          }, {
            name: '兵',
            pos: [{
              x: 8,
              y: 3
            }]
          }]
        },
        step:0,
        keyBoard:[[{
          name:'红棋',
          key:'red'
        },{
          name:'黑棋',
          key:'black'
        }]
        ],
        chess_step:[], //棋谱数组
        actions:{
          all: [{name:'进',key:1},{name:'退',key:-1},{name:'平',key:0}],
          notAll:[{name:'进',key:1},{name:'退',key:-1}],
          red:[{name:'一',key:1},{name:'二',key:2},{name:'三',key:3},{name:'四',key:4},{name:'五',key:5},{name:'六',key:6},{name:'七',key:7},{name:'八',key:8},{name:'九',key:9}],
          black:[{name:'1',key:1},{name:'2',key:2},{name:'3',key:3},{name:'4',key:4},{name:'5',key:5},{name:'6',key:6},{name:'7',key:7},{name:'8',key:8},{name:'9',key:9}]
        },
        actionIndexs:[]
      }
    },
    computed:{
      pieces(){
        var redArgs = this.pieceList.red
        var blackArgs = this.pieceList.black
        return {
          red:redArgs.filter((o,i)=>redArgs.map(o=>o.name).indexOf(o.name) == i),
          black:blackArgs.filter((o,i)=>blackArgs.map(o=>o.name).indexOf(o.name) == i)
        }
      }
    },
    methods:{
      stepTo(key){
        this.step++;
        if(this.step == 1) {
          this.chess_step.push(key.key)
          this.keyBoard.push(this.pieces[key.key])
        }
        else if(this.step == 2) {
          this.chess_step.push(key.name)
          this.keyBoard.push(this.actions[this.chess_step[0]])
        }else if(this.step == 3){
          this.chess_step.push(key.key)
          if(!~['马','象','相','士','仕'].indexOf(this.chess_step[1]))
            this.keyBoard.push(this.actions.all)
          else
            this.keyBoard.push(this.actions.notAll)
        }else if(this.step == 4){
          this.chess_step.push(key.key)
          this.keyBoard.push(this.actions[this.chess_step[0]])
        }else if(this.step == 5){
          this.chess_step.push(key.key)
          this.doStep(()=>{
            this.$set(this,'chess_step',[])
            this.keyBoard.splice(4,1)
            this.keyBoard.splice(3,1)
            this.keyBoard.splice(2,1)
            this.keyBoard.splice(1,1)
            this.step=0
          })
        }
      },
      doStep(callback){
        var key = this.chess_step[0]

        var thisPiece = null

        var pieceIndex = null

        for(var i =0;i<this.pieceList[key].length;i++){
          var o = this.pieceList[key][i]
          let lastIndex = o.pos.length-1
          if(o.name == this.chess_step[1] && o.pos[lastIndex].x == this.chess_step[2]-1) {
            thisPiece = o
            pieceIndex = i
            break
          }
        }


        let lastIndex = thisPiece.pos.length-1

        if(this.chess_step[3] == 0)
          thisPiece.pos.push({
            x:this.chess_step[4]-1,
            y:thisPiece.pos[lastIndex].y
          })
        else if(this.chess_step[1] == '象' || this.chess_step[1] == '相'){
          thisPiece.pos.push({
            x:this.chess_step[4]-1,
            y:thisPiece.pos[lastIndex].y+this.chess_step[3]*2
          })
        }else if(this.chess_step[1] == '仕' || this.chess_step[1] == '士'){
          thisPiece.pos.push({
            x:this.chess_step[4]-1,
            y:thisPiece.pos[lastIndex].y+this.chess_step[3]*1
          })
        }else if(this.chess_step[1] == '马'){
          var step = 1
          if(Math.abs(this.chess_step[4]-this.chess_step[2]) == 1)
            step = 2
          thisPiece.pos.push({
            x:this.chess_step[4]-1,
            y:thisPiece.pos[lastIndex].y+this.chess_step[3]*step
          })
        }else{
          thisPiece.pos.push({
            x:thisPiece.pos[lastIndex].x,
            y:thisPiece.pos[lastIndex].y+this.chess_step[3]*this.chess_step[4]
          })
        }
        this.actionIndexs.push({
          key:key,
          index:pieceIndex
        })

        if(callback)
          callback()
      },
      back(){
        var lastAction = this.actionIndexs.pop()
        this.pieceList[lastAction.key][lastAction.index].pos.pop()
      }
    }
  }
</script>


<style lang="less" scoped>
  @board-size: 320px;
  .bg-board{
    position: relative;
    width: 100%;
    height: 100%;
  }
  .btn-back{
    position: absolute;
    top: 0;left: 0;
    border: 1px solid saddlebrown;
    color: saddlebrown;
    font-weight: bold;
    font-size: 20px;
    z-index: 999;
    padding:20px;
  }
  .chess-board-box {
    position: relative;
    height: 80%;
    background-color: bisque;
    .chess-board {
      width: @board-size;
      height: @board-size/8*9;
      position: absolute;
      margin: auto;
      top: 0;
      left: 0;
      bottom: 0;
      right: 0;
      border: 1px solid saddlebrown;
      font-size: 0;
      .row {
        .td {
          display: inline-block;
          width: @board-size/8;
          height: @board-size/8;
          border: 1px solid saddlebrown;
          box-sizing: border-box;
          .diagonal {
            left: 50%;
            position: relative;
            width: @board-size/8;
            height: @board-size/8;
            border: 1px solid saddlebrown;
            box-sizing: border-box;
            transform: rotate(45deg) scale(1.4);
            &.t {
              top: -50%;
            }
            &.b {
              bottom: -50%;
            }
            &.no-t {
              border-left: none;
              border-top: none;
            }
            &.no-b {
              border-right: none;
              border-bottom: none;
            }
          }
        }
        &.cross {
          height: @board-size/8;
          line-height: @board-size/8;
          font-size: 20px;
          color: saddlebrown;
          border: 1px solid saddlebrown;
          box-sizing: border-box;
        }
      }
    }
    .piece-box {
      width: @board-size;
      height: @board-size/8*9;
      position: absolute;
      margin: auto;
      top: 0;
      left: 0;
      bottom: 0;
      right: 0;
      .piece {
        cursor: pointer;
        position: absolute;
        width: @board-size/8*0.8;
        height: @board-size/8*0.8;

        margin-top: -@board-size/8*0.8/2;
        margin-left: -@board-size/8*0.8/2;

        border-radius: 50%;
        color: #333;
        line-height: @board-size/8*0.8;
        text-align: center;
        font-size: 20px;
        font-weight: bold;
        transition: .3s;
        &.black {
          background: #cd8250;
          box-shadow: 0 0 5px 5px #a75f2f;
        }
        &.red {
          background: #6f0d1f;
          box-shadow: 0 0 5px 5px  #460d1f;
          color: wheat;
        }
      }
      &.inversion {
        transform: rotate(180deg);
        .piece {
          transform: rotate(-180deg);
        }
      }
    }
  }
  .key-board-box{
    position: relative;
    height: 20%;
    background: blanchedalmond;
    .key-board{
      position: absolute;
      display: flex;
      bottom: 0;
      width: 100%;
      span{
        flex: 1;
        font-size: 20px;
        padding:20px 0;
        border: 1px solid saddlebrown;
        color: saddlebrown;
        font-weight: bold;
        &:hover{
          background: saddlebrown;
          color: white;
        }
      }
    }
  }
</style>
