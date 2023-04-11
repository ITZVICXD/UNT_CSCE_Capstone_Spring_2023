<template>
  <div class="km-chat-full-screen">
    <img :src="image" />
    <h1>Accessibility Chat Bot</h1>
  </div>
  <div class="box">
    <p>
      Welcome to the site! This website hosts a chat bot created
      by students in the 1 semester capstone of the University of North Texas. 
    </p>
    <p>
      The bot has yet to be named but it is created to assist 
      those working to make their websites accessbile according to the <a href="https://www.w3.org/TR/WCAG21/">WCAG2.1</a>.
    </p>
  </div>
  <div>
    <h1>How to Use the Bot</h1>
    <p class="box">
      To get started using the bot you can click the chat bubble in the bottom right corner.
    </p>
    <h1>Details and Warnings</h1>
    <div class="box">
      <ul>
        <li>
            You can have as many active chats as your want, they are preserved via cookies on your your system.<br>
            This means if you clear your cookies you <strong>clear</strong> your chat history with the bot.
        </li>
        <li>
          The bot is currently only trained on the <strong>WCAG 2.1</strong> success criterion and guidelines.<br>
          It is possible in the future it could be updated for general accessbility assistance.
        </li>
      </ul>
    </div>
  </div>
  <footer>&copy; <small>UNT Capstone One Semester 2</small></footer>
</template>

<script>
/* eslint-disable */
import image from "../Images/UNT.png"
export default {
  name: 'HelloWorld',
  data() {
    return {
      userInput: "",
      responses: [],
      image:image,
    }
  },
  methods: {
    sendInput() {
      this.generateResponse(this.userInput);
      this.userInput = "";
    },
    generateResponse(input) {
      var dto = {
        id: (this.responses.length),
        response: input
      }

      this.responses.push(dto);
    }
  },
  mounted() {
    (function (d, m) {
      var kommunicateSettings = {
        "appId": "26c906b8f28362855a4b941ea7bfc76fa",
        "onInit": function () {
          var iframeStyle = document.createElement('style');
          var classSettings = ".change-kommunicate-iframe-height{height:100%!important;width:100%!important;right:0!important;bottom:0!important;max-height: 100%!important;}";
          iframeStyle.type = 'text/css';
          iframeStyle.innerHTML = classSettings;
          document.getElementsByTagName('head')[0].appendChild(iframeStyle);
          var launcherIconStyle = "@media(min-width: 510px){.mck-sidebox.fade.in,.mck-box .mck-box-sm{width:100%; height:100%;max-height:100%!important;border-radius:0px!important;}.mck-sidebox{right:0!important;bottom:0!important;}}";
          Kommunicate.customizeWidgetCss(launcherIconStyle);

          var iframe = parent.document.getElementById("kommunicate-widget-iframe"),
            launcher = KommunicateGlobal.document.getElementById('mck-sidebox-launcher'),
            preChatPopup = KommunicateGlobal.document.querySelector('#chat-popup-widget-container .chat-popup-widget-text-wrapper'),
            closeButton = KommunicateGlobal.document.getElementById('km-chat-widget-close-button');

          [launcher, preChatPopup].forEach(function (element) {
            element && element.addEventListener('click', function () {
              iframe.classList.add("change-kommunicate-iframe-height");
            });
          });

          closeButton.addEventListener('click', function () {
            iframe.classList.remove("change-kommunicate-iframe-height");
          });
          Kommunicate.launchConversation();
          KommunicateGlobal.document.getElementById('mck-sidebox-launcher').click()
        }
      };
      var s = document.createElement("script"); s.type = "text/javascript"; s.async = true;
      s.src = "https://widget.kommunicate.io/v2/kommunicate.app";
      var h = document.getElementsByTagName("head")[0]; h.appendChild(s);
      window.kommunicate = m; m._globals = kommunicateSettings;
    })(document, window.kommunicate || {});
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .box {
    background-color: green;
    border: 5px white groove;
    padding: 10px;
    margin-top: 10px;
    margin-bottom: 10px;
  }

  .box ul li{
    padding: 5px;
  }
</style>