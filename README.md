# PostgreSQL Monitoring Stack

Production-ready monitoring solution for PostgreSQL using Prometheus, Grafana, and Loki.

## 🏗️ Architecture
```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│ PostgreSQL  │────▶│   Postgres   │────▶│ Prometheus  │
│             │     │   Exporter   │     │             │
└─────────────┘     └──────────────┘     └──────┬──────┘
                                                 │
┌─────────────┐     ┌──────────────┐            │
│ Linux Host  │────▶│     Node     │────────────┤
│             │     │   Exporter   │            │
└─────────────┘     └──────────────┘            │
                                                 ▼
┌─────────────┐                          ┌─────────────┐
│ PostgreSQL  │────▶│     Loki     │────▶│   Grafana   │
│    Logs     │     │              │     │             │
└─────────────┘     └──────────────┘     └─────────────┘
```

## 📋 Prerequisites

- Docker & Docker Compose installed
- PostgreSQL instance running
- Monitoring user created in PostgreSQL

## 🚀 Quick Start

### 1. Clone the repository
```bash
git clone <your-repo-url>
cd monitoring-stack
```

### 2. Configure environment
```bash
cp .env.example .env
# Edit .env with your PostgreSQL credentials
nano .env
```

### 3. Start the stack
```bash
docker-compose up -d
```

### 4. Access services
- Grafana: http://localhost:3000 (admin/your-password)
- Prometheus: http://localhost:9090
- Loki: http://localhost:3100

## 📊 Metrics Collected

### PostgreSQL Metrics
- Connection count & limits
- Transaction rates
- Query performance
- Replication lag
- Database size
- Cache hit ratio

### System Metrics
- CPU usage
- Memory usage
- Disk I/O
- Network traffic

## 📝 Logs Collected

- PostgreSQL error logs
- Slow query logs
- Connection logs
- Checkpoint logs

## 🔧 Configuration

### Adding new PostgreSQL instances

Edit `prometheus/prometheus.yml`:
```yaml
scrape_configs:
  - job_name: 'postgres_prod'
    static_configs:
      - targets: ['postgres_exporter:9187']
```

## 📚 Documentation

- [Prometheus Configuration](prometheus/README.md)
- [Grafana Dashboards](grafana/README.md)
- [Alert Rules](prometheus/alerts/README.md)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📄 License

MIT License

## 👤 Author

Your Name - DBA transitioning to DevOps
