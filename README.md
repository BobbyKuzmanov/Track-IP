Track IP Application Documentation
Overview

The Track IP application is designed to retrieve the IP address of the user and provide detailed location information based on the IP address. It utilizes external APIs to first determine the user's IP and then uses another service to look up the geographical location details associated with that IP address. This document outlines the functionalities provided by the Track IP application and guides on how to use them.
Requirements

    Python 3.x
    requests library

Before running the application, ensure that Python 3.x is installed on your system and the requests library is installed. You can install the requests library using pip:

bash

pip install requests

Application Structure

The application consists of two main functions:

    get_ip(): Retrieves the current IP address of the user.
    get_location(): Fetches the geographical location information associated with the IP address obtained from get_ip().

get_ip()

This function makes a GET request to the https://api64.ipify.org API with a query parameter format=json to retrieve the user's current IP address in JSON format. It returns the IP address as a string.
Return Value

    IP Address (str): The current IP address of the user.

get_location()

After retrieving the IP address using get_ip(), get_location() makes a GET request to the https://ipapi.co/{ip_address}/json/ API, substituting {ip_address} with the actual IP address. It fetches location details associated with the IP address.
Return Value

A dictionary containing the following keys:

    ip (str): The IP address.
    city (str): The city associated with the IP address.
    region (str): The region or state associated with the IP address.
    country (str): The country name associated with the IP address.

If any of the location details are unavailable, the corresponding value in the dictionary will be None.
Usage

To use the Track IP application, run the script. The get_location() function will be called, and it will print the location data dictionary to the console.

Example output:

python

{
    "ip": "123.456.78.90",
    "city": "New York",
    "region": "New York",
    "country": "United States"
}

Error Handling

The application does not explicitly handle errors like network issues or API failures. In case of such issues, the requests library may raise exceptions such as requests.exceptions.ConnectionError. Users of this script should implement error handling as needed based on their use case.
Conclusion

The Track IP application provides a simple way to retrieve the user's IP address and geographical location details. It can be integrated into larger projects or used as a standalone tool for location tracking purposes.
