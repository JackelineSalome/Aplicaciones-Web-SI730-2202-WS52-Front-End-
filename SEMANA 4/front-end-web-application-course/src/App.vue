<script>
export default {
  data() {
    return {
      value:"",
      date:null,
      state: null,
      checked:false,
      categories: [
        { name: "Lácteos", code: "LA" },
        { name: "Verduras", code: "VE" },
        { name: "Frutas", code: "FR" },
      ],
    };
  },
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
        <div class="9"> <InputText placeholder="Solo letras y números" id="nombre" class="w-full" /></div>
      </div>

      <div class="field grid">
        <label for="abbreviation" class="col-3 mb-2">{{ $t("abbreviation") }}</label>
        <div class="9"> <InputMask id="abbreviation" placeholder="Solo letras" v-model="value2" mask="aaaaaaaaaa" class="w-full" /></div>
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
        <div class="9"> <InputMask id="RUC" placeholder="Solo números" v-model="value1" mask="99999999999" /></div>
      </div>

      <div class="field grid">
        <label for="price" class="col-3 mb-2">{{ $t("price") }}</label>
        <InputNumber v-model="value1" mode="decimal" showButtons="price"/>
      </div>

      <div class="field grid">
        <label for="color1" class="col-3 mb-2">{{ $t("color") }}</label>
        <div class="9"> <ColorPicker v-model="color1" /></div>
      </div>

      <div class="field grid">
        <label for="fecha" class="col-3 mb-2">{{ $t("fecha") }}</label>
        <div class="9"> <Calendar inputId="fecha" v-model="date" :showIcon="true" /></div>
      </div>

      <div class="field grid">
        <label for="state" class="col-3 mb-2">{{ $t("state") }}</label>
        <div class="9">

          <RadioButton name="state1" value="Activo" v-model="state" />
          <label class="col-2" for="state1">{{$t("active")}}</label>
          <RadioButton name="state2" value="Suspendido" v-model="state" />
          <label class="col-2" for="state2">{{$t("suspended")}}</label>
          <RadioButton name="state3" value="DeBaja" v-model="state" />
          <label for="state3">{{$t("debaja")}}</label>
        </div>
      </div>

      <div class="field grid">
        <label for="afectoimpuesto" class="col-3 mb-2">{{ $t("afectoimpuesto") }}</label>
        <div class="9"> <Checkbox v-model="checked" :binary="true" /></div>
      </div>

      <div class="field grid">
        <label for="fotos" class="col-3 mb-2">{{ $t("fotos") }}</label>
        <div class="9"><FileUpload chooseLabel="Subir" mode="basic" name="demo[]" url="./upload" accept="image/*" /></div>
        <i class="pi pi-image col-2" style="font-size: 2.5rem"></i>
      </div>

      <div class="field grid">
        <label for="descripcion" class="col-3 mb-2">{{ $t("descripcion") }}</label>
        <div class="9"> <Textarea v-model="value3" rows="5" cols="30" /></div>
      </div>

      <div class="field grid">
        <div class="col-5 p-0">
          <Button label="Grabar"  />
        </div>
        <div class="col-2">
          <Button label="Limpiar" />
        </div>
      </div>

      <h2>
        {{ $tc("product",0) }}
      </h2>
    </div>
  </form>
</template>

<style scoped></style>
