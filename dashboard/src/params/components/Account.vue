<template>
  <div class="arguments-wrapper">
    <b-field
      :label="`${argument.name}: ${argument.type}`"
    >
      <b-input v-model="arg" :disabled="disabled" />
    </b-field>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class Account extends Vue {
  @Prop() public argument!: any;
  @Prop({ default: false }) public readonly disabled!: boolean;
  @Prop({ default: null }) public readonly defaultValue!: any;

  set arg(value) {
    console.log('Account', { [this.argument.name.toString()]: value });

    this.$emit('selected', { [this.argument.name.toString()]: value });
  }

  get arg() {
    return this.defaultValue || '';
  }


}
</script>

<style scoped>
 .arguments-wrapper {
   margin: 1em 0em 0em 1em;
 }
</style>