# GPT Integration Connector Package

This connector assists in integrating with GPT and facilitates operations related to getting responses from GPT models. The connector's code is written in PowerShell.

## Connectors:

### 1. GPTPrompt
Obtains a response from GPT based on the provided prompt.

**Inputs:**
- `strApiKey (String)`: API key for the GPT service.
- `strPrompt (String)`: The user's input message or prompt for the GPT model.
- `arrConversation (Array of Strings)`: Conversation messages including both past user and system messages.

**Outputs:**
- `boolOutHasError (Boolean)`: Indicates if an error has occurred.
- `strOutErrorMessage (String)`: Contains an error message if any error has occurred.
- `strOutResponse (String)`: Contains the GPT model's response.
- `arrOutConversation (Array of Strings)`: Updated conversation including the GPT model's response.

**Developer's Note:** The code uses PowerShell to send requests to the OpenAI GPT endpoint. It facilitates a conversation-like interaction where each message in the conversation can be either from the system or the user. The API response is added to the conversation, and the entire updated conversation is returned as an output. Ensure you have the necessary permissions and environment setup to execute PowerShell scripts and internet requests.

