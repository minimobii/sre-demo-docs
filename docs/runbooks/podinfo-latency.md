Алерт: PodInfoHighLatency
Severity: critical
Impact: Графики в Grafana показывают, что p95 времени ответа превышает 1 секунду. Пользователи ждут ответа дольше.


1. Проверить статус подов:
   kubectl -n podinfo get pods -l app.kubernetes.io/name=podinfo
2. Посмотреть логи проблемного пода
kubectl -n podinfo logs -l app.kubernetes.io/name=podinfo --tail=50
3. Проверить не упало ли восстановление
kubectl -n podinfo describe pod -l app.kubernetes.io/name=podinfo | grep -i "ready"

Шаги восстановления.
1. перезапустить деплоймент
kubectl -n podinfo rollout restart deployment podinfo
2. Проверить восстановление

Закройте инцидент и оставьте след
В статусе инцидента зафиксируйте время переключения, что помогло, что делали. Создайте задачу: «проверить причину 5xx и обновить playbook/мониторинг»
