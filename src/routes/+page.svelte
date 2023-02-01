<script>
  import { apiKey } from './apiKey.js';

  let code = '';

  async function refactorCode(code) {
    const response = await fetch('https://api.openai.com/v1/engines/gpt-3/jobs', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'Authorization': 'Bearer API_KEY',
      },
      body: JSON.stringify({
        prompt: `Refactor the following code:\n${code}\n`,
      }),
    });
    const result = await response.json();
    console.log(result);
  }
</script>

<h1>One Click Code Refactor</h1>
<textarea bind:value={code}></textarea>
<button on:click={refactorCode}>Refactor Code</button>
