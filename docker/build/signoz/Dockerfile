FROM signoz/signoz:v0.76.2

# Copy configuration files
COPY common/signoz/prometheus.yml /root/config/prometheus.yml
COPY common/dashboards /root/config/dashboards

# Create data directory
RUN mkdir -p /var/lib/signoz

# Set environment variables
ENV SIGNOZ_ALERTMANAGER_PROVIDER=signoz \
  SIGNOZ_TELEMETRYSTORE_CLICKHOUSE_DSN=tcp://clickhouse:9000 \
  SIGNOZ_SQLSTORE_SQLITE_PATH=/var/lib/signoz/signoz.db \
  DASHBOARDS_PATH=/root/config/dashboards \
  STORAGE=clickhouse \
  GODEBUG=netdns=go \
  TELEMETRY_ENABLED=true \
  DEPLOYMENT_TYPE=docker-standalone-amd

# Expose ports
EXPOSE 8080

# Health check
HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
  CMD wget --spider -q localhost:8080/api/v1/health

# Set command
CMD ["--config=/root/config/prometheus.yml", "--use-logs-new-schema=true", "--use-trace-new-schema=true"] 