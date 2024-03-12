version: '3.8'

services:
  blackbox_exporter:
    image: prom/blackbox-exporter:latest
    container_name: blackbox_exporter
    ports:
      - "9115:9115"
    command:
      - "--config.file=/etc/blackbox_exporter/config.yml"
    volumes:
      - blackbox_config:/etc/blackbox_exporter
    networks:
      - blackbox_network
    restart: always

networks:
  blackbox_network:
    driver: bridge

volumes:
  blackbox_config:
