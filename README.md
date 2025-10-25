# ddbog-agregando-ia-observabilidad
Agregando IA a la Observabilidad

## Desplegando la app de Opentelemetry
git clone https://github.com/open-telemetry/opentelemetry-demo.git
cd opentelemetry-demo/
docker compose up --force-recreate --remove-orphans --detach


### Arquitectura
https://opentelemetry.io/docs/demo/architecture/

### Acceso grafana
Web store: http://157.137.225.33:8080/
Grafana: http://157.137.225.33:8080/grafana/
Load Generator UI: http://157.137.225.33:8080/loadgen/
Jaeger UI: http://157.137.225.33:8080/jaeger/ui/
Tracetest UI: http://157.137.225.33:11633/, only when using make run-tracetesting
Flagd configurator UI: http://157.137.225.33:8080/feature


### Referencias
https://opentelemetry.io/docs/demo/docker-deployment/

## Gemini

docker network create devops

docker pull node:22-alpine
docker run -it --name gemini --rm --network devops --entrypoint sh node:22-alpine
apk add vim
npm install -g @google/gemini-cli
cd /tmp
mkdir .gemini
```json
cat .gemini/settings.json 
{
  "security": {
    "auth": {
      "selectedType": "gemini-api-key"
    }
  },

`
  "mcpServers": {
    "grafana": {
      "type": "sse",
      "url": "http://grafana:8000/sse"
    }
  }
}
```

export GEMINI_API_KEY="THIS_IS_AN_EXAMPLE"
#gemini
gemini -m gemini-2.0-flash

### Referencias
https://geminicli.com/docs/tools/mcp-server/
https://modelcontextprotocol.io/docs/getting-started/intro
https://github.com/google-gemini/gemini-cli



## Grafana MCP
docker pull mcp/grafana

docker run --rm --network devops --name grafana -i -e GRAFANA_URL=http://157.137.225.33:8080/grafana -e GRAFANA_SERVICE_ACCOUNT_TOKEN=THIS_IS_AN_EXAMPLE mcp/grafana 

### Referencias
https://medium.com/@syed_usman_ahmed/setup-the-grafana-mcp-server-on-docker-1d77e22ecf9a
https://github.com/grafana/mcp-grafana
