# pritunl-slack-app

Pritunl Slack App Helm Chart

## Installation

### Repository Setup and Update

```bash
helm repo add nathanielvarona http://nathaniel.varona.dev/helm-charts/
helm repo update
```

### App Deployment

#### Basic Use _(for Mocking/Testing)_

```bash
helm install nathanielvarona/pritunl-slack-app --generate-name
```

#### Install with Custom Values Override

```bash
cat <<EOF | helm install pritunl-slack-app nathanielvarona/pritunl-slack-app \
  --create-namespace --namespace pritunl-slack-app \
  --values -

replicaCount: 2
image:
  repository: nathanielvarona/pritunl-slack-app
  pullPolicy: IfNotPresent
  tag: "0.1.7"
env:
  credentials:
    PRITUNL_BASE_URL: https://vpn.enterprise-domain.tld/
    PRITUNL_API_SECRET: XXXX
    PRITUNL_API_TOKEN: XXXX
    SLACK_SIGNING_SECRET: XXXX
    SLACK_BOT_TOKEN: XXXX
ingress:
  enabled: true
  className: "nginx"
  hosts:
    - host: vpn-slack-app.enterprise-domain.tld
      paths:
        - path: /
          pathType: ImplementationSpecific
EOF
```

Or values in a file

```bash
helm install pritunl-slack-app nathanielvarona/pritunl-slack-app \
  --create-namespace --namespace pritunl-slack-app \
  --values pritunl-slack-app-custom-values-override.yaml
```
