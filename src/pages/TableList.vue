<template>
  <div class="content">
    <div class="md-layout">
      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100"
      >
        <md-card>
          <md-card-header data-background-color="grey">
            <h4 class="title">2018 Lexus ES Hybrid</h4>
            <p class="category">Driving history</p>
          </md-card-header>
          <md-card-content>
            <simple-table table-header-color="grey"></simple-table>
          </md-card-content>
        </md-card>
      </div>
    </div>
  </div>
</template>

<style scoped>
p.category {
  color: white !important;
}
</style>

<script>
import { SimpleTable } from "@/components";

export default {
  components: {
    SimpleTable
  }
};
</script>
