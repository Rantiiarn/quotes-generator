<template>
    <div class="container-fluid">
      <div>

 

      
    </div>
      <div class="row" >
        <div class="col-lg-6" v-for="data in datas" >      
          <br> <div class="card" style="width: 18rem;" pading >
      <div class="card-body"  >
    <h5 class="card-title">{{ data.isi }}</h5>
    <h6 class="card-subtitle mb-2 text-muted">{{ data.penulis }}</h6>
    <a href="http://twitter.com/share?text= + data.isi" target="_blank" class="text-primary  text-decoration-none ">twitter</a>
  
  </div>
  </div>
  <br>
 <button @click="getsatu" class="btn btn-primary">Generate</button>   
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