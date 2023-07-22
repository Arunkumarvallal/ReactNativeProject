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

```bash
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
