<template>
  <div class="container">
    <div class="mt-3">
      <div class="jumbotron">
        <h1 class="display-4">Make Earth beautiful again!</h1>
        <p class="lead">We live on this planet called Earth - think about what you might do, today or tomorrow - and
          make the most of it.</p>
        <hr class="my-4">
        <p style="font-style: italic">The Earth is what we have in common.</p>
      </div>
    </div>

    <div class="row">
      <div class="col align-self-center d-flex justify-content-end">
        <button type="button" class="btn bg-primary text-white" @click="indexIn"><</button>
      </div>
      <div class="col-8 text-center">
        <img :src="url" class="imageRound">
      </div>
      <div class="col align-self-center">
        <button type="button" class="btn bg-primary text-white" @click="indexDe">></button>
      </div>
    </div>


    <div class="row mt-5">
      <div class="col-12 col-sm-6">
        <div class="textBackground p-2">
          <h4>Our mission</h4>
          <ul>
            <li>To inspire humanity – both in the air and on the ground</li>
            <li>To create a better everyday life for the many people</li>
            <li>To spread the power of optimism</li>
            <li>To accelerate the world's transition to sustainable energy</li>
            <li>Spread ideas</li>
          </ul>
        </div>
      </div>
      <div class="col-12 col-sm-6">
        <h3>Our directors</h3>
        <table class="table table-striped" style="border: 1px solid black">
          <thead class="thead-dark">
          <tr>
            <th scope="col">FullName</th>
            <th scope="col">Email</th>
            <th scope="col">Phone Number</th>
          </tr>
          </thead>
          <tbody>
          <tr v-for="(item, index) in employees" :key="index">
            <td>{{item.name}}</td>
            <td>{{item.email}}</td>
            <td>{{item.phone}}</td>
          </tr>
          </tbody>
        </table>
      </div>
    </div>

    <div class="row mt-5 mb-5">
      <div class="col-12 text-center">
        <iframe width="560" height="315" src="https://www.youtube.com/embed/Vb2ZXRh74WU" frameborder="0"
                allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
                allowfullscreen></iframe>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        data() {
            return {
                employees: [],
                imageUrls: ['https://edgit.eu/wp-content/uploads/2019/02/small-company-vast-knowledge.jpg', 'https://www.mobihealthnews.com/sites/default/files/merger.jpg', 'https://images.financialexpress.com/2017/12/doing-business-620x413.jpg'],
                url: 'https://edgit.eu/wp-content/uploads/2019/02/small-company-vast-knowledge.jpg',
                imageIndex: 0,
            }
        },

        mounted() {
            this.getData()
        },

        methods: {
            async getData() {
                try {
                    let res = await this.$axios.get('https://jsonplaceholder.typicode.com/users')
                    this.employees = res.data
                    this.employees.splice(0, 5)
                } catch (err) {
                    console.log(err)
                }
            },

            indexIn() {
                this.imageIndex = this.imageIndex + 1
                if (this.imageIndex > 2) {
                    this.imageIndex = 0
                }
                this.url = this.imageUrls[this.imageIndex]
            },

            indexDe() {
                this.imageIndex = this.imageIndex - 1
                if (this.imageIndex < 0) {
                    this.imageIndex = 2
                }
                this.url = this.imageUrls[this.imageIndex]
            }
        }
    }
</script>


<style>
  .imageRound {
    border-radius: 50%;
  }

  .textBackground {
    background-color: #E9ECEF;
    border-radius: 16px;
  }

  @media screen and (max-width: 991px) {
    img {
      width: 75%;
    }
  }
</style>

