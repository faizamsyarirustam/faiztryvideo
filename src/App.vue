<script >
  export default{
   data(){
    return{
      datasensor:"",
      datasensor2:"100"
    }
   },
   created(){
    // this.getData()
   },
   methods:{
    // getData(){
    //   alert("HELLO");
    // },
    // getData2(){
    //   alert("HELLO 2");
    // },
    async ubah (){
      const dataku = await fetch("http://localhost:82/sensor1")
      const datajson = await dataku.json()
      console.log(datajson)
      this.datasensor = datajson.sensor
      console.log(this.datasensor)
    }
   }
  }
</script>

<template>
  <body class="h-screen flex-row justify-center ">
    <div class=" w-full align-text-top flex items-center justify-center"> 
    HELLO {{ datasensor }}
    <div class="w-4"></div>
    <button @click="ubah" class="bg-orange-500 rounded-xl p-4"> AMBIL DATA</button>
  </div>
  <div class="mt-6 flex justify-center">
    <table class="border-collapse border border-slate-500">
      <tr>
        <td class = "border border-slate-300 p-3 flex justify-center">
          Tanggal
        </td>
        <td class="border border-slate-300 p-3"> Suhu </td>
      </tr>
      <tr v-for ="i in datasensor">
        <td class="border border-slate-300 p-3">{{ i.tanggal }}</td>
        <td class="border border-slate-300 p-3">{{i.suhu}}</td>
      </tr>
    </table>
  </div>
  </body>
</template>

<!-- <style>
  .halo{
    font-size: x-large;
    color:black;
    font-weight: bold;

  }
</style> -->


