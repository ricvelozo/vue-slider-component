<template>
	<div id="app">
		<section data-title="Default">
			<div>
				<vue-slider ref="slider1" v-bind="demo.default" :val="demo.default.val" @callback="callback('default', $event)"></vue-slider>
				<h3><small>Value: </small>{{ demo.default.val }}</h3>
			</div>
			<div>
				<code>{
				<template v-for="(value, key, index) of demo.default">
					<span class="green">{{ key }}</span>: <span class="yellow">{{ value }}</span><small class="gray ml-sm">// {{ demo.annotation[key] }}</small><br>
				</template>}</code>
			</div>
		</section>
		<section data-title="Demo">
			<div>
				<vue-slider ref="slider2" v-bind="demo.demo1" @callback="callback('demo1', $event)"></vue-slider>
				<h3><small>Value: </small>{{ demo.demo1.val }}</h3>
				<div class="btn-group">
					<button @click="setValue('demo1', 21)">set value = 21</button>
					<button @click="setIndex('slider2', 2)">set index = 2</button>
					<button @click="setDisabled('demo1')">set disabled</button>
					<button @click="setTooltip('demo1')">switch tooltip</button>
					<button @click="getValue('slider2')">getValue()</button>
					<button @click="getIndex('slider2')">getIndex()</button>
				</div>
			</div>
			<div>
				<code>{
				<template v-for="(value, key, index) of demo.demo1">
					<span class="green">{{ key }}</span>: <span class="yellow">{{ value }}</span><br>
				</template>}</code>
			</div>
		</section>
		<section data-title="Custom Data">
			<div>
				<vue-slider ref="slider3" v-bind="demo.demo2" @callback="callback('demo2', $event)"></vue-slider>
				<h3><small>Value: </small>{{ demo.demo2.val }}</h3>
				<div class="btn-group">
					<button @click="setValue('demo2', '2016-10-06')">set value = 2016-10-06</button>
					<button @click="setIndex('slider3', 3)">set index = 3</button>
					<button @click="setDisabled('demo2')">set disabled</button>
					<button @click="setTooltip('demo2')">switch tooltip</button>
					<button @click="getValue('slider3')">getValue()</button>
					<button @click="getIndex('slider3')">getIndex()</button>
				</div>
			</div>
			<div>
				<code>{
				<template v-for="(value, key, index) of demo.demo2">
					<span class="green">{{ key }}</span>: <span class="yellow">{{ value }}</span><br>
				</template>}</code>
			</div>
		</section>
		<section data-title="Range">
			<div>
				<vue-slider ref="slider4" v-bind="demo.demo3" @callback="callback('demo3', $event)"></vue-slider>
				<h3><small>Value: </small>{{ demo.demo3.val }}</h3>
				<div class="btn-group">
					<button @click="setValue('demo3', [100, 200])">set value = [100, 200]</button>
					<button @click="setIndex('slider4', 50)">set index = 50</button>
					<button @click="setDisabled('demo3')">set disabled</button>
					<button @click="setTooltip('demo3')">switch tooltip</button>
					<button @click="getValue('slider4')">getValue()</button>
					<button @click="getIndex('slider4')">getIndex()</button>
				</div>
			</div>
			<div>
				<code>{
				<template v-for="(value, key, index) of demo.demo3">
					<span class="green">{{ key }}</span>: <span class="yellow">{{ value }}</span><br>
				</template>}</code>
			</div>
		</section>
		<section data-title="Range + Custom Data">
			<div>
				<vue-slider ref="slider5" v-bind="demo.demo4" @callback="callback('demo4', $event)"></vue-slider>
				<h3><small>Value: </small>{{ demo.demo4.val }}</h3>
				<div class="btn-group">
					<button @click="setValue('demo4', ['10-02', '10-12'])">set value = ["10-02", "10-12"]</button>
					<button @click="setIndex('slider5', 15)">set index = 15</button>
					<button @click="setDisabled('demo4')">set disabled</button>
					<button @click="setTooltip('demo4')">switch tooltip</button>
					<button @click="getValue('slider5')">getValue()</button>
					<button @click="getIndex('slider5')">getIndex()</button>
				</div>
			</div>
			<div>
				<code>{
				<template v-for="(value, key, index) of demo.demo4">
					<span class="green">{{ key }}</span>: <span class="yellow">{{ value }}</span><br>
				</template>}</code>
			</div>
		</section>
		<section data-title="Vertical">
			<div>
				<vue-slider ref="slider6" v-bind="demo.demo5" :reverse="true" tooltipDir="left" @callback="callback('demo5', $event)" @drag-start="start" @drag-end="end"></vue-slider>
				<vue-slider ref="slider6" v-bind="demo.demo5" :reverse="false" tooltipDir="right" @callback="callback('demo5', $event)" @drag-start="start" @drag-end="end"></vue-slider>
				<h3><small>Value: </small>{{ demo.demo5.val }}</h3>
				<div class="btn-group">
					<button @click="setValue('demo5', 80)">set value = 80</button>
					<button @click="setIndex('slider6', 15)">set index = 15</button>
					<button @click="setDisabled('demo5')">set disabled</button>
					<button @click="setTooltip('demo5')">switch tooltip</button>
					<button @click="getValue('slider6')">getValue()</button>
					<button @click="getIndex('slider6')">getIndex()</button>
				</div>
			</div>
			<div>
				<code>{
				<template v-for="(value, key, index) of demo.demo5">
					<span class="green">{{ key }}</span>: <span class="yellow">{{ value }}</span><br>
				</template>}</code>
			</div>
		</section>
	</div>
</template>

<script>
import vueSlider from './vue2-slider.vue';

export default {
	components: {
		vueSlider
	},
	data () {
		return {
			demo: {
				default: {
					width: 'auto',
					height: 4,
					direction: 'horizontal',
					dotSize: 16,
					eventType: 'auto',
					min: 0,
					max: 100,
					interval: 1,
					disabled: false,
					show: true,
					tooltip: 'always',
					tooltipDir: 'top',
					piecewise: false,
					reverse: false,
					speed: 0.5,
					val: 0
				},
				demo1: {
					width: 250,
					height: 8,
					dotSize: 20,
					min: 1,
					max: 25,
					interval: 4,
					disabled: false,
					show: true,
					speed: 0.3,
					reverse: false,
					tooltip: 'hover',
					piecewise: true,
					val: 1
				},
				demo2: {
					width: '80%',
					tooltip: 'always',
					disabled: false,
					piecewise: true,
					tooltipDir: 'bottom',
					styles: {
						margin: '0 10% 50px',
					},
					data: [
					  "2016-10-01",
					  "2016-10-02",
					  "2016-10-03",
					  "2016-10-04",
					  "2016-10-05",
					  "2016-10-06",
					  "2016-10-07"
					],
					val: '2016-10-01'
				},
				demo3: {
					width: '100%',
					height: 8,
					dotSize: 20,
					min: 0,
					max: 500,
					interval: 5,
					disabled: false,
					show: true,
					tooltip: 'always',
					piecewise: false,
					val: [0, 100]
				},
				demo4: {
					width: '100%',
					height: 4,
					dotSize: 14,
					min: 1,
					max: 100,
					interval: 3,
					disabled: false,
					show: true,
					tooltip: 'always',
					piecewise: true,
					data: [
						'10-01',
						'10-02',
						'10-03',
						'10-04',
						'10-05',
						'10-06',
						'10-07',
						'10-08',
						'10-09',
						'10-10',
						'10-11',
						'10-12',
						'10-13',
						'10-14',
						'10-15',
						'10-16',
						'10-17',
						'10-18',
						'10-19',
						'10-20'
					],
					val: ['10-01', '10-05']
				},
				demo5: {
					width: 4,
					height: 300,
					dotSize: 12,
					eventType: 'auto',
					min: 0,
					max: 100,
					interval: 1,
					disabled: false,
					show: true,
					tooltip: 'always',
					piecewise: false,
					styles: {
						display: 'inline-block',
						marginLeft: '30px'
					},
					direction: 'vertical',
					speed: 0.5,
					val: 0
				},
				annotation: {
					width: '组件宽度',
					height: '组件高度',
					direction: '组件方向',
					eventType: '事件类型',
					dotSize: '滑块大小',
					min: '最小值',
					max: '最大值',
					interval: '分段间隔',
					disabled: '是否不可用',
					show: '是否显示组件',
					speed: '动画速度',
					tooltip: '是否显示工具提示',
					tooltipDir: '工具提示方向',
					piecewise: '是否显示分段样式',
					reverse: '是否反向组件',
					val: '值'
				}
			}
		}
	},
	methods: {
		/* ------- Vue 2.x Two-way ------- */
		callback(name, val) {
			let obj = this.demo[name]
			obj.val = val
		},
		/* ------------------------------- */
		setDisabled(name) {
			let obj = this.demo[name]
			obj.disabled = !obj.disabled
		},
		setTooltip(name) {
			let obj = this.demo[name]
			obj.tooltip = obj.tooltip === 'hover' ? 'always' : 'hover'
		},
		setValue(name, num) {
			let obj = this.demo[name]
			obj.val = num
		},
		setIndex(name, num) {
			let slider = this.$refs[name]
			slider.setIndex(num)
		},
		getValue(name) {
			let slider = this.$refs[name]
			alert(slider.getValue())
		},
		getIndex(name) {
			let slider = this.$refs[name]
			alert(slider.getIndex())
		},
		start() {
			this.demo.demo5.speed = 0
		},
		end() {
			this.demo.demo5.speed = 0.5
		}
	}
}
</script>

<style>
body {
	font-family: Helvetica, sans-serif;
	margin: 0;
	padding: 0;
}

section {
	padding: 60px 20px 20px 20px;
	margin: 10px;
	box-shadow: 0 0 5px 3px rgba(0, 0, 0, .36);
	max-width: 800px;
	overflow: hidden;
	position: relative;
	display: flex;
	flex-direction: column;
}

section::after {
	content: attr(data-title);
	position: absolute;
	left: 5px;
	top: 5px;
	font-size: 14px;
	font-weight: bold;
	color: #333;
}
.btn-group {
	margin: 10px 0;
}

.btn-group button, .upload-group label {
    padding: 8px 12px;
    display: inline-block;
    border: none;
    background-color: #ccc;
    border-radius: 3px;
    margin: 5px 10px 5px 0;
}

.green {
	color: #2ecc71;
}

.yellow {
	color: #ffd400;
	white-space: pre-wrap;
}

.gray {
	color: #D3DCE6;
}

.ml-sm {
	margin-left: 5px;
}

code {
    padding: 10px 20px;
    margin: 0;
    display: block;
    background-color: #333;
    color: #fff;
    white-space: pre-line;
    font-family: Consolas, Monaco, Droid, Sans, Mono, Source, Code, Pro, Menlo, Lucida, Sans, Type, Writer, Ubuntu, Mono;
    border-radius: 5px;
}
</style>
