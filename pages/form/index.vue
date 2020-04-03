<template>
  <div class="container">
    <div class="row mt-3 mb-5">
      <div class="col"></div>
      <div class="col-10 col-sm-6">
        <div class="card border-dark">
          <div class="card-header bg-dark">
            <span class="h5 text-dark">.</span>
          </div>
          <div class="card-body">
            <h5 class="card-title">Send us your question</h5>

            <input class="form-control mb-3" placeholder="Name" v-model="question.name">

            <input class="form-control mb-3" placeholder="Email" v-model="question.email">

            <label for="sel1">Your age:</label>
            <select class="form-control mb-3" id="sel1">
              <option v-for="item in 99">{{item}}</option>
            </select>

            <span>Your favourite place: </span>

            <div class="custom-control custom-radio">
              <input type="radio" class="custom-control-input" id="rbtn1" name="rbtnGroup" checked>
              <label class="custom-control-label" for="rbtn1">Air</label>
            </div>
            <div class="custom-control custom-radio">
              <input type="radio" class="custom-control-input" id="rbtn2" name="rbtnGroup">
              <label class="custom-control-label" for="rbtn2">Ground</label>
            </div>
            <div class="custom-control custom-radio mb-3">
              <input type="radio" class="custom-control-input" id="rbtn3" name="rbtnGroup">
              <label class="custom-control-label" for="rbtn3">Water</label>
            </div>

            <textarea class="form-control mb-3" placeholder="Your question" v-model="question.text"></textarea>

            <div class="mb-3">
              <label> <input type="checkbox"> Contact me via email</label>
            </div>

            <div align="right">
              <button type="button" class="btn bg-primary text-white" @click="submit">Submit</button>
            </div>
          </div>
        </div>
      </div>
      <div class="col"></div>
    </div>

    <chart-bar></chart-bar>
    <chart-doughnut></chart-doughnut>
    <chart-line></chart-line>

    <map></map>

  </div>
</template>

<script>
    import Swal from "sweetalert2"
    import ChartBar from "../../components/ChartBar";
    import ChartDoughnut from "../../components/ChartDoughnut";
    import ChartLine from "../../components/ChartLine";
    import Map from "../../components/Map";

    export default {
        components: {
            ChartBar,
            ChartDoughnut,
            ChartLine,
            Map
        },
        data() {
            return {
                question: {
                    name: '',
                    email: '',
                    text: ''
                },
                text: "",
            }
        },

        methods: {
            submit() {
                this.$axios.get('http://localhost:5000/users')
            },

            saveToFile() {
                let link = document.createElement('a');
                link.download = 'question.txt';
                let blob = new Blob([JSON.stringify(this.question)], {type: 'text/plain'});
                link.href = URL.createObjectURL(blob);
                link.click();
                URL.revokeObjectURL(link.href);
            }
        }
    }
</script>
