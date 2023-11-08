# Class-13 Reading Notes: Local Storage

*sources:* [Local Storage and How To Use It On Websites](https://www.smashingmagazine.com/2010/10/local-storage-and-how-to-use-it/), chatGPT

## Why would a developer use local storage for a web application?

Developers use local storage for web applications for various reasons, primarily to store data on the client-side (in the user's browser) instead of on the server. Local storage provides a way to store and retrieve data, such as settings, user preferences, or application-specific data, directly in the user's browser.

## What information should not be stored in local storage?

Certain types of information should not be stored in local storage due to security and privacy concerns. Local storage is accessible to JavaScript running on the same domain, which means that sensitive information stored there may be vulnerable to potential security risks if not handled properly.

- passwords
- authentication tokes
- PII
- Financial data
- session data (session identifiers or user roles)
- API Keys and secrets

## Local storage can store what type of data? How would you convert it to that type before storing?

Local storage can store data in the form of strings. It only accepts string data, which means that before storing any other data types (e.g., numbers, objects, arrays), you need to convert them to strings. This conversion process is often referred to as "serialization."