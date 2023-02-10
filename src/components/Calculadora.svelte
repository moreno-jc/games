<script>
    let a=0;
    let b=0;
    let r=0;
    
    function Suma() {
      r= a+b
      }
    function Resta() {
      r=a-b
      }
    function Multiplicacion() {
      r=a*b
      }
    function Division() {
      r=a/b
      }
  </script>
  
  <h1>Calculadora</h1>
  
   <label>
      <input type="number" bind:value={a} />
   </label>
  
  
  <button class="suma" on:click|once={Suma}>
      +
  </button>
  <button class="resta" on:click|once={Resta}>
      -
  </button>
  <button class="multiplicacion" on:click|once={Multiplicacion}>
      x
  </button>
  <button class="division" on:click|once={Division}>
      /
  </button>
  
  <label>
      <input type="number" bind:value={b} />
  </label>
  
  <p> El valor de a es: {r}</p>
  
  
  <style>
  h1{
   color: tomato;
   text-align: center;
  }
  .suma{
  background-color:#62a9b7;
  border: 0cm;
  }
  .resta{
      background-color:#9cc928;
  border: 0cm;  
  }
  .multiplicacion{
      background-color:#62b768;
  border: 0cm;
  }
  .division{
      background-color:#b7629e;
  border: 0cm;
  }
  </style>
  
  