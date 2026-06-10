# PeakPick

PeakPick là repo trung tâm để truy cập nhanh các repository con của project microservices. Repo này dùng Git submodule để gắn reference tới từng repo con.

## Demo

https://peakpick.tech

## Bối Cảnh Phát Triển

Ban đầu project được làm theo hướng service-based trong cùng một codebase để nhóm dễ phát triển và kiểm thử luồng nghiệp vụ. Sau khi các service chính đã ổn định, nhóm migrate thử sang mô hình microservices bằng cách tách từng service, frontend và deployment thành các repository độc lập.

Repo này đóng vai trò trung tâm để gom reference tới toàn bộ repository con sau khi migrate.

## Danh Sách Repository

| Phần | Repository |
|---|---|
| Frontend | [peakpick-frontend](https://github.com/tadyuh76/peakpick-frontend) |
| API Gateway | [peakpick-api-gateway](https://github.com/tadyuh76/peakpick-api-gateway) |
| Identity Service | [peakpick-identity-service](https://github.com/tadyuh76/peakpick-identity-service) |
| Catalog Service | [peakpick-catalog-service](https://github.com/tadyuh76/peakpick-catalog-service) |
| Order Service | [peakpick-order-service](https://github.com/tadyuh76/peakpick-order-service) |
| Slot Service | [peakpick-slot-service](https://github.com/tadyuh76/peakpick-slot-service) |
| Store Operations Service | [peakpick-store-ops-service](https://github.com/tadyuh76/peakpick-store-ops-service) |
| Inventory Service | [peakpick-inventory-service](https://github.com/tadyuh76/peakpick-inventory-service) |
| Notification Service | [peakpick-notification-service](https://github.com/tadyuh76/peakpick-notification-service) |
| Analytics Service | [peakpick-analytics-service](https://github.com/tadyuh76/peakpick-analytics-service) |
| Deployment | [peakpick-deployment](https://github.com/tadyuh76/peakpick-deployment) |

## Cách Clone Kèm Repository Con

```bash
git clone --recurse-submodules https://github.com/tadyuh76/peakpick.git
```

Nếu đã clone repo trung tâm trước đó:

```bash
git submodule update --init --recursive
```

## Tổng Quan Runtime

```text
peakpick-frontend
-> peakpick-api-gateway
-> identity / catalog / order / slot / store-ops / inventory / notification / analytics

Order, Slot, Store Ops, Inventory, Notification, Analytics
-> RabbitMQ events

Mỗi service có PostgreSQL database riêng.
```

## Cách Chạy Project

Clone repo trung tâm kèm submodule, sau đó chạy Docker Compose trong repo deployment:

```bash
cd peakpick-deployment
docker compose up --build
```

Phần deploy production nằm trong [peakpick-deployment](https://github.com/tadyuh76/peakpick-deployment).
