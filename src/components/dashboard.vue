<template>
  <div>
    <div>

      <div class="row q-pt-lg">
        <div class="col-lg-1 col-md-1 col-sm-1 col-xs-1"></div>
        <div class="col-lg-10 col-md-10 col-sm-10 col-xs-10">
          
          <div class="row">
            <div class="col-lg-3 col-md-3 col-sm-12 col-xs-12 col-block">
              <div class="card-container-tasks">

                <div style="display:flex;justify-content: space-between;">
                  <div class="text-h6">Tasks</div>
                  <div class="q-pa-xs">
                    <q-btn
                      label="add task"
                      color="red"
                      @click="medium = true"
                      dense
                      size="sm"
                    />
                  </div>
                </div>

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

      <q-dialog
        v-model="medium"
      >
        <q-card style="width: 700px; max-width: 80vw;">
          <q-card-section class="row items-center q-pb-none">
            <div class="text-h6">Add a new Task</div>
            <q-space />
            <q-btn icon="close" flat round dense v-close-popup />
          </q-card-section>

          <q-card-section>
            <q-form @submit.prevent="addTodo">
              <q-input 
                type="textarea"
                filled
                v-model="newTaskAdded"
                outlined dense
                @keyup.enter="addTodo"
                :rules="[ val => val && val.length > 0 || 'Please enter Task Details']"
                ref="newTaskAdded"
              />
              <div class="q-py-md" style="text-align:center;">
                <q-btn 
                  label="Add new Task"
                  no-caps 
                  dense 
                  color="red"
                  type="submit"
                />
              </div>
            </q-form>
          </q-card-section>

        </q-card>
      </q-dialog>
     
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
      medium: false,
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

    }
  },
            
  methods: {
    addTodo() {
      if (this.newTaskAdded) {
        this.todoTasks.push({ name: this.newTaskAdded });
        this.newTaskAdded = "";
        this.medium = false
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