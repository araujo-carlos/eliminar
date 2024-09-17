<!-- Script JS -->
<script>

  import * as d3 from 'd3';
  
  let numbers = [24,33,42,54,63,71,77,87,92,98]
  let numbers2= [23,35,45,56,50,43,38,32,28,25]
  let años= [2014,2015, 2016, 2017, 2018, 2019, 2020, 2021, 2022, 2023]
  let diferencia = [+1,-2,-3,-2,+13,+28,+49,+55,+62,+73]
  
  let scale = d3.scaleRadial()
      .domain([0, d3.max(numbers)])
      .range([92, 392]);
  
  let BarScale = d3.scaleLinear()
       .domain([d3.min(diferencia), d3.max(diferencia)])
       .range([0, 100]);
  
  
  </script>
  
  <!-- Estructura contenido HTML -->
  
  
  <div class="main_container">
    <!-- Título y subtítulo -->
    <div class="header">
    <h1 class="title">antes de salir...<span class="highlight3">¿Te pusiste protector?</span></h1>
    <h2 class="subtitle">En los últimos diez años, Argentina ha registrado un alarmante aumento en los niveles de radiación ultravioleta (UV), superando incluso a otros países de Sudamérica como Brasil y Chile. El cambio climático, junto con la debilitación de la capa de ozono, ha intensificado este fenómeno.</h2>
  </div>
  </div>
  
  
  
  <div class="columns_container">
  <div class="circle_section">
  <h3 class="circle_title"> El aumento significativo en <span class="highlight">Argentina</span> y la estabilidad relativa en <span class="highlight2">Sudamerica</span></h3>
  <div class="chart_container">
    {#each numbers as number, i}
    <div class="row">
  <class class="circle_container">
    <div class="mascara_circ" style="width: {scale(numbers[i])}px; height: {scale(numbers[i])}px;"></div>
    <div class="mascara_circ2" style="width: {scale(numbers2[i])}px; height: {scale(numbers2[i])}px;"></div>
    <p class="circle_number">{años[i]}</p>
  </class>
  </div>
  {/each}
  
  </div>
  </div>
  
  
  
    <!-- Contenedor de las barras de diferencias -->
    <div class="difference_bar_container">
      <div class="central_line"></div>
      {#each diferencia as diferencia, i}
      <div class="bar_wrapper">
        <div class="bar" style="width: {Math.abs(BarScale(diferencia))}px; background-color: {diferencia < 0 ? 'green' : 'red'}; transform: translateX({diferencia < 0 ? -Math.abs(BarScale(diferencia)) : 0}px);">
        </div>
      </div>
      {/each}
    </div>
  </div>
  
  
  
  
  
  <div class="image_section">
    <h3 class="image_title">El preocupante cambio de los últimos 10 años, en el índice UV en Argentina</h3>
    <div class="images_container">
      <div class="image_container">
        <div class="flourish-embed flourish-map" data-src="visualisation/19371951"><script src="https://public.flourish.studio/resources/embed.js"></script><noscript><img src="https://public.flourish.studio/visualisation/19371951/thumbnail" width="100%" alt="map visualization" /></noscript></div>
      </div>
      <div class="image_container">
        <div class="flourish-embed flourish-map" data-src="visualisation/19372132"><script src="https://public.flourish.studio/resources/embed.js"></script><noscript><img src="https://public.flourish.studio/visualisation/19372132/thumbnail" width="100%" alt="map visualization" /></noscript></div>
      </div>
  </div>
  </div>
  
  
  
  
  <!-- Estilos CSS -->
  <style>
  @import url('https://fonts.googleapis.com/css2?family=Source+Sans+3:ital,wght@0,200..900;1,200..900&display=swap');
  
      /* Contenedor principal */
      .main_container {
      font-family: "Source Sans 3", sans-serif;
      text-align: center;
      padding: 20px;
    }
  
    /* Estilo para el título */
    .title {
      font-size: 60px;
      margin: 0;
      padding: 10px 0;
      color: rgb(94, 7, 7);
      font-weight: 200;
      margin-top: 40px;
      margin-bottom: 40px;
    }
  
    .highlight3 {
      font-weight: 600;
    }
  
    /* Estilo para el subtítulo */
    .subtitle {
      font-size: 18px;
      color: rgb(0, 0, 0);
      padding: 10px 345px;
      font-weight: 300;
      margin-bottom: 60px;
    }
  
      .highlight {
      color: #70150e; 
      font-weight: bold;
    }
  
    .highlight2 {
      color: #e7770f; 
      font-weight: bold;
    }
  
    .header{
      margin-bottom: 40px;
    }
  
      /* Estilo para el título sobre las filas de círculos */
      .circle_title {
      font-size: 24px;
      margin-bottom: 60px;
      text-align: center;
      font-weight: 400;
    }
  
    /* Estilo para el título sobre la imagen */
    .image_title {
      font-size: 24px;
      margin-top: 10px;
      margin-bottom: 10px;
      text-align: center;
      font-weight: 400;
    }
  
    /* Contenedor para los círculos y la imagen */
    .circle_section {
      display: flex;
      flex-direction: column;
      align-items: left;
      width: 100%;
      padding: 0px 250px;
    }
  
      /* Contenedor principal para 2 columnas y 5 filas */
      .chart_container {
      display: flex;
      flex-direction: column;
      align-items: flex-start; /* Alineamos hacia la izquierda */
      gap: 20px; /* Espacio entre los círculos */
    }
  
  
      /* Contenedor de los círculos */
      .circle_container {
      position: relative;
      flex-direction: column;
      width: 400px;
      height: 400px;
      background: white;
    }
    
    /* Regla para los dos círculos */
    .mascara_circ,
    .mascara_circ2 {
      position: absolute;
      /* Centrado respecto al contenedor */
      top: 50%;
      left: 50%;
      /* Centrado respecto a su propio ancho */
      transform: translateX(-50%) translateY(-50%);
      /* Ruta al svg de semicírculos izquierdo */
      background-image: url("/images/vis.datos-03.svg");
      /* Tamaño del svg */
      background-size: 300px; 
      background-position: center;
      background-repeat: no-repeat;
      /* Convierte el div en círculo */
      border-radius: 50%; 
  
    }
    /* Cambia el svg de semicír */
    .mascara_circ2 {
      background-image: url("/images/vis.datos-04.svg");
    }
  
     /* Estilo del número debajo de cada círculo */
     .circle_number {
      font-size: 20px;
      color: black;
      font-weight: 600;
      text-align: center;
    }
  
    /* Contenedor de la sección de imágenes */
    .image_section {
      display: flex;
      flex-direction: column;
      align-items: center;
      width: 100%;
      margin-top: 10px;
    }
  
    /* Contenedor de las imágenes */
    .images_container {
      display: flex;
      justify-content: center; /* Centra las imágenes en su contenedor */
      gap: 20px; /* Espacio entre las imágenes */
    }
  
    /* Contenedor individual de cada imagen */
    .image_container {
      flex: 1;
      width: 100%; /* Cada imagen ocupará casi la mitad del ancho disponible */
      height: 100%;
      object-fit: contain;
    }
  
    .row {
      display: flex;
      align-items: center;
      margin-bottom: 20px;
    }
  
  
  
  .difference_bar_container {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    position: relative;
    margin-left: 20px;
  }
  
  .bar_wrapper {
    display: flex;
    align-items: center;
    height: 150px;
    position: relative;
  }
  
  .central_line {
    position: absolute;
    top: 0;
    left: 0;
    width: 2px;
    height: 100%;
    background-color: black;
  }
  
  .bar {
    height: 10px;
    margin: 5px 0;
    position: absolute;
    top: 50%;
  }
  
  .columns_container {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    width: 100%;
  }
  
  
  
  </style>