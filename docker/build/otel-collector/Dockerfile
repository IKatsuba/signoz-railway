FROM signoz/signoz-otel-collector:v0.111.34

# Copy configuration files
COPY docker/otel-collector-config.yaml /etc/otel-collector-config.yaml
COPY common/signoz/otel-collector-opamp-config.yaml /etc/manager-config.yaml

# Set environment variables
ENV OTEL_RESOURCE_ATTRIBUTES="host.name=signoz-host,os.type=linux" \
  LOW_CARDINAL_EXCEPTION_GROUPING=false

# Expose ports
EXPOSE 4317 4318

# Set command
CMD ["--config=/etc/otel-collector-config.yaml", \
  "--manager-config=/etc/manager-config.yaml", \
  "--copy-path=/var/tmp/collector-config.yaml", \
  "--feature-gates=-pkg.translator.prometheus.NormalizeName"] 