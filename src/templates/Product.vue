<template>
    <Layout>
        <div v-if="this.$page.gcms.product" class="product_layout" >
            <div> 
              <g-image :src="product.images[0].url" class="img" alt="new image" />    
            </div>
            <div>
                <h1> {{ product.name }} </h1>
                <p > {{ product.description }} </p>
                <p>
                    ${{ product.price}}
                </p>
                <p>
                    ${{ product.orderItems}}
                </p>
            </div>
            
        </div>
    </Layout>
</template>

<script>
export default {
    data() {
        return {
            product: {
                name: '',
                description:'',
                images: [{
                    url: ''
                }]

            }
        
        }
    },
    created(){
        this.product = this.$page.gcms.product
        console.log('Product here', this.product)
    }
}  
</script>

<page-query>
query GetProduct($id: ID) {
    gcms {
        product(where: {id: $id}) {
                id
            name
            description
            price
            images{
                url
            }
        }
    }
}
</page-query>

<style scoped>
    .img{
        width: 300px;
    }
    .product_layout{
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        margin-top: 2rem;
    }
</style>