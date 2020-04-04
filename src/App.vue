<template>
  <div id="app">
      <header>
        <span> {{header}}</span>
      </header>

<!--- Custom event listener jun component bata generate bhiaracha tesle nai listen garcha -->
    <HelloWorld @customEventFromChild="methodOfParent($event)" :msg="dataProps" :funcThroughProps="data => `${data.id}) ${data.name}`">
      

      <h3>
          {{defaultSlot}}
      </h3>
      <h3 slot="mySlot">
          {{namedSlot}}
      </h3>

      <!-- scoped slot uses parameter passed from the child defined in slot-scope attribute
      arko way to incorporate parent data into child using html tags -->
      <template slot-scope="props" slot="scopedSlot">
         {{props.data.id}}) {{props.data.name}} <span style="color: red">{{dataFromParent}}</span>
      </template>

    </HelloWorld>


    <footer>
      <div></div>
       <span >{{footer}} </span>
    </footer>

  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data(){
    return{
      defaultSlot: "1)Data passed from default slot",
      namedSlot : "2)Data passed from named slot",
      dataProps : "Message from using prop",
      dataFromParent: "Message from parent",
      header: "Vue Header",
      footer: "Vue footer"
    }
  },
  methods:{
      methodOfParent(data){
        this.header = data;
        this.footer = data;
      }
  },
  components: {
    HelloWorld
  }
}
</script>


<style type="text/css" scoped>
 header{
    background-color: grey; 
    height: 50px; 
    margin-bottom: 20px; 
    text-align: center;

  }

  footer{
    background-color: grey; 
    height: 50px; 
    margin-bottom: 20px; 
    text-align: center;

  }
</style>

