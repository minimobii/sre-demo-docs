# Runbook: Высокая задержка PodInfo

## Симптомы
- Сработал алерт `PodInfoHighLatency` в Alertmanager.
- Графики в Grafana показывают, что p95 времени ответа превышает 1 секунду.

## Быстрые проверки
1. Проверить статус подов:
   ```bash
   kubectl -n podinfo get pods -l app.kubernetes.io/name=podinfo
