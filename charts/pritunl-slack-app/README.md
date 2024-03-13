# pritunl-slack-app

Pritunl Slack App Helm Chart

## Installation

### Repository Setup and Update

```bash
helm repo add nathanielvarona http://nathanielvarona.github.io/helm-charts/
helm repo update
```

### App Deployment

#### Basic Installation
> _For Mocking and Testing only!_

```bash
helm install nathanielvarona/pritunl-slack-app --generate-name
```

#### With Custom Override Values Deployment
> _In a Development or Production Environment._

```bash
helm install pritunl-slack-app nathanielvarona/pritunl-slack-app \
  --create-namespace --namespace pritunl-slack-app --version 0.1.4 \
  --values - <<EOF

replicaCount: 2
image:
  repository: nathanielvarona/pritunl-slack-app
  pullPolicy: IfNotPresent
  tag: "0.1.8"
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
  tls:
    - secretName: vpn-slack-app.enterprise-domain.tld-tls-secret
      hosts:
        - vpn-slack-app.enterprise-domain.tld

EOF
```

_Or use the custom override values from the values file._

```bash
helm install pritunl-slack-app nathanielvarona/pritunl-slack-app \
  --create-namespace --namespace pritunl-slack-app \
  --values pritunl-slack-app-custom-override-values.yaml
```
