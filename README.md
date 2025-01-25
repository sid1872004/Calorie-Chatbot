Food Calorie Tracker Chatbot Readme

Overview

Essentially, this is a very basic chatbot that allows users to record the kinds of food they ate and their total calorie consumption for a day. There are two main technologies it relies on:

Nutritionix API: Fetches nutritional information from the user input for food items.

Google Generative AI: Google responded with a message and motivation based on the person's food and calorie intake.

The script provides a conversational method to track calories, prompting the user to enter what they ate and responding with calorie data along with incentivizing discussion.

Dependencies

requests: Used to interface with the Nutritionix API to fetch food nutrient information.

google-generativeai: This is used to generate responses from Google’s Generative AI model so that we can engage the user in a conversation.

Setup

Install required packages:

pip install requests google-generativeai # For asynchronous calls

Set up your API keys:

Nutritionix API: Sign up with Nutritionix API to get your API key and App ID

Google Generative AI API: To get your Google Generative AI API key, go to the Google Cloud Console and create a new project, followed by enabling the Generative AI API.

You would replace "AIzaSyCo_F_JDyyIeB2FXQ1Cl10zQS-C-C2NJu0" with your actual Google Generative AI API key.

Nutritionix App ID: <-- Replace 1b64d367 with your App ID.

Simply change "d8f88e2c3fd0d9ee44a1abc4a972a84b" with the Nutritionix API key.

Script Flow

The chatbot begins by asking the user what they ate today.

Step 1: Fetch Calories : The script fetches the nutritional details of the food items the user is talking about from the Nutritionix API.

Response Generation: The Generative AI model generates a user-friendly, entertaining, and motivational response based on the friendliest format of food items and calories in the user's input.

Log: Food items and calories logged with daily calorie count updated.

Functions

def get_food_calories(user_input):

Sends user input (food description) to Nutritionix API and receives the calories for the food items.

This could also return a list of food items with the number of calories each and the total number of calories for all.

def chatbot_response(user_input, food_items, daily_calories):

Using Google Generative AI, produces an optimistic, encouraging reply

Examines the user's diet and the calories they consume each day and gives feedback.

main():

The main function that run the conversation with user

This will repeat until the user wishes to exit, logging any calorie information and providing feedback on the different types of food inputted.

Example

User Interaction:

So here we go: Food Calorie Tracker Chatbot, GPT-4. What did you eat today? (type 'exit' to quit): apple, banana Chatbot Response: Well done! So you’ve already had a healthful snack today! An apple provides 95 kcal, while a banana has 105 kcal. Keep it up! Food Log: apple: 95 kcal, banana: 105 kcal Daily Calories So Far: 200 kcal

Notes

In similar approach, the Nutritionix API expects the user to give clear food description that could be interpreted.

It offers an easy and fun way to record daily calories and promote healthy eating habits.

Future Enhancements

Handle exceptions where the api cannot process certain food requests.

Monitor food targets and furnish more personalized motivating feedback.

Keep a more detailed food log (e.g. query logs over days/weeks).
