## Schema package summary

The schema package provides data structures and functions for interacting with various components of the LocalAI system. It includes types for representing API responses, models, and other related information.

### Core components

The package consists of several core components, each responsible for handling specific aspects of the LocalAI system:

1. **ElevenLabsTTS**: This component handles text-to-speech (TTS) requests using the ElevenLabs API. It includes the ElevenLabsTTSRequest struct for storing the text to be converted to speech, the model ID, and the language code.

2. **Jina**: This component is responsible for handling requests and responses related to reranking documents. It includes the JINARerankRequest struct for storing the query, documents to be reranked, the desired number of top results, and the backend to use.

3. **LocalAI**: This component handles communication between different components of the LocalAI system. It includes the LocalAIRequest interface for representing any request to LocalAI, and the BasicModelRequest struct as a concrete implementation of this interface.

4. **OpenAI**: This component interacts with the OpenAI API for various tasks such as text generation, translation, and more. It includes the OpenAIResponse struct for storing the response from the API, the ErrorResponse struct for handling errors, and the OpenAIModel struct for representing an OpenAI model.

5. **Prediction**: This component handles prediction requests and responses. It includes the PredictionOptions struct for storing various options for making predictions, such as the language, whether to translate the input, and parameters related to the prediction algorithm.

6. **Request**: This component handles generic requests