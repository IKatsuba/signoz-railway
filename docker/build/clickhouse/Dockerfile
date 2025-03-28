FROM clickhouse/clickhouse-server:24.1.2-alpine

# Copy configuration files
COPY common/clickhouse/config.xml /etc/clickhouse-server/config.xml
COPY common/clickhouse/users.xml /etc/clickhouse-server/users.xml
COPY common/clickhouse/custom-function.xml /etc/clickhouse-server/custom-function.xml
COPY common/clickhouse/cluster.xml /etc/clickhouse-server/config.d/cluster.xml
COPY common/clickhouse/user_scripts /var/lib/clickhouse/user_scripts/

# Create data directory
RUN mkdir -p /var/lib/clickhouse

# Set permissions
RUN chown -R clickhouse:clickhouse /var/lib/clickhouse

# Expose ports
EXPOSE 9000 8123 9181

# Health check
HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
  CMD wget --spider -q 0.0.0.0:8123/ping

# Set ulimits
RUN ulimit -n 262144

USER clickhouse 