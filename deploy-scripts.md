以下为部署脚本

```dockerfile
docker pull ghcr.io/indexical-metrics-measure-advisory/watchmen-web-client:${version}
docker tag ghcr.io/indexical-metrics-measure-advisory/watchmen-web-client:${version} docker-all.repo.ebaotech.com/indexical-metrics-measure-advisory/watchmen-web-client:${version}
docker push docker-all.repo.ebaotech.com/indexical-metrics-measure-advisory/watchmen-web-client:${version}

docker pull ghcr.io/indexical-metrics-measure-advisory/watchmen-matryoshka-doll:${version}
docker tag ghcr.io/indexical-metrics-measure-advisory/watchmen-matryoshka-doll:${version} docker-all.repo.ebaotech.com/indexical-metrics-measure-advisory/watchmen-matryoshka-doll:${version}
docker push docker-all.repo.ebaotech.com/indexical-metrics-measure-advisory/watchmen-matryoshka-doll:${version}

docker pull ghcr.io/indexical-metrics-measure-advisory/watchmen-matryoshka-dqc:${version}
docker tag ghcr.io/indexical-metrics-measure-advisory/watchmen-matryoshka-dqc:${version} docker-all.repo.ebaotech.com/indexical-metrics-measure-advisory/watchmen-matryoshka-dqc:${version}
docker push docker-all.repo.ebaotech.com/indexical-metrics-measure-advisory/watchmen-matryoshka-dqc:${version}
```



