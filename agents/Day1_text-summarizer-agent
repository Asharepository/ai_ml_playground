import os
from openai import OpenAI
from dotenv import load_dotenv

load_dotenv()

# Load your API key from environment variable
client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))

def summarize_text(text: str, summary_length: str = "short") -> str:
    """
    Summarizes the given text using GPT.
    
    Args:
        text (str): The text to summarize.
        summary_length (str): "short" or "detailed".
    
    Returns:
        str: The summarized text.
    """
    prompt = f"Summarize the following text in a {summary_length} paragraph:\n\n{text}"

    response = client.chat.completions.create(
        model="gpt-4o-mini",  # or "gpt-4" if you have access
        messages=[{"role": "user", "content": prompt}],
        temperature=0.5
    )

    return response.choices[0].message.content.strip()

if __name__ == "__main__":
    input_text = input("Enter text to summarize:\n")
    print("\n--- Summary ---")
    print(summarize_text(input_text))
