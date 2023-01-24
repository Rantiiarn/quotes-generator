<template>
    <div class="container m-auto">
   
      <div class="row" >
        <div class="col-lg-6 m-auto mt-5" v-for="data in datas" >      
          <br> <div class="card" style="width: 18rem;"  >
      <div class="card-body" >
        <h3 class="text-dark text-center fw-bolder">Quotes</h3>
    <h5 class="card-title">{{ data.isi }}</h5>
    <h6 class="card-subtitle mb-2 text-muted">{{ data.penulis }}</h6>
    <a href="http://twitter.com/share?text= + data.isi" target="_blank" class="text-primary  text-decoration-none ">twitter</a><br>
  
    <button @click="getsatu" class="btn btn-primary">Generate</button>
    <NuxtLink to="/tambah" class="btn btn-success mx-3">Tambah</NuxtLink>
  </div> 
  </div>
  <br>
</div>
  
  </div>
</div>
</template>
<script setup>
const supabase = useSupabaseClient()
const datas = ref([])
async function getData() {
  const { data, eror } = await supabase
  .from("quotes")
  .select()
  .limit(1)
 

  datas.value = data
  console.log(data)
}
async function getsatu(){
  const{data,error}= await supabase
  .from("random_quotes")
  .select()
  .limit(1)

  datas.value=data
}
onMounted(()=> {
  getData()
})
</script>