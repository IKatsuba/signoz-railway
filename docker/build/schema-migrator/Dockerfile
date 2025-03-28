FROM signoz/signoz-schema-migrator:v0.111.34

# Set environment variables
# ENV DSN=tcp://clickhouse:9000
# ARG DSN

CMD exec /app/schema-migrator sync --dsn=$DSN --up=