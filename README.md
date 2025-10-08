<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Chat Application UI</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: "Poppins", sans-serif;
    }

    body {
      background-color: #f2f5f9;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .chat-container {
      width: 420px;
      height: 600px;
      background: white;
      border-radius: 15px;
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.15);
      display: flex;
      flex-direction: column;
      overflow: hidden;
    }

    /* Header */
    .chat-header {
      background: #4a6cf7;
      color: white;
      padding: 15px;
      text-align: center;
      font-weight: 600;
      font-size: 18px;
      letter-spacing: 0.5px;
    }

    /* Messages Area */
    .chat-messages {
      flex: 1;
      padding: 15px;
      overflow-y: auto;
      display: flex;
      flex-direction: column;
    }

    .message {
      max-width: 75%;
      margin: 8px 0;
      padding: 10px 15px;
      border-radius: 20px;
      font-size: 14px;
      line-height: 1.4;
    }

    .sent {
      align-self: flex-end;
      background: #4a6cf7;
      color: white;
      border-bottom-right-radius: 5px;
    }

    .received {
      align-self: flex-start;
      background: #e5e5ea;
      color: #333;
      border-bottom-left-radius: 5px;
    }

    /* Input area */
    .chat-input {
      display: flex;
      align-items: center;
      padding: 10px;
      border-top: 1px solid #ddd;
      background: #fafafa;
    }

    .chat-input input {
      flex: 1;
      border: none;
      outline: none;
      padding: 10px;
      border-radius: 20px;
      background: #f1f3f6;
      font-size: 14px;
      margin-right: 10px;
    }

    .chat-input button {
      background: #4a6cf7;
      color: white;
      border: none;
      padding: 10px 15px;
      border-radius: 50%;
      cursor: pointer;
      transition: 0.3s;
    }

    .chat-input button:hover {
      background: #3d5bdd;
    }

    /* Scrollbar */
    .chat-messages::-webkit-scrollbar {
      width: 6px;
    }

    .chat-messages::-webkit-scrollbar-thumb {
      background: #ccc;
      border-radius: 3px;
    }
  </style>
</head>
<body>
  <div class="chat-container">
    <div class="chat-header">Chat Application UI</div>

    <div class="chat-messages" id="chatMessages">
      <div class="message received">Hey there! 👋</div>
      <div class="message sent">Hello! How are you?</div>
      <div class="message received">I'm good, thanks! Working on a project.</div>
      <div class="message sent">Nice! Tell me more 😄</div>
    </div>

    <div class="chat-input">
      <input type="text" id="messageInput" placeholder="Type a message..." />
      <button id="sendBtn">➤</button>
    </div>
  </div>

  <script>
    const sendBtn = document.getElementById("sendBtn");
    const input = document.getElementById("messageInput");
    const chat = document.getElementById("chatMessages");

    sendBtn.addEventListener("click", sendMessage);
    input.addEventListener("keypress", (e) => {
      if (e.key === "Enter") sendMessage();
    });

    function sendMessage() {
      const text = input.value.trim();
      if (text === "") return;

      const msg = document.createElement("div");
      msg.classList.add("message", "sent");
      msg.textContent = text;
      chat.appendChild(msg);

      input.value = "";
      chat.scrollTop = chat.scrollHeight;

      // Simulated reply
      setTimeout(() => {
        const reply = document.createElement("div");
        reply.classList.add("message", "received");
        reply.textContent = "Got it! 👍";
        chat.appendChild(reply);
        chat.scrollTop = chat.scrollHeight;
      }, 1000);
    }
  </script>
</body>
</html>
