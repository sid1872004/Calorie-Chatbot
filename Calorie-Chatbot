import requests
import google.generativeai as genai

genai.configure(api_key="AIzaSyCo_F_JDyyIeB2FXQ1Cl10zQS-C-C2NJu0")

APP_ID = "1b64d367"
APP_KEY = "d8f88e2c3fd0d9ee44a1abc4a972a84b"

def get_food_calories(user_input):
    response = requests.post(
        "https://trackapi.nutritionix.com/v2/natural/nutrients",
        json={"query": user_input},
        headers={
            "x-app-id": APP_ID,
            "x-app-key": APP_KEY,
            "Content-Type": "application/json",
        },
    )
    if response.status_code == 200:
        data = response.json()
        food_items = [f"{food['food_name']}: {food['nf_calories']} kcal" for food in data["foods"]]
        total_calories = sum(food["nf_calories"] for food in data["foods"])
        return food_items, total_calories
    return None, 0

def chatbot_response(user_input, food_items, daily_calories):
    model = genai.GenerativeModel("gemini-1.5-flash")
    food_list = "\n".join(food_items)
    prompt = (
        f"You are a friendly calorie tracker chatbot. The user says: '{user_input}'. "
        f"Here are the food items and calories: \n{food_list}\n"
        f"Their total daily calorie intake so far is {daily_calories} kcal. "
        f"Respond in a motivational and engaging way."
    )
    return model.generate_content(prompt).text

def main():
    print("Welcome to the Food Calorie Tracker Chatbot!")
    user_calories = 0

    while True:
        user_input = input("\nWhat did you eat today? (type 'exit' to quit): ")
        if user_input.lower() == "exit":
            print("Goodbye! Stay healthy!")
            break

        food_items, calories = get_food_calories(user_input)
        if food_items:
            user_calories += calories
            response = chatbot_response(user_input, food_items, user_calories)
            print(f"\nChatbot Response:\n{response}")
            print(f"\nFood Log: {', '.join(food_items)}")
            print(f"Daily Calories So Far: {user_calories} kcal")
        else:
            print("Sorry, I couldn't process your input. Please try again.")

if __name__ == "__main__":
    main()
