<template>
    <div>

        <div class="sidepane col-sm-2 col-md-2 col-lg-2">
            <div class="form">
                <h3>Form</h3>
                <input type="file" accept="image/*"  @change="onChange" class="form-control"
                       placeholder="Upload Your Images" name="upload"/>
                <button id="submit"  class="btn btn-default">upload</button>
                <!-- Upload Form here -->
            </div>
            <hr/>
            <div class="assets">
                <h3>Assets</h3>
                <div class="text">
                    <h4>Text</h4>
                    <button id="addText" class="btn btn-default">Add Text</button>
                    <input value="" />
                </div>
                <div class="image">
                    <h4>Images</h4>
                    <ul class="list-unstyled">
                        <li v-for="item in images" v-bind:key="item.length">
                            <img :src="item.pathLong">
                        </li>
                    </ul>
                </div>
            </div>
        </div>
        <div class="canvas col-sm-8 col-md-8 col-lg-8">
            <div class="block">
                <div id="preview">
                    <img v-if="item.imageUrl" :src="item.imageUrl" />
                </div>
            </div>
        </div>
    </div>
</template>


<script>
	export default {
		name: 'HelloWorld',
		data() {
			return {
				images: [],
                text: "",
				item: {
					image: null,
					imageUrl: null
				}
			};
		},
		props: {
			msg: String
		},

		mounted() {
			this.importAll(require.context('../images/', true, /\.png$/));
		},

		methods: {
			importAll(r) {
				r.keys().forEach(key => (this.images.push({pathLong: r(key), pathShort: key})));
			},
			onChange(e) {
				const file = e.target.files[0]
				this.image = file
				this.item.imageUrl = URL.createObjectURL(file)
			}
		},
	}
</script>

<style scoped>
    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }
</style>
