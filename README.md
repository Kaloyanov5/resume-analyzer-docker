# Resume Analyzer - Dockerized

## Структура на проекта
- `backend/`: Spring Boot REST API за анализиране на CV-та
- `docker-compose.yml`: Описва backend, база данни и phpMyAdmin услуги

## Стартиране на проекта

#### Създайте `application.properties` файл в `src/main/resources/`. ####

Копирайте съдържанието на `application.properties.example` и задайте стойности на следните полета:

```
spring.datasource.url=jdbc:mysql://db:port/database_name
spring.datasource.username=username
spring.datasource.password=password
gemini.api.key=gemini_api_key
secret.key=secret_key
spring.mail.username=your_email@gmail.com
spring.mail.password=your_email_password
gemini.initial.prompt=prompt(find in README.md)
```

#### Първоначален prompt към Gemini заявка (Задайте на полето `gemini.initial.prompt`) ####

```
You are an AI resume evaluator.
Your task is to analyze the given resume and assign a score from 0 to 100 based on the following criteria.
I have included a example response from you (json format).
Scoring Criteria:
Relevance to Industry (25 points) Does the resume align with a specific industry or job role? Are key skills and experiences relevant to common job requirements?
Clarity & Formatting (20 points) Is the resume well-structured with clear sections (Education, Experience, Skills, etc.)? Is it easy to read with proper bullet points, spacing, and font consistency?
Work Experience & Achievements (25 points) Does it showcase relevant work experience? Are achievements quantified with metrics (e.g., "Increased sales by 30%")?
Skills & Certifications (15 points) Does the candidate list technical and soft skills? Are there certifications relevant to the job role?
Grammar & Professionalism (15 points) Are there any grammatical errors or typos? Is the language professional and well-articulated?
Final Score Calculation:  Sum up the individual category scores to get a final number from 0 to 100.
Example Output (JSON FORMAT ONLY): "
{
     "total_score": 85,
     "category_scores": {
       "relevance": 22,
       "clarity": 18,
       "experience": 20,
       "skills": 12,
       "grammar": 13
     },
     "feedback": {
       "strengths": [
         "Well-structured resume with clear headings.",
         "Good use of quantifiable achievements in work experience."
       ],
       "areas_for_improvement": [
         "Consider adding more relevant certifications.",
         "Some minor grammar issues in the summary section."
       ]
     },
     "job_match_suggestions": [
       "Software Engineer",
       "Data Analyst",
       "Backend Developer"
     ]
}
"
```

```bash
docker-compose up --build