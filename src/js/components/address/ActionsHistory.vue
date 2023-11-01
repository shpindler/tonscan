<template>
  <div class="actions-container">
    <table class="actions">
      <thead class="actions__header">
        <tr class="actions__row">
          <td class="actions__cell">Type</td>
          <td class="actions__cell">Price</td>
          <td class="actions__cell">From</td>
          <td class="actions__cell">To</td>
          <td class="actions__cell">Time</td>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item of items" :key="item.id" class="actions__row">
          <td class="actions__cell">
            <Component :is="getTypeIcon(item.type)" />
            <span>{{item.type}}</span>
          </td>
          <td class="actions__cell">{{item.price}}</td>
          <td class="actions__cell">{{item.from}}</td>
          <td class="actions__cell">{{item.to}}</td>
          <td class="actions__cell">{{item.time}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      default() {
        return [];
      },
    }
  },
  methods: {
    async getTypeIcon(type) {
      return await import(`@img/icons/getgems/icon__${type}`).default;
    },
  },
}
</script>

<style lang="scss">
.actions-container {
  padding: 20px;
  background-color: #333;
  color: #fff;

  table {
    width: 100%;
    border-collapse: collapse;

    th,
    td {
      padding: 8px 15px;
      border: 1px solid #444;
    }

    thead {
      th {
        background-color: #222;
      }
    }

    tbody {
      tr:nth-child(odd) {
        background-color: #444;
      }
    }
  }
}
</style>