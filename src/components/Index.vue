<template>
    <div>
        <h1>Product</h1>

        <table class="table table-hover">
            <thead>
            <tr>
                <td>Id</td>
                <td>Name</td>
                <td>Price</td>
            </tr>
            </thead>

            <tbody>
                <tr v-for="item in items" :key="item.id">
                    <td>{{ item.id }}</td>
                    <td>{{ item.name }}</td>
                    <td>{{ item.price }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>

    export default {
        data(){
            return{
                items: []
            }
        },

        created: function()
        {
            this.fetchItems();
        },

        methods: {
            fetchItems()
            {
              let uri = 'http://localhost:8089/api/v2/index';
              this.axios.get(uri).then((response) => {
                  this.items = response.data;
                  console.log(this.items);
              });
            },
        }
    }
</script>
