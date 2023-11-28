# Consultant-AI-Zephyr

This repository contains code for a simple chat web app that integrates with Azure OpenAI. Please note that some portions of the app use preview APIs.

## Changing Environment Variables

To modify environment variables, you need access to the web app in Azure. The web app, named "Consultant-AI-Zephyr," is located in the "Horst" resource group. When on the web app's start page in the Azure interface, select the "Configurations" option in the left menu. The app settings are located there. A variable has been created for all adjustable OpenAI parameters. For instance, you can change the system message under `AZURE_OPENAI_SYSTEM_MESSAGE`.

After making changes and pressing "save," the WebApp takes a few minutes to apply the changes. Here are some variables that can be changed:

| App Setting | (Default) Value | Note |
| --- | --- | --- |
|AZURE_OPENAI_RESOURCE| | The name of your Azure OpenAI resource |
|AZURE_OPENAI_MODEL| | The name of your model deployment |
|AZURE_OPENAI_MODEL_NAME| gpt-35-turbo-16k | The name of the model |
|AZURE_OPENAI_KEY| | One of the API keys of your Azure OpenAI resource |
|AZURE_OPENAI_TEMPERATURE| 0 | Sampling temperature between 0 and 2. Higher values like 0.8 make the output more random, while lower values like 0.2 make it more focused. A value of 0 is recommended when using your data.|
|AZURE_OPENAI_TOP_P| 1.0 | An alternative to sampling with temperature, called nucleus sampling. Set to 1.0 when using your data.|
|AZURE_OPENAI_MAX_TOKENS| 1000 | Maximum number of tokens allowed for the generated answer. |
|AZURE_OPENAI_STOP_SEQUENCE| | Up to 4 sequences where the API will stop generating further tokens. Represent these as a string joined with "|", e.g., `"stop1|stop2|stop3"` |
|AZURE_OPENAI_SYSTEM_MESSAGE| You are an AI assistant that helps people find information. | A brief description of the role and tone the model should use |
|AZURE_OPENAI_PREVIEW_API_VERSION| 2023-06-01-preview | API version when using Azure OpenAI on your data |
|AZURE_OPENAI_STREAM| True | Whether or not to use streaming for the response |

## Running Locally

To run the app locally and make changes to the code, follow these steps:

1. Install Python (https://www.python.org/downloads/).
2. Clone the GitHub repo.
3. Create an .env file in the main folder with the following content:

    ```plaintext
    AZURE_OPENAI_RESOURCE=
    AZURE_OPENAI_MODEL=
    AZURE_OPENAI_KEY=
    AZURE_OPENAI_MODEL_NAME=
    AZURE_OPENAI_TEMPERATURE=
    AZURE_OPENAI_TOP_P=
    AZURE_OPENAI_MAX_TOKENS=
    AZURE_OPENAI_STOP_SEQUENCE=
    AZURE_OPENAI_SYSTEM_MESSAGE=
    AZURE_OPENAI_PREVIEW_API_VERSION=2023-06-01-preview
    AZURE_OPENAI_STREAM=True
    ```

   Use values from the app settings of the web app.
4. Run the following command to install the required packages:
```bash 
pip install -r requirements.txt 
```

5. Execute the following to start the app:
```bash
start.cmd
```
You can now see your app running on http://127.0.0.1:5000

## Making Changes Available
To make changes available via the web app, commit them to the main branch. After that, 
execute the following command in the terminal:
```bash 
git push azure main:master
``` 
This command commits the changes to the Azure repository, and the web app is redeployed. 
Once the process is complete, the changes are available under the link of the web app.