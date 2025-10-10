





# Three.js

https://threejs.org
http://www.webgl3d.cn
https://tonite.dance , https://showroom.littleworkshop.fr
https://www.iqiyi.com/v_19rri0vxp0.html
https://cdn.bootcdn.net/ajax/libs/three.js/r128/three.js
https://www.youtube.com/c/BrunoSimon/videos

three.js是JavaScript编写的WebGL第三方库，提供了非常多的3D显示功能。参考了OpenGL规范。canvas是简单的2D图形，不能调用显卡，但是WebGL可以调用显卡接口。WebGL接口比较底层，需要掌握大量数学知识和3D空间的知识概念才能开发出来，离散数学和矩阵相乘。

node下载：npm install three --save-dev

源文件内容：大部分内容都是example
bulid项目生成源码three.js是项目引入的文件min是打包文件，module是模块化的文件
docs是文档
editor是盒子编辑器
examples/js&jsm别人开发好的插件二次封装的控制器，textures是材质
src源码，有好多模块，animation动画 audio音频 cameras摄像机 core核心 extras附件 geometries几何体 helpers辅助对象 lights灯光 loaders加载器 materials材质 math数学 object对象 renderers渲染器 scenes场景 textures纹理贴图特效
test测试
utils

threejs是基于canvas标签的

模型mesh：几何体geometries有立方体球体圆锥等，还能定义自己的几何体无数的三角形组成的。加载器loaders能把建模师创建好的模型导入进来，MMD OBJ MLTF。虚拟模型光线
场景scene：存放不同的模型。
相机camera：世界的第一人称，有渲染范围
渲染器renderer：渲染到标签中。投影渲染后期特效。
上面四个缺一不可



操作流程
1生成几何体材质添加到场景中。
2生成场景导入模型。
3生成相机添加控制器。
4生成渲染器，场景和相机添加到渲染器当中。建立和canvas的关联。
5动画（更新）模块，动画连续相机控制



```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<title>Three test</title>
	<style>
		body {margin: 0;padding: 0;overflow: hidden;}
		canvas {margin: 0;}</style>
	<script type="text/javascript" src="three.js"></script>
</head>
<body>
<canvas id="canvas"></canvas>
<script>

	// 画布,重置画布大小
	let width = window.innerWidth;
	let height = window.innerHeight;
	const canvas = document.querySelector("#canvas");
	window.onload = resize;
	window.onresize = resize;
	function resize() {
		width = canvas.width = window.innerWidth;
		height = canvas.height = window.innerHeight;
		renderer.setSize(width, height);
	}

	// 场景
	const scene = new THREE.Scene();
	// 相机
	const camera = new THREE.PerspectiveCamera(75, width / height, 0.01, 1000);
	camera.position.z = 8;
	camera.lookAt(0, 0, 0);

	// 渲染器
	const renderer = new THREE.WebGLRenderer({canvas});

	// 灯光
	const light = new THREE.AmbientLight(0xffffff, 0.5);

	// 几何体
	const geometry = new THREE.BoxGeometry(5, 5, 5);
	const material = new THREE.MeshNormalMaterial();
	const box = new THREE.Mesh(geometry, material);
	box.rotation.x = 45;
	box.rotation.y = 45;
	scene.add(box);

	function animation() {
		requestAnimationFrame(animation);
		box.rotation.x += 0.01;
		box.rotation.y += 0.01;
		renderer.render(scene, camera);
	}
	animation();

</script>
</body>
</html>



```




几何体与材质
世界坐标系，x向右y向上z向前三条轴
向量，THREE.Vector(1,2,3)
控制器，/examples/js/controls/OrbitControls.js 可以用鼠标移动拖拽缩放























