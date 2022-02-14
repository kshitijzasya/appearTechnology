<template>
    <div class="row">
      <div class="col-md-6">
        <div class="form_bg">
          <h3>Your Interest Calculator</h3>
          <div class="input_bg">
            <label for="customRange1" class="form-label form_label_new"
              >Loan Amount</label
            >
            <div class="chrome">
              <output type="" class="form-range" id="range-output"
                >$ {{ rangeChange }}</output
              >
              <input type="range" value="1000" max="35000" step="1000" v-on:input="inputChange"/>
            </div>
          </div>

          <div class="input_bg">
            <label class="form-label">Loan Terms</label>
            <select class="form-select" aria-label="Default select example" @change="loanYearChange">
              <option v-for="term in loanTerms" :key="term.id" :value="term.id" :selected="selectedLoanTerm === term.id">{{term.name}}</option>
            </select>
          </div>

          <div class="input_bg">
            <label class="form-label">Repayment Terms</label>
            <select class="form-select" aria-label="Default select example" @change="repaymentTermsChange">
              <option v-for="term in repaymentTerms" :key="term.id" :value="term.id" :selected="selectedRepaymentTerm === term.id">{{term.text}}</option>
            </select>
          </div>

          <div class="input_bg">
            <div class="total_amount">
              <label>{{ repaymentTerms.find(i => i.id == selectedRepaymentTerm).text}} Repayment</label>
              <h4>${{ monthlyRepayment }}</h4>
            </div>

            <div class="total_amount">
              <label>Total Repayment</label>
              <h4>${{ totalReplayment }}</h4>
            </div>
          </div>
          <div class="input_bg">
            <button type="button" class="btn btn-primary">
              Calculate repayments
            </button>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
    name: 'Calculator',   
    data: function() {
        return {
            rangeValue: 0,
            loanTerms:[
                {
                    id: 1,
                    name: '1 Years',
                },
                {
                    id: 2,
                    name: '2 Years',
                },
                {
                    id: 3,
                    name: '3 Years',
                },
                {
                    id: 4,
                    name: '4 Years',
                }
            ],
            repaymentTerms: [
                { id: 1, text: 'Weekly' },
                { id: 2, text: 'Fortnightly' },
                { id: 3, text: 'Monthly' },
                { id: 4, text: 'Yearly' }
            ],
            selectedLoanTerm: 1,
            selectedRepaymentTerm: 1,
            monthlyRepayment: 99.62,
            totalReplayment: 99.63
        }
    },
    computed: {
        rangeChange: function() {
            return this.rangeValue;
        }
    },
    methods: {
        inputChange: function(e) {
            let _this = e.target; 
        var value = ((_this.value - _this.min) / (_this.max - _this.min)) * 100; 
        _this.style.background = 'linear-gradient(to right, #4339cd 0%, #4339cd ' + value + '%, #e9e9e9 ' + value + '%)'; 
        this.rangeValue = _this.value;
        },
        loanYearChange: function(e) {
            this.selectedLoanTerm = e.target.value
        },
        repaymentTermsChange: function(e) {
            this.selectedRepaymentTerm = e.target.value;
        }
    }
}
</script>
<style>
.bg_left
{
	background:#2e2fd5;

}
.no_margin
{
	margin:0px !important;
	padding:0px !important;
	
}
.bg_right img
{
	width:100%;
	height:100%;
	
}

.form_bg
{
    position: fixed;
    padding: 20px;
    border-radius: 5px;
    background: white;
    top: 15%;
	width:40%;
	margin-left:50px;
}

.total_amount h4 {
    font-weight: bold;
}

.input_bg
{
	float:left;
	width:100%;
	margin-bottom:30px;
	
}

.form_bg h3 {
    margin-bottom: 50px;
}

.input_bg label {
    font-weight: bold;
	
}

.form_label_new
{
	position:absolute;
	
}
.input_bg output {
    color: #4339cd;
    font-weight: bold;
	float: right;
    width: auto;
}


.total_amount
{
	float:left;
	width:50%;
	
}

.input_bg button
{
	width:100%;
	padding:10px;
	margin-top:30px;
	font-size: 20px;
	background:#302ed9;
	
}

.chrome input {

    background: linear-gradient( #dfdfdf 50%, #dfdfdf 100%);
     border-radius: 8px;
    height: 7px;
    width: 100%;
    outline: none; 
    transition: background 450ms ease-in;
    -webkit-appearance: none;
  }
  
  input::-webkit-slider-thumb {
    background-color: #3028bc;
    border-radius: 0;
    height: 15px;
    width: 15px;
    border-radius: 50%;
    -webkit-appearance: none;
  }

</style>