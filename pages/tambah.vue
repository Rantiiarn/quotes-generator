<template>
  <div class="">

  
  <div class="col-md-6 m-auto mt-5 card p-3 ">
    <h3 class="text-dark text-center fw-bolder mb-3">IsiQuotes</h3>
<form @submit.prevent="simpan">
<div class="row mb-3">
  <label for="colFormLabel" class="col-sm-2 col-form-label">penulis</label>
  <div class="col-sm-10">
    <input type="text" class="form-control  " id="qoutes" placeholder="penulis" v-model="penulis">
  </div>
</div>
<div class="row mb-3">
  <label for="colFormLabel" class="col-sm-2 col-form-label">Your Quotes</label>
  <div class="col-sm-10">
    <textarea type="text" class="form-control" id="colFormLabel" placeholder="" v-model="isi"></textarea>
  </div>

</div>

<button type="submit" class="btn btn-primary ">sumbit</button>
</form>
</div> 
</div>
</template>


<script setup>


const supabase = useSupabaseClient()

const isi = ref()
const penulis = ref()
async function simpan() {
  await supabase
  .from("quotes")
  .insert({
    penulis: penulis.value,
    isi: isi.value,

  })
  navigateTo("/")
}
</script>
