<!-- loio490f55db60364538aa0e7e5b7f3479fa -->

# OpenAI



## Context

You can access LLMs through the `foundation-models` and `orchestration` scenarios.

To use a model through the `orchestration` scenario, using the harmonized API, see [Orchestration](orchestration-8d02235.md).

**For more information about available models, including conversion rates for tokens, rate limits, and deprecation dates, see SAP Note [3437766](https://me.sap.com/notes/3437766).**



## Accessing Models through Orchestration

Orchestration offers a harmonized API that allows you to use different models without changing the client code. You likely have an orchestration deployment running in your default resource group. If you want to access models through orchestration in a different resource group, you'll need to create an orchestration deployment for your chosen resource group. For more information, see .[Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md).

Access to orchestration of generative AI models is provided under the global AI scenario `orchestration`, which is managed by SAP AI Core.

To access generative AI models using orchestration, you'll need to add following information to the `model` module of your orchestration workflow:

-   The name of your chosen model
-   The version name of your chosen version. If no model version is listed, it is not applicable.

For more information about supported models and associated costs, see SAP Note [3505347](https://me.sap.com/notes/3505347)

For more information about orchestration workflows, see [Orchestration Workflow V2](orchestration-workflow-v2-41a0247.md).



## Accessing Models through the `foundation-models` Scenario

You can access foundation models by creating a deployment for the model that you want to use. To do this, you'll need an auth token from your SAP AI Core instance. For more information, see [Get an Auth Token](get-an-auth-token-0808d42.md) and [Create a Deployment](create-a-deployment-b32e7a8.md).

To create your deployment, you'll need the following information:

-   The scenario: `foundation-models`
-   The `executableId`: `azure-openai`

-   The name of your chosen model
-   The version name of your chosen version. If no model version is listed, it is not applicable.

To use a specific version of a model, or to upgrade model versions manually, specify the model version your model deployment. To upgrade automatically, use model version: `latest`. For more information, see [Model Lifecycle](model-lifecycle-313fe25.md). If no model version is listed, it is not applicable.

Open AI models are remote models.

After creating a deployment for your model, you consume the model using prompts. To access the model, you'll need your deployment ID, this can be set as an environment variable.

Ensure that you've set the following headers:


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Authorization

</td>
<td valign="top">

Bearer $AUTH\_TOKEN

</td>
</tr>
<tr>
<td valign="top">

AI-Resource-Group

</td>
<td valign="top">

The resource group used in the activation steps

</td>
</tr>
<tr>
<td valign="top">

$DEPLOYMENT\_URL

</td>
<td valign="top">

The deployment URL for your generative AI model. For more information, see [Create a Deployment](create-a-deployment-b32e7a8.md).

Alternatively, you can replace the `$DEPLOYMENT_URL` placeholder in the curl command with your deployment URL.

</td>
</tr>
</table>



<a name="loio490f55db60364538aa0e7e5b7f3479fa__consumption"/>

## Consumption

The following examples show how you can consume various generative AI models using curl. For more information about prompts, see the tutorial [Prompt LLMs in the Generative AI Hub in SAP AI Core & Launchpad](https://developers.sap.com/tutorials/ai-core-generative-ai.html).

> ### Tip:  
> If you use a Windows device, use Windows PowerShell, and replace `curl` with `curl.exe`.

For more information about supported parameters, see [Supported Parameters](supported-parameters-55d2197.md).



<a name="loio490f55db60364538aa0e7e5b7f3479fa__section_d1y_bxc_z1c"/>

## Completions

For more information from the model provider, see [Microsoft Azure Open AI Chat Completions](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions).



### o4-mini | o3 | gpt-4.1 | gpt-4.1-mini | gpt-4.1-nano | gpt-5 | gpt-5-mini | gpt-5-nano | gpt-5.1 | gpt-5.2 | gpt-5.4 | gpt-5.4-nano | gpt-5.5 | GPT-5.6-Sol | GPT-5.6-Terra | GPT-5.6-Luna

**Text Input**

```
curl --location '$DEPLOYMENT_URL/chat/completions?api-version=2023-05-15' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "messages": [
        {
            "role": "user",
            "content": "sample input prompt"
        }
    ],
    "max_tokens": 100,
    "temperature": 0,
    "frequency_penalty": 0,
    "presence_penalty": 0,
    "stop": "null"
}'
```



### **o1 | o3-mini**

```
curl --location '$DEPLOYMENT_URL/chat/completions?api-version=2024-12-01-preview' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "messages": [
      {
        "role": "user",
        "content": "Hello!"
      }
    ]
  }'
```



### GPT-4o | GPT-4o Mini

Image input

```

curl --location '$DEPLOYMENT_URL/chat/completions?api-version=2023-05-15' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
    "messages": [
        {
            "role": "user",
            "content": [
                {
                    "type": "text",
                    "text": "Describe this picture:"
                },
                {
                    "type": "image_url",
                    "image_url": {
                        "url": "https://path/images/image.png"
                    }
                }
            ]
        }
    ],
    "max_tokens": 10
}'
```



<a name="loio490f55db60364538aa0e7e5b7f3479fa__section_eq3_wbm_pgc"/>

## Embeddings

For more information from the model provider, see [Microsoft Azure Open AI Embeddings](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#embeddings).



### text-embedding-ada-002 | text-embedding-3-small | text-embedding-3-large

```
curl --location '$DEPLOYMENT_URL/embeddings?api-version=2023-05-15' \
--header 'AI-Resource-Group: <Resource Group Id>' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer $AUTH_TOKEN" \
--data '{
	"input": "sample input prompt"
}'
```



## Realtime

For more information from the model provider, see [Microsoft Azure OpenAI Realtime Audio](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/realtime-audio-reference?view=foundry-classic).

`gpt-realtime` can be accessed via WebSockets, via any programming language that supports WebSockets.

The following example uses Python language and the WebSockets library to interact with the `gpt-realtime` model.

Before running your python script, you must complete the following steps:

1.  Create a Python virtual environment.

    ```
    python3 -m venv .venv
    source .venv/bin/activate 
    ```

2.  Install the OpenAI Python client library.

    ```
    pip3 install 'openai[realtime]' 'sounddevice'
    ```

3.  Set the required environment variables.

    ```
    export BEARER_TOKEN='<yourToken>'
    export DEPLOYMENT_URL='<yourDeploymentUrl'
    export RESOURCE_GROUP='<yourResourceGroup>'
    ```

4.  To use the model with **audio** input, run the script with the following parameters:

    ```
    python3 speech-to-speech.py
    ```

    To use the model with **text** input, run the script with the following parameters:

    ```
    python3 speech-to-speech.py --mode text
    ```


You can use the Realtime API via WebSockets to send text or audio input to the model and receive audio output in real time. The Realtime API via WebRTC is not supported.

**Speech to Speech**

The following example uses the OpenAI client library to interact with the gpt-realtime model via WebSockets.

```
 import argparse
import asyncio
import base64
import json
import os
import sounddevice as sd
import websockets
from websockets.exceptions import ConnectionClosedOK, ConnectionClosedError

parser = argparse.ArgumentParser(description='GPT Realtime API Client')
parser.add_argument('--mode', choices=['audio', 'text'], default='audio',
                    help='Input mode: audio (microphone) or text (keyboard). Default: audio')
args = parser.parse_args()
INPUT_MODE = args.mode

SAMPLE_RATE = 24000
CHUNK_SIZE = 8192
AUDIO_FORMAT = 'int16'

BEARER_TOKEN = os.getenv("BEARER_TOKEN")
RESOURCE_GROUP = os.getenv("RESOURCE_GROUP")
DEPLOYMENT_URL = os.getenv("DEPLOYMENT_URL")

WEBSOCKET_URL = f"{DEPLOYMENT_URL}/v1/realtime"

# Print control configuration
PRINT_CONFIG = {
    "usage_metadata": True,
    "session_updates": True,
    "debug": True
}

async def _check_for_exit():
    """Monitor for exit command input"""
    while True:
        try:
            line = await asyncio.to_thread(input, "")
            if line.strip().lower() == "exit":
                return True
        except (EOFError, KeyboardInterrupt):
            return True
        await asyncio.sleep(0.1)


async def audio_player(queue: asyncio.Queue):
    with sd.RawOutputStream(samplerate=SAMPLE_RATE, channels=1, dtype=AUDIO_FORMAT) as audio_out:
        while True:
            pcm = await queue.get()
            if pcm is None:
                break
            audio_out.write(pcm)
            queue.task_done()


async def receive_messages(ws, audio_queue, response_complete_event=None):
    """Receive and process WebSocket messages"""
    try:
        async for message in ws:
            data = json.loads(message)
            msg_type = data.get("type")

            if msg_type == "session.created":
                session_id = data.get("session", {}).get("id", "unknown")
                if PRINT_CONFIG["session_updates"]:
                    print(f"Connected. Session ID: {session_id}")

            elif msg_type == "session.updated":
                if PRINT_CONFIG["session_updates"]:
                    print(f"Session updated: {data.get('session', {})}")

            # User transcript (transcribes what you said but for audio mode only)
            elif msg_type == "conversation.item.input_audio_transcription.completed":
                transcript = data.get("transcript", "")
                if transcript and INPUT_MODE == "audio":
                    print(f"You said: {transcript}")

            # Model transcript (streamed in real time)
            elif msg_type == "response.output_audio_transcript.delta":
                delta = data.get("delta", "")
                if delta:
                    print(delta, end="", flush=True)

            elif msg_type == "response.output_audio_transcript.done":
                print()  # finish transcript line

            elif msg_type == "response.done":
                response_data = data.get("response", {})
                usage = response_data.get("usage")
                if usage and PRINT_CONFIG["usage_metadata"]:
                    print(f"Usage metadata: {usage}")

                # Signal that response is complete (for text mode)
                if response_complete_event:
                    response_complete_event.set()

            # Model's audio playback
            elif msg_type == "response.output_audio.delta":
                audio_b64 = data.get("delta")
                if audio_b64:
                    pcm = base64.b64decode(audio_b64)
                    await audio_queue.put(pcm)

            elif msg_type == "error":
                error_data = data.get("error", {})
                error_type = error_data.get('type', 'unknown')
                error_msg = error_data.get('message', 'No message')

                print(f"\n[ERROR] {error_type}: {error_msg}")

                if PRINT_CONFIG["debug"]:
                    print(f"\n[DEBUG] Full error data: {json.dumps(data, indent=2)}")

    except ConnectionClosedOK:
        pass
    except ConnectionClosedError as e:
        if e.code is None or e.code == 1006:
            print("\n" + "="*80)
            print("ERROR: Connection closed unexpectedly")
            print("="*80)
        else:
            print(f"\nConnection closed: Code {e.code} - {e.reason}")
    except Exception as e:
        print(f"Receive error: {e}")


async def text_input_sender(ws, response_complete_event):
    """Send text messages from keyboard input"""
    print("\nType your message and press Enter. Type 'exit' to quit.\n")

    while True:
        try:
            user_text = await asyncio.to_thread(input, "You: ")

            if user_text.strip().lower() == "exit":
                print("Exit requested, ending session...")
                break

            if not user_text.strip():
                continue

            # Clear the response complete flag
            response_complete_event.clear()
            print("Assistant: ", end="", flush=True)

            text_message = {
                "type": "conversation.item.create",
                "item": {
                    "type": "message",
                    "role": "user",
                    "content": [
                        {
                            "type": "input_text",
                            "text": user_text
                        }
                    ]
                }
            }
            await ws.send(json.dumps(text_message))

            # Request response
            response_request = {
                "type": "response.create"
            }
            await ws.send(json.dumps(response_request))

            # Wait for response to complete before prompting again
            await response_complete_event.wait()

        except (EOFError, KeyboardInterrupt):
            print("\nKeyboard interrupt received, ending session...")
            break
        except Exception as e:
            print(f"\nInput error: {e}")
            break


async def main():
    print("Starting GPT Realtime API session...")

    audio_queue = asyncio.Queue()
    player_task = asyncio.create_task(audio_player(audio_queue))

    headers = {
        "AI-Resource-Group": RESOURCE_GROUP,
        "Authorization": f"Bearer {BEARER_TOKEN}",
    }

    session_config = {
        "type": "realtime",
        "output_modalities": ["audio"],
        "instructions": "Only respond in English. You are a helpful assistant.",
        "audio": {
            "input": {
                "format": {
                    "type": "audio/pcm",
                    "rate": 24000
                }
            },
            "output": {
                "format": {
                    "type": "audio/pcm",
                    "rate": 24000
                },
                "voice": "alloy"
            }
        }
    }

    # Add transcription for audio mode
    if INPUT_MODE == "audio":
        session_config["audio"]["input"]["transcription"] = {
            "model": "whisper-1"
        }
        session_config["audio"]["input"]["turn_detection"] = {
            "type": "server_vad",
            "threshold": 0.5,
            "prefix_padding_ms": 300,
            "silence_duration_ms": 200,
            "create_response": True
        }

    setup_msg = {
        "type": "session.update",
        "session": session_config
    }

    try:
        async with websockets.connect(WEBSOCKET_URL, additional_headers=headers) as ws:
            print("WebSocket connection successful")
            await ws.send(json.dumps(setup_msg))

            receiver_task = asyncio.create_task(receive_messages(ws, audio_queue))

            # Wait a bit for session to be established
            await asyncio.sleep(1)

            if INPUT_MODE == "audio":
                exit_task = asyncio.create_task(_check_for_exit())

                with sd.RawInputStream(
                    samplerate=SAMPLE_RATE,
                    blocksize=CHUNK_SIZE,
                    channels=1,
                    dtype=AUDIO_FORMAT
                ) as audio_in:
                    try:
                        print("Real time audio is currently being captured. Type 'exit' to quit.")

                        while not exit_task.done():
                            # Check if receiver task is still running
                            if receiver_task.done():
                                break

                            audio_chunk, overflowed = audio_in.read(CHUNK_SIZE)
                            chunk_b64 = base64.b64encode(audio_chunk).decode('ascii')
                            frame = {"type": "input_audio_buffer.append", "audio": chunk_b64}

                            try:
                                await ws.send(json.dumps(frame))
                            except Exception as e:
                                print(f"Send error: {e!r}")
                                break

                            await asyncio.sleep(0.01)

                        if exit_task.done():
                            print("Exit requested, ending session...")

                    except KeyboardInterrupt:
                        print("\nKeyboard interrupt received, ending session...")

                    finally:
                        # Clean up tasks
                        if not exit_task.done():
                            exit_task.cancel()
                        if not receiver_task.done():
                            receiver_task.cancel()

                        # Stop audio player
                        await audio_queue.put(None)
                        await player_task

                        print("Session closed.")

            else:
                print(f"Text mode active. Audio responses will play through speakers.")

                try:
                    # Create event to signal when response is complete
                    response_complete_event = asyncio.Event()
                    response_complete_event.set()  # Initially set so first input doesn't wait

                    # Update receiver task to pass the event
                    receiver_task.cancel()
                    receiver_task = asyncio.create_task(receive_messages(ws, audio_queue, response_complete_event))

                    text_sender_task = asyncio.create_task(text_input_sender(ws, response_complete_event))

                    # Wait for text sender or receiver to complete
                    done, pending = await asyncio.wait(
                        [text_sender_task, receiver_task],
                        return_when=asyncio.FIRST_COMPLETED
                    )

                    for task in pending:
                        task.cancel()
                        try:
                            await task
                        except asyncio.CancelledError:
                            pass

                except KeyboardInterrupt:
                    print("\nKeyboard interrupt received, ending session...")

                finally:
                    # Stop audio player
                    await audio_queue.put(None)
                    await player_task
                    print("Session closed.")

    except websockets.exceptions.InvalidStatus as e:
        # Handle HTTP status code errors during connection
        status = e.response.status_code
        print("\n" + "="*80)
        print(f"ERROR: Connection Failed (HTTP {status})")
        print("="*80)

        print(f"\n{e}")

        print(f"\nCurrent configuration:")
        print(f"  URL: {WEBSOCKET_URL}")
        print(f"  Resource Group: {RESOURCE_GROUP}")

    except websockets.exceptions.WebSocketException as e:
        print(f"\n" + "="*80)
        print(f"ERROR: WebSocket Error")
        print("="*80)
        print(f"\n{e}")
        print("\nPossible causes:")
        print("  - Network connectivity issues")
        print("  - Endpoint is unreachable")
        print("  - Firewall or proxy blocking connection")

    except Exception as e:
        print(f"\n" + "="*80)
        print("ERROR: Unexpected Error")
        print("="*80)
        print(f"\n{type(e).__name__}: {e}")

        if PRINT_CONFIG["debug"]:
            import traceback
            traceback.print_exc()
    finally:
        # Ensure audio player is stopped
        await audio_queue.put(None)
        await player_task


if __name__ == "__main__":
    asyncio.run(main())
```

When you want to end your session, you can close the connection by:

-   Running `exit`
-   Pressing [CTRL\] + [C\] 



<a name="loio490f55db60364538aa0e7e5b7f3479fa__section_urc_c1p_1bc"/>

## Removing a Model

If you want to remove a model, delete its deployment. For more information, see [Delete a Single Deployment](https://help.sap.com/viewer/db13d59d17204c01b3b79c24fb82a19a/CLOUD/en-US/1b0b3612e5f948a6af5e593a61f711ce.html "") :arrow_upper_right:

-   **[Responses API](responses-api-a40ffca.md)**  


**Related Information**  


[Access the Chat Completion using the SAP AI SDK for Java](https://sap.github.io/ai-sdk/docs/java/foundation-models/openai/chat-completion)

[Access the Chat Completion using the SAP AI SDK for JavaScript](https://sap.github.io/ai-sdk/docs/js/foundation-models/openai/chat-completion)

[Access the Embedding using the SAP AI SDK for Java](https://sap.github.io/ai-sdk/docs/java/foundation-models/openai/embedding)

[Access the Embedding using the SAP AI SDK for JavaScript](https://sap.github.io/ai-sdk/docs/js/foundation-models/openai/embedding)

