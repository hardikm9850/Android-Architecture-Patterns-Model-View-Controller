# Android-Architecture-Patterns-Model-View-View-Model

# Android Architecture Patterns: Model-View-View-Model

## PROBLEM STATEMENT 
An app which displays the top-rated English movies in a list. Display the movie title along with the rating of the movie. Implement a cache to store the top-rated movie data into a Room database locally. Use the cache data when the app requests the data, if data is not available in cache or in offilne mode, then fetch data from the API and update the cache. Also add a workmanager to update the cache once in a day.

TMDB console URL: https://www.themoviedb.org/ 

API key URL: https://www.themoviedb.org/settings/api

**API information:**

|   |   |
| ------------ | ------------ |
|  API type  |  GET|
|  BASE URL | https://api.themoviedb.org/3/  |
|  TOP RATED MOVIE ENDPOINT | /movie/top_rated  |
|  GET PARAMETER |  api_key  |


Libraries used
1. Room database
2. Coroutines
3. Retrofit 
4. LiveData
5. WorkManager
6. ViewModel
7. Mockito

App architecture is a way of organizing the different modules of the project in a way to make the code easy to understand, well structured, easier to work with and manage the responsibility of each module efficiently. There are many architecture patterns available in Android like Model-View-Controller(MVC), Model-View-Presenter(MVP), Model-View-Intent(MVI), Model-View-View-Model(MVVM) etc. Here we are going to focus on Model-View-View-Model(MVVM) App architecture. 

**Why Model-View-View-Model(MVVM)?**

· Officially endorsed by Google

· Leverage the use of lifecycle aware components

· Easier to distribute the responsibility across different module

· Make the app Maintainable and Robust

Let's look at a high level diagram of the Model-View-View-Model(MVVM) architecture.

![alt text](https://github.com/gaikwadChetan93/Android-Architecture-Patterns-Model-View-Controller/blob/master/Architecture%20Diagram.png?raw=true)





Let’s explore each component and their responsibilities in detail 

1. **UI**: This component contains Activity and Fragment. Some of the responsibilities of this component are as follow 

	Should contain only UI logic like displaying the data, responding to user action and Managing the UI state 

	Should not hold any UI data 

	Should not have any business logic 

	Delegate the control to the ViewModel component if any user action requires any data or manipulation of existing data 

2. **ViewModel**: This component contains the subclass of ViewModel. ViewModel classes are also responsible to manage the LiveData objects which are observed by the UI component to communicate the data. Some of the responsibilities of this component are as follow 

	Hold the data required for UI 

	Contains some business logic 

	Can perform transformation on the data, calculation or computation task 

	Delegate the control to the Repository If any new data is require 

	Should not contain any API or Database logic, Data source is completely abstract from ViewModel 

3. **Repository**: This component manages the data layer of the app and abstract the data layer from the rest of the app. Some of the responsibilities of this component are as follow 

	Decides which data layer(API or Database) to communicate when the application needs the data 

	Implements the caching for the application 

4. **Database**: This component manages the database of the application. The primary responsibility of this component is to communicate with the database and collaborate all the logic related to the database manipulation at one place 

5. **Network**: This component manages the API network calls of the application. The primary responsibility of this component is to communicate with External API service and collaborate all the logic related to the network API service at one place 
