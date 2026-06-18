# ali1092-SC/js-pairing-exercises

> JavaScript pairing exercises focused on API data transformation, sorting, and merging with Jest tests and a mock JSON server.

## Overview

This repository provides a starting point for JavaScript pairing exercises focused on reading from a mock API and then sorting, transforming, and merging data to meet test expectations. The project includes a complete test suite with Jest, a working mock API client wrapping axios, and a JSON server serving mock captain and ship data.

The exercises are designed to teach asynchronous JavaScript patterns, HTTP client usage, data transformation logic, and test-driven development through practical API integration challenges. Learners work with a mock API client to fetch data, then implement service functions that sort, filter, merge, and transform the data to pass progressive Jest tests.

### Key Features

- Mock API client (apiClient.js) using axios for promise-based data access
- JSON server providing captains and ships mock data on port 4000
- Jest test framework with watch mode for test-driven development
- ESLint with Airbnb configuration for code quality enforcement
- Pre-configured VSCode launch configuration for debugging Jest tests
- Progressive exercise structure with skipped tests to enable incremental completion

## Getting Started

1. Start the mock API with npm run api
2. Start the tests with npm test (Jest runs in watch mode and reruns automatically on file changes)
3. Complete the service implementations in captains-service.js to make tests pass
4. Remove the 'x' prefix from xtest definitions to progressively enable skipped tests

The apiClient.test.js tests are complete and verify that the mock API is running and correctly configured. The mock API client must be running to support the captains-service.js functions.

## System Architecture

The system consists of three primary layers: a mock data API, an HTTP client layer, and service implementations that transform and combine data. The architecture is designed for educational purposes to teach API interaction, data transformation patterns, and asynchronous JavaScript fundamentals.

### Component Stack

- Mock API Layer: json-server serving captains and ships endpoints from api/db.json on port 4000
- HTTP Client: axios-based apiClient configured to localhost:4000
- Service Layer: captains-service.js implementing data transformation logic
- Test Layer: Jest test suite validating all functionality

### Data Flow Architecture

## Project Structure

### Repository Layout

| Directory | Purpose | Key Files |
| --- | --- | --- |
| / (root) | Configuration and entry point | package.json, README.md, .eslintrc.json, WIKI.md |
| src/ | Application source code and tests | apiClient.js, captains-service.js, *.test.js |
| api/ | Mock API data storage | db.json |
| .vscode/ | VSCode development configuration | launch.json, settings.json |

### File Manifest

- .eslintrc.json - ESLint configuration with Airbnb preset and Jest plugin support
- .vscode/launch.json - Jest debugging configuration for VSCode with runInBand and watchAll flags
- .vscode/settings.json - Auto-formatting and linting settings for VSCode with eslint.autoFixOnSave enabled
- README.md - Project documentation and getting started guide
- WIKI.md - Generated wiki documentation
- package.json - Dependencies and NPM scripts (test, api, api:stop)
- package-lock.json - Locked dependency versions for reproducible installs
- api/db.json - Mock data for captains and ships collections with 4 records each
- src/apiClient.js - Axios HTTP client wrapper with baseURL configuration
- src/apiClient.test.js - API client verification tests (3 tests, all active)
- src/captains-service.js - Service implementation stub for data transformation
- src/captains-service.test.js - Service functionality tests with progressive skipping

## NPM Scripts & Configuration

| Script | Command | Purpose |
| --- | --- | --- |
| test | jest --watch --verbose | Run Jest in watch mode with verbose output, reruns on file changes |
| api | json-server --port 4000 ./api/db.json | Start mock JSON server on port 4000 serving api/db.json |
| api:stop | pkill -f 'json-server' || true | Stop the running JSON server process |

### Jest Configuration

```json
"jest": {
  "testEnvironment": "node",
  "reporters": ["default"],
  "watchPlugins": [
    "jest-watch-typeahead/filename",
    "jest-watch-typeahead/testname"
  ]
}
```

## Dependencies

### Production Dependencies

| Package | Version | Purpose |
| --- | --- | --- |
| axios | ^1.9.0 | HTTP client library for making API requests |
| json-server | ^1.0.0-beta.15 | Mock JSON API server for development and testing |

### Development Dependencies

- @babel/preset-env ^7.29.5 - Babel preset for ES2015+ transpilation
- eslint ^8.57.1 - JavaScript linter
- eslint-config-airbnb ^19.0.4 - Airbnb ESLint configuration
- eslint-config-prettier ^9.1.2 - Disable ESLint rules conflicting with Prettier
- eslint-plugin-import ^2.32.0 - ESLint plugin for import statements
- eslint-plugin-jest ^29.15.2 - ESLint plugin for Jest
- jest ^30.4.2 - Testing framework
- jest-watch-typeahead ^3.0.1 - Watch mode plugin for interactive filtering
- prettier ^3.8.3 - Code formatter

## Mock API Data Structure

The mock API serves two primary collections: captains and ships. These are related through captain.ship referencing ship.id. The JSON server runs on port 4000 and provides RESTful endpoints for both collections.

### Captains Collection

Returns array of 4 captain objects, each containing id, first name, last name, age, and ship ID reference.

| Field | Type | Example | Description |
| --- | --- | --- | --- |
| id | string | SQ2WI | Unique captain identifier |
| first | string | Jack | Captain's first name |
| last | string | Sparrow | Captain's last name |
| age | number | 48 | Captain's age in years |
| ship | string | BC13V | Foreign key reference to ships.id |

### Ships Collection

Returns array of 4 ship objects, each containing id, name, crew count, and propulsion type.

| Field | Type | Example | Description |
| --- | --- | --- | --- |
| id | string | DRPHT | Unique ship identifier |
| name | string | USS Enterprise NCC-1701-D | Official ship name |
| crewCount | number | 1012 | Number of crew members |
| propulsion | string | Warp Drive | Propulsion system type |

### Sample Data

```json
{
  "captains": [
    {
      "id": "SQ2WI",
      "first": "Jack",
      "last": "Sparrow",
      "age": 48,
      "ship": "BC13V"
    },
    {
      "id": "R6TZN",
      "first": "Malcolm",
      "last": "Reynolds",
      "age": 34,
      "ship": "V7B8T"
    },
    {
      "id": "UXWPK",
      "first": "Jean Luc",
      "last": "Picard",
      "age": 64,
      "ship": "DRPHT"
    },
    {
      "id": "KZUC8",
      "first": "Han",
      "last": "Solo",
      "age": 33,
      "ship": "1M6GB"
    }
  ],
  "ships": [
    {
      "id": "DRPHT",
      "name": "USS Enterprise NCC-1701-D",
      "crewCount": 1012,
      "propulsion": "Warp Drive"
    },
    {
      "id": "BC13V",
      "name": "Black Pearl",
      "crewCount": 44,
      "propulsion": "Wind"
    },
    {
      "id": "1M6GB",
      "name": "Millenium Falcon",
      "crewCount": 2,
      "propulsion": "Hyperdrive"
    },
    {
      "id": "V7B8T",
      "name": "Serenity",
      "crewCount": 5,
      "propulsion": "Radion/Accelerator Core"
    }
  ]
}
```

## API Client Layer

The apiClient module wraps axios and configures it to communicate with the mock JSON server running on localhost:4000. It provides a thin abstraction layer for HTTP requests, enabling promise-based asynchronous data fetching.

### Implementation

```javascript
import axios from 'axios';

axios.defaults.baseURL = 'http://localhost:4000';

export default axios;
```

### API Client Tests

Three verification tests ensure the API client is properly configured and can communicate with both endpoints. All tests in apiClient.test.js are active (not skipped) to verify the mock API is running and correctly configured.

- Test 1: Verifies apiClient.defaults.baseURL is set to 'http://localhost:4000'
- Test 2: Verifies GET /captains endpoint returns 200 status and 4 captain records
- Test 3: Verifies GET /ships endpoint returns 200 status and 4 ship records

## Captains Service Layer

The captains-service module is the primary implementation file where learners write service functions that fetch and transform data from the mock API. It imports apiClient to make HTTP requests and exports functions that perform data operations.

### Current Implementation

```javascript
import apiClient from './apiClient';

export const getCaptains = () => null;
```

### Service Functions to Implement

1. getCaptains() - Returns all captains from /captains endpoint
2. firstNames() - Extracts first names from all captains in their original order
3. firstNamesSorted() - Returns first names sorted alphabetically
4. totalAge() - Calculates the sum of all captains' ages
5. captainBio(id) - Merges captain data with their associated ship data for a given captain ID, returning transformed field names
6. captainsWithShipNamesBySize() - Returns all captains with ship names merged and sorted by crew size ascending

### Test Structure

The captains-service.test.js file contains 6 test cases. The first test (getCaptains) is active and must pass initially. The remaining 5 tests are prefixed with 'x' (xtest) to skip them during early development. Learners progressively remove the 'x' prefix as they implement each function.

| Test Name | Status | Expected Output | Data Operations |
| --- | --- | --- | --- |
| returns data from captains endpoint | Active | Array of 4 captain objects | Fetch from /captains |
| captain first names | Skipped (xtest) | ["Jack", "Malcolm", "Jean Luc", "Han"] | Extract first names, preserve order |
| captain first names sorted alphabetically | Skipped (xtest) | ["Han", "Jack", "Jean Luc", "Malcolm"] | Extract first names, sort alphabetically |
| captain combined total age | Skipped (xtest) | 179 | Sum all ages: 48+34+64+33 |
| captain and ship combined for given captain id | Skipped (xtest) | { id, firstName, lastName, shipId, shipName } | Merge captain + ship data, transform field names |
| Captains sorted by ship size | Skipped (xtest) | Array of captains with ship names, sorted by crewCount ascending | Merge all captains with ships, sort by crewCount |

## Linting & Code Quality

The project is configured with ESLint for code quality and Prettier for automatic formatting. VSCode is configured to automatically apply ESLint fixes and format code on save.

### ESLint Configuration

```json
{
  "extends": ["airbnb", "prettier"],
  "plugins": ["jest"],
  "rules": {
    "no-console": "off",
    "no-unused-vars": "off",
    "import/prefer-default-export": "off",
    "linebreak-style": "off",
    "jest/no-disabled-tests": "off",
    "jest/no-focused-tests": "off",
    "jest/no-identical-title": "error",
    "jest/prefer-to-have-length": "warn",
    "jest/valid-expect": "error"
  },
  "env": {
    "jest/globals": true
  }
}
```

### VSCode Settings

```json
{
  "eslint.autoFixOnSave": true,
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  }
}
```

Key ESLint rules modifications: console logging is allowed for debugging, unused variables are ignored during development, default exports are not required, and Jest test disabling/focusing is permitted to support the progressive test skipping structure.

## Debugging in VSCode

VSCode is pre-configured with a Jest debugging launch configuration that allows developers to debug tests directly in the IDE.

### Jest All Configuration

```json
{
  "type": "node",
  "request": "launch",
  "name": "Jest All",
  "program": "${workspaceFolder}/node_modules/.bin/jest",
  "args": [
    "--runInBand",
    "--watchAll=true"
  ],
  "console": "integratedTerminal",
  "internalConsoleOptions": "neverOpen",
  "disableOptimisticBPs": true,
  "windows": {
    "program": "${workspaceFolder}/node_modules/jest/bin/jest"
  }
}
```

The configuration uses --runInBand to execute tests sequentially for better debugging, --watchAll=true to enable watch mode, and includes a Windows-specific program path for cross-platform compatibility. Output appears in the integrated terminal rather than the debug console.

## Learning Outcomes

By completing the exercises in this repository, learners will develop proficiency in several key JavaScript and software development areas:

- Asynchronous JavaScript patterns using Promises and async/await
- HTTP client usage with axios for API communication
- Data transformation and manipulation using array methods (map, filter, reduce, sort)
- Data merging and joining from multiple sources
- Test-driven development with Jest
- Mock API usage for development and testing
- Code organization and separation of concerns (client layer vs service layer)
- Debugging JavaScript code in VSCode
- Code quality enforcement with ESLint and Prettier

---
*Generated by Forge Wiki · 2026-06-18*