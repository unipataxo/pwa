<template>
<div>
      <h1>Dashboard</h1>
        <div class="row dashboard-info-widgets">
    <div class="col-md-6 col-xl-6">
      <vuestic-widget class="info-widget">
        <div class="info-widget-inner">
          <div class="stats">
            <div class="stats-number">
              <i class="ion ion-md-arrow-up text-primary stats-icon"></i>
              16
            </div>
            <div class="stats-title">{{'dashboard.aquarios' | translate}}</div>
          </div>
        </div>
      </vuestic-widget>
    </div>
    <div class="col-md-6 col-xl-6">
      <vuestic-widget class="info-widget">
        <div class="info-widget-inner">
          <div class="stats">
            <div class="stats-number">
              <i class="ion ion-md-arrow-down text-danger stats-icon"></i>
              5M
            </div>
            <div class="stats-title">{{'dashboard.camaroes' | translate}}</div>
          </div>
        </div>
      </vuestic-widget>
    </div>
    <div class="col-md-6 col-xl-6">
      <vuestic-widget class="info-widget">
        <div class="info-widget-inner">
          <div class="stats">
            <div class="stats-number">
              10
            </div>
            <div class="stats-title">{{'dashboard.locais' | translate}}</div>
          </div>
        </div>
      </vuestic-widget>
    </div>
    <div class="col-md-6 col-xl-6">
      <vuestic-widget class="info-widget">
        <div class="info-widget-inner">
          <div class="stats">
            <div class="stats-number">
              <i class="ion ion-md-arrow-up text-primary stats-icon"></i>
              550
            </div>
            <div class="stats-title">{{'dashboard.funcionarios' | translate}}</div>
          </div>
        </div>
      </vuestic-widget>
    </div>
  </div>
</div>

</template>

<script>
  export default {
    name: 'dashboard-info-widgets',
    data () {
      return {
      }
    },
    mounted () {
      this.$refs.circleProgress.$data.value = 70
    }
  }
</script>

<style lang="scss" scoped>
  @import "../../sass/_variables.scss";

  .stats-number, .stats-title {
    line-height: 1;
  }

  .info-widget-inner {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    position: relative;
    width: 100%;

    &.has-chart {
      justify-content: space-between;
    }

    .stats {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100%;
    }
  }

  .stats-number {
    position: relative;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    font-size: 2.625rem;
    margin-bottom: 0.5rem;

    .stats-icon {
      font-size: 1.5625rem;
      position: absolute;
      top: 0.625rem;
      left: -1.25rem;

      &.icon-wide {
        left: -1.875rem;
      }
    }
  }

</style>
