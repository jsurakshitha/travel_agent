# travel_agent
# AI-Powered Travel Planner Agent ✈️

## Problem Statement

Travel planning is often a **complex, time-consuming, and inefficient** process. Users spend hours navigating multiple websites to find destinations, compare prices for flights and hotels, and piece together itineraries. This fragmented approach leads to frustration and missed opportunities for a truly personalized and seamless travel experience.

## Proposed Solution

Our solution is an **AI-powered Travel Planner Agent** designed to transform complex travel planning into a seamless and enjoyable process. This intelligent assistant leverages generative AI and real-time data to create **personalized and optimized travel plans** tailored to individual user preferences, budgets, and constraints.

## Key Features ✨

* **Personalized Itinerary Generation**: Crafts custom multi-day travel itineraries based on user input, including destinations, dates, budget, interests (e.g., family-friendly, adventurous), and specific preferences.
* **Real-time Data Integration**: Fetches live data from various APIs for current weather conditions, flight availability, hotel prices, and local events to provide up-to-date and accurate recommendations.
* **Intelligent Recommendations**: Suggests optimal destinations, accommodation options, transportation routes, and local guides, ensuring a smooth and relevant travel experience.
* **Seamless Booking Management**: (Conceptual) Provides a framework to integrate with booking platforms, managing reservations and alerting users to any changes or delays.
* **On-the-Go Optimization**: (Conceptual) Adapts itineraries dynamically to account for real-time changes in conditions (e.g., flight delays, sudden weather shifts) or user feedback during the trip.

## Technology Stack 🛠️

* **Core AI**:
    * **IBM Granite Model**: Utilized as the primary large language model for understanding natural language queries, generating coherent itineraries, and providing contextual information.
    * **IBM Cloud Lite Services**: The foundational cloud platform for hosting and managing the AI agent. This includes:
        * **IBM Cloud Watsonx AI Studio**: For developing and testing the AI models.
        * **IBM Cloud Watsonx AI Runtime**: For deploying and serving the Granite model for inference.
        * **IBM Cloud Agent Lab**: (Conceptual) For orchestrating the agent's various components and tools.
* **Programming Language**: Python
* **Frameworks & Libraries**:
    * **LangChain / IBM Agent Lab Orchestration**: (Conceptual) For building the conversational flow, integrating external tools (APIs), and connecting to the IBM Granite model.
    * **External APIs**: For real-time data fetching (e.g., Google Maps API, weather APIs, flight/hotel booking APIs).
    * **Streamlit / Flask**: (Optional - for building a simple web UI) For creating an interactive front-end for the agent.

## Conceptual Code Snippet (Illustrative Example)

This conceptual Python code demonstrates the core logic of how the agent would orchestrate an API call to fetch real-time data and then use the IBM Granite model (simulated here) to generate a personalized itinerary. **This code is for illustrative purposes to show architectural understanding and is not runnable without a full project implementation and actual IBM Watsonx AI API setup.**

```python
# This is a conceptual example and won't run without proper API keys,
# IBM Watsonx AI setup, and a robust data retrieval system.

import os
# In a real project, you would import actual IBM Watsonx AI client libraries
# from ibm_watsonx_ai.ml_api_v1 import APIClient
# from ibm_watsonx_ai.enums import ModelTypes
# from ibm_watsonx_ai.completion import Completion

# Placeholder class for a hypothetical IBM Granite client
class IBMGraniteClient:
    def __init__(self, api_key, project_id):
        self.api_key = api_key
        self.project_id = project_id
        # In a real scenario, this would initialize the actual IBM Watsonx AI client
        print("Initialized conceptual IBM Granite Client.")

    def generate_itinerary(self, prompt, max_tokens=500):
        # This simulates calling the IBM Granite model for itinerary generation
        # In reality, you'd make a POST request to the IBM Watsonx AI API endpoint
        print(f"Sending prompt to Granite: '{prompt[:100]}...'")
        
        # Simulated response from the Granite model
        simulated_response = """
        **Day 1: Arrival in Rome 🇮🇹**
        - **Morning:** Arrive at Leonardo da Vinci–Fiumicino Airport (FCO). Take the Leonardo Express train to Termini Station.
        - **Afternoon:** Check into your hotel near the Pantheon. Explore the Pantheon and Piazza Navona.
        - **Evening:** Enjoy a traditional Roman dinner at a trattoria in Trastevere.

        **Day 2: Ancient Rome Exploration 🏛️**
        - **Morning:** Visit the Colosseum and Roman Forum. (Pre-book tickets!).
        - **Afternoon:** Explore Palatine Hill.
        - **Evening:** Stroll through the charming streets near your hotel.

        **Day 3: Vatican City & Art 🎨**
        - **Morning:** Tour Vatican City: St. Peter's Basilica and Vatican Museums (including Sistine Chapel). (Book tour in advance!).
        - **Afternoon:** Visit Castel Sant'Angelo.
        - **Evening:** Enjoy gelato near the Trevi Fountain.
        """
        return simulated_response

# Placeholder for real-time data retrieval functions (e.g., calling external APIs)
def get_real_time_travel_data(location, dates, interests):
    # This function would call various APIs (weather, flight, hotel, local events)
    # and return consolidated real-time information.
    print(f"Fetching real-time data for {location}, {dates}, with interests: {interests}...")
    # Simulated data
    return {
        "weather": "Sunny, 25°C",
        "flights_available": "Many direct flights",
        "hotels_nearby": "Several 4-star hotels available in city center.",
        "local_events": "No major festivals during these dates."
    }

class TravelPlannerAgent:
    def __init__(self, granite_client):
        self.granite_client = granite_client

    def plan_trip(self, user_query):
        # 1. Natural Language Understanding (Simplified for concept)
        # In a real system, advanced NLP would extract entities like destination, dates, preferences.
        destination = "Rome"
        dates = "August 2025"
        preferences = "sightseeing, food, family-friendly"
        
        print(f"\nUser Query: '{user_query}'")
        print(f"Detected: Destination={destination}, Dates={dates}, Preferences={preferences}")

        # 2. Retrieve Relevant Real-time Data
        real_time_data = get_real_time_travel_data(destination, dates, preferences)
        print(f"Real-time data fetched: {real_time_data}")

        # 3. Construct the Prompt for the IBM Granite Model
        # The prompt combines user intent with retrieved context
        prompt = f"""
        User wants to plan a trip to {destination} in {dates}.
        Preferences include: {preferences}.
        Here's real-time information:
        Weather: {real_time_data['weather']}
        Flights: {real_time_data['flights_available']}
        Hotels: {real_time_data['hotels_nearby']}
        Events: {real_time_data['local_events']}

        Please generate a detailed, personalized 3-day travel itinerary for {destination}, keeping {preferences} in mind. Include suggestions for activities, meals, and practical tips.
        """
        
        # 4. Generate the Itinerary using IBM Granite
        print("Generating itinerary using IBM Granite model...")
        itinerary = self.granite_client.generate_itinerary(prompt)
        
        return itinerary

# --- How you might conceptually use the agent ---
if __name__ == "__main__":
    # Replace with your actual IBM Watsonx AI API Key and Project ID from your IBM Cloud account
    # It's best practice to load these from environment variables or a secure configuration.
    WATSONX_API_KEY = os.getenv("WATSONX_API_KEY", "YOUR_ACTUAL_WATSONX_API_KEY")
    PROJECT_ID = os.getenv("PROJECT_ID", "YOUR_ACTUAL_PROJECT_ID")

    # Initialize the conceptual Granite client
    granite_connector = IBMGraniteClient(api_key=WATSONX_API_KEY, project_id=PROJECT_ID)

    # Initialize the Travel Planner Agent with the Granite client
    agent = TravelPlannerAgent(granite_connector)

    # Simulate a user query
    user_input = "Plan a 3-day trip to Rome for sightseeing and good food in August."
    
    # Get the trip plan
    trip_plan = agent.plan_trip(user_input)
    
    print("\n--- Final Generated Trip Plan ---")
    print(trip_plan)
