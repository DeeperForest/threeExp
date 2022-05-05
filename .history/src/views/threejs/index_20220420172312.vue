eslint-disable no-useless-escape
<template>
    <canvas id="con"></canvas>
</template>
<script>
import * as THREE from 'three'

var scene = THREE.Scene()

scene.background = new THREE.Color('white')

let camera = new THREE.PerspectiveCamera(fov, aspect, near, far)

this.camera.position.set(0, 10, 20)
{
    const color = 0xf1f1f1 // 光的颜色
    const intensity = 1 // 光的强度
    const light = new THREE.DirectionalLight(color, intensity)
    light.castShadow = true // 开启castShadow生成动态的投影
    light.position.set(10, 300, 20) // 设置灯光的位置
    this.scene.add(light) // 将灯光添加到场景中
}
</script>
