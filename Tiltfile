k8s_yaml(kustomize('kubernetes/tilt'))
k8s_yaml('kubernetes/base/db.yaml')
k8s_yaml('kubernetes/base/push.yaml')
k8s_yaml('kubernetes/base/kube-state-metrics.yaml')

k8s_resource(
  objects=['db:Service'],
  new_name='db'
)

local_resource(
    name='prometheus', resource_deps=['db'],
    serve_cmd='kubectl -n prometheus port-forward svc/db 9090:9090',
    links=["http://localhost:9090"]
)

local_resource(
    name='pushgateway', resource_deps=['push'],
    serve_cmd='kubectl -n prometheus port-forward svc/push 9091:9091',
    links=["http://localhost:9091"]
)
