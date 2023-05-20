# helm-charts
Collective Helm Charts from my Various Open-Source Projects

[![Lint and Test Charts](https://github.com/nathanielvarona/helm-charts/actions/workflows/ci.yml/badge.svg)](https://github.com/nathanielvarona/helm-charts/actions/workflows/ci.yml)
[![Release Charts](https://github.com/nathanielvarona/helm-charts/actions/workflows/release.yml/badge.svg)](https://github.com/nathanielvarona/helm-charts/actions/workflows/release.yml)
[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/pritunl-slack-app)](https://artifacthub.io/packages/search?repo=pritunl-slack-app)

## Usage

```bash
helm repo add nathanielvarona http://nathaniel.varona.dev/helm-charts/
helm repo update
helm install nathanielvarona/<APP CHART>
```