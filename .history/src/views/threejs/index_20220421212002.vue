<template>
  <div>
    <div id="container"></div>
  </div>
</template>

<script>
import * as THREE from 'three'
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js'
export default {
  data() {
    return {
      camera: null,
      scene: null,
      renderer: null,
      mesh: null,
      controls: null
    }
  },
  mounted() {
    this.init()
    this.animate()
  },
  methods: {
    // 初始化
    init: function() {
      //  创建场景对象Scene
      this.scene = new THREE.Scene()

      this.scene.background = new THREE.Color('black')
      // 网格模型添加到场景中
      const geometry = new THREE.BoxGeometry(0.2, 0.2, 0.2)
      // const material = new THREE.MeshNormalMaterial({
      //   color: 'white'
      // })
      this.mesh = new THREE.Mesh(geometry)
      this.scene.add(this.mesh)

      /**
       * 相机设置
       */
      const container = document.getElementById('container')
      // 确定视野范围 视场/长宽比/近面距离/远面距离
      this.camera = new THREE.PerspectiveCamera(
        70,
        container.clientWidth / container.clientHeight,
        0.01,
        10
      )

      // 相机位置
      this.camera.position.z = 1

      /**
       * 创建渲染器对象
       */
      this.renderer = new THREE.WebGLRenderer({ antialias: true })
      this.renderer.setSize(container.clientWidth, container.clientHeight)
      container.appendChild(this.renderer.domElement)

      // 创建相机控件对象
      this.controls = new OrbitControls(this.camera, this.renderer.domElement)
      // 设置控制器聚焦点
      // this.controls.target.set(0, 5, 0)
    },

    // 动画
    animate: function() {
      requestAnimationFrame(this.animate)
      this.mesh.rotation.x += 0.01
      this.mesh.rotation.y += 0.02
      this.renderer.render(this.scene, this.camera)
    }
  }
}
</script>

<style>
#container {
  position: absolute;
  width: 100%;
  height: 100%;
}
</style>
