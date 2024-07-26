### Smart PDF Chat Using RAG and Amazon Bedrock

This project creates an AI chatbot that allows users to upload text documents which are stored and converted into vector embedding through the Bedrock model and stored in s3, when you ask questions it is converted to embedding and compared to the chunk of text in your s3 data.

### **Technologies Used**
- Amazon Bedrock
- Amazon S3
- Docker
- FAISS
- RAG
- LangChain

## Architecture

1. **Document Chunking**: The uploaded document is broken up into manageable chunks of text.
2. **Vector Embedding**: Each chunk is converted to FAISS vectors using Amazon Titan Embeddings.
3. **Vector Storage**: The vectors are stored in a vector store within an S3 bucket.
4. **Question Submission**: The user submits a question to the chatbot.
5. **Vector Matching**: The question is converted to a vector using Amazon Titan Embeddings and matched to the closest vectors in the vector store.
6. **Response Generation**: The combined content from the matching vectors and the original question is passed to a large language model (LLM) to generate the best answer.

## Key Features

- **Custom Document Interaction**: Upload your own document and interact with it through the chatbot.
- **Context-Aware Responses**: The chatbot provides answers based on the context of the uploaded document.
- **Efficient Vector Storage**: Utilizes FAISS vectors stored in S3 for fast and efficient retrieval.

## Setup

### AWS S3 Bucket

1. **Create an S3 Bucket**:
   - Go to the [AWS Management Console]
   - Navigate to the S3 service.
   - Click on "Create bucket".
   - Name the bucket `bedrock-chatbot-pdf` and leave everything else default.
   - Click "Create bucket".
   - create a folder inside your bucket `bedrock-chatbot-pdf` and name it `my_faiss`

2. **Generate an IAM Access Key**:
   - Go to the IAM service in the AWS Management Console.
   - Select "Users" and then your IAM user.
   - Go to the "Security credentials" tab.
   - Click "Create access key".
   - Save the access key ID and secret access key securely.

### Install AWS CLI

1. **Download the AWS CLI Installer**:
   - Download the installer from the [AWS CLI installation page](https://aws.amazon.com/cli/).

2. **Run the Installer**

3. **Verify the Installation**:
   ```bash
   aws --version


## Configure the CLI:
 ```bash
aws configure
 ```

### **Enter your AWS credentials**

- AWS Access Key ID: YOUR_ACCESS_KEY_ID
- AWS Secret Access Key: YOUR_SECRET_ACCESS_KEY
- Default region name: us-west-2
- Default output format: 


## Usage
### Backend
1. **Clone the repository**
```bash
git clone https://github.com/willie191998/AI-PDF-Chat-Using-RAG-and-Bedrock/tree/main
```

2. **Navigate to the admin directory**
```bash
cd Smart-PDF-Chat-Using-RAG-and-Bedrock/Admin
````

3. **Build the Docker image**
```bash
docker build -t pdf-reader-admin .
````

4. **Run the Docker container on port `8083`**
```bash
docker run -d -e BUCKET_NAME=bedrock-chatbot-pdf -v ~/.aws:/root/.aws -p 8083:8083 -it pdf-reader-admin
````

## Frontend
1. **Navigate to the user directory**
```bash
cd ../user
```

2. **Build the Docker image**
```bash
docker build -t pdf-reader-client.
````

3. **Run the Docker container on port `8084`**
```bash
docker run -d -e BUCKET_NAME=bedrock-chatbot-pdf -v ~/.aws:/root/.aws -p 8084:8084 -it pdf-reader-client
```

## Screenshots
Check out the images folder for the screenshot of the output response.
