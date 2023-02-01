<script>
  import { apiKey } from './apiKey.js';
  import axios from 'axios';

  let inputCode;
  let instruction = 'todo';

  async function refactorCode() {
    try {
      const response = await axios({
        method: 'post',
        url: 'https://api.openai.com/v1/edits',
        headers: {
          'Content-Type': 'application/json',
          'Authorization': `Bearer ${apiKey}`
        },
        data: {
          "model": 'code-davinci-edit-001',
          "input": inputCode,
          "instruction": instruction
        }
      });
      console.log(response.data);
    } catch (error) {
      console.error(error);
    }
  }
</script>

<div class="container">
  <h1>One Click Code Refactor</h1>
  <p>Copy paste your code here</p>
  <textarea bind:value={inputCode}></textarea>
  <button on:click={refactorCode}>Refactor Code</button>
</div>

<style>
  .container {
    background-color: #333;
    color: #fff;
    font-family: sans-serif;
    padding: 20px;

    display: flex;
    flex-direction: column;
    align-items: center;
  }

  h1 {
    text-align: center;
    margin-top: 0;
    margin-bottom: 16px;
  }

  p {
    margin-top: 0;
  }

  textarea {
    width: 375px;
    height: 130px;
    background-color: #555;
    color: #fff;
    border: none;
    padding: 10px;
    font-size: 16px;
  }

  @media (max-width: 440px) {
    textarea {
      width: 100%;
    }
  }

  @media (max-width: 300px) {
    textarea {
      width: 160px;
    }
  }

  @media (max-width: 250px) {
    textarea {
      width: 100%;
    }
  }

  button {
    display: block;
    margin: 20px auto;
    margin-bottom: 5px;
    padding: 10px 20px;
    background-color: #fff;
    color: #333;
    border: none;
    cursor: pointer;
  }
</style>
