<template>
  <div id="globe-container" ref="globeContainer"></div>
</template>

<script>
import * as THREE from 'three';
import ThreeGlobe from 'three-globe';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls';
import countries from '@/data/globe.json';

export default {
  name: 'MyGlobe',
  props: {
    routes: {
      type: Array,
      required: true, // Expect an array of shipping routes with coordinates
    },
  },
  mounted() {
    this.initGlobe();
  },
  methods: {
    initGlobe() {
      const container = this.$refs.globeContainer;

      // Create scene
      const scene = new THREE.Scene();

      // Create camera
      const camera = new THREE.PerspectiveCamera(
        75,
        container.clientWidth / container.clientHeight,
        0.1,
        1000
      );
      camera.position.z = 200;

      // Create renderer
      const renderer = new THREE.WebGLRenderer({ antialias: true });
      renderer.setSize(container.clientWidth, container.clientHeight);
      container.appendChild(renderer.domElement);

      console.log('Routes data: ', this.routes);

      // Add a globe using ThreeGlobe
      const globe = new ThreeGlobe()
        //Arc data
        .arcsData(this.routes)
        .arcStartLat((d) => d.startLat)
        .arcStartLng((d) => d.startLng)
        .arcEndLat((d) => d.endLat)
        .arcEndLng((d) => d.endLng)
        .arcStroke((d) => (d.stroke || [0.3, 0.5, 0.7][Math.floor(Math.random() * 3)])) //scale with transaction / checkout value
        .arcDashLength(2)
        .arcDashGap(8)
        .arcDashAnimateTime(4000)
        .arcDashInitialGap((d) => (d.order || 1) * 0.5) // Stagger animation based on order
        .arcColor((d) => d.color || 'rgba(255, 255, 255, 0.8)')
        //Rings data
        .ringsData([
          { lat: 51.5074, lng: -0.1278, color: () => `#336ecc` },
          { lat: 48.8566, lng: 2.3522, color: () => `#336ecc` },
        ])
        .ringColor((ring) => (t) => ring.color(t)) // Color changes over time
        .ringMaxRadius(5) // Maximum size of the rings
        .ringPropagationSpeed(2) // Speed at which the rings expand
        .ringRepeatPeriod(4000) // Period between rings
        //Country data
        .hexPolygonsData(countries.features)
        .hexPolygonResolution(3)
        .hexPolygonMargin(0.7)
        .hexPolygonColor(() => 'rgba(255, 255, 255, 0.3)')
        .showAtmosphere(true)
        .atmosphereColor('#336ecc')
        .atmosphereAltitude(0.1);

      scene.add(globe);

      // Add lights
      const ambientLight = new THREE.AmbientLight(0xffffff, 0.6);
      const directionalLight = new THREE.DirectionalLight(0xffffff, 0.8);
      directionalLight.position.set(400, 200, 300);
      scene.add(ambientLight, directionalLight);

      // Add controls
      const controls = new OrbitControls(camera, renderer.domElement);
      controls.autoRotate = true;
      controls.autoRotateSpeed = 0.5;
      controls.minPolarAngle=Math.PI / 3.5
      controls.maxPolarAngle=Math.PI - Math.PI / 3

      // Animation loop
      const animate = () => {
        requestAnimationFrame(animate);
        controls.update();
        renderer.render(scene, camera);
      };

      animate();

      // Handle resize
      window.addEventListener('resize', () => {
        camera.aspect = container.clientWidth / container.clientHeight;
        camera.updateProjectionMatrix();
        renderer.setSize(container.clientWidth, container.clientHeight);
      });
    },
  },
};
</script>

<style scoped>
#globe-container {
  width: 100%;
  height: 100vh;
  overflow: hidden;
}
</style>
