<template>
    <div class="card"  >
        <div class="card-body">
        <h5 class="card-title"
            :class="{'text-success': item.completed}"
        >
            {{item.title}}
        </h5>
        <h6 class="card-subtitle"
            :class="overdueCss"
            v-if="item.dueDate && !item.completed">
            {{dueDateLabel}}: {{formattedDate}}
        </h6>
        <div class="todo-controls">
            <button 
            class="btn btn-sm btn-outline-success"
            @click.prevent="markCompleted"
             v-if="!item.completed">
            Complete
            </button>
        </div>
        <!-- <p v-else>This has no due date</p> -->
        </div>
    </div>
</template>
<script>
export default {
    props: ['item'],
    computed: {
        formattedDate() {
            let dt = this.item.dueDate;
            return dt.toLocaleDateString("ru-RU");
        },
        isOverdue() {
            return this.item.dueDate.getTime() < Date.now();
        },
        dueDateLabel() {
            return this.isOverdue ? 'Overdue' : 'Due';
        },
        overdueCss() {
            return {
                'text-danger': this.isOverdue,
                'text-uppercase': this.isOverdue
            };
        }
    },
    methods: {
        markCompleted() {
            this.item.completed = true;
            this.$emit('item-completed');
        }
    }
}
</script>

<style scoped>
.card {
  margin-top: 15px;
}
.card .todo-controls {
  position: absolute;
  bottom: 0;
  right: 0;
  padding: 5px;
  visibility: hidden;
}
.card:hover .todo-controls {
  visibility: visible;
}
</style>