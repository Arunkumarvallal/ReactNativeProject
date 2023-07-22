React Native Project 

# The Directory Structure
Here is a bird’s eye view of the recommended directory structure:

```bash
-src
    |--- assets
    |--- screens
    |--- navigation
    |--- services
    |--- components
    |--- types
    |--- redux
    |--- utils
```
Let’s go through each directory and its purpose in more detail.

## 1. assets
For optimal organization, store all static assets, like fonts and images, in the "assets" directory. Consider creating individual subdirectories within it for each asset type. For example:
```bash
assets
  |--- fonts
  |--- images
```
## 2. screens

```bash
screens
  |--- Home
         | --- index.js
         | --- style.js
  |--- Settings
         | --- index.js
         | --- style.js
```
In the project structure, place all application screens or pages within the "screens" directory. Each screen should have its dedicated directory with the following files:

```index.js``` This file will export the screenName as the default export for a shortened import path.

```styles.ts``` Store the screen's styles in this file.

```helper.ts``` For utility functions like business logic or state management, you can use this file. For instance, you could have a function that returns the buttonColor based on a specific status. It's advisable to keep the logic in your component file to a minimum. This approach promotes code abstraction and testability.

```components (optional)``` Any reusable components used by the screen.

##  3. navigation

In the project, the navigation directory is the designated location for storing all code related to navigation functionality. This directory should include the following components:

```NavigationContainer``` This is the top-level component that acts as a wrapper for all the screens in your application. It manages the navigation state and provides the necessary context for navigation to work correctly.

```Route``` The "Route" folder is where you define and manage your application routes. This includes configuring various navigation stacks, tab bars, and drawers, which are essential for defining the flow between different screens or sections of your app.

```NavigationService``` The "NavigationService" file is responsible for encapsulating the reference to your defined routes. It acts as an intermediary layer for handling navigation from outside components, such as deep links or notifications. This way, other parts of your app can trigger navigation without directly accessing the navigation components.

```linking``` The configuration for deep linking.

## 4. services

In the project, the "services" directory serves as the designated location for storing all code related to external services, particularly APIs. Organizing your services into separate subdirectories for each service type is a recommended practice. This structure allows for better maintainability and clarity when dealing with different services.

```bash
screens
  |--- API
  |--- AuthService
  |--- DataService
  |--- PaymentService
  |--- ThirdPartyService
  |--- NotificationService
 
```
Within the "services" directory, you may have the following subdirectories:

```API``` This subdirectory is intended for code related to general API communication or for common API functionalities that may be shared across different services.

```AuthService``` In this subdirectory, you would place code related to authentication services, such as handling user login, registration, and token management.

```DataService``` The "DataService" subdirectory is where you'd put code for handling data-related services, such as fetching, updating, and managing data from various sources.

```PaymentService``` This subdirectory would contain code specific to payment-related services, such as integrating with payment gateways and processing transactions.

```NotificationService``` In this subdirectory, you would place code for handling push notifications and interacting with notification APIs.

```ThirdPartyService``` For any other external services not fitting into the above categories, you can create a "ThirdPartyService" subdirectory to accommodate them.

## 5. components

The "components" directory is the designated location for storing all reusable components. To ensure a consistent and organized structure, each component should have its own directory containing the following files:

```index.ts``` This file serves as the main entry point for the component, allowing you to import and use it more conveniently elsewhere in your codebase.

```ComponentName.tsx``` The TypeScript file (with the .tsx extension) is the actual implementation of the component. It contains the JSX code and TypeScript typings for the component's props and state, ensuring type safety and better code clarity.

```styles.ts``` The "styles.ts" file holds the styling information for the component. You can define the component's CSS or any other styling related to its appearance in this file.

## 6. types

The "types" folder serves as the designated location for storing all TypeScript interfaces and types. Utilizing TypeScript in your project allows you to catch errors during compile-time instead of run-time, leading to a more robust and safer codebase.

```ts
// UserInterface.ts
export interface User {
  id: string;
  name: string;
  email: string;
  // Other user-related properties
}

export interface UserProfile {
  userId: string;
  bio: string;
  // Other profile-related properties
}
```

## 7. redux

```bash
redux
  |--- store.ts
  |--- slices
         |--- UserSlice.ts
         |--- PostSlice.ts
```

 if you are using Redux as the state management library, it's a good practice to create a separate folder to organize all Redux-related files. The "redux" folder should contain the following files:

```store.ts``` This file is responsible for creating the Redux store and configuring it with any middleware or enhancers required for your app. The store is the central place that holds the state of your application.

```slices``` This folder should contain all the Redux slices in your app. A Redux slice represents a distinct piece of the Redux store that can be updated independently of the rest of the store. Each slice should be placed in a separate file with a descriptive name that reflects the data or functionality it manages. For example, you can have a ```UserSlice.ts``` file to handle user-related data.

In ```store.ts```, you would configure and create the Redux store:

```ts
// store.ts
import { configureStore, getDefaultMiddleware } from '@reduxjs/toolkit';
import rootReducer from './slices';

const middleware = [...getDefaultMiddleware()];

const store = configureStore({
  reducer: rootReducer,
  middleware,
});

export default store;

```

In ```UserSlice.ts```, you would define the Redux slice for managing user-related data:
```ts
// UserSlice.ts
import { createSlice, PayloadAction } from '@reduxjs/toolkit';

interface UserState {
  id: string;
  name: string;
  email: string;
  // Other user-related properties
}

const initialState: UserState = {
  id: '',
  name: '',
  email: '',
  // Other initial values
};

const userSlice = createSlice({
  name: 'user',
  initialState,
  reducers: {
    setUser: (state, action: PayloadAction<UserState>) => {
      return { ...state, ...action.payload };
    },
    // Other user-related reducers
  },
});

export const { setUser } = userSlice.actions;
export default userSlice.reducer;

```
## 8. utils
The "utils" folder is a convenient location to house various utility functions and helper classes that don't directly belong to a specific feature or module of the app. These utility functions can be utilized across different parts of the app to perform common tasks, enhance functionality, or handle specific operations in a reusable and centralized manner.

```bash
utils
    |--- Analytics.ts
    |--- Validator.ts
    |--- Logger.ts
    |--- ErrorManager.ts
    |--- string.ts
    |--- constants.ts
    |--- enums.ts
```

```Analytics.ts``` This file may contain functions or classes responsible for handling analytics events, such as tracking user interactions, page views, or custom events for better understanding user behavior and app performance.

```Validator.ts``` The "Validator.ts" file can include utility functions or classes related to data validation. These functions can be used to validate user inputs, form fields, or any other data that needs to conform to specific rules or constraints.

```Logger.ts``` In "Logger.ts," you may have functions or classes dedicated to logging activities and messages. These utilities can help with debugging, error tracking, and providing insights into the application's behavior during development.

```ErrorManager.ts``` The "ErrorManager.ts" file can contain utility functions or classes responsible for handling and managing errors in a consistent manner. This may include custom error types, error handling strategies, or error reporting to external services.

```string.ts``` In this file, you might find utility functions related to string manipulation, such as formatting, truncating, or parsing strings.

```constants.ts``` The "constants.ts" file can hold various constants and configuration values used throughout the app. This keeps the constants centralized, making it easier to modify them in one place if needed.

```enums.ts``` In "enums.ts," you can define enumerations or constant sets that represent specific options or choices within the app. This can help avoid hardcoding values and provide a more semantic way of representing data.


# Getting Started

>**Note**: Make sure you have completed the [React Native - Environment Setup](https://reactnative.dev/docs/environment-setup) instructions till "Creating a new application" step, before proceeding.

## Step 1: Start the Metro Server

First, you will need to start **Metro**, the JavaScript _bundler_ that ships _with_ React Native.

To start Metro, run the following command from the _root_ of your React Native project:

```bash
# using npm
npm start

```

## Step 2: Start your Application

Let Metro Bundler run in its _own_ terminal. Open a _new_ terminal from the _root_ of your React Native project. Run the following command to start your _Android_ or _iOS_ app:

### For Android

```bash
# using npm
npm run android

```

### For iOS

```bash
# using npm
npm run ios

```

If everything is set up _correctly_, you should see your new app running in your _Android Emulator_ or _iOS Simulator_ shortly provided you have set up your emulator/simulator correctly.

This is one way to run your app — you can also run it directly from within Android Studio and Xcode respectively.

## Step 3: Modifying your App

Now that you have successfully run the app, let's modify it.

1. Open `App.tsx` in your text editor of choice and edit some lines.
2. For **Android**: Press the <kbd>R</kbd> key twice or select **"Reload"** from the **Developer Menu** (<kbd>Ctrl</kbd> + <kbd>M</kbd> (on Window and Linux) or <kbd>Cmd ⌘</kbd> + <kbd>M</kbd> (on macOS)) to see your changes!

   For **iOS**: Hit <kbd>Cmd ⌘</kbd> + <kbd>R</kbd> in your iOS Simulator to reload the app and see your changes!

## Congratulations! :tada:

You've successfully run and modified your React Native App. :partying_face:

# Troubleshooting

If you can't get this to work, see the [Troubleshooting](https://reactnative.dev/docs/troubleshooting) page.
