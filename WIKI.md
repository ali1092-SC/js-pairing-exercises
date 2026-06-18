# ali1092-SC/js-pairing-exercises

> JavaScript pairing exercises focused on API data transformation, sorting, and merging with Jest tests and a mock JSON server.

## Overview

This repository provides a starting point for JavaScript pairing exercises focused on reading from a mock API and then sorting, transforming, and merging data to meet test expectations. The project includes a complete test suite with Jest, a working mock API client wrapping axios, and a JSON server that serves mock captain and ship data.

### Purpose

The exercises are designed to teach asynchronous JavaScript patterns, HTTP client usage, data transformation logic, and test-driven development through practical API integration challenges.

### Key Features

- Mock API client (apiClient.js) using axios for promise-based data access
- JSON server providing captains and ships mock data on port 4000
- Jest test framework with watch mode for test-driven development
- ESLint with Airbnb configuration for code quality enforcement
- Pre-configured VSCode launch configuration for debugging Jest tests
- Progressive exercise structure with skipped tests to enable incremental completion

## Getting Started

1. Start the mock api with npm run api
2. Start the tests with npm test (Jest runs in watch mode and reruns automatically on file changes)
3. Complete the service implementations in captains-service.js to make tests pass
4. Remove the 'x' prefix from xtest definitions to progressively enable skipped tests

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
| getCaptains | none | Promise<Captain[]> | Fetch all captains from API endpoint /captains | Active |
| firstNames | none | Promise<string[]> | Extract and return captain first names in original order | Skipped (xtest) |
| firstNamesSorted | none | Promise<string[]> | Extract first names and sort alphabetically | Skipped (xtest) |
| totalAge | none | Promise<number> | Calculate sum of all captain ages (expected: 179) | Skipped (xtest) |
| captainBio | captainId: string | Promise<CaptainBio> | Merge captain and ship data for single captain by ID | Skipped (xtest) |
| captainsWithShipNamesBySize | none | Promise<CaptainWithShip[]> | All captains with ship names sorted by crew count ascending | Skipped (xtest) |

### Test Expectations

#### getCaptains() - Active Test

Returns all 4 captain objects directly from the API endpoint.

```javascript
// Expected output from getCaptains()
[
  {
    id: 'SQ2WI',
    first: 'Jack',
    last: 'Sparrow',
    age: 48,
    ship: 'BC13V'
  },
  {
    id: 'R6TZN',
    first: 'Malcolm',
    last: 'Reynolds',
    age: 34,
    ship: 'V7B8T'
  },
  {
    id: 'UXWPK',
    first: 'Jean Luc',
    last: 'Picard',
    age: 64,
    ship: 'DRPHT'
  },
  {
    id: 'KZUC8',
    first: 'Han',
    last: 'Solo',
    age: 33,
    ship: '1M6GB'
  }
]
```

#### firstNames() - Skipped Test

Extracts first names from captains in original order.

```javascript
// Expected output from firstNames()
['Jack', 'Malcolm', 'Jean Luc', 'Han']
```

#### firstNamesSorted() - Skipped Test

Extracts first names and returns them in alphabetical order.

```javascript
// Expected output from firstNamesSorted()
['Han', 'Jack', 'Jean Luc', 'Malcolm']
```

#### totalAge() - Skipped Test

Calculates sum of all captain ages.

```javascript
// Expected output from totalAge()
// 48 + 34 + 64 + 33 = 179
179
```

#### captainBio(captainId) - Skipped Test

Merges captain data with corresponding ship data for a given captain ID. Transforms field names and requires fetching ship details.

```javascript
// Expected output from captainBio('R6TZN')
{
  id: 'R6TZN',
  firstName: 'Malcolm',
  lastName: 'Reynolds',
  shipId: 'V7B8T',
  shipName: 'Serenity'
}
```

#### captainsWithShipNamesBySize() - Skipped Test

Returns all captains with ship names substituted for ship IDs, sorted by ship crew count in ascending order.

```javascript
// Expected output from captainsWithShipNamesBySize()
// Sorted by crewCount: 2, 5, 44, 1012
[
  {
    id: 'KZUC8',
    first: 'Han',
    last: 'Solo',
    age: 33,
    ship: 'Millenium Falcon'  // crewCount: 2
  },
  {
    id: 'R6TZN',
    first: 'Malcolm',
    last: 'Reynolds',
    age: 34,
    ship: 'Serenity'  // crewCount: 5
  },
  {
    id: 'SQ2WI',
    first: 'Jack',
    last: 'Sparrow',
    age: 48,
    ship: 'Black Pearl'  // crewCount: 44
  },
  {
    id: 'UXWPK',
    first: 'Jean Luc',
    last: 'Picard',
    age: 64,
    ship: 'USS Enterprise NCC-1701-D'  // crewCount: 1012
  }
]
```

## NPM Scripts & Commands

| Command | Script | Description |
| --- | --- | --- |
| npm test | jest --watch --verbose | Runs Jest test suite in watch mode with verbose output; automatically reruns on file changes |
| npm run api | json-server --port 4000 ./api/db.json | Starts JSON server on port 4000 serving data from api/db.json |
| npm run api:stop | pkill -f 'json-server' || true | Stops all running json-server processes |

## Development Configuration

### ESLint Configuration

Project uses Airbnb ESLint preset with Prettier formatting, Jest plugin support, and custom rule overrides to allow disabled tests and console statements.

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

### VSCode Debugging

Pre-configured Jest launch configuration for VSCode enables debugging with breakpoints. Runs Jest in band with watch mode enabled.

### VSCode Settings

Auto-formatting on save with ESLint auto-fix enabled. Code actions on save run ESLint fixes explicitly.

```json
{
  "eslint.autoFixOnSave": true,
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  }
}
```

## Dependencies & Versions

### Production Dependencies

| Package | Version | Purpose |
| --- | --- | --- |
| axios | ^1.9.0 | HTTP client for making API requests |
| json-server | ^1.0.0-beta.15 | Mock REST API server for development |

### Development Dependencies

| Package | Version | Purpose |
| --- | --- | --- |
| @babel/preset-env | ^7.29.5 | Babel preset for ES6+ transpilation |
| eslint | ^8.57.1 | JavaScript linting and code quality |
| eslint-config-airbnb | ^19.0.4 | Airbnb ESLint configuration preset |
| eslint-config-prettier | ^9.1.2 | Prettier ESLint configuration for code formatting |
| jest | ^30.4.2 | Test framework and test runner |
| jest-watch-typeahead | ^3.0.1 | Watch mode plugin for Jest with typeahead search |
| prettier | ^3.8.3 | Code formatter |

## Exercise Workflow

The exercise follows a test-driven development approach with progressive complexity. Tests are initially skipped to reduce noise, then enabled one at a time as implementations are completed.

### Step-by-Step Workflow

1. Start mock API server: npm run api (runs on localhost:4000)
2. Start Jest test runner: npm test (runs in watch mode)
3. Verify API connectivity: All tests in apiClient.test.js should pass
4. Implement getCaptains(): First test in captains-service.test.js should pass immediately
5. Enable and implement firstNames(): Remove 'x' from xtest, implement function to extract first names
6. Enable and implement firstNamesSorted(): Implement sorting logic on extracted names
7. Enable and implement totalAge(): Implement aggregation logic to sum all ages
8. Enable and implement captainBio(id): Implement data merge logic to combine captain and ship data
9. Enable and implement captainsWithShipNamesBySize(): Implement sorting by ship crew count and name substitution

### Key Implementation Patterns

- All service functions are async and return Promises
- apiClient.get() is used to fetch data from /captains and /ships endpoints
- Data transformations require mapping, filtering, reducing, and sorting array operations
- Ship data requires joining with captain data using ship ID as foreign key
- Field names are transformed in output objects (e.g., first -> firstName)

---
*Generated by Forge Wiki · 2026-06-18*