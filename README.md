# Golinai — Empowering AI with Decentralized Technology

## Inspiration

The idea behind "Golinai" emerged from the need to integrate large language models (LLMs) with decentralized applications. By leveraging Linera's blockchain ecosystem, we aim to create a seamless, decentralized platform for running LLMs, ensuring data privacy, security, and scalability.

## What it does

"Golinai" is an application that runs a large language model as a service within the Linera blockchain. Key features include:

- **Prompt Submission:** Users can submit prompts and receive responses generated by the LLM.
- **Decentralized Storage:** Future versions will store model data on-chain or in decentralized storage.
- **Local Model Serving:** The application currently uses a local HTTP service to provide model data to the wallet implementation.

## How we built it

"Golinai" is built using the Linera framework and Rust programming language. The core components include:

1. **Model Integration:** Utilizing the TinyLlama model by A. Karpathy, served locally.
2. **GraphQL Interface:** Exposing a `prompt` field to handle user inputs and generate responses.
3. **Backend Services:** Deploying the application bytecode to the Linera chain and setting up a local Python server for model serving.

## Challenges we ran into

Developing "Golinai" involved several challenges:

- **Model Serving:** Implementing a local HTTP service to serve model data.
- **On-Chain Storage:** Planning for future integration of on-chain or decentralized storage solutions.
- **Performance:** Ensuring acceptable performance for larger LLMs, potentially requiring hardware acceleration.

## Accomplishments that we're proud of

We successfully:

- **Integrated LLM with Linera:** Created a seamless integration of LLM within the Linera blockchain ecosystem.
- **Developed a User-Friendly Interface:** Provided an intuitive web frontend for interacting with the AI model.
- **Ensured Security and Privacy:** Maintained data privacy and security through decentralized technology.

## What we learned

Throughout the development of "Golinai," we gained insights into:

- **LLM Integration:** Understanding the complexities of integrating LLMs with decentralized applications.
- **GraphQL Implementation:** Utilizing GraphQL for efficient data handling and user interactions.
- **Future Scaling:** Identifying the need for hardware acceleration and improved storage solutions for larger models.

## What's next for Golinai

Future plans for "Golinai" include:

- **Decentralized Storage:** Implementing on-chain or external decentralized storage for model data.
- **Performance Optimization:** Enhancing performance with hardware acceleration for larger models.
- **Expanded Features:** Introducing more advanced AI features and improving the user experience.
- **Community Engagement:** Building a community around "Golinai" to foster collaboration and innovation.

## Getting Started

### Prerequisites

Ensure you have the model and tokenizer locally:

```bash
wget -O model.bin -c https://huggingface.co/karpathy/tinyllamas/resolve/main/stories42M.bin
wget -c https://huggingface.co/spaces/lmz/candle-llama2/resolve/main/tokenizer.json
```

Run the Python server to serve models locally:

```bash
python3 -m http.server 10001
```

### Setup

Set up your local network and deploy the application:

```bash
export PATH="$PWD/target/debug:$PATH"
source /dev/stdin <<<"$(linera net helper 2>/dev/null)"
linera_spawn_and_read_wallet_variables linera net up --testing-prng-seed 37

cd ..
APP_ID=$(linera project publish-and-create llm)
```

### Using the LLM Application

Start the node service and web frontend:

```bash
PORT=8080
linera service --port $PORT &

cd llm/web-frontend
npm install --no-save
BROWSER=none npm start
```

Access the application via the provided URL:

```bash
echo "http://localhost:3000/$CHAIN?app=$APP_ID&port=$PORT"
```

## Built With

- **Linera**
- **Rust**
- **TinyLlama**

Explore the integration of AI and blockchain with "Golinai" and experience the future of decentralized AI applications!