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

### NPM Scripts

| Script | Command | Description |
| --- | --- | --- |
| test | jest --watch --verbose | Run Jest test suite in watch mode with verbose output |
| api | json-server --port 4000 ./api/db.json | Start mock JSON server on port 4000 serving api/db.json |
| api:stop | pkill -f 'json-server' || true | Stop running json-server process |

### Dependencies

### Production Dependencies

| Package | Version | Purpose |
| --- | --- | --- |
| axios | ^1.9.0 | HTTP client for API requests with promise support |
| json-server | ^1.0.0-beta.15 | Mock REST API server for development and testing |

### Development Dependencies

| Package | Version | Purpose |
| --- | --- | --- |
| @babel/preset-env | ^7.29.5 | Babel preset for modern JavaScript transpilation |
| eslint | ^8.57.1 | JavaScript linter for code quality |
| eslint-config-airbnb | ^19.0.4 | Airbnb ESLint configuration ruleset |
| eslint-config-prettier | ^9.1.2 | Prettier integration with ESLint |
| jest | ^30.4.2 | JavaScript test framework and runner |
| jest-watch-typeahead | ^3.0.1 | Jest watch mode plugin for filtering tests by filename or testname |
| prettier | ^3.8.3 | Code formatter |

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
| firstNames | none | Promise<string[]> | Extract and return captain first names in original order | Skipped |
| firstNamesSorted | none | Promise<string[]> | Extract first names and sort alphabetically | Skipped |
| totalAge | none | Promise<number> | Calculate combined total age of all captains (179) | Skipped |
| captainBio | captainId: string | Promise<CaptainBio> | Merge captain and ship data by captain id, transforming field names | Skipped |
| captainsWithShipNamesBySize | none | Promise<Captain[]> | Return captains sorted by ship crew size ascending, replacing ship id with ship name | Skipped |

### Test Expectations

#### getCaptains()

Returns all 4 captains from the API with unmodified structure. Test verifies array length is 4 and first captain matches Jack Sparrow (id: SQ2WI).

#### firstNames()

Extracts first names in order: ['Jack', 'Malcolm', 'Jean Luc', 'Han']

#### firstNamesSorted()

Sorts first names alphabetically: ['Han', 'Jack', 'Jean Luc', 'Malcolm']

#### totalAge()

Sums all captain ages: 48 + 34 + 64 + 33 = 179

#### captainBio(captainId)

Merges captain and ship data by matching captain.ship to ship.id and returns transformed object with firstName, lastName, shipId, and shipName fields. Example for Malcolm Reynolds: {id: 'R6TZN', firstName: 'Malcolm', lastName: 'Reynolds', shipId: 'V7B8T', shipName: 'Serenity'}

#### captainsWithShipNamesBySize()

Returns all captains sorted by associated ship crew count ascending, with ship id replaced by ship name. Serenity (5 crew) first, USS Enterprise (1012 crew) last.

## Development Configuration

### ESLint Configuration

ESLint is configured with Airbnb ruleset extended with Prettier for code formatting. Jest plugin is enabled with relaxed rules for disabled and focused tests. Console logging is allowed for debugging purposes.

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

### VSCode Debug Configuration

Jest launch configuration provides integrated terminal debugging with runInBand and watchAll flags to run tests sequentially and in watch mode. Windows compatibility is handled with explicit jest.bin path.

### VSCode Editor Settings

Auto-formatting is enabled on save with both ESLint and Prettier integration. Editor applies ESLint fixes automatically via code actions when files are saved.

```json
{
  "eslint.autoFixOnSave": true,
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  }
}
```

## Jest Test Framework

Jest is configured as the test runner with Node testEnvironment. Watch plugins enable filtering tests by filename or testname during development. Test files are automatically discovered with .test.js suffix.

### Jest Configuration

```json
"jest": {
  "testEnvironment": "node",
  "reporters": [
    "default"
  ],
  "watchPlugins": [
    "jest-watch-typeahead/filename",
    "jest-watch-typeahead/testname"
  ]
}
```

The test suite is run in watch mode via `npm test`, which automatically reruns affected tests when source files are modified. Jest watch plugins allow filtering by test filename or test name during interactive watch sessions.

## Test Structure

### API Client Tests

Three tests verify that the API client is properly configured and can successfully communicate with the mock JSON server endpoints. These tests must pass before service layer tests can run.

1. apiClient configuration test - checks baseURL is set to http://localhost:4000
2. Captains endpoint test - verifies GET /captains returns 200 status and 4 records
3. Ships endpoint test - verifies GET /ships returns 200 status and 4 records

All apiClient tests use async/await with explicit assertion counts. Error handling includes helpful messaging to ensure the json-server is started before running tests.

### Captains Service Tests

Six test cases are defined in captains-service.test.js. The first test (getCaptains) is active and enabled. The remaining five tests are prefixed with 'x' (xtest) to skip them initially, allowing incremental completion as each function is implemented.

| Test Name | Line Range | Status | Description |
| --- | --- | --- | --- |
| returns data from captains endpoint | 3-14 | Active | Verifies getCaptains() returns 4 captain objects |
| captain first names | 16-21 | Skipped | Tests firstNames() extraction |
| captain first names sorted alphabetically | 23-28 | Skipped | Tests firstNamesSorted() alphabetic ordering |
| captain combined total age | 30-35 | Skipped | Tests totalAge() summation |
| captain and ship combined for given captain id | 37-48 | Skipped | Tests captainBio() data merge |
| Captains sorted by ship size | 50-80 | Skipped | Tests captainsWithShipNamesBySize() sorting and transformation |

## Data Transformation Patterns

The pairing exercises teach several core data transformation patterns. These patterns are essential for real-world API integration and data processing tasks.

### Extraction Pattern

Extract specific fields from objects in an array using Array.map(). Example: extract first names from captain objects.

### Sorting Pattern

Sort arrays by field value using Array.sort() with custom comparators. Can sort strings alphabetically or numbers numerically.

### Aggregation Pattern

Reduce arrays to single values using Array.reduce(). Example: calculate total age by summing individual captain ages.

### Join/Merge Pattern

Combine data from multiple API endpoints using Array.find() to match records by foreign key. Example: combine captain data with ship data by matching captain.ship to ship.id.

### Field Transformation Pattern

Rename and restructure object properties while merging. Example: transform first/last to firstName/lastName and ship id to shipName when merging captain and ship data.

## Development Workflow

The development workflow is designed for test-driven development with immediate feedback and incremental progress.

### Step 1: Start the Mock API

```bash
npm run api
```

This starts json-server on localhost:4000 serving the captains and ships collections from api/db.json.

### Step 2: Start the Test Suite

```bash
npm test
```

Jest starts in watch mode with verbose output. Initially, the apiClient tests should pass (verifying API connection), while captains-service tests will fail or be skipped.

### Step 3: Implement Functions

Edit src/captains-service.js to implement each required function. As each function is completed and tests pass, unskip the next test by removing the 'x' from xtest.

### Step 4: Verify Incrementally

Jest watch mode automatically reruns affected tests as files are saved. The jest-watch-typeahead plugins allow filtering tests by name during development for focused debugging.

---
*Generated by Forge Wiki · 2026-06-18*