---
forge-wiki: true
generated-at: 2026-06-18T14:18:56.741Z
generator-version: "1.0"
repo: ali1092-SC/js-pairing-exercises
branch: main
section-count: 15
---

```forge-wiki-data
{"repoName":"ali1092-SC/js-pairing-exercises","repoNote":"JavaScript pairing exercises teaching API integration, data transformation, and asynchronous patterns through Jest tests and a mock JSON server.","lastUpdatedAt":"2024-01-01T00:00:00Z","sections":[{"id":"overview","title":"Overview","parentId":null,"sourceFiles":[{"path":"README.md","lineStart":1,"lineEnd":20}],"content":[{"type":"paragraph","text":"This repository provides a starting point for JavaScript pairing exercises focused on reading from a mock API and sorting, transforming, and merging data to meet test expectations. The project includes a complete test suite with Jest, a working mock API client wrapping axios, and a JSON server serving mock captain and ship data."},{"type":"paragraph","text":"The exercises are designed to teach asynchronous JavaScript patterns, HTTP client usage, data transformation logic, and test-driven development through practical API integration challenges. Learners work with a mock API client to fetch data, then implement service functions that sort, filter, merge, and transform the data to pass progressive Jest tests."},{"type":"heading","level":2,"text":"Key Features"},{"type":"unorderedList","items":["Mock API client (apiClient.js) using axios for promise-based data access","JSON server providing captains and ships mock data on port 4000","Jest test framework with watch mode for test-driven development","ESLint with Airbnb configuration for code quality enforcement","Pre-configured VSCode launch configuration for debugging Jest tests","Progressive exercise structure with skipped tests to enable incremental completion"]}]},{"id":"getting-started","title":"Getting Started","parentId":null,"sourceFiles":[{"path":"README.md","lineStart":21,"lineEnd":45}],"content":[{"type":"paragraph","text":"Follow these steps to set up and begin working on the exercises:"},{"type":"orderedList","items":["Start the mock API with npm run api","Start the tests with npm test (Jest runs in watch mode and reruns automatically on file changes)","Complete the service implementations in captains-service.js to make tests pass","Remove the 'x' prefix from xtest definitions to progressively enable skipped tests"]},{"type":"paragraph","text":"The apiClient.test.js tests are complete and verify that the mock API is running and correctly configured. The mock API client must be running to support the captains-service.js functions."}]},{"id":"system-architecture","title":"System Architecture","parentId":null,"sourceFiles":[{"path":"README.md","lineStart":46,"lineEnd":65},{"path":"package.json","lineStart":1,"lineEnd":35}],"content":[{"type":"paragraph","text":"The system consists of three primary layers: a mock data API, an HTTP client layer, and service implementations that transform and combine data. The architecture is designed for educational purposes to teach API interaction, data transformation patterns, and asynchronous JavaScript fundamentals."},{"type":"heading","level":2,"text":"Component Stack"},{"type":"unorderedList","items":["Mock API Layer: json-server serving captains and ships endpoints from api/db.json on port 4000","HTTP Client: axios-based apiClient configured to localhost:4000","Service Layer: captains-service.js implementing data transformation logic","Test Layer: Jest test suite validating all functionality"]},{"type":"heading","level":2,"text":"Data Flow Architecture"},{"type":"diagram","title":"API Data Transformation Flow","nodes":[{"id":"json-server","label":"JSON Server (Port 4000)","type":"database"},{"id":"api-client","label":"apiClient (Axios)","type":"orchestrator"},{"id":"captains-service","label":"captains-service.js","type":"orchestrator"},{"id":"jest-tests","label":"Jest Tests","type":"output"}],"edges":[{"from":"json-server","to":"api-client","label":"GET /captains, /ships"},{"from":"api-client","to":"captains-service","label":"Promise data"},{"from":"captains-service","to":"jest-tests","label":"Transformed data"}]}]},{"id":"project-structure","title":"Project Structure","parentId":null,"sourceFiles":[{"path":"README.md","lineStart":66,"lineEnd":90}],"content":[{"type":"heading","level":2,"text":"Repository Layout"},{"type":"table","headers":["Directory","Purpose","Key Files"],"rows":[["/ (root)","Configuration and entry point","package.json, README.md, .eslintrc.json, WIKI.md"],["src/","Application source code and tests","apiClient.js, captains-service.js, *.test.js"],["api/","Mock API data storage","db.json"],[".vscode/","VSCode development configuration","launch.json, settings.json"]]},{"type":"heading","level":2,"text":"File Manifest"},{"type":"unorderedList","items":[".eslintrc.json - ESLint configuration with Airbnb preset and Jest plugin support",".vscode/launch.json - Jest debugging configuration for VSCode with runInBand and watchAll flags",".vscode/settings.json - Auto-formatting and linting settings for VSCode with eslint.autoFixOnSave enabled","README.md - Project documentation and getting started guide","WIKI.md - Generated wiki documentation","package.json - Dependencies and NPM scripts (test, api, api:stop)","package-lock.json - Locked dependency versions for reproducible installs","api/db.json - Mock data for captains and ships collections with 4 records each","src/apiClient.js - Axios HTTP client wrapper with baseURL configuration","src/apiClient.test.js - API client verification tests (3 tests, all active)","src/captains-service.js - Service implementation stub for data transformation","src/captains-service.test.js - Service functionality tests with progressive skipping"]}]},{"id":"npm-scripts-configuration","title":"NPM Scripts & Configuration","parentId":null,"sourceFiles":[{"path":"package.json","lineStart":8,"lineEnd":24}],"content":[{"type":"heading","level":2,"text":"Available Scripts"},{"type":"table","headers":["Script","Command","Purpose"],"rows":[["test","jest --watch --verbose","Run Jest in watch mode with verbose output, reruns on file changes"],["api","json-server --port 4000 ./api/db.json","Start mock JSON server on port 4000 serving api/db.json"],["api:stop","pkill -f 'json-server' || true","Stop the running JSON server process"]]},{"type":"heading","level":2,"text":"Jest Configuration"},{"type":"code","language":"json","content":"\"jest\": {\n  \"testEnvironment\": \"node\",\n  \"reporters\": [\"default\"],\n  \"watchPlugins\": [\n    \"jest-watch-typeahead/filename\",\n    \"jest-watch-typeahead/testname\"\n  ]\n}"}]},{"id":"dependencies","title":"Dependencies","parentId":null,"sourceFiles":[{"path":"package.json","lineStart":25,"lineEnd":50}],"content":[{"type":"heading","level":2,"text":"Production Dependencies"},{"type":"table","headers":["Package","Version","Purpose"],"rows":[["axios","^1.9.0","HTTP client library for making API requests"],["json-server","^1.0.0-beta.15","Mock JSON API server for development and testing"]]},{"type":"heading","level":2,"text":"Development Dependencies"},{"type":"unorderedList","items":["@babel/preset-env ^7.29.5 - Babel preset for ES2015+ transpilation","eslint ^8.57.1 - JavaScript linter","eslint-config-airbnb ^19.0.4 - Airbnb ESLint configuration","eslint-config-prettier ^9.1.2 - Disable ESLint rules conflicting with Prettier","eslint-plugin-import ^2.32.0 - ESLint plugin for import statements","eslint-plugin-jest ^29.15.2 - ESLint plugin for Jest","jest ^30.4.2 - Testing framework","jest-watch-typeahead ^3.0.1 - Watch mode plugin for interactive filtering","prettier ^3.8.3 - Code formatter"]}]},{"id":"eslint-configuration","title":"ESLint Configuration","parentId":null,"sourceFiles":[{"path":".eslintrc.json","lineStart":1,"lineEnd":25}],"content":[{"type":"paragraph","text":"The project uses ESLint with Airbnb configuration extended with Prettier rules. Jest globals are enabled to support test functions."},{"type":"code","language":"json","content":"{\n  \"extends\": [\"airbnb\", \"prettier\"],\n  \"plugins\": [\"jest\"],\n  \"rules\": {\n    \"no-console\": \"off\",\n    \"no-unused-vars\": \"off\",\n    \"import/prefer-default-export\": \"off\",\n    \"linebreak-style\": \"off\",\n    \"jest/no-disabled-tests\": \"off\",\n    \"jest/no-focused-tests\": \"off\",\n    \"jest/no-identical-title\": \"error\",\n    \"jest/prefer-to-have-length\": \"warn\",\n    \"jest/valid-expect\": \"error\"\n  },\n  \"env\": {\n    \"jest/globals\": true\n  }\n}"},{"type":"paragraph","text":"Key customizations include disabling no-console to allow debug logging, and disabling no-unused-vars and no-focused-tests to support the exercise workflow where test functions may be initially unused or focused."}]},{"id":"vscode-configuration","title":"VSCode Configuration","parentId":null,"sourceFiles":[{"path":".vscode/launch.json","lineStart":1,"lineEnd":20},{"path":".vscode/settings.json","lineStart":1,"lineEnd":9}],"content":[{"type":"heading","level":2,"text":"Debug Configuration"},{"type":"paragraph","text":"The launch.json provides a Jest All configuration for debugging all tests in VSCode."},{"type":"code","language":"json","content":"{\n  \"version\": \"0.2.0\",\n  \"configurations\": [\n    {\n      \"type\": \"node\",\n      \"request\": \"launch\",\n      \"name\": \"Jest All\",\n      \"program\": \"${workspaceFolder}/node_modules/.bin/jest\",\n      \"args\": [\"--runInBand\", \"--watchAll=true\"],\n      \"console\": \"integratedTerminal\",\n      \"internalConsoleOptions\": \"neverOpen\",\n      \"disableOptimisticBPs\": true\n    }\n  ]\n}"},{"type":"heading","level":2,"text":"Editor Settings"},{"type":"paragraph","text":"VSCode is configured to automatically fix ESLint issues and format code on save using Prettier."},{"type":"code","language":"json","content":"{\n  \"eslint.autoFixOnSave\": true,\n  \"editor.formatOnSave\": true,\n  \"editor.codeActionsOnSave\": {\n    \"source.fixAll.eslint\": \"explicit\"\n  }\n}"}]},{"id":"mock-api-data","title":"Mock API Data Structure","parentId":null,"sourceFiles":[{"path":"api/db.json","lineStart":1,"lineEnd":50}],"content":[{"type":"paragraph","text":"The mock API serves two primary collections: captains and ships. These are related through captain.ship referencing ship.id. The JSON server runs on port 4000 and provides RESTful endpoints for both collections."},{"type":"heading","level":2,"text":"Captains Collection"},{"type":"paragraph","text":"Returns array of 4 captain objects, each containing id, first name, last name, age, and ship ID reference."},{"type":"table","headers":["Field","Type","Example","Description"],"rows":[["id","string","SQ2WI","Unique captain identifier"],["first","string","Jack","Captain's first name"],["last","string","Sparrow","Captain's last name"],["age","number","48","Captain's age in years"],["ship","string","BC13V","Foreign key reference to ships.id"]]},{"type":"heading","level":2,"text":"Ships Collection"},{"type":"paragraph","text":"Returns array of 4 ship objects, each containing id, name, crew count, and propulsion type."},{"type":"table","headers":["Field","Type","Example","Description"],"rows":[["id","string","DRPHT","Unique ship identifier"],["name","string","USS Enterprise NCC-1701-D","Official ship name"],["crewCount","number","1012","Number of crew members"],["propulsion","string","Warp Drive","Propulsion system type"]]},{"type":"heading","level":2,"text":"Sample Data"},{"type":"code","language":"json","content":"{\n  \"captains\": [\n    {\n      \"id\": \"SQ2WI\",\n      \"first\": \"Jack\",\n      \"last\": \"Sparrow\",\n      \"age\": 48,\n      \"ship\": \"BC13V\"\n    },\n    {\n      \"id\": \"R6TZN\",\n      \"first\": \"Malcolm\",\n      \"last\": \"Reynolds\",\n      \"age\": 34,\n      \"ship\": \"V7B8T\"\n    },\n    {\n      \"id\": \"UXWPK\",\n      \"first\": \"Jean Luc\",\n      \"last\": \"Picard\",\n      \"age\": 64,\n      \"ship\": \"DRPHT\"\n    },\n    {\n      \"id\": \"KZUC8\",\n      \"first\": \"Han\",\n      \"last\": \"Solo\",\n      \"age\": 33,\n      \"ship\": \"1M6GB\"\n    }\n  ],\n  \"ships\": [\n    {\n      \"id\": \"DRPHT\",\n      \"name\": \"USS Enterprise NCC-1701-D\",\n      \"crewCount\": 1012,\n      \"propulsion\": \"Warp Drive\"\n    },\n    {\n      \"id\": \"BC13V\",\n      \"name\": \"Black Pearl\",\n      \"crewCount\": 44,\n      \"propulsion\": \"Wind\"\n    },\n    {\n      \"id\": \"1M6GB\",\n      \"name\": \"Millenium Falcon\",\n      \"crewCount\": 2,\n      \"propulsion\": \"Hyperdrive\"\n    },\n    {\n      \"id\": \"V7B8T\",\n      \"name\": \"Serenity\",\n      \"crewCount\": 5,\n      \"propulsion\": \"Radion/Accelerator Core\"\n    }\n  ]\n}"}]},{"id":"api-client-layer","title":"API Client Layer","parentId":null,"sourceFiles":[{"path":"src/apiClient.js","lineStart":1,"lineEnd":5}],"content":[{"type":"paragraph","text":"The apiClient module wraps axios and configures it to communicate with the mock JSON server running on localhost:4000. It provides a thin abstraction layer for HTTP requests, enabling promise-based asynchronous data fetching."},{"type":"heading","level":2,"text":"Implementation"},{"type":"code","language":"javascript","content":"import axios from 'axios';\n\naxios.defaults.baseURL = 'http://localhost:4000';\n\nexport default axios;"}]},{"id":"api-client-tests","title":"API Client Tests","parentId":null,"sourceFiles":[{"path":"src/apiClient.test.js","lineStart":1,"lineEnd":30}],"content":[{"type":"paragraph","text":"Three verification tests ensure the API client is properly configured and can communicate with both endpoints. All tests in apiClient.test.js are active (not skipped) to verify that the mock API is running correctly."},{"type":"heading","level":2,"text":"Test Suite"},{"type":"orderedList","items":["apiClient configuration test - Verifies baseURL is set to http://localhost:4000","api/captains endpoint test - Confirms GET /captains returns status 200 with 4 captain records","api/ships endpoint test - Confirms GET /ships returns status 200 with 4 ship records"]},{"type":"code","language":"javascript","content":"import apiClient from './apiClient';\n\ntest('apiClient is configured to point to api', () => {\n  expect(apiClient.defaults.baseURL).toBe('http://localhost:4000');\n});\n\ntest('api/captains endpoint works', async () => {\n  expect.assertions(2);\n  try {\n    const response = await apiClient.get('/captains');\n    expect(response.status).toBe(200);\n    expect(response.data).toHaveLength(4);\n  } catch (error) {\n    console.log('Be sure you have started the mock api: npm run api');\n    throw error;\n  }\n});\n\ntest('api/ships endpoint works', async () => {\n  expect.assertions(2);\n  try {\n    const response = await apiClient.get('/ships');\n    expect(response.status).toBe(200);\n    expect(response.data).toHaveLength(4);\n  } catch (error) {\n    console.log('Be sure you have started the mock api: npm run api');\n    throw error;\n  }\n});"}]},{"id":"captains-service-layer","title":"Captains Service Layer","parentId":null,"sourceFiles":[{"path":"src/captains-service.js","lineStart":1,"lineEnd":5}],"content":[{"type":"paragraph","text":"The captains-service module is the primary implementation target for the exercises. It imports the apiClient and implements functions that fetch, transform, merge, and aggregate captain and ship data."},{"type":"heading","level":2,"text":"Current Implementation"},{"type":"code","language":"javascript","content":"import apiClient from './apiClient';\n\nexport const getCaptains = () => null;"},{"type":"paragraph","text":"The getCaptains function is stubbed and must be implemented to call apiClient.get('/captains') and return the captain data."}]},{"id":"captains-service-tests","title":"Captains Service Tests","parentId":null,"sourceFiles":[{"path":"src/captains-service.test.js","lineStart":1,"lineEnd":92}],"content":[{"type":"paragraph","text":"The captains-service.test.js file contains a progressive test suite. The first test is active, while the remaining tests are skipped with the 'xtest' prefix to be incrementally enabled as exercises are completed."},{"type":"heading","level":2,"text":"Active Tests"},{"type":"orderedList","items":["returns data from captains endpoint - Verifies getCaptains() returns all 4 captain records with correct first captain data"]},{"type":"heading","level":2,"text":"Skipped Tests (xtest)"},{"type":"orderedList","items":["captain first names - Extract first names array: ['Jack', 'Malcolm', 'Jean Luc', 'Han']","captain first names sorted alphabetically - Extract and sort first names: ['Han', 'Jack', 'Jean Luc', 'Malcolm']","captain combined total age - Sum all captain ages: 179","captain and ship combined for given captain id - Merge captain and ship data by ID with transformed field names","Captains sorted by ship size - Join captains with ship data and sort by crew count ascending, replacing ship ID with ship name"]},{"type":"code","language":"javascript","content":"import * as captainsService from './captains-service';\n\ntest('returns data from captains endpoint', async () => {\n  const captains = await captainsService.getCaptains();\n  const firstCaptain = {\n    id: 'SQ2WI',\n    first: 'Jack',\n    last: 'Sparrow',\n    age: 48,\n    ship: 'BC13V'\n  };\n\n  expect(captains).toHaveLength(4);\n  expect(captains[0]).toEqual(firstCaptain);\n});\n\nxtest('captain first names', async () => {\n  const expectedNames = ['Jack', 'Malcolm', 'Jean Luc', 'Han'];\n  const firstNames = await captainsService.firstNames();\n\n  expect(firstNames).toEqual(expectedNames);\n});\n\nxtest('captain first names sorted alphabetically', async () => {\n  const expectedNames = ['Han', 'Jack', 'Jean Luc', 'Malcolm'];\n  const firstNamesSorted = await captainsService.firstNamesSorted();\n\n  expect(firstNamesSorted).toEqual(expectedNames);\n});\n\nxtest('captain combined total age', async () => {\n  const expectedTotalAge = 179;\n  const totalAge = await captainsService.totalAge();\n\n  expect(totalAge).toEqual(expectedTotalAge);\n});\n\nxtest('captain and ship combined for given captain id', async () => {\n  const expectedData = {\n    id: 'R6TZN',\n    firstName: 'Malcolm',\n    lastName: 'Reynolds',\n    shipId: 'V7B8T',\n    shipName: 'Serenity'\n  };\n  const captainShipData = await captainsService.captainBio('R6TZN');\n\n  expect(captainShipData).toEqual(expectedData);\n});\n\nxtest('Captains sorted by ship size', async () => {\n  const expectedData = [\n    {\n      id: 'KZUC8',\n      first: 'Han',\n      last: 'Solo',\n      age: 33,\n      ship: 'Millenium Falcon'\n    },\n    {\n      id: 'R6TZN',\n      first: 'Malcolm',\n      last: 'Reynolds',\n      age: 34,\n      ship: 'Serenity'\n    },\n    {\n      id: 'SQ2WI',\n      first: 'Jack',\n      last: 'Sparrow',\n      age: 48,\n      ship: 'Black Pearl'\n    },\n    {\n      id: 'UXWPK',\n      first: 'Jean Luc',\n      last: 'Picard',\n      age: 64,\n      ship: 'USS Enterprise NCC-1701-D'\n    }\n  ];\n  const captainsWithShipNamesBySize = await captainsService.captainsWithShipNamesBySize();\n\n  expect(captainsWithShipNamesBySize).toEqual(expectedData);\n});"}]},{"id":"exercise-progression","title":"Exercise Progression Guide","parentId":null,"sourceFiles":[{"path":"src/captains-service.test.js","lineStart":1,"lineEnd":92}],"content":[{"type":"paragraph","text":"The exercises follow a progressive difficulty curve, building on each other to teach data manipulation patterns. Each implementation teaches a new JavaScript concept."},{"type":"heading","level":2,"text":"Exercise Sequence"},{"type":"orderedList","items":["getCaptains() - Basic API call using promise-based axios client, tests that the API integration works","firstNames() - Array mapping, extract captain.first from all records, tests array transformation","firstNamesSorted() - Array sorting, combine map and sort operations, teaches sort ordering and comparators","totalAge() - Array reduction, sum all captain.age values, teaches reduce pattern for aggregation","captainBio(id) - Data merging by ID, join captain and ship records by foreign key, tests nested data fetching and object composition","captainsWithShipNamesBySize() - Complex join and sort, merge all captains with ships, sort by crewCount, replace ID with name, teaches complex data transformation"]},{"type":"paragraph","text":"To enable the next exercise, locate the xtest in captains-service.test.js and remove the 'x' prefix to convert it to a regular test. Then implement the corresponding function in captains-service.js."}]},{"id":"data-transformation-patterns","title":"Data Transformation Patterns","parentId":null,"sourceFiles":[{"path":"src/captains-service.test.js","lineStart":15,"lineEnd":92}],"content":[{"type":"paragraph","text":"The exercises teach fundamental JavaScript data transformation patterns essential for modern web development."},{"type":"heading","level":2,"text":"Core Patterns Covered"},{"type":"unorderedList","items":["Array.map() - Transform array elements, taught through firstNames() and captainBio()","Array.sort() - Order array elements, taught through firstNamesSorted() and captainsWithShipNamesBySize()","Array.reduce() - Aggregate array values, taught through totalAge()","Promise chains - Async data fetching, taught through getCaptains() and multi-step transformations","Object merging - Combine data from multiple sources, taught through captainBio() and captainsWithShipNamesBySize()","Array.find() - Search for specific elements, implicitly used in join operations","Complex composition - Combining multiple patterns, taught through final captainsWithShipNamesBySize()"]}]}]}
```

# ali1092-SC/js-pairing-exercises

> JavaScript pairing exercises teaching API integration, data transformation, and asynchronous patterns through Jest tests and a mock JSON server.

## Overview

This repository provides a starting point for JavaScript pairing exercises focused on reading from a mock API and sorting, transforming, and merging data to meet test expectations. The project includes a complete test suite with Jest, a working mock API client wrapping axios, and a JSON server serving mock captain and ship data.

The exercises are designed to teach asynchronous JavaScript patterns, HTTP client usage, data transformation logic, and test-driven development through practical API integration challenges. Learners work with a mock API client to fetch data, then implement service functions that sort, filter, merge, and transform the data to pass progressive Jest tests.

### Key Features

- Mock API client (apiClient.js) using axios for promise-based data access
- JSON server providing captains and ships mock data on port 4000
- Jest test framework with watch mode for test-driven development
- ESLint with Airbnb configuration for code quality enforcement
- Pre-configured VSCode launch configuration for debugging Jest tests
- Progressive exercise structure with skipped tests to enable incremental completion

## Getting Started

Follow these steps to set up and begin working on the exercises:

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

### Available Scripts

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

## ESLint Configuration

The project uses ESLint with Airbnb configuration extended with Prettier rules. Jest globals are enabled to support test functions.

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

Key customizations include disabling no-console to allow debug logging, and disabling no-unused-vars and no-focused-tests to support the exercise workflow where test functions may be initially unused or focused.

## VSCode Configuration

### Debug Configuration

The launch.json provides a Jest All configuration for debugging all tests in VSCode.

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Jest All",
      "program": "${workspaceFolder}/node_modules/.bin/jest",
      "args": ["--runInBand", "--watchAll=true"],
      "console": "integratedTerminal",
      "internalConsoleOptions": "neverOpen",
      "disableOptimisticBPs": true
    }
  ]
}
```

### Editor Settings

VSCode is configured to automatically fix ESLint issues and format code on save using Prettier.

```json
{
  "eslint.autoFixOnSave": true,
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  }
}
```

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

## API Client Tests

Three verification tests ensure the API client is properly configured and can communicate with both endpoints. All tests in apiClient.test.js are active (not skipped) to verify that the mock API is running correctly.

### Test Suite

1. apiClient configuration test - Verifies baseURL is set to http://localhost:4000
2. api/captains endpoint test - Confirms GET /captains returns status 200 with 4 captain records
3. api/ships endpoint test - Confirms GET /ships returns status 200 with 4 ship records

```javascript
import apiClient from './apiClient';

test('apiClient is configured to point to api', () => {
  expect(apiClient.defaults.baseURL).toBe('http://localhost:4000');
});

test('api/captains endpoint works', async () => {
  expect.assertions(2);
  try {
    const response = await apiClient.get('/captains');
    expect(response.status).toBe(200);
    expect(response.data).toHaveLength(4);
  } catch (error) {
    console.log('Be sure you have started the mock api: npm run api');
    throw error;
  }
});

test('api/ships endpoint works', async () => {
  expect.assertions(2);
  try {
    const response = await apiClient.get('/ships');
    expect(response.status).toBe(200);
    expect(response.data).toHaveLength(4);
  } catch (error) {
    console.log('Be sure you have started the mock api: npm run api');
    throw error;
  }
});
```

## Captains Service Layer

The captains-service module is the primary implementation target for the exercises. It imports the apiClient and implements functions that fetch, transform, merge, and aggregate captain and ship data.

### Current Implementation

```javascript
import apiClient from './apiClient';

export const getCaptains = () => null;
```

The getCaptains function is stubbed and must be implemented to call apiClient.get('/captains') and return the captain data.

## Captains Service Tests

The captains-service.test.js file contains a progressive test suite. The first test is active, while the remaining tests are skipped with the 'xtest' prefix to be incrementally enabled as exercises are completed.

### Active Tests

1. returns data from captains endpoint - Verifies getCaptains() returns all 4 captain records with correct first captain data

### Skipped Tests (xtest)

1. captain first names - Extract first names array: ['Jack', 'Malcolm', 'Jean Luc', 'Han']
2. captain first names sorted alphabetically - Extract and sort first names: ['Han', 'Jack', 'Jean Luc', 'Malcolm']
3. captain combined total age - Sum all captain ages: 179
4. captain and ship combined for given captain id - Merge captain and ship data by ID with transformed field names
5. Captains sorted by ship size - Join captains with ship data and sort by crew count ascending, replacing ship ID with ship name

```javascript
import * as captainsService from './captains-service';

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

xtest('captain first names', async () => {
  const expectedNames = ['Jack', 'Malcolm', 'Jean Luc', 'Han'];
  const firstNames = await captainsService.firstNames();

  expect(firstNames).toEqual(expectedNames);
});

xtest('captain first names sorted alphabetically', async () => {
  const expectedNames = ['Han', 'Jack', 'Jean Luc', 'Malcolm'];
  const firstNamesSorted = await captainsService.firstNamesSorted();

  expect(firstNamesSorted).toEqual(expectedNames);
});

xtest('captain combined total age', async () => {
  const expectedTotalAge = 179;
  const totalAge = await captainsService.totalAge();

  expect(totalAge).toEqual(expectedTotalAge);
});

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

## Exercise Progression Guide

The exercises follow a progressive difficulty curve, building on each other to teach data manipulation patterns. Each implementation teaches a new JavaScript concept.

### Exercise Sequence

1. getCaptains() - Basic API call using promise-based axios client, tests that the API integration works
2. firstNames() - Array mapping, extract captain.first from all records, tests array transformation
3. firstNamesSorted() - Array sorting, combine map and sort operations, teaches sort ordering and comparators
4. totalAge() - Array reduction, sum all captain.age values, teaches reduce pattern for aggregation
5. captainBio(id) - Data merging by ID, join captain and ship records by foreign key, tests nested data fetching and object composition
6. captainsWithShipNamesBySize() - Complex join and sort, merge all captains with ships, sort by crewCount, replace ID with name, teaches complex data transformation

To enable the next exercise, locate the xtest in captains-service.test.js and remove the 'x' prefix to convert it to a regular test. Then implement the corresponding function in captains-service.js.

## Data Transformation Patterns

The exercises teach fundamental JavaScript data transformation patterns essential for modern web development.

### Core Patterns Covered

- Array.map() - Transform array elements, taught through firstNames() and captainBio()
- Array.sort() - Order array elements, taught through firstNamesSorted() and captainsWithShipNamesBySize()
- Array.reduce() - Aggregate array values, taught through totalAge()
- Promise chains - Async data fetching, taught through getCaptains() and multi-step transformations
- Object merging - Combine data from multiple sources, taught through captainBio() and captainsWithShipNamesBySize()
- Array.find() - Search for specific elements, implicitly used in join operations
- Complex composition - Combining multiple patterns, taught through final captainsWithShipNamesBySize()

---
*Generated by Forge on 2026-06-18*