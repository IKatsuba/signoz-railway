FROM signoz/signoz-schema-migrator:v0.111.34

# Set environment variables
# ENV DSN=tcp://clickhouse:9000
ARG DSN

# Create entrypoint script
RUN echo '#!/bin/sh\n\
  if [ "$1" = "sync" ]; then\n\
  exec /app/schema-migrator sync --dsn=\$DSN --up=\n\
  elif [ "$1" = "async" ]; then\n\
  exec /app/schema-migrator async --dsn=\$DSN --up=\n\
  else\n\
  echo "Usage: $0 {sync|async}"\n\
  exit 1\n\
  fi' > /entrypoint.sh && chmod +x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
CMD ["sync"] 