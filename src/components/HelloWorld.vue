<template>
  <div>
    Slot
    <hr>
    <slot></slot>
    <slot name="mySlot"></slot>

    Scoped Slots
    <hr>
    <div v-for="(data) in myDummyData" :key="data.id">
        <slot name="scopedSlot" :data="data">
        </slot>
    </div>

    <br>
    Props
    <hr>
    <h3>{{msg}}</h3>

    props from function
    <hr>
    <div v-for="(data) in myDummyData2" :key="data.id">
        {{funcThroughProps(data)}}
    </div>

    Emit
    <hr>
    <button @click="customEvent">
      Button of child
    </button>

   </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    funcThroughProps: Function
  },
  data(){
    return{
        myDummyData: [
          {
            id : '1',
            name : 'John doe'
          },
          {
            id : '2',
            name : 'Jane doe'
          }

        ],

         myDummyData2: [
          {
            id : '3',
            name : 'Mary doe'
          },
          {
            id : '4',
            name : 'Harry doe'
          }

        ],

        dataFromChild: 'Data from Child'

    }
  },

  methods:{
    //this.$emit le chai custom event generate gariracha jasle garda child component ko data parent component le use garna paaos
    customEvent(){
      this.$emit('customEventFromChild',this.dataFromChild);
    }
  }
}
</script>

