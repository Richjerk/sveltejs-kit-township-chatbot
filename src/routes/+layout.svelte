<script>
  import Header from './Header.svelte';
  import './styles.css';

  let chatMessages = [
    // Initialize with welcome message or any existing messages
    { text: "Welcome to the Township Small Business Chatbot.", isUser: false },
  ];

  // Function to handle user input and generate bot responses
  const handleUserInput = (userMessage) => {
    // Add the user's message to the chat
    chatMessages = [...chatMessages, { text: userMessage, isUser: true }];

    // Replace this with your OpenAI integration to get bot responses
    const botResponse = "Sure, I can help you with that. How can I assist you further?";
    
    // Add the bot's response to the chat
    chatMessages = [...chatMessages, { text: botResponse, isUser: false }];
  };
</script>

<div class="app">
  <Header />

  <main>
    <div class="chat-container">
      {#each chatMessages as message (message.text)}
        <div class:{"user-message": message.isUser, "bot-message": !message.isUser}>
          {message.text}
        </div>
      {/each}
    </div>

    <!-- User input field and submit button -->
    <div class="user-input">
      <input type="text" placeholder="Type your message" />
      <button on:click={submitUserInput}>Send</button>
    </div>
  </main>

  <footer>
    <p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to learn SvelteKit</p>
  </footer>
</div>

<style>
  .app {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  main {
    flex: 1;
    display: flex;
    flex-direction: column;
    padding: 1rem;
    width: 100%;
    max-width: 64rem;
    margin: 0 auto;
    box-sizing: border-box;
  }

  .chat-container {
    flex: 1;
    display: flex;
    flex-direction: column;
    overflow-y: auto;
    padding: 1rem;
    border: 1px solid #ccc;
    border-radius: 5px;
  }

  .user-message {
    align-self: flex-end;
    background-color: #007aff;
    color: white;
    border-radius: 10px 10px 0 10px;
    margin: 5px;
    padding: 10px;
    max-width: 70%;
  }

  .bot-message {
    align-self: flex-start;
    background-color: #f0f0f0;
    border-radius: 10px 10px 10px 0;
    margin: 5px;
    padding: 10px;
    max-width: 70%;
  }

  .user-input {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 1rem;
  }

  .user-input input {
    flex: 1;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    margin-right: 10px;
  }

  .user-input button {
    background-color: #007aff;
    color: white;
    border: none;
    border-radius: 5px;
    padding: 10px 20px;
    cursor: pointer;
  }

  footer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 12px;
  }

  footer a {
    font-weight: bold;
  }

  @media (min-width: 480px) {
    footer {
      padding: 12px 0;
    }
  }
</style>
