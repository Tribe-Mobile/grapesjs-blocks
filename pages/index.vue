<template>
  <div>
    <div>
      <div id="gjs">
      </div>
    </div>
    <div class="blocks"></div>
  </div>
</template>

<script>
import 'grapesjs/dist/css/grapes.min.css';
import grapesjs from 'grapesjs'


export default {
  name: 'new',
  data() {
    return {
      editor: null,
      content: '',
    }
  },
  methods: {},
  mounted() {
    this.editor = grapesjs.init({
      // Indicate where to init the editor. You can also pass an HTMLElement
      container: '#gjs',
      // Get the content for the canvas directly from the element
      // As an alternative we could use: `components: '<h1>Hello World Component!</h1>'`,
      fromElement: true,
      // Size of the editor
      height: '300px',
      width: 'auto',
      // Disable the storage manager for the moment
      storageManager: false,
      // Avoid any default panel
      panels: {defaults: []},
      blockManager: {
        appendTo: '.blocks',
        blocks: [
          {
            id: 'section', // id is mandatory
            label: '<b>Section</b>', // You can use HTML/SVG inside labels
            attributes: {class: 'gjs-block-section'},
            content: `<section>
          <h1>This is My simple title</h1>
          <div>This is just a Lorem text: Lorem ipsum dolor sit amet</div>
        </section>`,
          }, {
            id: 'text',
            label: 'Text',
            content: '<div data-gjs-type="text">Insert your text here</div>',
          },
        ]
      },
    });
  },
}
</script>
<style scoped>
#mydiv {
  position: absolute;
  z-index: 9;
  background-color: #f1f1f1;
  border: 1px solid #d3d3d3;
  text-align: center;
}

#mydivheader {
  padding: 10px;
  cursor: move;
  z-index: 10;
  background-color: #2196F3;
  color: #fff;
}

/* Let's highlight canvas boundaries */
#gjs {
  border: 3px solid #444;
}

/* Reset some default styling */
.gjs-cv-canvas {
  top: 0;
  width: 100%;
  height: 100%;
}

.gjs-block {
  width: auto;
  height: auto;
  min-height: auto;
}

</style>
