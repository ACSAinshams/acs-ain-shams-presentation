<script setup>
import { onMounted, onBeforeUnmount, ref } from 'vue'
import * as THREE from 'three'
const host = ref(null)
let renderer, scene, camera, mesh, frame, resize
onMounted(() => {
  scene = new THREE.Scene(); camera = new THREE.PerspectiveCamera(38,1,.1,100); camera.position.z=4.4
  renderer = new THREE.WebGLRenderer({alpha:true,antialias:true}); renderer.setPixelRatio(Math.min(devicePixelRatio,2)); host.value.appendChild(renderer.domElement)
  const geo = new THREE.IcosahedronGeometry(1.05,5)
  const mat = new THREE.MeshPhysicalMaterial({color:0x087bff,metalness:.72,roughness:.18,wireframe:true,transparent:true,opacity:.72})
  mesh = new THREE.Mesh(geo,mat); scene.add(mesh)
  const core = new THREE.Mesh(new THREE.IcosahedronGeometry(.72,4),new THREE.MeshBasicMaterial({color:0x0a5fff,wireframe:true,transparent:true,opacity:.18}));scene.add(core)
  scene.add(new THREE.PointLight(0x21aaff,22,10));
  resize=()=>{const w=host.value.clientWidth,h=host.value.clientHeight;renderer.setSize(w,h);camera.aspect=w/h;camera.updateProjectionMatrix()};resize();window.addEventListener('resize',resize)
  const tick=()=>{frame=requestAnimationFrame(tick);mesh.rotation.x+=.002;mesh.rotation.y+=.004;core.rotation.y-=.002;renderer.render(scene,camera)};tick()
})
onBeforeUnmount(()=>{cancelAnimationFrame(frame);window.removeEventListener('resize',resize);renderer?.dispose()})
</script>
<template><div ref="host" class="orb"></div></template>
<style scoped>.orb{width:100%;height:100%;min-height:350px;filter:drop-shadow(0 0 35px #087bff66)}.orb :deep(canvas){display:block}</style>
