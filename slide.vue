<template>
  <div class="hello">
  		
	      <div class="box" @touchstart="onStart"   @touchmove="onMove" @touchend="onEnd">
	      
	      <div class="sbox" :style="item.color" v-show="Index===index" :class="{annimate:Index===index+1}" v-for="(item,index) in bgcolor" ></div>
	        
		      	<ul class="circle">
		      	   <li :class="{active:Index===index}"  v-for="(item,index) in bgcolor" ></li>
		      	</ul>	
	      	
	      </div>
	    
  </div>
</template>	
      	
<script>
export default {
	props:{
		
		bgcolor:{
			type:Array
			
		},
		time:{
			type:Number,
			default:3000
		}
	},
  data(){
  	
  	return{
  		 
  		 Index:0,
  		 arr:[],
  		 page:'',
  		 settime:''
  		 }	
  		 	
  		},
  		mounted(){
		
  			this.run()
  			  
  		},
  	methods:{ 	
  		
  	run(){
     this.settime=setInterval(()=>{
  		 		this.Index++
  		 	  if(this.Index>=this.bgcolor.length){
       	
       	   this.Index=0
       	
           }
       
  		 	},this.time)
      
    },
    onStart(e){
     this.page=e.touches[0].pageX
     
    
     },
     onMove(e){
  		 let tou=e.touches[0]
  		 let page=tou.pageX
       let num=this.page-page
       this.arr.push(num)
  		},
  		onEnd(){
  			
  	this.compu
  			
  		}
   },
   computed:{
     
  		compu(){
  			let num=this.arr[this.arr.length-1]
	  		  if(num>0){
	  		  	this.Index++
	         if(this.Index>=this.bgcolor.length){
	       	
	       	   this.Index=0
	       	
	        }
  	
  		  }else{
  		  	
  		  	this.Index--
  		    if(this.Index<0){
  		    	
  		    	this.Index=this.bgcolor.length-1
  		    	
  		    }
  		    
  		 
  		   }
  	
  		}
   }
 
}  	
  		    	
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
*{ margin: 0;
   padding:0;
   list-style: none;}
.box{ position: relative;}  
.hello .sbox{
	width:100%;
	height:200px;
	position: absolute;
	top:0;
	left:0;
	z-index:-1
	
}	
.circle li{ width:10px;
            height:10px;
            border-radius:100%;
            background: blue;
            float: left;
            margin:3px;
            }
.circle{ display:inline-block;
         text-align:center;
         margin-top:180px;
           }
.active{background:aliceblue!important;}
.annimate{
	animation:show 1s;
}	
	
@keyframes show{
		0%{ width: 0;}
		
		100%{ width: 100%;}
	}	


</style> 	