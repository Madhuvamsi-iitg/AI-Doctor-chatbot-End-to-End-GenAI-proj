**Project: AI Doctor Chatbot (RAG-based Medical Assistant)**  
**GitHub Repository Summary**  

This project is a **Retrieval-Augmented Generation (RAG)-based AI Doctor Chatbot** designed to provide accurate and context-aware medical responses using advanced language models and cloud technologies. The system leverages structured medical knowledge from a dedicated textbook to deliver reliable answers while prioritizing scalability, efficiency, and user accessibility.  

---

### **Key Components & Workflow**  
1. **Data Ingestion & Processing**  
   - Extracted medical textbook content and split it into semantically meaningful chunks using **LangChain's text splitters**.  
   - Generated embeddings for each chunk using **Hugging Face's Sentence Transformers** (`all-MiniLM-L6-v2`) to capture contextual relationships.  

2. **Vector Database (Pinecone)**  
   - Stored embeddings in **Pinecone**, a cloud-native vector database, for efficient similarity searches and low-latency retrieval.  

3. **LLM Integration (Groq)**  
   - Utilized **Groq's ultra-fast LLM API** with the **Gemma2-9b-it model** to generate human-readable, medically relevant responses.  
   - Combined retrieved context from Pinecone with Groq's generative capabilities to ensure answers are grounded in the textbook data (RAG architecture).  

4. **Frontend & Backend**  
   - Built a user-friendly web interface with **Flask** for real-time interactions.  
   - Integrated LangChain's pipeline to orchestrate retrieval, context augmentation, and response generation.  

5. **Deployment & DevOps**  
   - Containerized the application using **Docker** for environment consistency.  
   - Automated CI/CD pipelines via **GitHub Actions** to enable seamless testing, building, and deployment to **AWS EC2**.  
   - Configured AWS EC2 for scalable cloud hosting, ensuring high availability.  

---

### **Key Features**  
✅ **RAG Architecture**: Combines retrieval from medical textbooks with generative AI for accuracy and relevance.  
✅ **Cloud-Native Design**: Uses Pinecone (vector DB) and AWS (hosting) for scalability and low latency.  
✅ **Open-Source LLM**: Leverages Groq's high-speed inference for real-time responses.  
✅ **CI/CD Pipeline**: Automated deployment ensures rapid iteration and reliability.  
✅ **Privacy-First**: No sensitive user data is stored; all interactions are ephemeral.  

---

### **Technologies Used**  
- **Frameworks**: LangChain, Flask  
- **LLM & Embeddings**: Groq (Gemma2-9b-it), Hugging Face (`sentence-transformers/all-MiniLM-L6-v2`)  
- **Database**: Pinecone (vector DB)  
- **Cloud & DevOps**: AWS EC2, Docker, GitHub Actions (CI/CD)  
- **Tools**: GitHub, Python  

# AWS-CICD-Deployment-with-Github-Actions

## 1. Login to AWS console.

## 2. Create IAM user for deployment

	#with specific access

	1. EC2 access : It is virtual machine

	2. ECR: Elastic Container registry to save your docker image in aws


	#Description: About the deployment

	1. Build docker image of the source code

	2. Push your docker image to ECR

	3. Launch Your EC2 

	4. Pull Your image from ECR in EC2

	5. Lauch your docker image in EC2

	#Policy:

	1. AmazonEC2ContainerRegistryFullAccess

	2. AmazonEC2FullAccess

	
## 3. Create ECR repo to store/save docker image
    - Save the URI: 025066271145.dkr.ecr.us-east-1.amazonaws.com/medicalchatbot

	
## 4. Create EC2 machine (Ubuntu) 

## 5. Open EC2 and Install docker in EC2 Machine:
	
	
	#optinal

	sudo apt-get update -y

	sudo apt-get upgrade
	
	#required

	curl -fsSL https://get.docker.com -o get-docker.sh

	sudo sh get-docker.sh

	sudo usermod -aG docker ubuntu

	newgrp docker
	
# 6. Configure EC2 as self-hosted runner:
    setting>actions>runner>new self hosted runner> choose os> then run command one by one


# 7. Setup github secrets:

   - AWS_ACCESS_KEY_ID
   - AWS_SECRET_ACCESS_KEY
   - AWS_DEFAULT_REGION
   - ECR_REPO
   - PINECONE_API_KEY
   - OPENAI_API_KEY
