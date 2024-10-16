<script setup>

    const chosenTerm = defineModel('chosenTerm');
    const loanValue = defineModel('loanValue');

    // Loan calculations - for monthly payment and total loan payment
    let interestRate = 9.9;
    let interestRateDecimal = (interestRate / 100) / 12;
    let monthlyPayments = ((loanValue.value * interestRateDecimal) / (1-Math.pow((1 + interestRateDecimal), - chosenTerm.value))).toFixed(2);
    let totalCost = monthlyPayments * chosenTerm.value;

</script>

<template>

    <div class="application">

        <div class="recap">

            <div class="appLoanValue">
                <p>You would like to borrow:</p>
                <h3>£{{new Intl.NumberFormat().format(loanValue)}}</h3>
            </div>
            
            <div class="appLoanTerm">
                <p>You want to pay it back over:</p>
                <h3>{{chosenTerm}} months</h3>
            </div>

            <div class="appInterest">
                <p>Estimated monthly payment:</p>
                <h3>£{{new Intl.NumberFormat().format(monthlyPayments)}}</h3>
            </div>
            
            <div class="appEstCost">
                <p>Estimated total to pay:</p>
                <h3>£{{new Intl.NumberFormat().format(totalCost)}}</h3>
            </div>
            
        </div>

        <h1>{Application form here}</h1>

        <div class="whiteExtent"></div>
        <div class="whiteExtent"></div>

    </div>

</template>