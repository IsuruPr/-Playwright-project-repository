# Singlish to Sinhala Translation - Playwright Test Automation

A comprehensive Playwright test automation suite for validating Singlish to Sinhala conversion/translation functionality. This project includes extensive test cases covering positive scenarios, negative edge cases, and UI behavior validation.

## Project Overview

**Project Name:** Singlish to Sinhala Translation Test Suite  
**Framework:** Playwright (E2E Testing)  
**Test Language:** JavaScript  
**Test Coverage:** 
- 24 Positive Test Cases (happy path scenarios)
- 10 Negative Test Cases (robustness validation)
- 1 UI Behavior Test (real-time updates)

## Features

- **Comprehensive Test Coverage**: Tests spanning multiple domains including daily language usage, punctuation handling, mixed language scenarios, and edge cases
- **Multiple Grammar Focus Areas**: Simple sentences, compound sentences, questions, commands, tenses, and more
- **Input Variation Testing**: Short (S), Medium (M), and Long (L) input length validation
- **HTML Reporting**: Automatic test report generation with detailed execution metrics
- **Cross-browser Support**: Tests configured to run on Chromium, Firefox, and WebKit
- **Performance Metrics**: Execution time tracking for each test case
- **CSV & JSON Results**: Test results exported in multiple formats for analysis

## Project Structure

```
.
├── tests/
│   └── singlish-to-sinhala.spec.js      # Main test specification file with 32 test cases
├── playwright-report/                    # Generated HTML test reports
├── test-results/                         # Generated test artifacts and traces
├── playwright.config.js                  # Playwright configuration
├── package.json                          # Project dependencies and scripts
├── test-results.json                     # Test results in JSON format
├── test-results.csv                      # Test results in CSV format
├── .gitignore                            # Git ignore rules
└── README.md                             # This file
```

## Installation

### Prerequisites

- **Node.js** (v16 or higher)  
- **npm** (comes with Node.js)

### Setup Steps

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd Assigment
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```
   This will install:
   - `@playwright/test` - Playwright test framework
   - `@types/node` - TypeScript type definitions for Node.js

3. **Verify installation**
   ```bash
   npx playwright --version
   ```

## Running the Tests

### Run All Tests
```bash
npm test
```

### Run Tests in Headed Mode (browser visible)
```bash
npx playwright test --headed
```

### Run Tests for a Specific Browser
```bash
npx playwright test --project=chromium
npx playwright test --project=firefox
npx playwright test --project=webkit
```

### Run a Single Test File
```bash
npx playwright test tests/singlish-to-sinhala.spec.js
```

### Run Tests Matching a Pattern
```bash
npx playwright test -g "Simple Sentence"
```

### Debug Mode (opens Playwright Inspector)
```bash
npx playwright test --debug
```

### Generate and View HTML Report
```bash
npx playwright test
npx playwright show-report
```

## Test Categories

### Positive Test Cases (Pos_Fun_0001-0024)
- Simple, compound, and complex sentences
- Interrogative questions and imperative commands
- Positive and negative grammatical forms
- Past, present, and future tenses
- Plural usage and polite forms
- Common greetings and informal phrases
- Mixed Singlish and English text
- Punctuation and formatting handling
- Currency format and special characters

### Negative Test Cases (Neg_Fun_0001-0010)
- Joined words without spaces
- Mixed language ambiguity
- Incorrect spelling/typos
- Very long input stress testing
- Special characters only
- English-only text
- Repeated words patterns
- Incomplete sentences
- Mixed case text
- Uncommon slang

### UI Behavior Tests (Pos_UI_0001)
- Real-time Sinhala output updates while typing
- Usability flow validation

## Configuration

### playwright.config.js
The configuration file includes:
- **testDir**: Tests located in `./tests` directory
- **fullyParallel**: Tests run in parallel for faster execution
- **retries**: Automatic retry on CI environments
- **reporter**: HTML report generation
- **trace**: Captures traces on first retry for debugging
- **projects**: Configured for Chromium, Firefox, and WebKit browsers

### Modifying Base URL
To test against a different application instance, update `playwright.config.js`:
```javascript
use: {
  baseURL: 'http://your-app-url.com',
},
```

## Test Results

After running tests, results are generated in multiple formats:

### HTML Report
- Location: `playwright-report/index.html`
- View with: `npx playwright show-report`
- Contains detailed execution metrics, screenshots, and video traces

### JSON Results
- Location: `test-results.json`
- Machine-readable format for integration with other tools

### CSV Results
- Location: `test-results.csv`
- Spreadsheet-compatible format

## Continuous Integration

For CI/CD pipeline integration, the configuration automatically enables:
- Test retry (2 retries on CI)
- Serial execution (1 worker)
- Fail build on CI if `test.only` is accidentally left in code

Example GitHub Actions integration:
```yaml
- name: Run Playwright tests
  run: npm test

- name: Upload report
  if: always()
  uses: actions/upload-artifact@v3
  with:
    name: playwright-report
    path: playwright-report/
```

## Debugging

### Using Playwright Inspector
```bash
npx playwright test --debug
```
This opens an interactive inspector where you can:
- Step through tests
- Inspect the page
- Execute commands in the console
- Review test logs

### Viewing Test Traces
The configuration captures traces on first retry. View them:
```bash
npx playwright show-trace test-results/trace.zip
```

## Troubleshooting

### Tests fail with "Target page, context or browser has been closed"
- Ensure the application is running
- Check the `baseURL` in playwright.config.js

### No HTML report generated
```bash
npx playwright test
npx playwright show-report
```

### Browser installation issues
```bash
npx playwright install
```

### Clear test artifacts
```bash
rm -rf test-results playwright-report
```

## Performance Metrics

The test suite tracks execution time for each test case:
- **Average execution time**: ~2-3 seconds per test
- **Total suite runtime**: ~60-120 seconds depending on browser and system
- **Parallel execution**: 4+ test workers recommended for optimal performance

## Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| @playwright/test | ^1.58.1 | Playwright test framework |
| @types/node | ^25.1.0 | TypeScript type definitions |

## Contributing

1. Ensure new tests follow the existing naming convention: `[Pos/Neg]_[Category]_[Number]`
2. Add comprehensive test descriptions
3. Include test metadata (type, grammar focus, input length)
4. Run `npm test` before submitting
5. Ensure HTML report shows all tests passing

## License

ISC

## Support

For issues or questions:
1. Check the Playwright documentation: https://playwright.dev
2. Review existing test cases for examples
3. Enable debug mode: `npx playwright test --debug`

## Additional Resources

- [Playwright Documentation](https://playwright.dev)
- [Playwright API Reference](https://playwright.dev/docs/api/class-playwrightassertions)
- [Best Practices](https://playwright.dev/docs/best-practices)
- [CI/CD Integration Guide](https://playwright.dev/docs/ci)
