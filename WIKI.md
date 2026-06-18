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
- Progressive exercise structure with skipped tests to enable incrementally

## System Architecture

The system consists of three primary layers: a mock data API, an HTTP client layer, and service implementations that transform and combine data. The architecture is designed for educational purposes to teach API interaction, data transformation patterns, and asynchronous JavaScript fundamentals.

### Component Stack

- Mock API Layer: json-server serving captains and ships endpoints from api/db.json
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

### Complete File Listing

- .eslintrc.json - ESLint configuration with Airbnb preset and Jest plugin support
- .vscode/launch.json - Jest debugging configuration for VSCode
- .vscode/settings.json - Auto-formatting and linting settings for VSCode
- README.md - Project documentation and getting started guide
- WIKI.md - Generated wiki documentation
- package.json - Dependencies and NPM scripts
- package-lock.json - Locked dependency versions for reproducible installs
- api/db.json - Mock data for captains and ships collections
- src/apiClient.js - Axios HTTP client wrapper with baseURL configuration
- src/apiClient.test.js - API client verification tests
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
| ship | string | BC13V | Foreign key to ships.id |

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

Three verification tests ensure the API client is properly configured and can communicate with both endpoints:

- Configuration test: Verifies baseURL is set to http://localhost:4000
- Captains endpoint test: Confirms /captains returns 200 status with 4 captain records
- Ships endpoint test: Confirms /ships returns 200 status with 4 ship records

All tests in apiClient.test.js are active (not skipped) to verify the mock API is running correctly before service layer tests execute.

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
| getCaptains | none | Promise<Captain[]> | Fetch all captains from API | Active |
| firstNames | none | Promise<string[]> | Extract and return captain first names in original order | Skipped (xtest) |
| firstNamesSorted | none | Promise<string[]> | Extract first names and sort alphabetically | Skipped (xtest) |
| totalAge | none | Promise<number> | Calculate sum of all captain ages (179) | Skipped (xtest) |
| captainBio | captainId: string | Promise<CaptainBio> | Merge captain and ship data for single captain | Skipped (xtest) |
| captainsWithShipNamesBySize | none | Promise<CaptainWithShip[]> | All captains with ship names sorted by crew count ascending | Skipped (xtest) |

### Test Data and Expected Outputs

#### getCaptains() - Active Test

```javascript
// Expected output
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

```javascript
// Expected output
['Jack', 'Malcolm', 'Jean Luc', 'Han']
```

#### firstNamesSorted() - Skipped Test

```javascript
// Expected output
['Han', 'Jack', 'Jean Luc', 'Malcolm']
```

#### totalAge() - Skipped Test

```javascript
// Expected output
179
```

#### captainBio(captainId) - Skipped Test

```javascript
// captainBio('R6TZN') expected output
{
  id: 'R6TZN',
  firstName: 'Malcolm',
  lastName: 'Reynolds',
  shipId: 'V7B8T',
  shipName: 'Serenity'
}
```

#### captainsWithShipNamesBySize() - Skipped Test

```javascript
// Expected output (sorted by crew count ascending)
[
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
]
```

## Development Workflow

The project uses npm scripts to manage the development lifecycle. Two processes must run simultaneously: the mock API server and the Jest test runner. Each provides real-time feedback for test-driven development.

### NPM Scripts

| Script | Command | Purpose |
| --- | --- | --- |
| test | jest --watch --verbose | Start Jest in watch mode with verbose output; auto-reruns on file changes |
| api | json-server --port 4000 ./api/db.json | Start JSON server on port 4000 serving mock captain and ship data |
| api:stop | pkill -f 'json-server' || true | Stop running JSON server process (safe on systems without process) |

### Getting Started Steps

1. Install dependencies: npm install
2. Start the mock API in one terminal: npm run api
3. Start the tests in another terminal: npm test
4. Jest runs in watch mode and will rerun tests automatically when project files are saved
5. Complete captains-service.js implementations to get tests passing
6. Remove the 'x' from xtest declarations to enable previously skipped tests progressively

### Progressive Test Activation

To reduce alarming red logging on first run, all but the first test in captains-service.test.js are skipped using the xtest() function. As you implement each service function, remove the 'x' from xtest to change it to test() and enable that test for validation.

## Code Quality and Configuration

### ESLint Configuration

The project uses ESLint with the Airbnb style guide and Prettier integration for consistent code formatting and quality enforcement.

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

Notable rule customizations: console logging is enabled for debugging, unused variables are allowed during exercise development, and disabled tests are permitted to support the progressive test activation pattern.

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

VSCode automatically fixes ESLint violations and formats code on save using Prettier, providing immediate feedback and maintaining code quality without manual intervention.

### Jest Debugging Configuration

A launch configuration enables debugging Jest tests directly from VSCode with breakpoint support and integrated terminal output.

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

## Dependencies and Tooling

### Production Dependencies

| Package | Version | Purpose |
| --- | --- | --- |
| axios | ^1.9.0 | Promise-based HTTP client for API requests |
| json-server | ^1.0.0-beta.15 | RESTful mock API server using JSON file as data source |

### Development Dependencies

| Package | Version | Purpose |
| --- | --- | --- |
| @babel/preset-env | ^7.29.5 | Babel preset for transpiling modern JavaScript to compatible syntax |
| eslint | ^8.57.1 | JavaScript code quality and style linter |
| eslint-config-airbnb | ^19.0.4 | Airbnb's ESLint configuration preset |
| eslint-config-prettier | ^9.1.2 | ESLint configuration disabling rules conflicting with Prettier |
| eslint-plugin-import | ^2.32.0 | ESLint plugin validating import/export syntax |
| eslint-plugin-jest | ^29.15.2 | ESLint plugin for Jest-specific linting rules |
| jest | ^30.4.2 | Test framework and runner with assertion library |
| jest-watch-typeahead | ^3.0.1 | Jest watch mode plugin enabling typeahead filtering |
| prettier | ^3.8.3 | Code formatter ensuring consistent style across files |

---
*Generated by Forge Wiki · 2026-06-18*