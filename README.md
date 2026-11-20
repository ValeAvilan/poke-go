# Poke Go

A mobile Pokémon browser built with Expo, React Native, and TypeScript. Explore Pokémon from PokéAPI and open a detail sheet with a larger sprite and a background that matches the Pokémon's primary type.

## Features

- Browse the first 20 Pokémon from PokéAPI.
- View each Pokémon's name, primary type, and front and back sprites.
- Identify types through color-coded cards.
- Tap a card to open a detail sheet with a larger front sprite and a type-colored background.

## Built With

- Expo SDK 58
- React Native and React
- TypeScript
- Expo Router for file-based navigation
- [PokéAPI](https://pokeapi.co/) for Pokémon data and sprite URLs

## Getting Started

### Requirements

- A Node.js version supported by Expo SDK 58 and npm
- A compatible Expo Go installation on a physical device, or a configured Android emulator or iOS simulator
- Internet access to load Pokémon data and images

### Installation

```bash
git clone https://github.com/ValeAvilan/poke-go.git
cd poke-go
npm ci
```

### Run the App

```bash
npm start
```

Use the terminal's QR code to open the app in a compatible Expo Go installation, or select an available emulator or simulator.

You can also use these scripts:

```bash
npm run android
npm run ios
npm run web
```

These commands start the development server for the selected platform. Native sheet presentation may differ from the web experience.

## Project Structure

```text
src/
  app/
    _layout.tsx    # Stack navigation and detail sheet options
    index.tsx      # Pokémon fetching, type colors, and card list
    details.tsx    # Selected Pokémon's name, type, image, and background
assets/           # App icons and splash assets
app.json          # Expo configuration
```

## How It Works

1. The home screen requests 20 Pokémon from `https://pokeapi.co/api/v2/pokemon?limit=20`.
2. It fetches each Pokémon's details in parallel using `Promise.all`.
3. It stores the names, sprites, and types in React state and renders the cards.
4. The first type determines each card's background color.
5. Selecting a card navigates to `/details`, passing the name, primary type, front sprite URL, and color as route parameters.
6. The details screen reads those values with `useLocalSearchParams` and displays the selected Pokémon.

## Development Checks

```bash
npx tsc --noEmit
npm run lint
```

The lint script uses Expo's ESLint setup. If ESLint is not configured yet, the first run may install dependencies and create a configuration file.

## Current Scope

The app currently loads a fixed list of 20 Pokémon. Search, pagination, offline storage, and on-screen loading and error states are not implemented. Pokémon with multiple types are displayed using their first type.

## License

This project is distributed under the [MIT License](LICENSE).

Pokémon names and imagery belong to their respective owners. Pokémon data is provided by PokéAPI.
