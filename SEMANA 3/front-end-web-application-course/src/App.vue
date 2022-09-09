<script>
export default {
  data() {
    return {
      value:0,
      value1:1,
      value2:" ",
      categories: [
        { name: "Lácteos", code: "LA" },
        { name: "Verduras", code: "VE" },
        { name: "Frutas", code: "FR" },
      ],
    };
  },
  data1() {
    return {
      state: null,
      categories: [
        {name: 'Activo', key: 'Activo'},
        {name: 'Suspendido', key: 'Suspendido'},
        {name: 'De Baja', key: 'De Baja'},
      ],
      selectedCategory: null
    }
  },
  created() {
    this.selectedCategory = this.categories[1].name;
  }
};
</script>

<template>
  <form>
    <div class="card">
      <h1>
        {{ $t("greeting", {name :"Profe" } ) }}
      </h1>

      <div class="field grid">
        <label class="col-3 mb-2" for="code">{{ $t("code") }}</label>
        <div class="col-7 p-0">
          <InputText id="code" />
        </div>
        <div class="col-2">
          <Button label="validar" />
        </div>
      </div>

      <div class="field grid">
        <label for="name" class="col-3 mb-2" >{{ $t("name") }}</label>
        <div class="9"> <InputText id="nombre" class="w-full" /></div>
      </div>

      <div class="field grid">
        <label for="abbreviation" class="col-3 mb-2">{{ $t("abbreviation") }}</label>
        <div class="9"> <InputMask id="abbreviation" v-model="value2" mask="aaaaaaaaaa" class="w-full" /></div>
      </div>

      <div class="field grid">
        <label for="category" class="col-3 mb-2">{{ $t("category") }}</label>
        <div class="col-9 p-0"> <pv-dropdown
          id="category"
          :options="categories"
          optionLabel="code"
          placeholder="Select a category"
          class="w-full"
        ></pv-dropdown></div>
      </div>

      <div class="field grid">
        <label for="RUC" class="col-3 mb-2">{{ $t("RUC") }}</label>
        <div class="9"> <InputMask id="RUC" v-model="value1" mask="9999999" /></div>
      </div>

      <div class="field grid">
        <label for="price" class="col-3 mb-2">{{ $t("price") }}</label>
        <InputNumber v-model="value" mode="decimal" showButtons="price"/>
      </div>

      <div class="field grid">
        <label for="color" class="col-3 mb-2">{{ $t("color") }}</label>
        <div class="9"> <ColorPicker v-model="color1" /></div>
      </div>

      <div class="field grid">
        <label for="fecha" class="col-3 mb-2">{{ $t("fecha") }}</label>
        <div class="9"> <Calendar inputId="fecha" v-model="date3" :showIcon="true" /></div>
      </div>

      <div class="field grid">
        <label for="state" class="col-3 mb-2">{{ $t("state") }}</label>
        <div class="9"> <div v-for="category of categories" :key="category.key" class="field grid">
          <RadioButton :inputId="category.key" name="category" :value="category.name" v-model="selectedCategory" />
            <div class="col-2">
              <label :for="category.key">{{category.name}}</label>
            </div>
          </div>
        </div>
      </div>

      <div class="field grid">
        <label for="afectoimpuesto" class="col-3 mb-2">{{ $t("afectoimpuesto") }}</label>
        <div class="9"> <Checkbox v-model="checked" :binary="true" /></div>
      </div>

      <div class="field grid">
        <label for="descripcion" class="col-3 mb-2">{{ $t("descripcion") }}</label>
        <div class="9"> <Checkbox v-model="checked" :binary="true" /></div>
      </div>

      <h2>
        {{ $tc("product",0) }}
      </h2>
    </div>
  </form>
</template>

<style scoped></style>
