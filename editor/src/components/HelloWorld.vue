<template>
    <div>
    <div class="sidepane col-sm-2 col-md-2 col-lg-2">
        <div class="form">
            <h3>Form</h3>
            <input type="file" class="form-control" placeholder="Upload Your Images" name="upload">
            <button id="submit" class="btn btn-default">upload</button>
            <!-- Upload Form here -->
        </div>
        <hr />
        <div class="assets">
            <h3>Assets</h3>
            <div class="text">
                <h4>Text</h4>
                <button id="addText" class="btn btn-default">Add Text</button>
            </div>
            <div class="image">
                <h4>Images</h4>
                <ul class="list-unstyled">
                    <!-- List of images here -->
                    <!-- <li><img src="images/sample.jpeg" class="img-rounded" /></li> -->
                </ul>
            </div>
        </div>
    </div>
    <div class="canvas col-sm-8 col-md-8 col-lg-8">
        <div class="block">
        </div>
    </div>
    </div>
</template>



<script>
	import Vue from 'vue';
//	import axios from 'axios';
//	import VueAxios from 'vue-axios';

    const api = 'https://picsum.photos/200/300';
	Vue.axios.get(api).then((response) => {
		console.log(response)
	});

	export default {
		name: 'HelloWorld',
		props: {
			msg: String
		}
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
