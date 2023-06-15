<template>
  <div id="app">
    <form>
      <div class="mb-3">
        <label for="name" class="form-label">Name</label>
        <input
          id="name"
          name="name"
          class="form-control"
          type="text"
          v-model="state.name"
        />
      </div>
      <div class="mb-3">
        <label for="tiefe" class="form-label">Tiefe</label>
        <input
          id="tiefe"
          name="tiefe"
          class="form-control"
          type="number"
          v-model="state.tiefe"
        />
      </div>
      <div class="mb-3">
        <label for="ort" class="form-label">Ort</label>
        <!-- GDIK -->
        <gdik-input
          id="ort"
          name="ort"
          class="form-control p-0"
          draw-type="LineString"
          config-url="https://configuration.dev.gdik.de/configs/541b1ac8-f898-11ed-9868-3e72854101d6.json"
          :value="state.ort"
          @change="state.ort = $event.target.value ? $event.target.value : null"
        ></gdik-input>
      </div>
    </form>
  </div>
  <hr />
  <h4>Form value</h4>
  <pre id="form-values">{{ state }}</pre>
</template>

<script>
import { reactive } from 'vue';
export default {
  name: 'App',
  setup() {
    const state = reactive({
      name: undefined,
      tiefe: undefined,
      ort: undefined,
    });

    // expose state to template
    return {
      state,
    };
  },
};
</script>

<style>
gdik-input {
  display: inline-block;
  width: 300px;
  height: 300px;
}
</style>
