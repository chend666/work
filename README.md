<!DOCTYPE html>
<html lang="en" >

<head>
  <meta charset="UTF-8">
  <title>VR</title>
  
  
  
      <link rel="stylesheet" href="css/style.css">

  
</head>

<body>

  <script src="https://aframe.io/releases/0.8.0/aframe.min.js"></script>
<script src="https://unpkg.com/aframe-environment-component/dist/aframe-environment-component.min.js"></script>
<script src="https://rawgit.com/mayognaise/aframe-html-shader/master/dist/aframe-html-shader.min.js"></script>
<script src="./aframe-look-at-component.min.js"></script>

<script>
  /* global AFRAME */
  	
  AFRAME.registerComponent('hide-on-click', {
    dependencies: ['raycaster'],
    schema: {
        target: {type: 'selector'}
    },
    init: function () {
        var data = this.data;
        var el = this.el;
        el.addEventListener('click', function () {
            el.setAttribute('visible', false);
            data.target.setAttribute('visible', true);
            setTimeout(function(){
                alert('Congratulation! You have a chicken!');
                window.location.reload();
            },5000);
        });
    }
});
</script>

<div id="textToDisplay"><img src="https://pic.mdcdn.cn/h5/pic/201701/frame_1.png" alt=""></div>
<a-scene>
  <a-entity environment="preset: forest; dressingAmount: 500"></a-entity>

  <a-entity hide-on-click="target:#chickenAnimate">
    <a-entity id="default_egg"
              geometry="primitive:plane;width:2;height:2;"
              look-at="[camera]"
              position="-3 2 -10"
              material="shader:html;target:#textToDisplay;transparent:true;fps:0;">
    </a-entity>
</a-entity>
<a-entity id="chickenAnimate" visible="false">
</a-entity>


  <!-- Camera + cursor. -->
  <a-entity  position="0 3 0" camera look-controls>
    <a-cursor id="cursor" animation__click="property: scale; startEvents: click; from: 0.1 0.1 0.1; to: 1 1 1; dur: 150" animation__fusing="property: fusing; startEvents: fusing; from: 1 1 1; to: 0.1 0.1 0.1; dur: 1500" event-set__1="_event: mouseenter; color: #0092d8"
      event-set__2="_event: mouseleave; color: black"></a-cursor>
  </a-entity>
</a-scene>
  
  

</body>

</html>
