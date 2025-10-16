# Mulheres cientistas em redes internacionais (1950-1970)
Nessa rede você consegue visualizar as conexões entre os países e as especialidades de mulheres que entre os anos 1950 e 1970 obtiveram algum tipo de colaboração internacional.
Para visualizar o nome, país e a especialidade de cada cientista, basta clicar nos respectivos nós da rede. 
<html>
    <head>
        <meta charset="utf-8">
        
            <script src="lib/bindings/utils.js"></script>
            <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/vis-network/9.1.2/dist/dist/vis-network.min.css" integrity="sha512-WgxfT5LWjfszlPHXRmBWHkV2eceiWTOBvrKCNbdgDYTHrT2AeLCGbF4sZlZw3UMN3WtL0tGUoIAKsu8mllg/XA==" crossorigin="anonymous" referrerpolicy="no-referrer" />
            <script src="https://cdnjs.cloudflare.com/ajax/libs/vis-network/9.1.2/dist/vis-network.min.js" integrity="sha512-LnvoEWDFrqGHlHmDD2101OrLcbsfkrzoSpvtSQtxK3RMnRV0eOkhhBN2dXHKRrUU8p2DGRTk35n4O8nWSVe1mQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
            
        
<center>
<h1></h1>
</center>

<!-- <link rel="stylesheet" href="../node_modules/vis/dist/vis.min.css" type="text/css" />
<script type="text/javascript" src="../node_modules/vis/dist/vis.js"> </script>-->
        <link
          href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/css/bootstrap.min.css"
          rel="stylesheet"
          integrity="sha384-eOJMYsd53ii+scO/bJGFsiCZc+5NDVN2yr8+0RDqr0Ql0h+rP48ckxlpbzKgwra6"
          crossorigin="anonymous"
        />
        <script
          src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/js/bootstrap.bundle.min.js"
          integrity="sha384-JEW9xMcG8R+pH31jmWH6WWP0WintQrMb4s7ZOdauHnUtxwoG2vI5DkLtS3qm9Ekf"
          crossorigin="anonymous"
        ></script>


        <center>
          <h1></h1>
        </center>
        <style type="text/css">

             #mynetwork {
                 width: 100%;
                 height: 900px;
                 background-color: #ffffff;
                 border: 1px solid lightgray;
                 position: relative;
                 float: left;
             }

             

             

             
        </style>
    </head>


    <body>
        <div class="card" style="width: 100%">
            
            
            <div id="mynetwork" class="card-body"></div>
        </div>

        
        

        <script type="text/javascript">

              // initialize global variables.
              var edges;
              var nodes;
              var allNodes;
              var allEdges;
              var nodeColors;
              var originalNodes;
              var network;
              var container;
              var options, data;
              var filter = {
                  item : '',
                  property : '',
                  value : []
              };

              

              

              // This method is responsible for drawing the graph, returns the drawn network
              function drawGraph() {
                  var container = document.getElementById('mynetwork');

                  

                  // parsing and collecting nodes and edges from the python
                  nodes = new vis.DataSet([{"borderWidth": 2, "borderWidthSelected": 4, "color": "#FF6B6B", "font": {"color": "#000000"}, "id": "Biologia/Sa\u00fade", "label": "Biologia/Sa\u00fade", "shape": "dot", "size": 35, "title": "\ud83d\udd2c Biologia/Sa\u00fade\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 3 mulheres\n\ud83c\udf0d 1 pa\u00edses\n\n\ud83d\udccb Cientistas:\n\u2022 Chana Malogolowkin\n\u2022 J\u00falia Vidigal Vasconcellos\n\u2022 Arlete Ubatuba"}, {"borderWidth": 2, "borderWidthSelected": 4, "color": "#FF6B6B", "font": {"color": "#000000"}, "id": "Cultura De Tecidos", "label": "Cultura De Tecidos", "shape": "dot", "size": 25, "title": "\ud83d\udd2c Cultura De Tecidos\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\ud83c\udf0d 1 pa\u00edses\n\n\ud83d\udccb Cientistas:\n\u2022 Laura Maria Tavares Queiroga"}, {"borderWidth": 2, "borderWidthSelected": 4, "color": "#FF6B6B", "font": {"color": "#000000"}, "id": "F\u00edsica/Astronomia", "label": "F\u00edsica/Astronomia", "shape": "dot", "size": 40, "title": "\ud83d\udd2c F\u00edsica/Astronomia\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 4 mulheres\n\ud83c\udf0d 3 pa\u00edses\n\n\ud83d\udccb Cientistas:\n\u2022 Anna Maria M. de Oliveira Freire (Endler)\n\u2022 Hertha Meyer\n\u2022 A\u00edda Hass\u00f3n-Voloch\n\u2022 Yeda Veiga Ferraz Pereira"}, {"borderWidth": 2, "borderWidthSelected": 4, "color": "#FF6B6B", "font": {"color": "#000000"}, "id": "Geografia/Geoci\u00eancias", "label": "Geografia/Geoci\u00eancias", "shape": "dot", "size": 40, "title": "\ud83d\udd2c Geografia/Geoci\u00eancias\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 4 mulheres\n\ud83c\udf0d 3 pa\u00edses\n\n\ud83d\udccb Cientistas:\n\u2022 Bertha Koiffman Becker\n\u2022 Maria do Carmo Corr\u00eaa Galv\u00e3o\n\u2022 Josildeth Gomes Consorte\n\u2022 Maria Thereza Ribeiro da Costa Prost"}, {"borderWidth": 2, "borderWidthSelected": 4, "color": "#FF6B6B", "font": {"color": "#000000"}, "id": "Matem\u00e1tica", "label": "Matem\u00e1tica", "shape": "dot", "size": 25, "title": "\ud83d\udd2c Matem\u00e1tica\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\ud83c\udf0d 1 pa\u00edses\n\n\ud83d\udccb Cientistas:\n\u2022 Maria Laura Mousinho Leite Lopes"}, {"borderWidth": 2, "borderWidthSelected": 4, "color": "#FF6B6B", "font": {"color": "#000000"}, "id": "Medicina", "label": "Medicina", "shape": "dot", "size": 30, "title": "\ud83d\udd2c Medicina\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 2 mulheres\n\ud83c\udf0d 2 pa\u00edses\n\n\ud83d\udccb Cientistas:\n\u2022 Lygia Madeira C\u00e9sar de Andrade\n\u2022 Aparecida Garcia"}, {"borderWidth": 2, "borderWidthSelected": 4, "color": "#FF6B6B", "font": {"color": "#000000"}, "id": "Psicologia/Psiquiatria", "label": "Psicologia/Psiquiatria", "shape": "dot", "size": 30, "title": "\ud83d\udd2c Psicologia/Psiquiatria\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 2 mulheres\n\ud83c\udf0d 2 pa\u00edses\n\n\ud83d\udccb Cientistas:\n\u2022 Marialzira Perestrello\n\u2022 Regina Sampaio Dias"}, {"borderWidth": 2, "borderWidthSelected": 4, "color": "#FF6B6B", "font": {"color": "#000000"}, "id": "Qu\u00edmica/Tecnologia", "label": "Qu\u00edmica/Tecnologia", "shape": "dot", "size": 70, "title": "\ud83d\udd2c Qu\u00edmica/Tecnologia\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 10 mulheres\n\ud83c\udf0d 5 pa\u00edses\n\n\ud83d\udccb Cientistas:\n\u2022 P\u00e9rola Zaltzman\n\u2022 Rosa Bernstein Scorzelli\n\u2022 Feiga Tiomno Rosenthal\n\u2022 Nancy Queiroz de Ara\u00fajo\n\u2022 Eloisa Biasotto Mano\n\u2022 Mireille Carneiro Felipe dos Santos\n\u2022 Dolores Prado\n\u2022 Clara T\u00f6r\u00f6k\n\u2022 Aida Esp\u00edndola\n\u2022 Dulcinea Moreira Parreira"}, {"borderWidth": 2, "borderWidthSelected": 4, "color": "#FF6B6B", "font": {"color": "#000000"}, "id": "Zoologia", "label": "Zoologia", "shape": "dot", "size": 25, "title": "\ud83d\udd2c Zoologia\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\ud83c\udf0d 1 pa\u00edses\n\n\ud83d\udccb Cientistas:\n\u2022 Bertha Maria J\u00falia Lutz"}, {"borderWidth": 2, "borderWidthSelected": 4, "color": "#4ECDC4", "font": {"color": "#000000"}, "id": "EUA", "label": "EUA", "shape": "dot", "size": 90, "title": "\ud83c\udf0d EUA\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 14 mulheres\n\ud83d\udd2c 7 \u00e1reas\n\n\ud83d\udccb Cientistas:\n\u2022 Bertha Koiffman Becker\n\u2022 Chana Malogolowkin\n\u2022 P\u00e9rola Zaltzman\n\u2022 Josildeth Gomes Consorte\n\u2022 Rosa Bernstein Scorzelli\n\u2022 Feiga Tiomno Rosenthal\n\u2022 Nancy Queiroz de Ara\u00fajo\n\u2022 J\u00falia Vidigal Vasconcellos\n\u2022 Laura Maria Tavares Queiroga\n\u2022 Arlete Ubatuba\n... e mais 4"}, {"borderWidth": 2, "borderWidthSelected": 4, "color": "#4ECDC4", "font": {"color": "#000000"}, "id": "Alemanha", "label": "Alemanha", "shape": "dot", "size": 40, "title": "\ud83c\udf0d Alemanha\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 4 mulheres\n\ud83d\udd2c 3 \u00e1reas\n\n\ud83d\udccb Cientistas:\n\u2022 Anna Maria M. de Oliveira Freire (Endler)\n\u2022 Maria do Carmo Corr\u00eaa Galv\u00e3o\n\u2022 Hertha Meyer\n\u2022 Clara T\u00f6r\u00f6k"}, {"borderWidth": 2, "borderWidthSelected": 4, "color": "#4ECDC4", "font": {"color": "#000000"}, "id": "Fran\u00e7a", "label": "Fran\u00e7a", "shape": "dot", "size": 40, "title": "\ud83c\udf0d Fran\u00e7a\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 4 mulheres\n\ud83d\udd2c 4 \u00e1reas\n\n\ud83d\udccb Cientistas:\n\u2022 Bertha Maria J\u00falia Lutz\n\u2022 Mireille Carneiro Felipe dos Santos\n\u2022 Maria Thereza Ribeiro da Costa Prost\n\u2022 Yeda Veiga Ferraz Pereira"}, {"borderWidth": 2, "borderWidthSelected": 4, "color": "#4ECDC4", "font": {"color": "#000000"}, "id": "Inglaterra", "label": "Inglaterra", "shape": "dot", "size": 35, "title": "\ud83c\udf0d Inglaterra\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 3 mulheres\n\ud83d\udd2c 2 \u00e1reas\n\n\ud83d\udccb Cientistas:\n\u2022 A\u00edda Hass\u00f3n-Voloch\n\u2022 Dolores Prado\n\u2022 Dulcinea Moreira Parreira"}, {"borderWidth": 2, "borderWidthSelected": 4, "color": "#4ECDC4", "font": {"color": "#000000"}, "id": "It\u00e1lia", "label": "It\u00e1lia", "shape": "dot", "size": 30, "title": "\ud83c\udf0d It\u00e1lia\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 2 mulheres\n\ud83d\udd2c 2 \u00e1reas\n\n\ud83d\udccb Cientistas:\n\u2022 Eloisa Biasotto Mano\n\u2022 Lygia Madeira C\u00e9sar de Andrade"}, {"borderWidth": 2, "borderWidthSelected": 4, "color": "#4ECDC4", "font": {"color": "#000000"}, "id": "Argentina", "label": "Argentina", "shape": "dot", "size": 25, "title": "\ud83c\udf0d Argentina\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\ud83d\udd2c 1 \u00e1reas\n\n\ud83d\udccb Cientistas:\n\u2022 Marialzira Perestrello"}]);
                  edges = new vis.DataSet([{"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Biologia/Sa\u00fade", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Biologia/Sa\u00fade \u2192 EUA\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 3 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Chana Malogolowkin\n\u2022 J\u00falia Vidigal Vasconcellos\n\u2022 Arlete Ubatuba", "to": "EUA", "value": 5.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Cultura De Tecidos", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Cultura De Tecidos \u2192 EUA\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Laura Maria Tavares Queiroga", "to": "EUA", "value": 2.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "F\u00edsica/Astronomia", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 F\u00edsica/Astronomia \u2192 Alemanha\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 2 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Anna Maria M. de Oliveira Freire (Endler)\n\u2022 Hertha Meyer", "to": "Alemanha", "value": 4.0}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "F\u00edsica/Astronomia", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 F\u00edsica/Astronomia \u2192 Fran\u00e7a\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Yeda Veiga Ferraz Pereira", "to": "Fran\u00e7a", "value": 2.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "F\u00edsica/Astronomia", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 F\u00edsica/Astronomia \u2192 Inglaterra\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 A\u00edda Hass\u00f3n-Voloch", "to": "Inglaterra", "value": 2.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Geografia/Geoci\u00eancias", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Geografia/Geoci\u00eancias \u2192 Alemanha\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Maria do Carmo Corr\u00eaa Galv\u00e3o", "to": "Alemanha", "value": 2.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Geografia/Geoci\u00eancias", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Geografia/Geoci\u00eancias \u2192 EUA\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 2 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Bertha Koiffman Becker\n\u2022 Josildeth Gomes Consorte", "to": "EUA", "value": 4.0}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Geografia/Geoci\u00eancias", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Geografia/Geoci\u00eancias \u2192 Fran\u00e7a\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Maria Thereza Ribeiro da Costa Prost", "to": "Fran\u00e7a", "value": 2.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Matem\u00e1tica", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Matem\u00e1tica \u2192 EUA\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Maria Laura Mousinho Leite Lopes", "to": "EUA", "value": 2.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Medicina", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Medicina \u2192 EUA\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Aparecida Garcia", "to": "EUA", "value": 2.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Medicina", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Medicina \u2192 It\u00e1lia\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Lygia Madeira C\u00e9sar de Andrade", "to": "It\u00e1lia", "value": 2.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Psicologia/Psiquiatria", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Psicologia/Psiquiatria \u2192 Argentina\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Marialzira Perestrello", "to": "Argentina", "value": 2.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Psicologia/Psiquiatria", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Psicologia/Psiquiatria \u2192 EUA\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Regina Sampaio Dias", "to": "EUA", "value": 2.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Qu\u00edmica/Tecnologia", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Qu\u00edmica/Tecnologia \u2192 Alemanha\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Clara T\u00f6r\u00f6k", "to": "Alemanha", "value": 2.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Qu\u00edmica/Tecnologia", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Qu\u00edmica/Tecnologia \u2192 EUA\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 5 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 P\u00e9rola Zaltzman\n\u2022 Rosa Bernstein Scorzelli\n\u2022 Feiga Tiomno Rosenthal\n\u2022 Nancy Queiroz de Ara\u00fajo\n\u2022 Aida Esp\u00edndola", "to": "EUA", "value": 8.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Qu\u00edmica/Tecnologia", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Qu\u00edmica/Tecnologia \u2192 Fran\u00e7a\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Mireille Carneiro Felipe dos Santos", "to": "Fran\u00e7a", "value": 2.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Qu\u00edmica/Tecnologia", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Qu\u00edmica/Tecnologia \u2192 Inglaterra\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 2 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Dolores Prado\n\u2022 Dulcinea Moreira Parreira", "to": "Inglaterra", "value": 4.0}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Qu\u00edmica/Tecnologia", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Qu\u00edmica/Tecnologia \u2192 It\u00e1lia\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Eloisa Biasotto Mano", "to": "It\u00e1lia", "value": 2.5}, {"color": {"color": "#848484", "highlight": "#FF6B6B"}, "from": "Zoologia", "smooth": {"type": "continuous"}, "title": "\ud83d\udd17 Zoologia \u2192 Fran\u00e7a\n\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\u2501\n\ud83d\udc65 1 mulheres\n\n\ud83d\udccb Cientistas:\n\u2022 Bertha Maria J\u00falia Lutz", "to": "Fran\u00e7a", "value": 2.5}]);

                  nodeColors = {};
                  allNodes = nodes.get({ returnType: "Object" });
                  for (nodeId in allNodes) {
                    nodeColors[nodeId] = allNodes[nodeId].color;
                  }
                  allEdges = edges.get({ returnType: "Object" });
                  // adding nodes and edges to the graph
                  data = {nodes: nodes, edges: edges};

                  var options = {"physics": {"enabled": true, "barnesHut": {"gravitationalConstant": -50000, "centralGravity": 0.5, "springLength": 200, "springConstant": 0.01, "damping": 0.5, "avoidOverlap": 0.8}, "maxVelocity": 10, "minVelocity": 0.75, "solver": "barnesHut", "timestep": 0.5, "stabilization": {"enabled": true, "iterations": 2000, "updateInterval": 50}}, "interaction": {"hover": true, "tooltipDelay": 100, "navigationButtons": true, "keyboard": true, "zoomView": true, "dragView": true}};

                  


                  

                  network = new vis.Network(container, data, options);

                  

                  

                  


                  

                  return network;

              }
              drawGraph();
        </script>
    </body>
</html>
