<template>
  <div class="budgetListWrap">
    <ElCard :header="header">
      <template v-if="!isEmpty">
        <div class="listItem" v-for="(item, prop) in list_item" :key="prop">
          <span class="budgetComment">{{ item.comment }}</span>

          <span class="budgetValue">{{ item.value }}</span>

          <ElButton type="danger" size="mini">Delete</ElButton>
        </div>
      </template>

      <ElAlert v-else type="info" :title="emptyTitle" :closable="false" />
    </ElCard>
  </div>
</template>

<script>
export default {
  name: "BudgetList",

  props: {
    list_item: {
      type: Object,
      default: () => ({}),
    },
  },

  data: () => ({
    header: "Budget List",
    emptyTitle: "Empty List",
  }),

  computed: {
    isEmpty() {
      return !Object.keys(this.list_item).length;
    },
  },
};
</script>

<style scoped>
.budgetListWrap {
  max-width: 500px;
  margin: 0 auto;
}
.listItem {
  display: flex;
  align-items: center;
  padding: 10px 15px;
}
.budgetValue {
  font-weight: bold;
  margin-left: auto;
  margin-right: 20px;
}
</style>
