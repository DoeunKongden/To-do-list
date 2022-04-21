<template>
  <div class="flex flex-center q-pt-xl">
    <q-card class="my-card">
      <q-card-section>
          <div class="text-h4 flex flex-center text-primary" style="width: 400px">To-Do-List</div>
      </q-card-section>

      <q-card-section>
         <div class="row justify-center">
             <div class="col-12 q-pb-md">
                <q-input label="Input To do " v-model="todoTask"/>
                 <div class="row justify-center q-pt-md">
                     <q-btn style="background: #FF0080; color: white" label="Add To Do " @click="handleAdd" />
                 </div>
             </div>
         </div>
      </q-card-section>
        <hr>
      <q-card-section v-if="todoList.length > 0">
          <!-- looping through todoList array -->

          <div class="row justify-center" v-for="(todoList,index) in todoList" :key="index">
              <div class="col-8 q-py-md">
                  {{todoList.value}}
              </div>

                <!-- Clear task -->
              <div class="col-auto q-py-md">
                  <!-- we put index here to tell what item to remove -->
                  <q-btn round dense flat icon="check" @click="handleFinish(index)"></q-btn> 
              </div>
          </div>
      </q-card-section>

        <q-card-section v-else>
            <div class="row justify-center">
                <div class="col-12">
                    <div class="text-h6 text-negative">
                        No more Task? Try adding some
                    </div>
                </div>
            </div>
        </q-card-section>
    </q-card>
  </div>
</template>

<script>
export default {
    data(){
        return{
            todoTask: '',
            todoList: [ ]
        }
    },
    methods:{
        handleAdd(){
            this.todoList.push({value: this.todoTask})
        },
        handleFinish(index){
            this.todoList.splice(index)
        }
    }
}
</script>

<style>

</style>