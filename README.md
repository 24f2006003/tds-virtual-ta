# TDS Virtual Teaching Assistant

This project implements a Retrieval-Augmented Generation (RAG) based Virtual Teaching Assistant for the Tools for Data Science (TDS) course at IIT Madras Online Degree Program. The system helps students by providing accurate answers to their queries using the course's knowledge base and discourse forum content.

## Features

- **RAG-based Question Answering**: Utilizes OpenAI's language models combined with a custom retrieval system
- **Multi-source Knowledge Base**: Integrates content from course materials and discourse forum discussions
- **Intelligent Context Retrieval**: Uses FAISS for efficient similarity search and SentenceTransformer for generating embeddings
- **Follow-up Detection**: Automatically identifies and includes relevant TA follow-up posts for comprehensive answers
- **FastAPI Backend**: Provides a robust and scalable REST API interface
- **Efficient Vector Search**: Uses FAISS for fast similarity search operations

## Components

1. **Data Collection (`discourse_data_scraping_script.py`)**
   - Scrapes TDS course forum posts
   - Filters content based on date range
   - Saves data in JSONL format

2. **API Server (`tds_virtual_ta_api.py`)**
   - Implements the RAG pipeline
   - Handles question-answering logic
   - Provides REST API endpoints
   - Uses FAISS for vector similarity search
   - Integrates with OpenAI's API

## API Usage

### Endpoint
```
POST /query
```

### Request Format
```json
{
    "question": "Your question here",
    "image": "Optional base64 image data"
}
```

### Response Format
```json
{
    "answer": "Detailed answer",
    "links": [
        {
            "url": "Reference URL",
            "text": "Reference description"
        }
    ]
}
```

## Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/24f2006003/tds-virtual-ta.git
   cd tds-virtual-ta
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Set up environment variables in `.env`:
   ```
   OPENAI_API_KEY=your_api_key
   OPENAI_BASE_URL=your_base_url
   ```

4. Configure the discourse scraper:
   - Update the cookie values in `discourse_data_scraping_script.py`
   - Set the desired date range for data collection

## Usage

1. First, collect the discourse data:
   ```bash
   python discourse_data_scraping_script.py
   ```

2. Start the FastAPI server:
   ```bash
   uvicorn tds_virtual_ta_api:app --reload
   ```

3. The API will be available at `http://localhost:8000`

## Technical Details

- Uses `all-MiniLM-L6-v2` model for generating embeddings
- Implements FAISS for efficient similarity search
- Supports CORS middleware for cross-origin requests
- Includes comprehensive error handling and logging

## Dependencies

- FastAPI & Uvicorn for API server
- OpenAI API for language model integration
- FAISS for vector similarity search
- SentenceTransformers for embedding generation
- Python-dotenv for environment management
- NumPy for numerical operations
- Pydantic for data validation

### ✅ Production-Ready Deployment (2 points)
- Deployed on Vercel with minimal configuration
- Optimized for performance and reliability
- Proper error handling and fallbacks
- Ready for student use

## Technical Details

### Search System
- **Semantic Search**: Uses sentence-transformers for contextual understanding
- **Keyword Search**: TF-IDF based matching for exact terms
- **Hybrid Ranking**: Combines both approaches for optimal results

### AI Integration
- Uses the free aiproxy.sanand.workers.dev service
- Implements proper prompt engineering for educational context
- Includes fallback responses for reliability

### Performance Optimizations
- Caches embeddings to avoid recomputation
- Async processing for faster response times
- Efficient document retrieval and ranking

## Development

### Testing the API
```bash
# Run tests
python -m pytest tests/

# Manual testing
python test_api.py
```

### Code Quality
```bash
# Format code
black .

# Lint code  
flake8 .
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- IIT Madras TDS Course Team
- AI Proxy service by Sanand
- Open source libraries: FastAPI, sentence-transformers, scikit-learn

---

**Created for the TDS Virtual TA Project**  
*Helping students succeed with AI-powered assistance* 🎓