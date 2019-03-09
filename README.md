### setup memo

0. initialize node project

    ```
    npm init
    ```

1. install modules

    ```
    npm i -S vue
    npm i -D parcel-bundler
    ```

2. update package.json

    ```
    {
      ...
      "scripts": {
        "dev": "parcel src/index.html",
        "watch": "parcel watch src/index.html",
        "build": "rm -rf dist/ && parcel build src/index.html"
      },
      ...
      "alias": {
        "vue": "./node_modules/vue/dist/vue.common.js"
      }
    }
    ```

3. write code

    ```
    # make source directory
    mkdir src && cd $_

    # create index.html
    cat << EOF > index.html
    <!DOCTYPE html>
    <html lang="en">
      <head>
        <title>Parcel - Vue</title>
      </head>
      <body>
        <div id="app"></div>
        <script src="./index.js"></script>
      </body>
    </html>
    EOF

    # create index.js (entry point of javascript)
    cat << EOF > index.js
    import Vue from 'vue';
    import App from './App.vue';

    Vue.component('App', App);

    new Vue({
      el: '#app',
      template: '<App></App>',
    });
    EOF

    # create main Vue component
    cat << EOF > App.vue
    <template>
      <div>
        <c-hello></c-hello>
      </div>
    </template>

    <script>
    import Vue from "vue";
    import Hello from "./components/Hello";
    export default Vue.extend({
      components: {
        'c-hello': Hello,
      },
      props: {},
      data() {
        return {};
      },
      computed: {},
      mounted() {
        const msg = this.getMsg();
        console.log(msg);
      },
      methods: {
        getMsg() {
          return "Hello Vue! (from App.vue)";
        },
      },
    });
    </script>

    <style>
    </style>
    EOF

    # create sub Vue component
    mkdir components && cd $_
    cat << EOF > Hello.vue
    <template>
      <div>
        <h1 class="hello">{{hello}}</h1>
      </div>
    </template>

    <script lang="ts">
    export default {
      props: {},
      data() {
        return {
          bundler: "Parcel",
        };
      },
      computed: {
        hello() {
          if (!this.bundler) return '';
          return 'Hello ' + this.bundler + '!';
        },
      },
      mounted() {
        console.log('Hello Vue! (from Hello.vue)');
      },
      methods: {},
    };
    </script>

    <style lang="postcss" scoped>
    .hello {
      color: green;
    }
    </style>
    EOF
    ```

4. run local dev server with hot module reload
    * terminal 1
        ```
          npm run dev
        ```
    * terminal 2
        ```
          npm run watch
        ```

5. access

    http://localhost:1234
