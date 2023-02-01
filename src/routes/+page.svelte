<script>
  import { apiKey } from './apiKey.js';
  import axios from 'axios';

  let code = '';

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
          "model": "text-davinci-edit-001",
          "input": "my input",
          "instruction": "instruction"
        }
      });
      console.log(response.data);
    } catch (error) {
      console.error(error);
    }
  }

  refactorCode();
</script>

<h1>One Click Code Refactor</h1>
<textarea bind:value={code}></textarea>
<button on:click={refactorCode}>Refactor Code</button>
