
# Weather Monitoring System

## Table of Contents
- [Overview](#overview)
- [Technologies Used](#technologies-used)
- [Setup Instructions](#setup-instructions)
- [Usage](#usage)
- [Functionality](#functionality)
- [Test Cases](#test-cases)
- [Contributing](#contributing)
- [Sample Input and Output](#sample-input-and-output)
- [Codebase and Build Scripts](#codebase-and-build-scripts)
- [Non-Functional Items](#non-functional-items)

## Overview
The Weather Monitoring System is a real-time data processing application designed to monitor weather conditions for major metros in India. It retrieves weather data from the OpenWeatherMap API, processes the data to provide insights such as daily aggregates, and triggers alerts based on user-defined thresholds. This system is capable of continuous data retrieval and offers a summary of weather conditions, including average, maximum, and minimum temperatures.

## Technologies Used
- **Python**: The programming language used to implement the application.
- **Requests**: A library for making HTTP requests to the OpenWeatherMap API.
- **Pandas**: A data manipulation and analysis library for processing weather data.
- **dotenv**: A library to load environment variables from a .env file.

## Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone <repository-url>
   cd weather_monitoring
   ```

2. **Set Up Virtual Environment (Optional but Recommended)**
   ```bash
   python -m venv venv
   ```

3. **Activate the Virtual Environment**
   - **Windows**:
     ```bash
     venv\Scripts\activate
     ```
   - **macOS/Linux**:
     ```bash
     source venv/bin/activate
     ```

4. **Install Required Libraries**
   ```bash
   pip install requests pandas python-dotenv
   ```

5. **Add Your API Key**
   - Create a file named `.env` in the project root.
   - Add your OpenWeatherMap API key to the `.env` file:
     ```
     API_KEY=your_api_key_here
     ```

## Usage
**Run the Application**: Execute the following command in your terminal:
```bash
python weather_monitor.py
```

**Monitor Output**: The application will continuously fetch weather data every 5 minutes and display the weather information for the specified cities in the console.

## Functionality
- **Data Retrieval**: The system retrieves weather data from the OpenWeatherMap API for the following cities:
  - Delhi
  - Mumbai
  - Chennai
  - Bangalore
  - Kolkata
  - Hyderabad

- **Temperature Conversion**: Converts temperatures from Kelvin to Celsius.

- **Daily Weather Summary**:
  - Roll up weather data and calculate:
    - Average temperature
    - Maximum temperature
    - Minimum temperature
    - Dominant weather condition

- **Alerting Thresholds**:
  - Define user-configurable thresholds for temperature.
  - Trigger alerts if weather conditions exceed defined thresholds.

- **Data Storage**: Store daily summaries and alerts (this can be expanded to include a database connection).

## Test Cases
- **System Setup**: Verify that the application starts successfully and connects to the OpenWeatherMap API.
- **Data Retrieval**: Simulate API calls and ensure correct parsing of weather data.
- **Temperature Conversion**: Test the conversion of temperature values from Kelvin to Celsius.
- **Daily Weather Summary**: Verify calculations of daily aggregates for multiple days.
- **Alerting Thresholds**: Ensure alerts are triggered when thresholds are breached.

## Contributing
Contributions are welcome! If you would like to contribute to this project, please follow these steps:
1. Fork the repository.
2. Create a new branch for your feature or fix.
3. Commit your changes and push to your branch.
4. Submit a pull request.

## Sample Input and Output

### Sample Inputs
**Weather Data from OpenWeatherMap API**:

**For Delhi**:
```json
{
  "main": {
    "temp": 295.15,
    "feels_like": 295.15,
    "temp_min": 293.15,
    "temp_max": 297.15
  },
  "weather": [
    {
      "main": "Clear"
    }
  ],
  "dt": 1697533200
}
```

**For Mumbai**:
```json
{
  "main": {
    "temp": 300.15,
    "feels_like": 302.15,
    "temp_min": 298.15,
    "temp_max": 301.15
  },
  "weather": [
    {
      "main": "Rain"
    }
  ],
  "dt": 1697533200
}
```

**User-defined Alert Thresholds**:
- Temperature threshold: 35 degrees Celsius
- Weather condition: Rain

### Sample Outputs
**Console Output for Weather Data Retrieval**:
```
After retrieving the weather data for Delhi:
Weather Update for Delhi:
Temperature: 22°C
Feels Like: 22°C
Min Temperature: 20°C
Max Temperature: 24°C
Condition: Clear
Time: 2023-10-18 14:00:00
```

**Daily Weather Summary**:
```
After processing multiple weather updates for Delhi and Mumbai over a day:
Daily Weather Summary for 2023-10-18:
- Delhi:
  Average Temperature: 22.5°C
  Maximum Temperature: 24°C
  Minimum Temperature: 20°C
  Dominant Condition: Clear
- Mumbai:
  Average Temperature: 27.5°C
  Maximum Temperature: 30°C
  Minimum Temperature: 25°C
  Dominant Condition: Rain
```

**Alert Triggered**:
```
Alert: The temperature in Mumbai has exceeded the threshold of 35°C. Current temperature: 36°C
```

**Note**: The temperature values are converted from Kelvin to Celsius by subtracting 273.15. For example, if the API returns a temperature of 300.15 K, it is converted to 300.15 - 273.15 = 27°C. The Dominant Condition is determined based on the frequency of weather conditions for the day.

## Codebase and Build Scripts
- **Code Organization**: The code is organized into a main script (`weather_monitor.py`) that handles data retrieval, processing, and alerting.
- **Build Scripts**: You can use `requirements.txt` to manage dependencies. Generate it by running:
  ```bash
  pip freeze > requirements.txt
  ```

## Non-Functional Items
- **Security**: The application uses environment variables to store sensitive information like API keys, reducing the risk of exposure in the codebase.
- **Performance**: The system retrieves data at configurable intervals (default 5 minutes) to balance performance and freshness of data. You can adjust this in the configuration settings.
- **Scalability**: The architecture allows for easy integration with a database to store historical data, which can be expanded in the future for more extensive analysis.

---


### Note
- The temperature values are converted from Kelvin to Celsius by subtracting 273.15. For example, if the API returns a temperature of `300.15` K, it is converted to `300.15 - 273.15 = 27°C`.
- The **Dominant Condition** is determined based on the frequency of weather conditions for the day. For example, if there are more `Clear` days than `Rain`, then `Clear` is chosen as the dominant condition.


