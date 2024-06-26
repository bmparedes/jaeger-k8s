
# Jaeger K8s v1.58 

## Descripcion

Este repositorio contiene la configuración de Jaeger K8s v1.58 en su version de producción, conectado a un Elasticsearch externo y un Prometheus. Esta configuración permite recopilar y analizar datos de rastreo distribuido de aplicaciones en contenedores Kubernetes.

## Componentes:

**Operador Jaeger K8s**: Automatiza la implementación y gestión de Jaeger en Kubernetes.

**Jaeger Collector**: Recopila datos de rastreo de las aplicaciones en contenedores.

**Jaeger Query**: Permite consultar y analizar los datos de rastreo.

**Elasticsearch**: Almacena los datos de rastreo.

**Prometheus**: Exporta métricas de rendimiento de Jaeger.


## Environment Variables


### Query Env
`serviceType: NodePort` 

`nodePort: 30158`
#### metricsStorage:
`type: prometheus`

`server-url: http://prometheus.prometheus.svc:9090/ `

### ingress
`enabled: false`

### Storage
`schedule: "30 3 * * 0"`

`max-traces: 1500`

`server-urls: http://elasticsearch.utilities.svc:9200`

`index-prefix: jaeger-k8s-prod`
## Uso 

Luego de modificar las variables segun los parametros de su entorno proceder a levantar el entorno

`kubectl apply -f cert-manager`

Entrar en la carpeta de operator:
`kubectl apply -f .`

Entrar en el directorio de jaeger: `kubectl apply -f .`
## Links Jaeger

- [Operator for Kubernetes](https://www.jaegertracing.io/docs/1.58/operator/)
- [Service Performance Monitoring](https://www.jaegertracing.io/docs/1.58/spm/)
