<template>
  <div>
    <div>
      <div class="row">
        <div class="col-lg-1 col-md-1 col-sm-1 col-xs-1"></div>
        <div class="col-lg-10 col-md-10 col-sm-10 col-xs-10">
          <div class="q-py-md">
            <q-input 
              v-model="newTaskAdded"
              outlined dense
              @keyup.enter="addTodo"
            />
          </div>
          <div class="q-py-md">
            <q-btn label="add me" color="orange" @click="addTodo" />
          </div>

        </div>
        <div class="col-lg-1 col-md-1 col-sm-1 col-xs-1"></div>
      </div>


      <div class="row q-pt-lg">
        <div class="col-lg-1 col-md-1 col-sm-1 col-xs-1"></div>
        <div class="col-lg-10 col-md-10 col-sm-10 col-xs-10">
          
          <div class="row">
            <div class="col-lg-3 col-md-3 col-sm-12 col-xs-12 col-block">
              <div class="card-container-tasks">
                <div class="text-h6" align="center">Tasks</div>
                <q-scroll-area
                  :thumb-style="thumbStyle"
                  :bar-style="barStyle"
                  style="height:400px;"
                  visible
                >
                  <draggable
                    :list="todoTasks"
                    group="tasks"
                  >
                    <div
                     class="list-group-item-pc"
                      v-for="todoTask in todoTasks"
                      :key="todoTask.name"
                    >
                      {{ todoTask.name }}
                    </div>

                  </draggable>

                </q-scroll-area>
              </div>
            </div>
            <div class="col-lg-3 col-md-3 col-sm-12 col-xs-12 col-block">
              <div class="card-container-in-progress">
                <div class="text-h6" align="center">In-Progress</div>
                <q-scroll-area
                  :thumb-style="thumbStyle"
                  :bar-style="barStyle"
                  style="height:400px;"
                  visible
                >
                  <draggable
                    :list="inProgress"
                    group="tasks"
                  >
                    <div
                      class="list-group-item-pc"
                      v-for="element in inProgress"
                      :key="element.name"
                    >
                      {{ element.name }}
                    </div>
                  </draggable>
                </q-scroll-area>
              </div>
            </div>
            <div class="col-lg-3 col-md-3 col-sm-12 col-xs-12 col-block">
              <div class="card-container-in-review">
                <div class="text-h6" align="center">In-Review</div>
                <q-scroll-area
                  :thumb-style="thumbStyle"
                  :bar-style="barStyle"
                  style="height:400px;"
                  visible
                >
                  <draggable
                    :list="inReview"
                    group="tasks"
                  >
                    <div
                      class="list-group-item-pc"
                      v-for="element in inReview"
                      :key="element.name"
                    >
                      {{ element.name }}
                    </div>
                  </draggable>
                </q-scroll-area>
              </div>
            </div>
            <div class="col-lg-3 col-md-3 col-sm-12 col-xs-12 col-block">
              <div class="card-container-complete">
                <div class="text-h6" align="center">Completed</div>
                <q-scroll-area
                  :thumb-style="thumbStyle"
                  :bar-style="barStyle"
                  style="height:400px;"
                  visible
                >
                  <draggable
                    :list="completed"
                    group="tasks"
                  >
                    <div
                      class="list-group-item-pc"
                      v-for="element in completed"
                      :key="element.name"
                    >
                      {{ element.name }}
                    </div>
                  </draggable>
                </q-scroll-area>
              </div>
            </div>
          </div>

        </div>
        <div class="col-lg-1 col-md-1 col-sm-1 col-xs-1"></div>
      </div>
     
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";
export default {
  components: {
    draggable
  },
  computed: {
  },
  data() {
    return{
      newTaskAdded: "",
      todoTasks: [
        { name: "Code Sign Up Page" },
        { name: "Test Dashboard" },
        { name: "Style Registration" },
        { name: "Help with Designs" },
      ],
      inProgress: [
        { name: "Testing Up Page" }
      ],
      inReview: [{ name: "Testing Up Page" }],
      completed:[{name: "Testing Completed"}],


      thumbStyle: {
        right: '0px',
        borderRadius: '5px',
        backgroundColor: '#ee6b6b',
        width: '5px',
        opacity: 0.75
      },
      barStyle: {
        right: '-2px',
        borderRadius: '9px',
        backgroundColor: '#ee6b6b',
        width: '9px',
        opacity: 0.2
      },
    }
  },
            
  methods: {
    addTodo() {
      if (this.newTaskAdded) {
        this.todoTask.push({ name: this.newTaskAdded });
        this.newTaskAdded = "";
      }
    }
  }

  
}
</script>

<style lang="scss">
$blue-color:#0C365A;
$green-color:#01D167;
$primary-color:#23CEFD;

.card-container-tasks{
  background-image: linear-gradient(#eac9d8, #fefefe);
  border-radius: 5px;
  padding: 5px;
  border: 1px solid #ddd;
}
.card-container-in-progress{
  background-image: linear-gradient(#ff421659, #fefefe);
  border-radius: 5px;
  padding: 5px;
  border: 1px solid #ddd;
}
.card-container-in-review{
  background-image: linear-gradient(#163dff59, #fefefe);
  border-radius: 5px;
  padding: 5px;
  border: 1px solid #ddd;
}
.card-container-complete{
  background-image: linear-gradient(#16ff4c59, #fefefe);
  border-radius: 5px;
  padding: 5px;
  border: 1px solid #ddd;
}
.list-group-item-pc{
  padding: 10px;
  border-radius: 2px;
	background-color: #fff; 
	margin-bottom: 10px;
	cursor: pointer;
	box-shadow: 4px 4px 2px #cac2c2;
}
.col-block{
  padding: 5px;
}
</style>