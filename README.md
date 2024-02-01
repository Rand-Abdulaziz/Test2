# Test2
name: SonarCloud Analysis

on:
  push:
    branches:
      - main

jobs:
  sonarcloud:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up JDK
        uses: actions/setup-java@v2
        with:
          distribution: 'adopt'
          java-version: '11'

      - name: SonarCloud Scan
        uses: sonarsource/sonarcloud-github-action@v1
        with:
          projectKey: ${{ secrets.SONAR_PROJECT_KEY }}
          organization: ${{ secrets.SONAR_ORGANIZATION }}
          token: ${{ secrets.SONAR_TOKEN }}
