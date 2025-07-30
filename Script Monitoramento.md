#!/bin/bash

URL="http://localhost"
LOG="/var/log/monitoramento.log"
DATA=$(date "+%d/%m/%Y %H:%M:%S")
STATUS=$(curl -s -o /dev/null -w "%{http_code}" $URL)

if [ "$STATUS" -ne 200 ]; then
  echo "$DATA - Site FORA DO AR - Código $STATUS" >> $LOG
  curl -H "Content-Type: application/json" \
       -X POST \
       -d "{\"content\": \"🚨 Site fora do ar! Código: $STATUS em $DATA\"}" \
       https://discord.com/api/webhooks/XXXXXXXXXXXXXXXX
else
  echo "$DATA - Site ONLINE - Código $STATUS" >> $LOG
fi
