<template>
  <div class="hello">
    <h1>Estudos</h1>
    <p v-if="!checkOpts.length">Adicione um item na checklist!</p>
    <table>
      <ul>
        <li
          v-for="(option, index) of checkOpts"
          v-bind:key="option.id">
          <CheckboxComponent
            name="radio-form"
            :label="option.label"
            :checked="option.checked"
            :onChange="onCheckChange(index)"
            :id="option.id" />
        </li>
      </ul>
    </table>
    <p>Itens pendentes: {{ pendingLength }}</p>
    <form @submit.prevent="addOpt">
      <input
        :value="newOpt"
        @change="onNewOptChange" /> <button type="submit">Adicionar</button>
    </form>
  </div>
</template>

<script>
import CheckboxComponent from '../components/form/Checkbox';

export default {
  name: 'HelloWorld',
  data: () => ({
    newOpt: '',
    checkOpts: [],
  }),
  computed: {
    pendingLength() {
      return this.checkOpts.filter(opt => !opt.checked).length;
    },
  },
  methods: {
    onNewOptChange(element) {
      const { value } = element.target;

      this.newOpt = value;
    },
    addOpt() {
      this.checkOpts.push({
        label: this.newOpt,
        checked: false,
        id: `check-${this.checkOpts.length}`,
      });
      this.newOpt = '';
    },
    onCheckChange(index) {
      const handleElement = function(element) {
        const { checked } = element.target;

        const newData = [];
        Object.assign(newData, this.checkOpts);

        newData[index] = {
          ...newData[index],
          checked,
        }

        this.checkOpts = newData;
      }

      return handleElement.bind(this)
    }
  },
  components: {
    CheckboxComponent,
  }
}
</script>

<style scoped>

</style>
