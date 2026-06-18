# ali1092-SC/js-pairing-exercises

> JavaScript pairing exercises focused on API data transformation, sorting, and merging with Jest tests and a mock JSON server.

## Overview

This repository provides a starting point for JavaScript pairing exercises focused on reading from a mock API and then sorting, transforming, and merging data to meet test expectations. The project includes a complete test suite with Jest, a working mock API client wrapping axios, and a JSON server that serves mock captain and ship data.

### Key Features

- Mock API client (apiClient.js) using axios for promise-based data access
- JSON server providing captains and ships mock data
- Jest test framework with watch mode for test-driven development
- ESLint with Airbnb configuration for code quality
- Pre-configured VSCode launch configuration for debugging

## System Architecture

The system consists of three primary layers: a mock data API, an HTTP client layer, and service implementations that transform and combine data. The architecture is designed for educational purposes to teach API interaction, data transformation patterns, and asynchronous JavaScript.

### Component Stack

- Mock API Layer: json-server serving captains and ships endpoints from api/db.json
- HTTP Client: axios-based apiClient configured to localhost:4000
- Service Layer: captains-service.js implementing data transformation logic
- Test Layer: Jest test suite validating all functionality

## Project Structure

### Repository Layout

| Directory | Purpose | Key Files |
| --- | --- | --- |
| / (root) | Configuration and entry point | package.json, README.md, .eslintrc.json |
| src/ | Application source code and tests | apiClient.js, captains-service.js, *.test.js |
| api/ | Mock API data storage | db.json |
| .vscode/ | VSCode development configuration | launch.json, settings.json |

### Complete File Listing

- .eslintrc.json - ESLint configuration with Airbnb preset
- .vscode/launch.json - Jest debugging configuration
- .vscode/settings.json - Auto-formatting and linting settings
- README.md - Project documentation
- WIKI.md - Generated wiki documentation
- package.json - Dependencies and NPM scripts
- package-lock.json - Locked dependency versions
- api/db.json - Mock data (captains and ships)
- src/apiClient.js - Axios HTTP client wrapper
- src/apiClient.test.js - API client verification tests
- src/captains-service.js - Service implementation (stub)
- src/captains-service.test.js - Service functionality tests

## Mock API Data Structure

The mock API serves two primary collections: captains and ships. These are related through captain.ship referencing ship.id.

### Captains Endpoint

Returns array of 4 captain objects, each containing id, first name, last name, age, and ship ID reference.

| Field | Type | Example | Description |
| --- | --- | --- | --- |
| id | string | SQ2WI | Unique captain identifier |
| first | string | Jack | Captain's first name |
| last | string | Sparrow | Captain's last name |
| age | number | 48 | Captain's age in years |
| ship | string | BC13V | Foreign key to ships.id |

### Ships Endpoint

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

The apiClient module wraps axios and configures it to communicate with the mock JSON server running on localhost:4000. It provides a thin abstraction layer for HTTP requests.

### Implementation

```javascript
import axios from 'axios';

axios.defaults.baseURL = 'http://localhost:4000';

export default axios;
```

### API Client Tests

Three verification tests ensure the API client is properly configured and can communicate with both endpoints:

- Configuration test: Verifies baseURL is set to localhost:4000
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

The test suite defines six functions to be implemented, with the first test active and the rest marked as skipped (xtest) to be progressively enabled:

| Function Name | Input | Output | Expected Behavior | Test Status |
| --- | --- | --- | --- | --- |
| getCaptains | none | Promise<Captain[]> | Fetch all captains from API | Active |
| firstNames | none | Promise<string[]> | Extract and return captain first names in original order | Skipped (xtest) |
| firstNamesSorted | none | Promise<string[]> | Extract first names and sort alphabetically | Skipped (xtest) |
| totalAge | none | Promise<number> | Calculate sum of all captain ages (179) | Skipped (xtest) |
| captainBio | captainId: string | Promise<CaptainBio> | Merge captain and ship data for single captain | Skipped (xtest) |
| captainsWithShipNamesBySize | none | Promise<CaptainWithShip[]> | All captains with ship names sorted by crew count ascending | Skipped (xtest) |

### Test Data Examples

Expected outputs from test suite:

```javascript
// firstNames expected output
['Jack', 'Malcolm', 'Jean Luc', 'Han']

// firstNamesSorted expected output
['Han', 'Jack', 'Jean Luc', 'Malcolm']

// totalAge expected output
179

// captainBio('R6TZN') expected output
{
  id: 'R6TZN',
  firstName: 'Malcolm',
  lastName: 'Reynolds',
  shipId: 'V7B8T',
  shipName: 'Serenity'
}

// captainsWithShipNamesBySize expected output (sorted by crew count ascending)
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

## Development Workflow

The project uses npm scripts to manage the development lifecycle. Two processes must run simultaneously: the mock API server and the Jest test runner.

### NPM Scripts

| Script | Command | Purpose |
| --- | --- | --- |
| api | npm run api | Start json-server on port 4000 serving api/db.json |
| api:stop | npm run api:stop | Terminate all json-server processes |
| test | npm test | Start Jest in watch mode with verbose output |

### Execution Steps

1. Start the mock API server: npm run api
2. In a separate terminal, start the test suite: npm test
3. Tests run in watch mode and automatically rerun on file save
4. Implement functions in src/captains-service.js to make tests pass
5. Progressively enable skipped tests by removing 'x' from xtest to test

### VSCode Integration

The project includes VSCode configuration for enhanced development experience:

- launch.json: Provides 'Jest All' debug configuration for running all tests with breakpoint support
- settings.json: Enables automatic ESLint fixing and Prettier formatting on save

## Code Quality Configuration

### Linting and Formatting

The project enforces consistent code style using ESLint with Airbnb configuration and Prettier for automatic formatting.

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

### Configuration Details

- Extends Airbnb style guide with Prettier compatibility
- Jest plugin enables jest-specific linting rules
- Console logging permitted for debugging
- Unused variables allowed during development
- ESLint auto-fix on save via VSCode settings
- Prettier formats code on save automatically

## Dependencies

### Production Dependencies

| Package | Version | Purpose |
| --- | --- | --- |
| axios | ^1.9.0 | Promise-based HTTP client for API requests |
| json-server | ^1.0.0-beta.15 | Mock REST API server for development |

### Development Dependencies

| Package | Version | Purpose |
| --- | --- | --- |
| @babel/preset-env | ^7.29.5 | Babel preset for modern JavaScript transpilation |
| eslint | ^8.57.1 | JavaScript linting tool |
| eslint-config-airbnb | ^19.0.4 | Airbnb JavaScript style guide for ESLint |
| eslint-config-prettier | ^9.1.2 | Disables ESLint rules conflicting with Prettier |
| jest | ^30.4.2 | JavaScript testing framework |
| jest-watch-typeahead | ^3.0.1 | Jest watch plugin for filtering tests by filename or test name |
| prettier | ^3.8.3 | Code formatter |

## Jest Configuration

Jest is configured for Node environment with enhanced watch plugins and default reporter.

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

### Configuration Details

- Test Environment: Node.js (not jsdom) for server-side testing
- Default Reporter: Standard Jest output format
- Watch Plugins: Typeahead filtering for both filenames and test names during watch mode

---
*Generated by Forge Wiki · 2026-06-18*