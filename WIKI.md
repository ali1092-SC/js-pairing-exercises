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

Three verification tests ensure the API client is properly configured and can communicate with both endpoints. All tests in apiClient.test.js are active (not skipped) to verify the mock API is running correctly before service layer tests execute.

- Configuration test: Verifies baseURL is set to http://localhost:4000
- Captains endpoint test: Confirms /captains returns 200 status with 4 captain records
- Ships endpoint test: Confirms /ships returns 200 status with 4 ship records

## Captains Service Layer

The captains-service module implements business logic for fetching, transforming, and combining captain and ship data. Currently, only the getCaptains() function is implemented; other functions remain as stubs for completion during the pairing exercise.

### Current Implementation

```javascript
import apiClient from './apiClient';

export const getCaptains = () => null;
```

### Required Service Functions

The test suite defines six functions to be implemented. The first test is active; the rest are marked as skipped (xtest) to be progressively enabled as each function is completed.

| Function Name | Input | Output | Expected Behavior | Test Status |
| --- | --- | --- | --- | --- |
| getCaptains | none | Promise<Captain[]> | Fetch all captains from API endpoint /captains, returning 4 captain objects in original order | Active |
| firstNames | none | Promise<string[]> | Extract captain first names and return array in original order | Skipped (xtest) |
| firstNamesSorted | none | Promise<string[]> | Extract captain first names and return array sorted alphabetically | Skipped (xtest) |
| totalAge | none | Promise<number> | Calculate and return sum of all captain ages | Skipped (xtest) |
| captainBio | captainId: string | Promise<CaptainBio> | Merge captain and ship data, transform field names (first->firstName, last->lastName, ship->shipId and shipName) | Skipped (xtest) |
| captainsWithShipNamesBySize | none | Promise<CaptainShip[]> | Fetch all captains, merge with ship names, sort by ship crew count ascending, replace ship IDs with ship names | Skipped (xtest) |

### Test Examples

#### getCaptains Test

```javascript
test('returns data from captains endpoint', async () => {
  const captains = await captainsService.getCaptains();
  const firstCaptain = {
    id: 'SQ2WI',
    first: 'Jack',
    last: 'Sparrow',
    age: 48,
    ship: 'BC13V'
  };

  expect(captains).toHaveLength(4);
  expect(captains[0]).toEqual(firstCaptain);
});
```

#### captainBio Test (Skipped)

```javascript
xtest('captain and ship combined for given captain id', async () => {
  const expectedData = {
    id: 'R6TZN',
    firstName: 'Malcolm',
    lastName: 'Reynolds',
    shipId: 'V7B8T',
    shipName: 'Serenity'
  };
  const captainShipData = await captainsService.captainBio('R6TZN');

  expect(captainShipData).toEqual(expectedData);
});
```

#### captainsWithShipNamesBySize Test (Skipped)

```javascript
xtest('Captains sorted by ship size', async () => {
  const expectedData = [
    {
      id: 'KZUC8',
      first: 'Han',
      last: 'Solo',
      age: 33,
      ship: 'Millenium Falcon'
    },
    {
      id: 'R6TZN',
      first: 'Malcolm',
      last: 'Reynolds',
      age: 34,
      ship: 'Serenity'
    },
    {
      id: 'SQ2WI',
      first: 'Jack',
      last: 'Sparrow',
      age: 48,
      ship: 'Black Pearl'
    },
    {
      id: 'UXWPK',
      first: 'Jean Luc',
      last: 'Picard',
      age: 64,
      ship: 'USS Enterprise NCC-1701-D'
    }
  ];
  const captainsWithShipNamesBySize = await captainsService.captainsWithShipNamesBySize();

  expect(captainsWithShipNamesBySize).toEqual(expectedData);
});
```

## Code Quality Configuration

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

The configuration enables automatic ESLint fixing and code formatting on save in VSCode. ESLint uses the Airbnb style guide with Prettier integration for consistent formatting. Jest-specific rules allow disabled and focused tests during development.

## Debugging Configuration

VSCode debugging configuration is pre-configured for Jest testing. The launch configuration runs Jest in band (sequential execution) with watch mode enabled for interactive debugging.

```json
{
  "version": "0.2.0",
  "configurations": [
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
  ]
}
```

### Usage

1. Press F5 or go to Run > Start Debugging in VSCode
2. Jest will launch in the integrated terminal with watch mode enabled
3. Set breakpoints by clicking on line numbers in the editor
4. Tests will pause execution at breakpoints for inspection

## Exercise Workflow

The exercise uses test-driven development (TDD) with progressive test enabling. Each function is tested incrementally by removing the 'x' prefix from xtest definitions, revealing new requirements as previous tests pass.

### Progression Steps

1. Implement getCaptains() to fetch captain data from /captains endpoint
2. Remove 'x' from 'xtest' in firstNames test, implement firstNames() to extract first names in order
3. Enable firstNamesSorted test and implement sorting of first names alphabetically
4. Enable totalAge test and implement sum calculation of all captain ages
5. Enable captainBio test and implement captain-ship data merge with field name transformation
6. Enable captainsWithShipNamesBySize test and implement ship name lookup plus crew count sorting

### Data Transformation Patterns

Throughout the exercises, learners practice essential data transformation patterns including:

- Fetching data asynchronously from multiple endpoints
- Array mapping to extract and transform fields
- Array sorting with custom comparator functions
- Array reduction for aggregation (e.g., summing ages)
- Object merging to combine related data from multiple sources
- Field name transformation and aliasing during data merge

---
*Generated by Forge Wiki · 2026-06-18*