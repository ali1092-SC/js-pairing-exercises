# ali1092-SC/js-pairing-exercises

> JavaScript pairing exercises focused on API data transformation, sorting, and merging with Jest tests and a mock JSON server.

## Overview

This repository provides a starting point for JavaScript pairing exercises focused on reading from a mock API and then sorting, transforming, and merging data to meet test expectations. The project includes a complete test suite with Jest, a working mock API client wrapping axios, and a JSON server serving mock captain and ship data.

### Purpose

The exercises are designed to teach asynchronous JavaScript patterns, HTTP client usage, data transformation logic, and test-driven development through practical API integration challenges. Learners work with a mock API client to fetch data, then implement service functions that sort, filter, merge, and transform the data to pass progressive Jest tests.

### Key Features

- Mock API client (apiClient.js) using axios for promise-based data access
- JSON server providing captains and ships mock data on port 4000
- Jest test framework with watch mode for test-driven development
- ESLint with Airbnb configuration for code quality enforcement
- Pre-configured VSCode launch configuration for debugging Jest tests
- Progressive exercise structure with skipped tests to enable incremental completion

## Getting Started

1. Start the mock API: npm run api
2. Start the tests: npm test (Jest runs in watch mode and reruns automatically on file changes)
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
| captainBio | captainId: string | Promise<CaptainBio> | Merge captain and ship data for single captain by ID; returns firstName, lastName, shipId, shipName | Skipped (xtest) |
| captainsWithShipNamesBySize | none | Promise<CaptainWithShip[]> | All captains with ship names sorted by crew count ascending (smallest to largest) | Skipped (xtest) |

### Test Specifications

- getCaptains: Returns 4 captain objects with id, first, last, age, and ship fields
- firstNames: Returns ['Jack', 'Malcolm', 'Jean Luc', 'Han'] in original API order
- firstNamesSorted: Returns ['Han', 'Jack', 'Jean Luc', 'Malcolm'] alphabetically sorted
- totalAge: Returns 179 (sum of 48 + 34 + 64 + 33)
- captainBio: For captainId 'R6TZN', returns {id: 'R6TZN', firstName: 'Malcolm', lastName: 'Reynolds', shipId: 'V7B8T', shipName: 'Serenity'}
- captainsWithShipNamesBySize: Returns captains sorted by ship crewCount in ascending order with ship names replacing ship IDs

## NPM Scripts and Configuration

| Script | Command | Purpose |
| --- | --- | --- |
| test | jest --watch --verbose | Run Jest in watch mode with verbose output; automatically reruns tests on file changes |
| api | json-server --port 4000 ./api/db.json | Start JSON server on port 4000 serving mock data from api/db.json |
| api:stop | pkill -f 'json-server' || true | Terminate the running JSON server process |

### Dependencies

| Dependency | Version | Purpose |
| --- | --- | --- |
| axios | ^1.9.0 | HTTP client for API requests |
| json-server | ^1.0.0-beta.15 | Mock REST API server |
| jest | ^30.4.2 | Testing framework and test runner |
| eslint | ^8.57.1 | JavaScript linting for code quality |
| @babel/preset-env | ^7.29.5 | Babel preset for ES2015+ transpilation |
| prettier | ^3.8.3 | Code formatter for consistent style |

### Jest Configuration

- testEnvironment: node - Runs tests in Node.js environment
- watchPlugins: jest-watch-typeahead - Enables filename and test name filtering in watch mode
- reporters: default - Uses Jest's default test reporter

## Development Environment

### VSCode Configuration

The project includes pre-configured VSCode settings for debugging and code quality. The launch.json provides a Jest debugging configuration, and settings.json enables automatic ESLint fixing and Prettier formatting on save.

- launch.json: 'Jest All' debug configuration runs Jest with --runInBand and --watchAll=true flags for step-by-step debugging
- settings.json: eslint.autoFixOnSave and editor.formatOnSave enabled for automatic code cleanup
- Editor applies ESLint fixes and Prettier formatting on every file save

### ESLint Rules

ESLint configuration extends Airbnb preset with Prettier compatibility and Jest-specific rules.

| Rule | Setting | Purpose |
| --- | --- | --- |
| no-console | off | Allow console logging for debugging |
| no-unused-vars | off | Permit unused variables during development |
| import/prefer-default-export | off | Allow named exports without default exports |
| jest/no-disabled-tests | off | Allow skipped tests (xtest) for progressive exercises |
| jest/no-focused-tests | off | Allow focused tests (test.only) |
| jest/no-identical-title | error | Prevent duplicate test names |
| jest/valid-expect | error | Enforce valid Jest expect assertions |

## Exercise Workflow

The pairing exercise follows a test-driven development approach with progressive difficulty. Start with the getCaptains function and progressively enable skipped tests as each function is implemented.

### Step-by-Step Process

1. Ensure npm run api is running in a separate terminal to serve mock data on port 4000
2. Run npm test to start Jest in watch mode
3. Implement getCaptains() in src/captains-service.js to fetch captains from the API
4. Verify getCaptains test passes
5. Remove 'x' from xtest('captain first names'...) to enable the firstNames test
6. Implement firstNames() to extract captain first names in original order
7. Repeat for each remaining xtest, enabling and implementing one function at a time
8. Final implementation should have all 6 service functions working and all tests passing

### Implementation Hints

- Use apiClient.get('/captains') and apiClient.get('/ships') to fetch data from the mock API
- Both API calls return promises that resolve with response.data arrays
- For captainBio(), fetch both captains and ships, then find the matching ship for the given captain ID
- For captainsWithShipNamesBySize(), join captain and ship data, then sort by ship.crewCount in ascending order
- Leverage array methods: map(), filter(), sort(), reduce() for data transformation
- Use async/await or .then() chains to handle promise-based API calls

---
*Generated by Forge Wiki · 2026-06-18*