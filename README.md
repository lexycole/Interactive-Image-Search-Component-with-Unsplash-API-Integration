# 🔍Interactive-Image-Search-Component-with-Unsplash-API-Integration


[![Language](https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E)]()
[![Language](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)]()


## ✍️ About 
This Vue.js component, named "App", enables users to search for images using the Unsplash API. Upon mounting, it retrieves images related to the query "African" and populates the component's data. Users can input a search topic, triggering an asynchronous call to fetch images based on the provided query, username, and location. The component utilizes axios for HTTP requests and integrates with Unsplash's API using an access token. With dynamic data handling and asynchronous loading, this component offers a seamless image search experience for users within Vue.js applications.


## 🗺 Features
- [x] **Image Search:** Users can search for images using a specific topic provided by the Unsplash API.
- [x] **Integration with Unsplash API:** The component integrates with the Unsplash API to fetch images based on the user's search query.
- [x]  **Asynchronous Loading:** HTTP requests to fetch images are handled asynchronously, ensuring smooth user experience without blocking the UI.
- [x] **Dynamic Data Handling:** The component dynamically updates its data with the fetched images, providing users with real-time search results.
- [x] **Timeout Functionality:** A timeout function is implemented to control the timing of certain actions, such as updating the "firstLoad" and "firstLoadSearch" flags, enhancing the component's responsiveness and performance.


## How to use
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

## 👨‍💻 Author 
[Akinro Olawale](https://github.com/lexycole)
