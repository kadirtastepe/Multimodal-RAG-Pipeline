# Multimodal-RAG-Pipeline
Anonymized Multimodal Retrieval Augmented Generation Pipeline for Internal Document Processing offers an AI-powered chatbot based on the current model GPT-5, designed to assist with any type of documentation. It provides quick and accurate responses to queries related to the provided documentation.

## Architecture:
![rag architecture](docs/RAG.png "RAG Architecture")

Developers
------------

If you have question or problems of any kind, do not hesitate to contact to the developer directly:

- Kadir Tastepe <ktastepe@cern.ch>

## Prerequisites
- Python 3.11
- Docker installation
- PostgreSQL database setup
- SAP BTP Global Account
- AWS S3 bucket for blob storage
- SAP AI Core service
- Gen AI Hub Deployments
- Required Python libraries (listed in `requirements.txt`)

## Getting Started

Get the repository
```
git clone https://github.com/kadirtastepe/Multimodal-RAG-Pipeline.git
```

Before start working on this project, ensure that all the required Python libraries and environment are properly set up. Each time you are working on this project, you must set up the software environment first.

1. Go to directory `cd Multimodal-RAG-Pipeline`.
1. First time only authentication `bash setup`.
1. Setup environment `source admin_setup`.
1. Make desired configuration as listed below.
1. To deploy RAG Pipeline on Cloud Foundry, for brevity execute `go`.

## Admin Interface:
![user interface](docs/user-interface.png "User Interface")

| Command | Meaning |
|---------|----------|
| `make all IMAGES=<app>` | Build selected image. [anonymizer/vectorizer/api] |
| `make clean` | Delete all docker images. |
| `make fetch` | Fetch the data to anonymizer. |
| `make anonymize_md` | Anonymize all fetched md files. |
| `make anonymize_json` | Anonymize fetched json data. |
| `make preprocess_md` | Preprocess all fetched md files. |
| `make preprocess_json` | Preprocess fetched json data. |
| `make tar` | Create a tar file including preprocessed data. |
| `make vectorize` | Vectorize the preprocessed data and sends to postgres. |
| `make update` | After fetching the json data process outdated entries. |
| `make chain` | Executes fetch and anonymize together. |
| `make help` | Show all configuration options. |

## Useful Features:
| Command | Options | Meaning |
|---------|---------|----------|
| `set_mode` | `anonymizer/vectorizer/api` | Change build option. |
| `vectorize` | `md/json` `numb_batches` | Change file type and the number of batches for vectorization. |
| `set_config` | `check etc/config.json` | Update the config file in cf apps without redeploying. |
| `set_slack` | `on/off` | Toogle slack communication on/off without redeploying. |
| `s3 ls` | | Check the files in the blobstore. |
| `s3 delete` | `file_name` | Delete the files in the blobstore. |
| `get_logs` | | Retrieve real-time logs from targeted apps. |




