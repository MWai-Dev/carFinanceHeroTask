<script setup>

    import { defineModel } from 'vue';

    const loanValueCheck = defineModel('loanValueCheck');
    const submitChange = defineModel('submitChange');
    const chosenTerm = defineModel('chosenTerm');
    const loanValue = defineModel('loanValue');

    // Handle form submission - load application page if form is completed correctly
    const submitForm = () => {
        if (loanValueCheck.value === false) {
            setTimeout(() => {
                submitChange.value = true;
            }, 1);
        }
    };

    // Handle when loan amount input changes
    const loanValueChange = (e) => {        
        loanValue.value = Number(e.target.value);
        
        setTimeout(() => {
            if (loanValue.value < 1000 || loanValue.value > 20000) {
                loanValueCheck.value = true;
            } else {
                loanValueCheck.value = false;
            }

            // add min/max value if value entered is too low/high
            // if (loanValue.value < 1000) {
            //     e.target.value = 1000;
            // } else if (loanValue.value > 20000) {
            //     e.target.value = 20000;
            // }            
        }, 1);        
    };

    // Handle when loan terms are selected
    const setTerm = (e) => {
        chosenTerm.value = Number(e.target.value);
        setTimeout(() => {
            console.log('Chosen Term', chosenTerm.value);
        }, 1);        
    };

</script>

<template>

    <div class="heroSection">

        <div class="heroCopy">

            <h1>Great finance deals to help you drive home in style</h1>

            <div class="carImage">
                <img src="../assets/car1.png" alt="Stylish car image" />
            </div>

            <div class="borrowCopy">
                <p>Borrow anything from:</p>
                <h2>£1,000 to £20,000</h2>
            </div>
            
            <p><strong>Rates from 9.9% APR</strong> The exact rate you will be offered will be based on your circumstances, subject to status.</p>
        
        </div>

        <form id="form" v-on:submit.prevent>

            <div class="loanSection">
                <label for="loanInput">Loan amount:</label>
                <div class="loanField"> 
                    <div class="fieldPrefix">£</div>               
                    <input id="loanInput" name="loanInput" type="number" ref="loanInput" value="5000" min="1000" max="20000" @change="(e) => loanValueChange(e)" required />
                </div>
            </div>

            <span v-if="loanValueCheck === true" class="error">
                Please enter between £1,000 & £20,000
            </span>

            <div class="termSection">
                <label for="loanInput">Loan term:</label>
                <div class="termField">
                    <ul class="termSelections">
                        <li>
                            <input id="term_6" name="term" type="radio" value="6" @click="(e) => setTerm(e)" checked>
                            <label for="term_6">6 months</label>
                        </li>
                        <li>
                            <input id="term_12" name="term" type="radio" value="12" @click="(e) => setTerm(e)">
                            <label for="term_12">12 months</label>
                        </li>
                        <li>
                            <input id="term_18" name="term" type="radio" value="18" @click="(e) => setTerm(e)">
                            <label for="term_18">18 months</label>
                        </li>
                        <li>
                            <input id="term_24" name="term" type="radio" value="24" @click="(e) => setTerm(e)">
                            <label for="term_24">24 months</label>
                        </li>
                        <li>
                            <input id="term_36" name="term" type="radio" value="36" @click="(e) => setTerm(e)">
                            <label for="term_36">36 months</label>
                        </li>
                    </ul>
                </div>                
            </div>

            <button id="formSubmit" type="submit" value="Get Your Quote"  @click="submitForm()">Get Your Quote</button>
    
        </form>

        <div class="whiteExtent"></div>
        <div class="whiteExtent"></div>

    </div>

</template>