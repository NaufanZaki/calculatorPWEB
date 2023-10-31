<template>
  <div class="calculator">
    <div class="display"></div>
    <div class="buttons">
      <button class="button clear">C</button>
      <button class="button operator">/</button>
      <button class="button operator">*</button>
      <button class="button operator">-</button>
      <button class="button number">1</button>
      <button class="button number">2</button>
      <button class="button number">3</button>
      <button class="button operator">+</button>
      <button class="button number">4</button>
      <button class="button number">5</button>
      <button class="button number">6</button>
      <button class="button number">7</button>
      <button class="button number">8</button>
      <button class="button number">9</button>
      <button class="button number zero">0</button>
      <button class="button number">.</button>
      <button class="button equal">=</button>
    </div>
  </div>
</template>
<script>
  document.addEventListener("DOMContentLoaded", function() {
    const display = document.querySelector('.display');
    const buttons = document.querySelectorAll('.button');

    let expression = '';

    buttons.forEach((button) => {
      button.addEventListener('click', () => {
        if (button.classList.contains('number')) {
          expression += button.textContent;
          display.textContent = expression;
        } else if (button.classList.contains('operator')) {
          expression += ` ${button.textContent} `;
          display.textContent = expression;
        } else if (button.classList.contains('equal')) {
          display.textContent = eval(expression);
          expression = '';
        } else if (button.classList.contains('clear')) {
          display.textContent = '';
          expression = '';
        }
      });
    });
  });
</script>
<style>
body {
    font-family: Arial, sans-serif;
    margin: 0;
  }
  
  .calculator {
    width: 320px;
    margin: 50px auto;
    background-color: #333;
    border-radius: 5px;
    box-shadow: 0px 0px 10px #ccc;
  }
  
  .display {
    height: 50px;
    padding: 10px;
    text-align: right;
    font-size: 24px;
    border-bottom: 1px solid #ccc;
  }
  
  .buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 1px;
  }
  
  .button {
    background-color: #fff;
    border: none;
    font-size: 18px;
    cursor: pointer;
  }
  
  .number {
    color: #333;
  }
  
  .operator {
    color: #f00;
  }
  
  .equal {
    background-color: #f00;
    color: #fff;
  }
  
  .zero {
    grid-column: 1 / 3;
  }
  
</style>
