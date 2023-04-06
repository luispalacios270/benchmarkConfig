# Lighthouse Benchmark GitHub Action Tester

This project is designed to test the integration of a GitHub Action with a Lighthouse benchmark. Lighthouse is an open-source, automated tool for improving the quality of web pages by measuring their performance, accessibility, best practices, and SEO. This project helps ensure that your GitHub Action can run a Lighthouse benchmark and provide valuable insights into your web application.

## Getting Started

To get started with this project, follow these steps:

1. Fork this repository to your GitHub account.
2. Set up your GitHub Action with Lighthouse by following the instructions provided in the next section.

### Prerequisites

- A GitHub account
- A web application to test (either hosted locally or online)

## GitHub Action Setup

1. In your forked repository, create a new file in the `.github/workflows` directory named `lighthouse.yml`.
2. Add the following configuration to your `lighthouse.yml` file:

```yaml
name: Lighthouse Benchmark

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  lighthouse:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout
      uses: actions/checkout@v2

    - name: Setup Node.js
      uses: actions/setup-node@v2
      with:
        node-version: 14

    - name: Install dependencies
      run: npm ci

    - name: Run Lighthouse
      uses: treosh/lighthouse-ci-action@v8
      with:
        urls: 'https://your-web-app-url-here/'
        uploadArtifacts: true
        temporaryPublicStorage: true
