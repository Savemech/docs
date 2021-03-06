---
editable: false
---

# Метод create
Создает кластер ClickHouse в указанном каталоге.
 

 
## HTTP-запрос {#https-request}
```
POST https://mdb.api.cloud.yandex.net/managed-clickhouse/v1/clusters
```
 
## Параметры в теле запроса {#body_params}
 
```json 
{
  "folderId": "string",
  "name": "string",
  "description": "string",
  "labels": "object",
  "environment": "string",
  "configSpec": {
    "version": "string",
    "clickhouse": {
      "config": {
        "logLevel": "string",
        "mergeTree": {
          "replicatedDeduplicationWindow": "integer",
          "replicatedDeduplicationWindowSeconds": "integer",
          "partsToDelayInsert": "integer",
          "partsToThrowInsert": "integer",
          "maxReplicatedMergesInQueue": "integer",
          "numberOfFreeEntriesInPoolToLowerMaxSizeOfMerge": "integer",
          "maxBytesToMergeAtMinSpaceInPool": "integer"
        },
        "compression": [
          {
            "method": "string",
            "minPartSize": "string",
            "minPartSizeRatio": "number"
          }
        ],
        "dictionaries": [
          {
            "name": "string",
            "structure": {
              "id": {
                "name": "string"
              },
              "key": {
                "attributes": [
                  {
                    "name": "string",
                    "type": "string",
                    "nullValue": "string",
                    "expression": "string",
                    "hierarchical": true,
                    "injective": true
                  }
                ]
              },
              "rangeMin": {
                "name": "string",
                "type": "string",
                "nullValue": "string",
                "expression": "string",
                "hierarchical": true,
                "injective": true
              },
              "rangeMax": {
                "name": "string",
                "type": "string",
                "nullValue": "string",
                "expression": "string",
                "hierarchical": true,
                "injective": true
              },
              "attributes": [
                {
                  "name": "string",
                  "type": "string",
                  "nullValue": "string",
                  "expression": "string",
                  "hierarchical": true,
                  "injective": true
                }
              ]
            },
            "layout": {
              "type": "string",
              "sizeInCells": "string"
            },

            // `configSpec.clickhouse.config.dictionaries[]` включает только одно из полей `httpSource`, `mysqlSource`, `clickhouseSource`, `mongodbSource`, `postgresqlSource`
            "fixedLifetime": "string",
            "lifetimeRange": {
              "min": "string",
              "max": "string"
            },
            // конец списка возможных полей`configSpec.clickhouse.config.dictionaries[]`

            "httpSource": {
              "url": "string",
              "format": "string"
            },
            "mysqlSource": {
              "db": "string",
              "table": "string",
              "port": "string",
              "user": "string",
              "password": "string",
              "replicas": [
                {
                  "host": "string",
                  "priority": "string",
                  "port": "string",
                  "user": "string",
                  "password": "string"
                }
              ],
              "where": "string",
              "invalidateQuery": "string"
            },
            "clickhouseSource": {
              "db": "string",
              "table": "string",
              "host": "string",
              "port": "string",
              "user": "string",
              "password": "string",
              "where": "string"
            },
            "mongodbSource": {
              "db": "string",
              "collection": "string",
              "host": "string",
              "port": "string",
              "user": "string",
              "password": "string"
            },
            "postgresqlSource": {
              "db": "string",
              "table": "string",
              "hosts": [
                "string"
              ],
              "port": "string",
              "user": "string",
              "password": "string",
              "invalidateQuery": "string",
              "sslMode": "string"
            }
          }
        ],
        "graphiteRollup": [
          {
            "name": "string",
            "patterns": [
              {
                "regexp": "string",
                "function": "string",
                "retention": [
                  {
                    "age": "string",
                    "precision": "string"
                  }
                ]
              }
            ]
          }
        ],
        "maxConnections": "integer",
        "maxConcurrentQueries": "integer",
        "keepAliveTimeout": "integer",
        "uncompressedCacheSize": "integer",
        "markCacheSize": "integer",
        "maxTableSizeToDrop": "integer",
        "maxPartitionSizeToDrop": "integer",
        "builtinDictionariesReloadInterval": "integer",
        "timezone": "string",
        "geobaseUri": "string"
      },
      "resources": {
        "resourcePresetId": "string",
        "diskSize": "string",
        "diskTypeId": "string"
      }
    },
    "zookeeper": {
      "resources": {
        "resourcePresetId": "string",
        "diskSize": "string",
        "diskTypeId": "string"
      }
    },
    "backupWindowStart": {
      "hours": "integer",
      "minutes": "integer",
      "seconds": "integer",
      "nanos": "integer"
    },
    "access": {
      "dataLens": true,
      "webSql": true,
      "metrika": true,
      "serverless": true
    }
  },
  "databaseSpecs": [
    {
      "name": "string"
    }
  ],
  "userSpecs": [
    {
      "name": "string",
      "password": "string",
      "permissions": [
        {
          "databaseName": "string"
        }
      ],
      "settings": {
        "readonly": "integer",
        "allowDdl": true,
        "insertQuorum": "integer",
        "connectTimeout": "integer",
        "receiveTimeout": "integer",
        "sendTimeout": "integer",
        "insertQuorumTimeout": "integer",
        "selectSequentialConsistency": true,
        "maxReplicaDelayForDistributedQueries": "integer",
        "fallbackToStaleReplicasForDistributedQueries": true,
        "replicationAlterPartitionsSync": "integer",
        "distributedProductMode": "string",
        "distributedAggregationMemoryEfficient": true,
        "distributedDdlTaskTimeout": "integer",
        "skipUnavailableShards": true,
        "compile": true,
        "minCountToCompile": "integer",
        "compileExpressions": true,
        "minCountToCompileExpression": "integer",
        "maxBlockSize": "integer",
        "minInsertBlockSizeRows": "integer",
        "minInsertBlockSizeBytes": "integer",
        "maxInsertBlockSize": "integer",
        "minBytesToUseDirectIo": "integer",
        "useUncompressedCache": true,
        "mergeTreeMaxRowsToUseCache": "integer",
        "mergeTreeMaxBytesToUseCache": "integer",
        "mergeTreeMinRowsForConcurrentRead": "integer",
        "mergeTreeMinBytesForConcurrentRead": "integer",
        "maxBytesBeforeExternalGroupBy": "integer",
        "maxBytesBeforeExternalSort": "integer",
        "groupByTwoLevelThreshold": "integer",
        "groupByTwoLevelThresholdBytes": "integer",
        "priority": "integer",
        "maxThreads": "integer",
        "maxMemoryUsage": "integer",
        "maxMemoryUsageForUser": "integer",
        "maxNetworkBandwidth": "integer",
        "maxNetworkBandwidthForUser": "integer",
        "forceIndexByDate": true,
        "forcePrimaryKey": true,
        "maxRowsToRead": "integer",
        "maxBytesToRead": "integer",
        "readOverflowMode": "string",
        "maxRowsToGroupBy": "integer",
        "groupByOverflowMode": "string",
        "maxRowsToSort": "integer",
        "maxBytesToSort": "integer",
        "sortOverflowMode": "string",
        "maxResultRows": "integer",
        "maxResultBytes": "integer",
        "resultOverflowMode": "string",
        "maxRowsInDistinct": "integer",
        "maxBytesInDistinct": "integer",
        "distinctOverflowMode": "string",
        "maxRowsToTransfer": "integer",
        "maxBytesToTransfer": "integer",
        "transferOverflowMode": "string",
        "maxExecutionTime": "integer",
        "timeoutOverflowMode": "string",
        "maxColumnsToRead": "integer",
        "maxTemporaryColumns": "integer",
        "maxTemporaryNonConstColumns": "integer",
        "maxQuerySize": "integer",
        "maxAstDepth": "integer",
        "maxAstElements": "integer",
        "maxExpandedAstElements": "integer",
        "inputFormatValuesInterpretExpressions": true,
        "inputFormatDefaultsForOmittedFields": true,
        "outputFormatJsonQuote_64BitIntegers": true,
        "outputFormatJsonQuoteDenormals": true,
        "lowCardinalityAllowInNativeFormat": true,
        "emptyResultForAggregationByEmptySet": true,
        "httpConnectionTimeout": "integer",
        "httpReceiveTimeout": "integer",
        "httpSendTimeout": "integer",
        "enableHttpCompression": true,
        "sendProgressInHttpHeaders": true,
        "httpHeadersProgressInterval": "integer",
        "addHttpCorsHeader": true
      },
      "quotas": [
        {
          "intervalDuration": "integer",
          "queries": "integer",
          "errors": "integer",
          "resultRows": "integer",
          "readRows": "integer",
          "executionTime": "integer"
        }
      ]
    }
  ],
  "hostSpecs": [
    {
      "zoneId": "string",
      "type": "string",
      "subnetId": "string",
      "assignPublicIp": true,
      "shardName": "string"
    }
  ],
  "networkId": "string",
  "shardName": "string"
}
```

 
Поле | Описание
--- | ---
folderId | **string**<br><p>Обязательное поле. Идентификатор каталога, в котором нужно создать кластер ClickHouse.</p> <p>Максимальная длина строки в символах — 50.</p> 
name | **string**<br><p>Обязательное поле. Имя кластера ClickHouse. Имя должно быть уникальным в каталоге.</p> <p>Максимальная длина строки в символах — 63. Значение должно соответствовать регулярному выражению <code>[a-zA-Z0-9_-]*</code>.</p> 
description | **string**<br><p>Описание кластера ClickHouse.</p> <p>Максимальная длина строки в символах — 256.</p> 
labels | **object**<br><p>Пользовательские метки для кластера ClickHouse как пары <code>key:value</code>. Максимум 64 на ресурс. Например, &quot;project&quot;: &quot;mvp&quot; или &quot;source&quot;: &quot;dictionary&quot;.</p> <p>Не более 64 на ресурс. Максимальная длина строки в символах для каждого ключа — 63. Каждый ключ должен соответствовать регулярному выражению <code>[a-z][-_0-9a-z]*</code>. Максимальная длина строки в символах для каждого значения — 63. Каждое значение должно соответствовать регулярному выражению <code>[-_0-9a-z]*</code>.</p> 
environment | **string**<br><p>Обязательное поле. Среда развертывания кластера ClickHouse.</p> <p>Среда развертывания.</p> <ul> <li>PRODUCTION: Стабильная среда с осторожной политикой обновления: во время регулярного обслуживания применяются только срочные исправления.</li> <li>PRESTABLE: Среда с более агрессивной политикой обновления: новые версии развертываются независимо от обратной совместимости.</li> </ul> 
configSpec | **object**<br><p>Обязательное поле. Конфигурация и ресурсы для хостов, которые должны быть созданы для кластера ClickHouse.</p> 
configSpec.<br>version | **string**<br><p>Версия серверного программного обеспечения ClickHouse.</p> 
configSpec.<br>clickhouse | **object**<br><p>Конфигурация и ресурсы для сервера ClickHouse.</p> 
configSpec.<br>clickhouse.<br>config | **object**<br><p>Конфигурация для сервера ClickHouse.</p> <p>Настройки конфигурации ClickHouse. Подробное описание для каждого набора настроек доступно в <a href="https://clickhouse.yandex/docs/ru/operations/server_settings/settings/">документации ClickHouse</a>.</p> <p>Любые настройки, не перечисленные здесь, не поддерживаются.</p> 
configSpec.<br>clickhouse.<br>config.<br>logLevel | **string**<br><p>Уровень логирования для кластера ClickHouse. Допустимые значения: &quot;TRACE&quot;, &quot;DEBUG&quot;, &quot;INFORMATION&quot;, &quot;WARNING&quot;, &quot;ERROR&quot;. См. описание в <a href="https://clickhouse.yandex/docs/ru/operations/server_settings/settings/#server_settings-logger">документации ClickHouse</a>.</p> 
configSpec.<br>clickhouse.<br>config.<br>mergeTree | **object**<br><p>Параметры движка MergeTree. См. описание в <a href="https://clickhouse.yandex/docs/ru/operations/server_settings/settings/#merge_tree">документации ClickHouse</a>.</p> <p>Настройки движка таблицы MergeTree.</p> 
configSpec.<br>clickhouse.<br>config.<br>mergeTree.<br>replicatedDeduplicationWindow | **integer** (int64)<br><p>Количество блоков хэшей, которые должен хранить ZooKeeper. Смотрите подробное описание в <a href="https://github.com/yandex/ClickHouse/blob/v18.1.0-stable/dbms/src/Storages/MergeTree/MergeTreeSettings.h#L59">ClickHouse sources</a>.</p> 
configSpec.<br>clickhouse.<br>config.<br>mergeTree.<br>replicatedDeduplicationWindowSeconds | **integer** (int64)<br><p>Период времени, в течение которого следует хранить блоки хэшей. См. описание в <a href="https://github.com/yandex/ClickHouse/blob/v18.1.0-stable/dbms/src/Storages/MergeTree/MergeTreeSettings.h#L64">ClickHouse sources</a>.</p> 
configSpec.<br>clickhouse.<br>config.<br>mergeTree.<br>partsToDelayInsert | **integer** (int64)<br>
configSpec.<br>clickhouse.<br>config.<br>mergeTree.<br>partsToThrowInsert | **integer** (int64)<br>
configSpec.<br>clickhouse.<br>config.<br>mergeTree.<br>maxReplicatedMergesInQueue | **integer** (int64)<br>
configSpec.<br>clickhouse.<br>config.<br>mergeTree.<br>numberOfFreeEntriesInPoolToLowerMaxSizeOfMerge | **integer** (int64)<br>
configSpec.<br>clickhouse.<br>config.<br>mergeTree.<br>maxBytesToMergeAtMinSpaceInPool | **integer** (int64)<br>
configSpec.<br>clickhouse.<br>config.<br>compression[] | **object**<br><p>Параметры сжатия для кластера ClickHouse. См. подробное описание в <a href="https://clickhouse.yandex/docs/ru/operations/server_settings/settings/#compression">документации ClickHouse</a>.</p> 
configSpec.<br>clickhouse.<br>config.<br>compression[].<br>method | **string**<br><p>Метод сжатия, используемый для указанной комбинации &quot;min_part_size&quot; и &quot;min_part_size_ratio&quot;.</p> <ul> <li>LZ4: <a href="https://lz4.github.io/lz4/">LZ4 compression algorithm</a>.</li> <li>ZSTD: <a href="https://facebook.github.io/zstd/">Zstandard compression algorithm</a>.</li> </ul> 
configSpec.<br>clickhouse.<br>config.<br>compression[].<br>minPartSize | **string** (int64)<br><p>Минимальный размер части таблицы.</p> <p>Минимальное значение — 1.</p> 
configSpec.<br>clickhouse.<br>config.<br>compression[].<br>minPartSizeRatio | **number** (double)<br><p>Минимальное отношение части к размеру всех данных в таблице.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[] | **object**<br><p>Конфигурация внешних словарей для кластера ClickHouse. См. подробное описание в <a href="https://clickhouse.yandex/docs/ru/query_language/dicts/external_dicts/">документации ClickHouse</a>.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>name | **string**<br><p>Обязательное поле. Имя внешнего словаря.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure | **object**<br>Обязательное поле. Набор атрибутов внешнего словаря. Подробное описание см. в [документации ClickHouse](https://clickhouse.yandex/docs/ru/query_language/dicts/external_dicts_dict_structure/).<br>
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>id | **object**<br><p>Один столбец с числовыми ключами для словаря.</p> <p>Числовой ключ.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>id.<br>name | **string**<br><p>Обязательное поле. Имя числового ключа.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>key | **object**<br><p>Составной ключ для словаря, содержащего один или несколько столбцов с ключами. Подробнее см. в <a href="https://clickhouse.yandex/docs/ru/query_language/dicts/external_dicts_dict_structure/#composite-key">документации ClickHouse</a>.</p> <p>Составной ключ.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>key.<br>attributes[] | **object**<br><p>Обязательное поле. Поля составного ключа.</p> <p>Должен содержать хотя бы один элемент.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>key.<br>attributes[].<br>name | **string**<br><p>Обязательное поле. Имя столбца.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>key.<br>attributes[].<br>type | **string**<br><p>Обязательное поле. Тип столбца.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>key.<br>attributes[].<br>nullValue | **string**<br><p>Значение по умолчанию для элемента без данных (например, пустая строка).</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>key.<br>attributes[].<br>expression | **string**<br><p>Выражение, описывающее атрибут, если применимо.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>key.<br>attributes[].<br>hierarchical | **boolean** (boolean)<br><p>Признак поддержки иерархии. Значение по умолчанию &quot;false&quot;.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>key.<br>attributes[].<br>injective | **boolean** (boolean)<br><p>Признакт инъективного отображения &quot;id -&gt; атрибут&quot;. Значение по умолчанию &quot;false&quot;.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>rangeMin | **object**<br><p>Поле, содержащее начало диапазона для словарей, которые хранятся в памяти способом &quot;RANGE_HASHED&quot;. Подробнее см.<a href="https://clickhouse.yandex/docs/ru/query_language/dicts/external_dicts_dict_layout/#range-hashed">документации ClickHouse</a></p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>rangeMin.<br>name | **string**<br><p>Обязательное поле. Имя столбца.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>rangeMin.<br>type | **string**<br><p>Обязательное поле. Тип столбца.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>rangeMin.<br>nullValue | **string**<br><p>Значение по умолчанию для элемента без данных (например, пустая строка).</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>rangeMin.<br>expression | **string**<br><p>Выражение, описывающее атрибут, если применимо.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>rangeMin.<br>hierarchical | **boolean** (boolean)<br><p>Признак поддержки иерархии. Значение по умолчанию &quot;false&quot;.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>rangeMin.<br>injective | **boolean** (boolean)<br><p>Признакт инъективного отображения &quot;id -&gt; атрибут&quot;. Значение по умолчанию &quot;false&quot;.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>rangeMax | **object**<br><p>Поле, содержащее конец диапазона для словарей, которые хранятся в памяти способом &quot;RANGE_HASHED&quot;. Подробнее см.<a href="https://clickhouse.yandex/docs/ru/query_language/dicts/external_dicts_dict_layout/#range-hashed">документации ClickHouse</a></p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>rangeMax.<br>name | **string**<br><p>Обязательное поле. Имя столбца.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>rangeMax.<br>type | **string**<br><p>Обязательное поле. Тип столбца.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>rangeMax.<br>nullValue | **string**<br><p>Значение по умолчанию для элемента без данных (например, пустая строка).</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>rangeMax.<br>expression | **string**<br><p>Выражение, описывающее атрибут, если применимо.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>rangeMax.<br>hierarchical | **boolean** (boolean)<br><p>Признак поддержки иерархии. Значение по умолчанию &quot;false&quot;.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>rangeMax.<br>injective | **boolean** (boolean)<br><p>Признакт инъективного отображения &quot;id -&gt; атрибут&quot;. Значение по умолчанию &quot;false&quot;.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>attributes[] | **object**<br><p>Обязательное поле. Описание полей, доступных для запросов к базе данных. Подробнее см. в <a href="https://clickhouse.yandex/docs/ru/query_language/dicts/external_dicts_dict_structure/#attributes">документации ClickHouse</a>.</p> <p>Должен содержать хотя бы один элемент.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>attributes[].<br>name | **string**<br><p>Обязательное поле. Имя столбца.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>attributes[].<br>type | **string**<br><p>Обязательное поле. Тип столбца.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>attributes[].<br>nullValue | **string**<br><p>Значение по умолчанию для элемента без данных (например, пустая строка).</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>attributes[].<br>expression | **string**<br><p>Выражение, описывающее атрибут, если применимо.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>attributes[].<br>hierarchical | **boolean** (boolean)<br><p>Признак поддержки иерархии. Значение по умолчанию &quot;false&quot;.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>structure.<br>attributes[].<br>injective | **boolean** (boolean)<br><p>Признакт инъективного отображения &quot;id -&gt; атрибут&quot;. Значение по умолчанию &quot;false&quot;.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>layout | **object**<br>Обязательное поле. Макет для хранения словаря в памяти. Подробное описание см. в [документации ClickHouse](https://clickhouse.yandex/docs/ru/query_language/dicts/external_dicts_dict_layout/).<br><p>Макет, определяющий способ хранения словаря в памяти.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>layout.<br>type | **string**<br><p>Обязательное поле. Тип макета для внешнего словаря.</p> <ul> <li>FLAT: Весь словарь хранится в памяти в виде плоских массивов. Доступно для любых источников словарей.</li> <li>HASHED: Весь словарь хранится в памяти в виде хэш-таблицы. Доступно для любых источников словарей.</li> <li>COMPLEX_KEY_HASHED: Аналогичен HASHED, для использования с составными ключами. Доступно для любых источников словарей.</li> <li>RANGE_HASHED: Весь словарь хранится в памяти в виде хэш-таблицы, с упорядоченным массивом диапазонов и соответствующих им значений. Доступно для любых источников словарей.</li> <li>CACHE: Словарь хранится в кэше с заданным количеством ячеек. Доступно для источников словарей MySQL, ClickHouse и HTTP.</li> <li>COMPLEX_KEY_CACHE: Аналогичен CACHE, для использования с составными ключами. Доступно для источников словарей MySQL, ClickHouse и HTTP.</li> </ul> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>layout.<br>sizeInCells | **string** (int64)<br><p>Количество ячеек в кэше. Округляется до степени двойки. Применимо только для типов макета CACHE и COMPLEX_KEY_CACHE.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>fixedLifetime | **string** (int64) <br>`configSpec.clickhouse.config.dictionaries[]` включает только одно из полей `fixedLifetime`, `lifetimeRange`<br><br><p>Жесткий интервал между обновлениями словаря.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>lifetimeRange | **object**<br>Диапазон интервалов между обновлениями словаря, из которых может выбирать ClickHouse. <br>`configSpec.clickhouse.config.dictionaries[]` включает только одно из полей `fixedLifetime`, `lifetimeRange`<br><br>
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>lifetimeRange.<br>min | **string** (int64)<br><p>Минимальное время жизни словаря.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>lifetimeRange.<br>max | **string** (int64)<br><p>Максимальное время жизни словаря.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>httpSource | **object**<br>HTTP-источник для словаря. <br>`configSpec.clickhouse.config.dictionaries[]` включает только одно из полей `httpSource`, `mysqlSource`, `clickhouseSource`, `mongodbSource`, `postgresqlSource`<br><br>
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>httpSource.<br>url | **string**<br><p>Обязательное поле. URL внешнего словаря, доступного по HTTP.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>httpSource.<br>format | **string**<br><p>Обязательное поле. Формат данных. Допустимые значения: все форматы, поддерживаемые диалектом ClickHouse SQL.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mysqlSource | **object**<br>MySQL-источник для словаря. <br>`configSpec.clickhouse.config.dictionaries[]` включает только одно из полей `httpSource`, `mysqlSource`, `clickhouseSource`, `mongodbSource`, `postgresqlSource`<br><br>
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mysqlSource.<br>db | **string**<br><p>Обязательное поле. Имя базы данных MySQL, к которой нужно подключаться.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mysqlSource.<br>table | **string**<br><p>Обязательное поле. Имя таблицы базы данных, которую следует использовать в качестве словаря ClickHouse.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mysqlSource.<br>port | **string** (int64)<br><p>Порт по умолчанию, который нужно использовать при подключении к реплике источника словаря.</p> <p>Допустимые значения — от 0 до 65535 включительно.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mysqlSource.<br>user | **string**<br><p>Имя пользователя по умолчанию для реплик источника словаря.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mysqlSource.<br>password | **string**<br><p>Пароль пользователя по умолчанию для реплик источника словаря.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mysqlSource.<br>replicas[] | **object**<br><p>Обязательное поле. Список реплик базы данных MySQL, используемой в качестве источника словаря.</p> <p>Должен содержать хотя бы один элемент.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mysqlSource.<br>replicas[].<br>host | **string**<br><p>Обязательное поле. Хост реплики MySQL.</p> <p>Максимальная длина строки в символах — 253.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mysqlSource.<br>replicas[].<br>priority | **string** (int64)<br><p>Обязательное поле. Приоритет реплики, который ClickHouse должен учитывать при подключении. Реплике с наивысшим приоритетом должно соответствовать наименьшее значение в этом поле.</p> <p>Значение должно быть больше 0.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mysqlSource.<br>replicas[].<br>port | **string** (int64)<br><p>Порт, который нужно использовать при подключении к реплике. Если для какой-либо реплики не указан порт, ClickHouse использует порт, указанный для источника.</p> <p>Допустимые значения — от 0 до 65535 включительно.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mysqlSource.<br>replicas[].<br>user | **string**<br><p>Имя пользователя базы данных MySQL.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mysqlSource.<br>replicas[].<br>password | **string**<br><p>Пароль пользователя базы данных MySQL.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mysqlSource.<br>where | **string**<br><p>Критерии выбора данных в указанной таблице MySQL.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mysqlSource.<br>invalidateQuery | **string**<br><p>Запрос на проверку состояния словаря, который позволит извлекать только обновленные данные. Дополнительные сведения см. в <a href="https://clickhouse.yandex/docs/ru/query_language/dicts/external_dicts_dict_lifetime/">документации ClickHouse on dictionaries</a>.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>clickhouseSource | **object**<br>ClickHouse-источник для словаря. <br>`configSpec.clickhouse.config.dictionaries[]` включает только одно из полей `httpSource`, `mysqlSource`, `clickhouseSource`, `mongodbSource`, `postgresqlSource`<br><br>
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>clickhouseSource.<br>db | **string**<br><p>Обязательное поле. Имя базы данных ClickHouse.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>clickhouseSource.<br>table | **string**<br><p>Обязательное поле. Имя таблицы в указанной базе данных, используемой в качестве источника словаря.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>clickhouseSource.<br>host | **string**<br><p>Обязательное поле. Хост ClickHouse для указанной базы данных.</p> <p>Максимальная длина строки в символах — 253.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>clickhouseSource.<br>port | **string** (int64)<br><p>Порт для подключения к хосту.</p> <p>Допустимые значения — от 0 до 65535 включительно.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>clickhouseSource.<br>user | **string**<br><p>Обязательное поле. Имя пользователя базы данных ClickHouse.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>clickhouseSource.<br>password | **string**<br><p>Пароль пользователя базы данных ClickHouse.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>clickhouseSource.<br>where | **string**<br><p>Критерии выбора данных в указанной таблице ClickHouse.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mongodbSource | **object**<br>MongoDB-источник для словаря. <br>`configSpec.clickhouse.config.dictionaries[]` включает только одно из полей `httpSource`, `mysqlSource`, `clickhouseSource`, `mongodbSource`, `postgresqlSource`<br><br>
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mongodbSource.<br>db | **string**<br><p>Обязательное поле. Имя базы данных MongoDB.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mongodbSource.<br>collection | **string**<br><p>Обязательное поле. Имя коллекции в указанной базе данных, которую следует использовать в качестве источника словаря.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mongodbSource.<br>host | **string**<br><p>Обязательное поле. Хост MongoDB для указанной базы данных.</p> <p>Максимальная длина строки в символах — 253.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mongodbSource.<br>port | **string** (int64)<br><p>Порт для подключения к хосту.</p> <p>Допустимые значения — от 0 до 65535 включительно.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mongodbSource.<br>user | **string**<br><p>Обязательное поле. Имя пользователя базы данных MongoDB.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>mongodbSource.<br>password | **string**<br><p>Пароль пользователя базы данных MongoDB.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>postgresqlSource | **object**<br>PostgreSQL-источник для словаря. <br>`configSpec.clickhouse.config.dictionaries[]` включает только одно из полей `httpSource`, `mysqlSource`, `clickhouseSource`, `mongodbSource`, `postgresqlSource`<br><br>
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>postgresqlSource.<br>db | **string**<br><p>Обязательное поле. Имя базы данных PostrgreSQL.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>postgresqlSource.<br>table | **string**<br><p>Обязательное поле. Имя таблицы в указанной базе данных, используемой в качестве источника словаря.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>postgresqlSource.<br>hosts[] | **string**<br><p>Обязательное поле. Имя хоста PostrgreSQL.</p> <p>Должен содержать хотя бы один элемент.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>postgresqlSource.<br>port | **string** (int64)<br><p>Порт для подключения к хосту.</p> <p>Допустимые значения — от 0 до 65535 включительно.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>postgresqlSource.<br>user | **string**<br><p>Обязательное поле. Имя пользователя базы данных PostrgreSQL.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>postgresqlSource.<br>password | **string**<br><p>Пароль пользователя базы данных PostrgreSQL.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>postgresqlSource.<br>invalidateQuery | **string**<br><p>Запрос на проверку состояния словаря, который позволит извлекать только обновленные данные. Дополнительные сведения см. в <a href="https://clickhouse.yandex/docs/ru/query_language/dicts/external_dicts_dict_lifetime/">документации ClickHouse on dictionaries</a>.</p> 
configSpec.<br>clickhouse.<br>config.<br>dictionaries[].<br>postgresqlSource.<br>sslMode | **string**<br><p>Режим SSL TCP/IP соединения с хостом PostgreSQL. Дополнительные сведения см. в <a href="https://www.postgresql.org/docs/current/libpq-ssl.html">PostgreSQL documentation</a>.</p> <ul> <li>DISABLE: SSL-соединение не используется.</li> <li>ALLOW: Сначала предпринимается попытка установить незашифрованное соединение. Если это не удается, устанавливается SSL-соединение.</li> <li>PREFER: Сначала предпринимается попытка установить SSL-соединение. Если это не удается, устанавливается незашифрованное соединение.</li> <li>VERIFY_CA: Устанавливается только SSL-соединение и только при условии, что сертификат выдан доверенным центром сертификации (CA).</li> <li>VERIFY_FULL: Устанавливается только SSL-соединение и только при условии, что сертификат выдан доверенным центром сертификации и что имя хоста сервера совпадает с указанным в сертификате.</li> </ul> 
configSpec.<br>clickhouse.<br>config.<br>graphiteRollup[] | **object**<br><p>Параметры свертки для движка таблицы GraphiteMergeTree.</p> 
configSpec.<br>clickhouse.<br>config.<br>graphiteRollup[].<br>name | **string**<br><p>Обязательное поле. Имя указанной комбинации параметров для свертки Graphite.</p> 
configSpec.<br>clickhouse.<br>config.<br>graphiteRollup[].<br>patterns[] | **object**<br><p>Обязательное поле. Шаблон, используемый для свертки.</p> <p>Должен содержать хотя бы один элемент.</p> 
configSpec.<br>clickhouse.<br>config.<br>graphiteRollup[].<br>patterns[].<br>regexp | **string**<br><p>Шаблон для имен метрик.</p> 
configSpec.<br>clickhouse.<br>config.<br>graphiteRollup[].<br>patterns[].<br>function | **string**<br><p>Обязательное поле. Имя агрегирующей функции, которую следует применить к данным старше возраста, указанного в &quot;<code>retention</code>&quot;.</p> 
configSpec.<br>clickhouse.<br>config.<br>graphiteRollup[].<br>patterns[].<br>retention[] | **object**<br><p>Обязательное поле. Возраст данных, которые следует использовать для прореживания.</p> <p>Должен содержать хотя бы один элемент.</p> 
configSpec.<br>clickhouse.<br>config.<br>graphiteRollup[].<br>patterns[].<br>retention[].<br>age | **string** (int64)<br><p>Минимальный возраст данных в секундах.</p> <p>Значение должно быть больше 0.</p> 
configSpec.<br>clickhouse.<br>config.<br>graphiteRollup[].<br>patterns[].<br>retention[].<br>precision | **string** (int64)<br><p>Точность определения возраста данных, в секундах.</p> <p>Значение должно быть больше 0.</p> 
configSpec.<br>clickhouse.<br>config.<br>maxConnections | **integer** (int64)<br><p>Максимальное количество входящих подключений.</p> <p>Минимальное значение — 10.</p> 
configSpec.<br>clickhouse.<br>config.<br>maxConcurrentQueries | **integer** (int64)<br><p>Максимальное количество одновременно обрабатываемых запросов.</p> <p>Минимальное значение — 10.</p> 
configSpec.<br>clickhouse.<br>config.<br>keepAliveTimeout | **integer** (int64)<br><p>Количество миллисекунд, в течение которых ClickHouse ожидает входящие запросы прежде чем закрыть подключение.</p> 
configSpec.<br>clickhouse.<br>config.<br>uncompressedCacheSize | **integer** (int64)<br><p>Размер кэша (в байтах) для несжатых данных, используемых таблицами MergeTree. См. подробное описание в <a href="https://clickhouse.yandex/docs/ru/operations/server_settings/settings/#uncompressed_cache_size">документации ClickHouse</a>.</p> 
configSpec.<br>clickhouse.<br>config.<br>markCacheSize | **integer** (int64)<br><p>Примерный размер (в байтах) кэша «меток», используемых таблицами MergeTree. Подробнее в <a href="https://clickhouse.yandex/docs/ru/operations/server_settings/settings/#mark_cache_size">документации ClickHouse</a>.</p> <p>Значение должно быть больше 5368709120.</p> 
configSpec.<br>clickhouse.<br>config.<br>maxTableSizeToDrop | **integer** (int64)<br><p>Максимальный размер таблицы, которую можно удалить с помощью запроса DROP. См. подробное описание в <a href="https://clickhouse.yandex/docs/ru/operations/server_settings/settings/#max_table_size_to_drop">документации ClickHouse</a>.</p> 
configSpec.<br>clickhouse.<br>config.<br>maxPartitionSizeToDrop | **integer** (int64)<br><p>Максимальный размер раздела, который можно удалить с помощью запроса DROP. См. подробное описание в <a href="https://clickhouse.yandex/docs/ru/operations/server_settings/settings/#max_partition_size_to_drop">документации ClickHouse</a>.</p> 
configSpec.<br>clickhouse.<br>config.<br>builtinDictionariesReloadInterval | **integer** (int64)<br><p>Параметр устарел и не имеет никакого эффекта.</p> 
configSpec.<br>clickhouse.<br>config.<br>timezone | **string**<br><p>Часовой пояс сервера, используемый в преобразованиях полей DateTime. Указывается как идентификатор IANA. См. подробное описание в <a href="https://clickhouse.yandex/docs/ru/operations/server_settings/settings/#timezone">документации ClickHouse</a>.</p> 
configSpec.<br>clickhouse.<br>config.<br>geobaseUri | **string**<br>
configSpec.<br>clickhouse.<br>resources | **object**<br><p>Ресурсы, выделенные хостам ClickHouse.</p> 
configSpec.<br>clickhouse.<br>resources.<br>resourcePresetId | **string**<br><p>Идентификатор набора вычислительных ресурсов, доступных хосту (процессор, память и т. д.). Все доступные наборы ресурсов перечислены в <a href="/docs/managed-clickhouse/concepts/instance-types">документации</a>.</p> 
configSpec.<br>clickhouse.<br>resources.<br>diskSize | **string** (int64)<br><p>Объем хранилища, доступного хосту, в байтах.</p> 
configSpec.<br>clickhouse.<br>resources.<br>diskTypeId | **string**<br><p>Тип хранилища для хоста. Возможные значения:</p> <ul> <li>network-hdd — сетевой HDD-диск;</li> <li>network-ssd — сетевой SSD-диск;</li> <li>local-ssd — локальное SSD-хранилище.</li> </ul> 
configSpec.<br>zookeeper | **object**<br><p>Конфигурация и ресурсы для сервера ZooKeeper.</p> 
configSpec.<br>zookeeper.<br>resources | **object**<br><p>Ресурсы, выделенные хостам ZooKeeper. Если не задано, будет использоваться минимальный доступный набор ресурсов. Все доступные наборы ресурсов можно получить с помощью запроса <a href="/docs/managed-clickhouse/api-ref/ResourcePreset/list">list</a>.</p> 
configSpec.<br>zookeeper.<br>resources.<br>resourcePresetId | **string**<br><p>Идентификатор набора вычислительных ресурсов, доступных хосту (процессор, память и т. д.). Все доступные наборы ресурсов перечислены в <a href="/docs/managed-clickhouse/concepts/instance-types">документации</a>.</p> 
configSpec.<br>zookeeper.<br>resources.<br>diskSize | **string** (int64)<br><p>Объем хранилища, доступного хосту, в байтах.</p> 
configSpec.<br>zookeeper.<br>resources.<br>diskTypeId | **string**<br><p>Тип хранилища для хоста. Возможные значения:</p> <ul> <li>network-hdd — сетевой HDD-диск;</li> <li>network-ssd — сетевой SSD-диск;</li> <li>local-ssd — локальное SSD-хранилище.</li> </ul> 
configSpec.<br>backupWindowStart | **object**<br><p>Время запуска ежедневного резервного копирования, в часовом поясе UTC.</p> <p>Represents a time of day. The date and time zone are either not significant or are specified elsewhere. An API may choose to allow leap seconds. Related types are <a href="https://github.com/googleapis/googleapis/blob/master/google/type/date.proto">google.type.Date</a> and <a href="https://github.com/protocolbuffers/protobuf/blob/master/src/google/protobuf/timestamp.proto">google.protobuf.Timestamp</a>.</p> 
configSpec.<br>backupWindowStart.<br>hours | **integer** (int32)<br><p>Hours of day in 24 hour format. Should be from 0 to 23. An API may choose to allow the value &quot;24:00:00&quot; for scenarios like business closing time.</p> 
configSpec.<br>backupWindowStart.<br>minutes | **integer** (int32)<br><p>Minutes of hour of day. Must be from 0 to 59.</p> 
configSpec.<br>backupWindowStart.<br>seconds | **integer** (int32)<br><p>Seconds of minutes of the time. Must normally be from 0 to 59. An API may allow the value 60 if it allows leap-seconds.</p> 
configSpec.<br>backupWindowStart.<br>nanos | **integer** (int32)<br><p>Fractions of seconds in nanoseconds. Must be from 0 to 999,999,999.</p> 
configSpec.<br>access | **object**<br><p>Политика доступа к БД</p> 
configSpec.<br>access.<br>dataLens | **boolean** (boolean)<br><p>Разрешить доступ для DataLens</p> 
configSpec.<br>access.<br>webSql | **boolean** (boolean)<br><p>Разрешить доступ для Web SQL</p> 
configSpec.<br>access.<br>metrika | **boolean** (boolean)<br><p>Разрешить доступ для Metrika</p> 
configSpec.<br>access.<br>serverless | **boolean** (boolean)<br><p>Разрешить доступ для Serverless</p> 
databaseSpecs[] | **object**<br><p>Обязательное поле. Описания баз данных, которые нужно создать в кластере ClickHouse.</p> <p>Должен содержать хотя бы один элемент.</p> 
databaseSpecs[].<br>name | **string**<br><p>Обязательное поле. Имя базы данных ClickHouse. Длина 1-63 символов.</p> <p>Максимальная длина строки в символах — 63. Значение должно соответствовать регулярному выражению <code>[a-zA-Z0-9_-]*</code>.</p> 
userSpecs[] | **object**<br><p>Обязательное поле. Описания пользователей базы данных, которых нужно создать в кластере ClickHouse.</p> <p>Должен содержать хотя бы один элемент.</p> 
userSpecs[].<br>name | **string**<br><p>Обязательное поле. Имя пользователя базы данных ClickHouse.</p> <p>Максимальная длина строки в символах — 63. Значение должно соответствовать регулярному выражению <code>[a-zA-Z0-9_]*</code>.</p> 
userSpecs[].<br>password | **string**<br><p>Обязательное поле. Пароль пользователя ClickHouse.</p> <p>Длина строки в символах должна быть от 8 до 128.</p> 
userSpecs[].<br>permissions[] | **object**<br><p>Набор разрешений, которые следует предоставить пользователю.</p> 
userSpecs[].<br>permissions[].<br>databaseName | **string**<br><p>Имя базы данных, к которой предоставляет доступ разрешение.</p> 
userSpecs[].<br>settings | **object**<br><p>Пользовательские настройки ClickHouse. Поддерживаемые параметры входят в число параметров, описанных в <a href="https://clickhouse.yandex/docs/ru/operations/settings/">документации ClickHouse</a>.</p> 
userSpecs[].<br>settings.<br>readonly | **integer** (int64)<br><p>Ограничивает разрешения для запросов, не относящихся к DDL. Чтобы ограничить разрешения для DDL-запросов, используйте настройку <code>allowDdl</code>.</p> <ul> <li><code>0</code> (по умолчанию) — нет ограничений.</li> <li><code>1</code>— разрешено выполнять только запросы на чтение данных.</li> <li><code>2</code> — разрешено выполнять запросы на чтение данных и изменение настроек.</li> </ul> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/permissions-for-queries/#settings_readonly">документации ClickHouse</a>.</p> <p>Допустимые значения — от 0 до 2 включительно.</p> 
userSpecs[].<br>settings.<br>allowDdl | **boolean** (boolean)<br><p>Определяет, разрешены ли DDL-запросы (например, <code>CREATE</code>, <code>ALTER</code>, <code>RENAME</code>, и т.д.).</p> <p>Значение по умолчанию: <code>true</code>.</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/permissions-for-queries/#settings_allow_ddl">документации ClickHouse</a>.</p> 
userSpecs[].<br>settings.<br>insertQuorum | **integer** (int64)<br><p>Включает или выключает кворумную запись в кластере ClickHouse. Если значение меньше <code>2</code>, то кворумная запись выключена, в противном случае она включена.</p> <p>Кворумная запись позволяет гарантировать, что за время, не большее чем <code>insertQuorumTimeout</code>, ClickHouse смог без ошибок записать данные в кворум из <code>insert_quorum</code> реплик. Все реплики в кворуме консистентны, т.е. содержат данные всех более ранних запросов <code>INSERT</code>. Использование кворума при записи позволяет гарантировать, что данные не потеряются при выходе из строя одной или нескольких реплик.</p> <p>При чтении данных, записанных с помощью кворумной записи, можно использовать настройку <code>selectSequentialConsistency</code>.</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#settings-insert_quorum">документации ClickHouse</a>.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>connectTimeout | **integer** (int64)<br><p>Время ожидания соединения в миллисекундах.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>10000</code>, 10 секунд).</p> <p>Значение должно быть больше 0.</p> 
userSpecs[].<br>settings.<br>receiveTimeout | **integer** (int64)<br><p>Время ожидания приема данных в миллисекундах.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>300000</code>, 300 секунд, 5 минут).</p> <p>Значение должно быть больше 0.</p> 
userSpecs[].<br>settings.<br>sendTimeout | **integer** (int64)<br><p>Время ожидания отправки данных в миллисекундах.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>300000</code>, 300 секунд, 5 минут).</p> <p>Значение должно быть больше 0.</p> 
userSpecs[].<br>settings.<br>insertQuorumTimeout | **integer** (int64)<br><p>Время ожидания кворумной записи в миллисекундах.</p> <p>Если кворумная запись включена, время ожидания прошло, а запись в <code>insertQuorum</code> реплик так не состоялась, то ClickHouse прервет выполнение <code>INSERT</code>-запроса и вернет ошибку. В этом случае клиент должен повторить запрос на запись того же блока на эту же или любую другую реплику.</p> <p>Минимальное значение: <code>1000</code>, одна секунда (по умолчанию: <code>60000</code>, одна минута).</p> <p>Минимальное значение — 1000.</p> 
userSpecs[].<br>settings.<br>selectSequentialConsistency | **boolean** (boolean)<br><p>Определяет поведение <code>SELECT</code>-запросов для реплицированных таблиц: если эта настройка включена, ClickHouse прервет выполнение запроса и вернет сообщение об ошибке в случае, если в реплике нет фрагментов данных, записанных с помощью кворумной записи. Фрагменты данных, записанные без использования кворумной записи, прочитаны не будут.</p> <p>Значение по умолчанию: <code>false</code> (последовательная консистентность выключена).</p> 
userSpecs[].<br>settings.<br>maxReplicaDelayForDistributedQueries | **integer** (int64)<br><p>Максимальная задержка реплики в миллисекундах. Если реплика отстает на значение больше установленного, она перестает использоваться и становится устаревшей.</p> <p>Минимальное значение: <code>1000</code>, 1 секунда (по умолчанию: <code>300000</code>, 300 секунд, 5 минут).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#settings-max_replica_delay_for_distributed_queries">документации ClickHouse</a>.</p> <p>Минимальное значение — 1000.</p> 
userSpecs[].<br>settings.<br>fallbackToStaleReplicasForDistributedQueries | **boolean** (boolean)<br><p>Включает или выключает форсирование запроса в устаревшую реплику в случае, если актуальные данные недоступны. Если этот параметр включен, то из устаревших реплик таблицы ClickHouse выбирает наиболее актуальную. Используется при выполнении <code>SELECT</code> из распределенной таблицы, которая указывает на реплицированные таблицы.</p> <p>Значение по умолчанию: <code>true</code> (форсирование запроса включено).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#settings-fallback_to_stale_replicas_for_distributed_queries">документации ClickHouse</a>.</p> 
userSpecs[].<br>settings.<br>replicationAlterPartitionsSync | **integer** (int64)<br><p>Условия ожидания завершения асинхронных действий на репликах для запросов <code>ALTER</code>:</p> <ul> <li><code>0</code> — не ждать.</li> <li><code>1</code> — ждать выполнения только у себя (значение по умолчанию).</li> <li><code>2</code> — ждать всех.</li> </ul> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/sql-reference/statements/alter/#synchronicity-of-alter-queries">документации ClickHouse</a>.</p> <p>Допустимые значения — от 0 до 2 включительно.</p> 
userSpecs[].<br>settings.<br>distributedProductMode | **string**<br><p>Определяет поведение распределенных подзапросов.</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#distributed-product-mode">документации ClickHouse</a>.</p> <ul> <li>DISTRIBUTED_PRODUCT_MODE_DENY: Значение по умолчанию. Запрещает использование этих типов подзапросов (возвращает исключение &quot;Double-distributed in/JOIN subqueries is denied&quot;).</li> <li>DISTRIBUTED_PRODUCT_MODE_LOCAL: Заменяет базу данных и таблицу в подзапросе локальными для конечного сервера (шарда), оставляя обычный IN / JOIN.</li> <li>DISTRIBUTED_PRODUCT_MODE_GLOBAL: Заменяет IN/JOIN запрос на GLOBAL IN/GLOBAL JOIN.</li> <li>DISTRIBUTED_PRODUCT_MODE_ALLOW: Позволяет использовать эти типы подзапросов.</li> </ul> 
userSpecs[].<br>settings.<br>distributedAggregationMemoryEfficient | **boolean** (boolean)<br><p>Включает или выключает режим экономии памяти при распределенной агрегации.</p> <p>При распределённой обработке запроса внешняя агрегация производится на удалённых серверах. Для того чтобы на сервере-инициаторе запроса использовалось немного оперативной памяти, нужно включить эту настройку.</p> <p>Значение по умолчанию: <code>false</code> (режим экономии памяти выключен).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/sql-reference/statements/select/group-by/#select-group-by-in-external-memory">документации ClickHouse</a>.</p> 
userSpecs[].<br>settings.<br>distributedDdlTaskTimeout | **integer** (int64)<br><p>Время ожидания выполнения DDL-запросов в миллисекундах.</p> 
userSpecs[].<br>settings.<br>skipUnavailableShards | **boolean** (boolean)<br><p>Включает или выключает тихий пропуск недоступных шардов.</p> <p>Шард считается недоступным, если все его реплики недоступны.</p> <p>Значение по умолчанию: <code>false</code> (тихий пропуск недоступных шардов выключен).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#settings-skip_unavailable_shards">документации ClickHouse</a>.</p> 
userSpecs[].<br>settings.<br>compile | **boolean** (boolean)<br><p>Включает или выключает компиляцию запросов. Если вы выполняете большое количество структурно идентичных запросов — включите эту настройку. При включенной компиляции такие запросы могут выполняться быстрее за счет использования скомпилированных частей запроса.</p> <p>Эта настройка используется совместно с <code>minCountToCompile</code>.</p> <p>Значение по умолчанию: <code>false</code> (компиляция выключена).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#compile">документации ClickHouse</a>.</p> 
userSpecs[].<br>settings.<br>minCountToCompile | **integer** (int64)<br><p>После какого количества структурно идентичных запросов начать компиляцию.</p> <p>Минимальное значение: <code>0</code> (по умолчанию: <code>3</code>).</p> <p>Для значения <code>0</code> компиляция выполняется синхронно: запрос ожидает окончания процесса компиляции перед продолжением выполнения. Рекомендуется использовать это значение только в целях тестирования.</p> <p>Для всех других значений компиляция выполняется асинхронно, в отдельном потоке. Когда часть запроса будет скомпилирована, она сразу же будет использована ClickHouse для подходящих запросов (включая те, которые выполняются в данный момент).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#min-count-to-compile">документации ClickHouse</a>.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>compileExpressions | **boolean** (boolean)<br><p>Включает или выключает компиляцию выражений. Если вы выполняете большое количество запросов, в которых используются идентичные выражения — включите эту настройку. При включенной компиляции выражений такие запросы могут выполняться быстрее за счет использования скомпилированных выражений.</p> <p>Эта настройка используется совместно с <code>minCountToCompileExpression</code>.</p> <p>Значение по умолчанию: <code>false</code> (компиляция выражений выключена).</p> 
userSpecs[].<br>settings.<br>minCountToCompileExpression | **integer** (int64)<br><p>После какого количества идентичных выражений начать их компиляцию.</p> <p>Минимальное значение: <code>0</code> (по умолчанию: <code>3</code>).</p> <p>Для значения <code>0</code> компиляция выполняется синхронно: запрос ожидает окончания процесса компиляции выражения перед продолжением выполнения. Рекомендуется использовать это значение только в целях тестирования.</p> <p>Для всех других значений компиляция выполняется асинхронно, в отдельном потоке. Когда выражение будет скомпилировано, оно сразу же будет использовано ClickHouse для подходящих запросов (включая те, которые выполняются в данный момент).</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>maxBlockSize | **integer** (int64)<br><p>Максимальный размер блока для чтения.</p> <p>Данные в ClickHouse обрабатываются по блокам (наборам кусочков столбцов). Внутренние циклы обработки для одного блока достаточно эффективны, но есть заметные издержки на каждый блок.</p> <p>Эта настройка — рекомендация, какой размер блока (в количестве строк) загружать из таблиц.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>65536</code>).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#setting-max_block_size">документации ClickHouse</a>.</p> <p>Значение должно быть больше 0.</p> 
userSpecs[].<br>settings.<br>minInsertBlockSizeRows | **integer** (int64)<br><p>Ограничивает минимальное количество строк в блоке, который может быть вставлен в таблицу запросом <code>INSERT</code>. Блоки меньшего размера склеиваются в блоки большего размера.</p> <p>Минимальное значение: <code>0</code>, склейка блоков выключена (по умолчанию: <code>1048576</code>).</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>minInsertBlockSizeBytes | **integer** (int64)<br><p>Ограничивает минимальное количество байтов в блоке, который может быть вставлен в таблицу запросом <code>INSERT</code>. Блоки меньшего размера склеиваются в блоки большего размера.</p> <p>Минимальное значение: <code>0</code>, склейка блоков выключена (по умолчанию: <code>‭268435456‬‬</code>, 256 МБ).</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>maxInsertBlockSize | **integer** (int64)<br><p>Позволяет формировать блоки указанного размера (в байтах) при вставке в таблицу. Эта настройка действует только в тех случаях, когда сервер сам формирует такие блоки.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>1048576</code>).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#settings-max_insert_block_size">документации ClickHouse</a>.</p> <p>Значение должно быть больше 0.</p> 
userSpecs[].<br>settings.<br>minBytesToUseDirectIo | **integer** (int64)<br><p>минимальный объём данных в байтах, необходимый для прямого (небуферизованного) чтения (Direct I/O) на диск.</p> <p>По умолчанию ClickHouse читает данные не напрямую с диска, а полагается на файловую систему и её кэш. Такое чтение эффективно при небольших объемах данных. Если данные читаются в больших объемах, эффективнее читать с диска напрямую, минуя кэш файловой системы.</p> <p>Если общий объём хранения всех данных для чтения превышает заданное значение настройки, тогда ClickHouse читает данные с диска напрямую.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code> (прямой ввод/вывод отключен).</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>useUncompressedCache | **boolean** (boolean)<br><p>Определяет, использовать ли кэш разжатых блоков. Использование кэша несжатых блоков может существенно сократить задержку и увеличить пропускную способность при работе с большим количеством коротких запросов. Включите эту настройку для пользователей, от которых идут частые короткие запросы.</p> <p>Этот настройка действует только для таблиц семейства MergeTree.</p> <p>Значение по умолчанию: <code>false</code> (кэш не используется).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#setting-use_uncompressed_cache">документации ClickHouse</a>.</p> 
userSpecs[].<br>settings.<br>mergeTreeMaxRowsToUseCache | **integer** (int64)<br><p>Ограничивает максимальный размер запроса в строках для использования кэша несжатых данных. Кэш не используется для запросов, превышающих указанный размер.</p> <p>Эта настройка используется совместно с <code>useUncompressedCache</code>.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>128x8192</code>).</p> <p>Значение должно быть больше 0.</p> 
userSpecs[].<br>settings.<br>mergeTreeMaxBytesToUseCache | **integer** (int64)<br><p>Ограничивает максимальный размер запроса в байтах для использования кэша несжатых данных. Кэш не используется для запросов, превышающих указанный размер.</p> <p>Эта настройка используется совместно с <code>useUncompressedCache</code>.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>192x10x1024x1024</code>).</p> <p>Значение должно быть больше 0.</p> 
userSpecs[].<br>settings.<br>mergeTreeMinRowsForConcurrentRead | **integer** (int64)<br><p>Ограничивает минимальное количество строк, которое надо прочитать из файла, чтобы использовать одновременное чтение. Если количество строк, прочитанных из файла, превышает заданное значение, то ClickHouse пытается выполнить одновременное чтение из этого файла в несколько потоков.</p> <p>Этот настройка действует только для таблиц семейства MergeTree.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>20x8192</code>).</p> <p>Значение должно быть больше 0.</p> 
userSpecs[].<br>settings.<br>mergeTreeMinBytesForConcurrentRead | **integer** (int64)<br><p>Ограничивает минимальное количество байт, которое надо прочитать из файла, чтобы использовать одновременное чтение. Если количество байт, прочитанных из файла, превышает заданное значение, то ClickHouse пытается выполнить одновременное чтение из этого файла в несколько потоков.</p> <p>Этот настройка действует только для таблиц семейства MergeTree.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>24x10x1024x1024</code>).</p> <p>Значение должно быть больше 0.</p> 
userSpecs[].<br>settings.<br>maxBytesBeforeExternalGroupBy | **integer** (int64)<br><p>задает порог потребления оперативной памяти (в байтах), по достижению которого временные данные, накопленные при выполнении операции агрегации <code>GROUP BY</code>, сбрасываются на диск для экономии оперативной памяти.</p> <p>По умолчанию агрегирование выполняется в памяти с помощью хэш-таблицы. Запрос может привести к необходимости агрегации больших объемов данных, которые могут не поместиться в оперативную память и вызвать ошибку при выполнении запроса (см. настройку <code>maxMemoryUsage</code>). Для таких запросов используйте эту настройку, чтобы ClickHouse сбрасывал данные на диск и успешно выполнял агрегацию.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, <code>GROUP BY</code> во внешней памяти отключен.</p> <p>При использовании агрегации во внешней памяти рекомендуется задать значение этой настройки в два раза меньше значения настройки <code>maxMemoryUsage</code> (по умолчанию максимальное использование памяти ограничено десятью гигабайтами).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/sql-reference/statements/select/group-by/#select-group-by-in-external-memory">документации ClickHouse</a>.</p> <p>Смотрите также настройку <code>distributedAggregationMemoryEfficient</code>.</p> 
userSpecs[].<br>settings.<br>maxBytesBeforeExternalSort | **integer** (int64)<br><p>Настройка аналогична <code>maxBytesBeforeExternalGroupBy</code>, за исключением того, что она применяется для операции сортировки (<code>ORDER BY</code>).</p> 
userSpecs[].<br>settings.<br>groupByTwoLevelThreshold | **integer** (int64)<br><p>Определяет порог количества ключей, при достижении которого начинается двухуровневая агрегация.</p> <p>Минимальное значение: <code>0</code>, порог не установлен (по умолчанию: <code>10000‬‬</code>).</p> 
userSpecs[].<br>settings.<br>groupByTwoLevelThresholdBytes | **integer** (int64)<br><p>Определяет порог количества байт в агрегате, при достижении которого начинается двухуровневая агрегация.</p> <p>Минимальное значение: <code>0</code>, порог не установлен (по умолчанию: <code>100000000‬‬</code>).</p> 
userSpecs[].<br>settings.<br>priority | **integer** (int64)<br><p>Определяет приоритет запроса.</p> <ul> <li><code>0</code> — приоритет не используется.</li> <li><code>1</code> — наивысший приоритет.</li> <li>и так далее. Чем больше число, тем ниже приоритет.</li> </ul> <p>Эта настройка выставляется для каждого запроса по отдельности.</p> <p>Если ClickHouse в текущий момент времени выполняет запросы с более высокими приоритетами, чем приоритет поступившего запроса, то выполнение такого запроса приостанавливается до завершения выполнения более приоритетных запросов.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, приоритет не используется.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>maxThreads | **integer** (int64)<br><p>Ограничивает максимальное количество потоков обработки запроса (без учёта потоков для чтения данных с удалённых серверов).</p> <p>Этот параметр относится к потокам, которые выполняют параллельно одни стадии конвейера выполнения запроса.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code> (значение вычисляется автоматически — это количество процессорных ядер без учёта Hyper-Threading).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#settings-max_threads">документации ClickHouse</a>.</p> <p>Значение должно быть больше 0.</p> 
userSpecs[].<br>settings.<br>maxMemoryUsage | **integer** (int64)<br><p>Ограничивает максимально возможный объём оперативной памяти (в байтах) для выполнения запроса на одном сервере. Настройка не учитывает объём свободной памяти или общий объём памяти на машине.</p> <p>Ограничение действует на один запрос, в пределах одного сервера.</p> <p>Минимальное значение: <code>0</code>, нет ограничения. В конфигурационном файле по умолчанию ограничение равно <code>10737418240</code> (10 ГБ).</p> <p>Если вы также используете настройки <code>maxBytesBeforeExternalGroupBy</code> или <code>maxBytesBeforeExternalSort</code>, рекомендуется, чтобы их значения были в два раза меньше значения <code>maxMemoryUsage</code>.</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/query-complexity/#settings_max_memory_usage">документации ClickHouse</a>.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>maxMemoryUsageForUser | **integer** (int64)<br><p>Ограничивает максимально возможный объём оперативной памяти (в байтах) для выполнения запросов пользователя на одном сервере. Настройка не учитывает объём свободной памяти или общий объём памяти на машине.</p> <p>Ограничение действует на все запросы пользователя, которые выполняются одновременно в пределах одного сервера.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>maxNetworkBandwidth | **integer** (int64)<br><p>Ограничивает скорость обмена данными по сети (байт в секунду) при выполнении одного запроса.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> 
userSpecs[].<br>settings.<br>maxNetworkBandwidthForUser | **integer** (int64)<br><p>Ограничивает скорость обмена данными по сети (байт в секунду). Эта настройка влияет на все одновременно выполняющиеся запросы пользователя.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> 
userSpecs[].<br>settings.<br>forceIndexByDate | **boolean** (boolean)<br><p>Если эта настройка включена, то запрос не выполняется при условии, что использовать индекс по дате невозможно. Этот настройка действует только для таблиц семейства MergeTree.</p> <p>Значение по умолчанию: <code>false</code> (настройка отключена, запрос выполняется, даже если ClickHouse не может использовать индекс по дате).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#settings-force_index_by_date">документации ClickHouse</a>.</p> 
userSpecs[].<br>settings.<br>forcePrimaryKey | **boolean** (boolean)<br><p>Если эта настройка включена, то запрос не выполняется при условии, что использовать индекс по первичному ключу невозможно. Этот настройка действует только для таблиц семейства MergeTree.</p> <p>Значение по умолчанию: <code>false</code> (настройка отключена, запрос выполняется, даже если ClickHouse не может использовать индекс по первичному ключу).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#settings-force_primary_key">документации ClickHouse</a>.</p> 
userSpecs[].<br>settings.<br>maxRowsToRead | **integer** (int64)<br><p>Ограничивает максимальное количество строк, которое можно прочитать из таблицы при выполнении запроса.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/query-complexity/#max-rows-to-read">документации ClickHouse</a>.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>maxBytesToRead | **integer** (int64)<br><p>Ограничивает максимальное количество байт (несжатых данных), которое можно прочитать из таблицы при выполнении запроса.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>readOverflowMode | **string**<br><p>Определяет поведение ClickHouse в ситуации, когда количество прочитанных данных <a href="https://clickhouse.tech/docs/ru/operations/settings/query-complexity/#restrictions-on-query-complexity">превысило ограничения</a>.</p> <ul> <li><code>throw</code> — прервать выполнение запроса, вернуть ошибку.</li> <li><code>break</code> — прервать выполнение запроса, вернуть неполный результат.</li> </ul> 
userSpecs[].<br>settings.<br>maxRowsToGroupBy | **integer** (int64)<br><p>Ограничивает максимальное количество уникальных ключей, получаемых в процессе агрегации. Эта настройка позволяет ограничить потребление оперативной памяти при агрегации.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>groupByOverflowMode | **string**<br><p>Определяет поведение ClickHouse в ситуации, когда количество уникальных ключей при агрегации <a href="https://clickhouse.tech/docs/ru/operations/settings/query-complexity/#restrictions-on-query-complexity">превысило ограничения</a>.</p> <ul> <li><code>throw</code> — прервать выполнение запроса, вернуть ошибку.</li> <li><code>break</code> — прервать выполнение запроса, вернуть неполный результат.</li> <li><code>any</code> — выполнить <code>GROUP BY</code> приближённо, продолжая агрегацию для ключей, которые попали в набор, без добавления новых ключей в набор.</li> </ul> 
userSpecs[].<br>settings.<br>maxRowsToSort | **integer** (int64)<br><p>Ограничивает максимальное количество строк для сортировки. Эта настройка позволяет ограничить потребление оперативной памяти при сортировке.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>maxBytesToSort | **integer** (int64)<br><p>Ограничивает максимальное количество байт (несжатых данных), которое можно прочитать из таблицы до сортировки. Эта настройка позволяет ограничить потребление оперативной памяти при сортировке.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>sortOverflowMode | **string**<br><p>Определяет поведение ClickHouse в ситуации, когда количество строк, полученных перед сортировкой, <a href="https://clickhouse.tech/docs/ru/operations/settings/query-complexity/#restrictions-on-query-complexity">превысило ограничения</a>.</p> <ul> <li><code>throw</code> — прервать выполнение запроса, вернуть ошибку.</li> <li><code>break</code> — прервать выполнение запроса, вернуть неполный результат.</li> </ul> 
userSpecs[].<br>settings.<br>maxResultRows | **integer** (int64)<br><p>Ограничивает количество строк результата. Это ограничение также проверяется для подзапросов и частей распределенных запросов, выполняемых на удаленных серверах.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>maxResultBytes | **integer** (int64)<br><p>Ограничивает количество байт результата. Это ограничение также проверяется для подзапросов и частей распределенных запросов, выполняемых на удаленных серверах.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>resultOverflowMode | **string**<br><p>определяет поведение ClickHouse в ситуации, когда объём результата <a href="https://clickhouse.tech/docs/ru/operations/settings/query-complexity/#restrictions-on-query-complexity">превысил ограничения</a>.</p> <ul> <li><code>throw</code> — прервать выполнение запроса, вернуть ошибку.</li> <li><code>break</code> — прервать выполнение запроса, вернуть неполный результат.</li> </ul> 
userSpecs[].<br>settings.<br>maxRowsInDistinct | **integer** (int64)<br><p>Ограничивает максимальное количество различных строк при использовании <code>DISTINCT</code>.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>maxBytesInDistinct | **integer** (int64)<br><p>Ограничивает максимальное количество байт (несжатых данных), занимаемых хэш-таблицей, при использовании <code>DISTINCT</code>.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>distinctOverflowMode | **string**<br><p>Определяет поведение ClickHouse в ситуации, когда количество данных при выполнении запроса <code>DISTINCT</code> <a href="https://clickhouse.tech/docs/ru/operations/settings/query-complexity/#restrictions-on-query-complexity">превысило ограничения</a>.</p> <ul> <li><code>throw</code> — прервать выполнение запроса, вернуть ошибку.</li> <li><code>break</code> — прервать выполнение запроса, вернуть неполный результат.</li> </ul> 
userSpecs[].<br>settings.<br>maxRowsToTransfer | **integer** (int64)<br><p>Ограничивает максимальное количество строк, которое можно передать на удалённый сервер или сохранить во временную таблицу при использовании <code>GLOBAL IN</code>.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>maxBytesToTransfer | **integer** (int64)<br><p>Ограничивает максимальное количество байт (несжатых данных), которых можно передать на удалённый сервер или сохранить во временную таблицу, при использовании <code>GLOBAL IN</code>.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>transferOverflowMode | **string**<br><p>Определяет поведение ClickHouse в ситуации, когда количество данных для передачи на другой сервер <a href="https://clickhouse.tech/docs/ru/operations/settings/query-complexity/#restrictions-on-query-complexity">превысило ограничения</a>.</p> <ul> <li><code>throw</code> — прервать выполнение запроса, вернуть ошибку.</li> <li><code>break</code> — прервать выполнение запроса, вернуть неполный результат.</li> </ul> 
userSpecs[].<br>settings.<br>maxExecutionTime | **integer** (int64)<br><p>Ограничивает максимальное время выполнения запроса в миллисекундах. На данный момент это ограничение не проверяется при одной из стадий сортировки а также при слиянии и финализации агрегатных функций.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>timeoutOverflowMode | **string**<br><p>Определяет поведение ClickHouse в ситуации, когда запрос <a href="https://clickhouse.tech/docs/ru/operations/settings/query-complexity/#restrictions-on-query-complexity">превысил ограничения</a> на время исполнения.</p> <ul> <li><code>throw</code> — прервать выполнение запроса, вернуть ошибку.</li> <li><code>break</code> — прервать выполнение запроса, вернуть неполный результат.</li> </ul> 
userSpecs[].<br>settings.<br>maxColumnsToRead | **integer** (int64)<br><p>Ограничивает максимальное количество столбцов, которые можно читать из таблицы в одном запросе. Если запрос требует чтения большего количества столбцов — он будет завершен с ошибкой.</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>maxTemporaryColumns | **integer** (int64)<br><p>Ограничивает максимальное количество временных столбцов, которое должно храниться в оперативной памяти одновременно при выполнении запроса (с учетом постоянных столбцов)</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>maxTemporaryNonConstColumns | **integer** (int64)<br><p>Ограничивает максимальное количество временных столбцов, которое должно храниться в оперативной памяти одновременно при выполнении запроса (без учета постоянных столбцов).</p> <p>Минимальное значение и значение по умолчанию: <code>0</code>, нет ограничения.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>settings.<br>maxQuerySize | **integer** (int64)<br><p>Ограничивает размер наибольшей части запроса (в байтах), которая может быть передана в оперативную память для разбора с помощью парсера SQL.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>262144</code>).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#settings-max_query_size">документации ClickHouse</a>.</p> <p>Значение должно быть больше 0.</p> 
userSpecs[].<br>settings.<br>maxAstDepth | **integer** (int64)<br><p>Ограничивает максимальную глубину вложенности синтаксического дерева.</p> <p>Для больших и сложных запросов может быть построено синтаксическое дерево очень большой глубины. При помощи этой настройки вы можете запретить выполнение излишне больших или неоптимальных запросов для больших таблиц.</p> <p>Например, запрос <code>SELECT *</code> в большинстве случаев породит более сложное и глубокое синтаксическое дерево, чем запрос <code>SELECT ... WHERE ...</code> с ограничениями и условиями. Наложение ограничения с помощью настройки может побудить пользователя оптимизировать излишне сложные запросы.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>1000</code>). Слишком маленькое значение может привести к невозможности выполнения большинства запросов.</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/query-complexity/#max-ast-depth">документации ClickHouse</a>.</p> <p>Значение должно быть больше 0.</p> 
userSpecs[].<br>settings.<br>maxAstElements | **integer** (int64)<br><p>Ограничивает максимальное количество элементов синтаксического дерева запроса (количество узлов дерева).</p> <p>Для больших и сложных запросов может быть построено синтаксическое дерево c очень большим количеством элементов. При помощи этой настройки вы можете запретить выполнение излишне больших или неоптимальных запросов для больших таблиц.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>50000</code>). Слишком маленькое значение может привести к невозможности выполнения большинства запросов.</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/query-complexity/#max-ast-elements">документации ClickHouse</a>.</p> <p>Значение должно быть больше 0.</p> 
userSpecs[].<br>settings.<br>maxExpandedAstElements | **integer** (int64)<br><p>Ограничивает максимальное количество элементов синтаксического дерева запроса (количество узлов дерева) после раскрытия псевдонимов и звездочки.</p> <p>Для больших и сложных запросов может быть построено синтаксическое дерево c очень большим количеством элементов. При помощи этой настройки вы можете запретить выполнение излишне больших или неоптимальных запросов для больших таблиц.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>500000</code>). Слишком маленькое значение может привести к невозможности выполнения большинства запросов.</p> <p>Значение должно быть больше 0.</p> 
userSpecs[].<br>settings.<br>inputFormatValuesInterpretExpressions | **boolean** (boolean)<br><p>Включает или выключает парсер SQL, если потоковый парсер не может проанализировать данные.</p> <p>Используйте эту настройку, если значения, которые вы хотите вставить в таблицу, содержат в себе выражения SQL.</p> <p>Например, при вставке в таблицу значения, содержащего в себе выражение <code>now()</code>, потоковый парсер не сможет распознать это выражение; запрос <code>INSERT</code> завершится с ошибкой, и никакие данные не будут вставлены в таблицу. При включенном парсере SQL выражение будет распознано корректно и в качестве значения будет вставлен результат выполнения SQL-функции <code>now()</code> (текущая дата и время).</p> <p>Эта настройка действует только в том случае, если вы используете формат <a href="https://clickhouse.tech/docs/ru/interfaces/formats/#data-format-values">Values</a> при вставке данных.</p> <p>Значение по умолчанию: <code>true</code> (парсер SQL включен).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/operations/settings/settings/#settings-input_format_values_interpret_expressions">документации ClickHouse</a>.</p> 
userSpecs[].<br>settings.<br>inputFormatDefaultsForOmittedFields | **boolean** (boolean)<br><p>Включает или выключает замену пропущенных полей значениями по умолчанию для типа данных столбца при вставке данных запросом <code>INSERT</code>.</p> <p>Значение по умолчанию: <code>true</code> (замена включена).</p> 
userSpecs[].<br>settings.<br>outputFormatJsonQuote_64BitIntegers | **boolean** (boolean)<br><p>Определяет формат чисел в JSON-выводе.</p> <p>Если эта настройка включена, то при выводе в JSON 64-битные числа (<code>UInt64</code> и <code>Int64</code>) выводятся в кавычках (из соображений совместимости с большинством реализаций JavaScript). Иначе — без кавычек.</p> <p>Значение по умолчанию: <code>false</code> (вывод 64-битных целых чисел в кавычках выключен).</p> 
userSpecs[].<br>settings.<br>outputFormatJsonQuoteDenormals | **boolean** (boolean)<br><p>Включает вывод специальных значений для чисел с плавающей запятой (<code>+nan</code>, <code>-nan</code>, <code>+inf</code> и <code>-inf</code>) при выводе в JSON.</p> <p>Значение по умолчанию: <code>false</code> (специальные значения не выводятся).</p> 
userSpecs[].<br>settings.<br>lowCardinalityAllowInNativeFormat | **boolean** (boolean)<br><p>Определяет, использовать ли тип LowCardinality в Native-формате.</p> <ul> <li><code>true</code> (по умолчанию) — да, использовать.</li> <li><code>false</code>— конвертировать столбцы LowCardinality в обычные столбцы для запроса <code>SELECT</code>, и конвертировать обычные столбцы в требуемый LowCardinality-столбец для запроса <code>INSERT</code>.</li> </ul> <p>Столбцы этого типа, также известные как «разреженные столбцы», позволяют более эффективно хранить данные в виде хэш-таблиц. Если данные это позволяют, ClickHouse использует столбец типа LowCardinality.</p> <p>Если вы используете сторонний клиент для ClickHouse, который не умеет работать со столбцами типа LowCardinality, то такой клиент не сможет правильно интерпретировать результат запроса, если в запросе будет присутствовать столбец типа LowCardinality. Выключите эту настройку, чтобы включать в результат столбец в обычном формате и позволить сторонним клиентам обработать результат.</p> <p>Официальный клиент ClickHouse умеет работать со столбцами типа LowCardinality.</p> <p>Значение по умолчанию: <code>true</code> (столбцы LowCardinality используются в Native-формате).</p> 
userSpecs[].<br>settings.<br>emptyResultForAggregationByEmptySet | **boolean** (boolean)<br><p>Позволяет возвращать пустой результат при выполнении агрегации данных без ключей (без <code>GROUP BY</code>) для пустого множества (например, <code>SELECT count(*) FROM table WHERE 0</code>).</p> <ul> <li><code>true</code>— ClickHouse вернет пустой результат.</li> <li><code>false</code> (по умолчанию) — ClickHouse вернет результат, состоящий из одной строки со значениями <code>NULL</code> для агрегатных функций, в соответствии со стандартом SQL.</li> </ul> 
userSpecs[].<br>settings.<br>httpConnectionTimeout | **integer** (int64)<br><p>Время ожидания установления HTTP-соединения в миллисекундах.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>1000</code>, 1 секунда).</p> 
userSpecs[].<br>settings.<br>httpReceiveTimeout | **integer** (int64)<br><p>Время ожидания приема данных через HTTP-соединение в миллисекундах.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>1800000</code>, 1800 секунд, 30 минут).</p> 
userSpecs[].<br>settings.<br>httpSendTimeout | **integer** (int64)<br><p>Время ожидания отправки данных через HTTP-соединение в миллисекундах.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>1800000</code>, 1800 секунд, 30 минут).</p> 
userSpecs[].<br>settings.<br>enableHttpCompression | **boolean** (boolean)<br><p>Включает или выключает сжатие данных в ответе на HTTP-запрос.</p> <p>По умолчанию ClickHouse хранит данные в сжатом виде. При выполнении запроса его результат представлен в несжатом виде. С помощью этой настройки вы можете указать ClickHouse сжимать результат запроса при отправке по HTTP.</p> <p>Чтобы ClickHouse сжал ответ при включенной настройке, добавьте в HTTP-запрос заголовок @b.</p> <p>ClickHouse поддерживает следующие методы сжатия: <code>gzip</code>, <code>br</code> и <code>deflate</code>.</p> <p>Значение по умолчанию: <code>false</code> (сжатие выключено).</p> <p>См. подробное описание в <a href="https://clickhouse.tech/docs/ru/interfaces/http/">документации ClickHouse</a>.</p> 
userSpecs[].<br>settings.<br>sendProgressInHttpHeaders | **boolean** (boolean)<br><p>Включает отсылку уведомления о ходе выполнения с использованием HTTP-заголовков <code>X-ClickHouse-Progress</code>.</p> <p>Значение по умолчанию: <code>false</code> (отсылка уведомлений выключена).</p> 
userSpecs[].<br>settings.<br>httpHeadersProgressInterval | **integer** (int64)<br><p>Задает минимальный интервал (в миллисекундах) между уведомлениями о ходе выполнения запроса с помощью HTTP-заголовка <code>X-ClickHouse-Progress</code>.</p> <p>Значение должно быть больше <code>0</code> (по умолчанию: <code>100</code>).</p> 
userSpecs[].<br>settings.<br>addHttpCorsHeader | **boolean** (boolean)<br><p>Включает заголовок CORS в HTTP-ответы.</p> <p>Значение по умолчанию: <code>false</code> (заголовок не включается в HTTP-ответы).</p> 
userSpecs[].<br>quotas[] | **object**<br><p>Представление квот ClickHouse. Каждая квота связана с пользователем и ограничивает использование ресурсов на определенный интервал. См. подробное описание в <a href="https://clickhouse.yandex/docs/ru/operations/quotas/">документации ClickHouse</a>.</p> 
userSpecs[].<br>quotas[].<br>intervalDuration | **integer** (int64)<br><p>Длительность интервала для квоты в миллисекундах. Минимальное значение — 1 секунда.</p> <p>Минимальное значение — 1000.</p> 
userSpecs[].<br>quotas[].<br>queries | **integer** (int64)<br><p>Общее количество запросов. 0-неограниченно.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>quotas[].<br>errors | **integer** (int64)<br><p>Количество запросов, которые вызвали исключение. 0-неограниченно.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>quotas[].<br>resultRows | **integer** (int64)<br><p>Общее число строк, приведенных в результате. 0-неограниченно.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>quotas[].<br>readRows | **integer** (int64)<br><p>Общее число исходных строк, считанных из таблиц для выполнения запроса, на всех удаленных серверах. 0-неограниченно.</p> <p>Минимальное значение — 0.</p> 
userSpecs[].<br>quotas[].<br>executionTime | **integer** (int64)<br><p>Общее время выполнения запроса, в миллисекундах. 0-неограниченно.</p> <p>Минимальное значение — 0.</p> 
hostSpecs[] | **object**<br><p>Обязательное поле. Конфигурации для отдельных хостов, которые должны быть созданы для кластера ClickHouse.</p> <p>Должен содержать хотя бы один элемент.</p> 
hostSpecs[].<br>zoneId | **string**<br><p>Идентификатор зоны доступности, в которой находится хост. Чтобы получить список доступных зон, используйте запрос <a href="/docs/compute/api-ref/Zone/list">list</a>.</p> <p>Максимальная длина строки в символах — 50.</p> 
hostSpecs[].<br>type | **string**<br><p>Обязательное поле. Тип развертываемого хоста.</p> <ul> <li>CLICKHOUSE: Хост ClickHouse.</li> <li>ZOOKEEPER: Хост ZooKeeper.</li> </ul> 
hostSpecs[].<br>subnetId | **string**<br><p>Идентификатор подсети, к которой должен принадлежать хост. Эта подсеть должна быть частью сети, к которой принадлежит кластер. Идентификатор сети задается в поле <a href="/docs/managed-clickhouse/api-ref/Cluster#representation">Cluster.networkId</a>.</p> <p>Максимальная длина строки в символах — 50.</p> 
hostSpecs[].<br>assignPublicIp | **boolean** (boolean)<br><p>Должен ли хост получить публичный IP-адрес при создании.</p> <p>После создания узла этот параметр изменить нельзя. Чтобы удалить назначенный публичный IP-адрес или назначить публичный IP уже созданному хосту, пересоздайте хост с нужным значением поля <code>assignPublicIp</code>.</p> <p>Возможные значения:</p> <ul> <li>false — не назначать хосту публичный IP-адрес.</li> <li>true — у хоста должен быть публичный IP-адрес.</li> </ul> 
hostSpecs[].<br>shardName | **string**<br><p>Имя шарда, которому принадлежит хост.</p> <p>Максимальная длина строки в символах — 63. Значение должно соответствовать регулярному выражению <code>[a-zA-Z0-9_-]*</code>.</p> 
networkId | **string**<br><p>Обязательное поле. Идентификатор сети, в которой нужно создать кластер.</p> <p>Максимальная длина строки в символах — 50.</p> 
shardName | **string**<br><p>Имя первого шарда в кластере. Если параметр не указан, используется значение <code>shard1</code>.</p> <p>Максимальная длина строки в символах — 63. Значение должно соответствовать регулярному выражению <code>[a-zA-Z0-9_-]*</code>.</p> 
 
## Ответ {#responses}
**HTTP Code: 200 - OK**

```json 
{
  "id": "string",
  "description": "string",
  "createdAt": "string",
  "createdBy": "string",
  "modifiedAt": "string",
  "done": true,
  "metadata": "object",

  //  включает только одно из полей `error`, `response`
  "error": {
    "code": "integer",
    "message": "string",
    "details": [
      "object"
    ]
  },
  "response": "object",
  // конец списка возможных полей

}
```
Ресурс Operation. Дополнительные сведения см. в разделе
[Объект Operation](/docs/api-design-guide/concepts/operation).
 
Поле | Описание
--- | ---
id | **string**<br><p>Идентификатор операции.</p> 
description | **string**<br><p>Описание операции. Длина описания должна быть от 0 до 256 символов.</p> 
createdAt | **string** (date-time)<br><p>Время создания ресурса в формате в <a href="https://www.ietf.org/rfc/rfc3339.txt">RFC3339</a>.</p> <p>Строка в формате <a href="https://www.ietf.org/rfc/rfc3339.txt">RFC3339</a>.</p> 
createdBy | **string**<br><p>Идентификатор пользователя или сервисного аккаунта, инициировавшего операцию.</p> 
modifiedAt | **string** (date-time)<br><p>Время, когда ресурс Operation последний раз обновлялся. Значение в формате <a href="https://www.ietf.org/rfc/rfc3339.txt">RFC3339</a>.</p> <p>Строка в формате <a href="https://www.ietf.org/rfc/rfc3339.txt">RFC3339</a>.</p> 
done | **boolean** (boolean)<br><p>Если значение равно <code>false</code> — операция еще выполняется. Если <code>true</code> — операция завершена, и задано значение одного из полей <code>error</code> или <code>response</code>.</p> 
metadata | **object**<br><p>Метаданные операции. Обычно в поле содержится идентификатор ресурса, над которым выполняется операция. Если метод возвращает ресурс Operation, в описании метода приведена структура соответствующего ему поля <code>metadata</code>.</p> 
error | **object**<br>Описание ошибки в случае сбоя или отмены операции. <br> включает только одно из полей `error`, `response`<br><br><p>Описание ошибки в случае сбоя или отмены операции.</p> 
error.<br>code | **integer** (int32)<br><p>Код ошибки. Значение из списка <a href="https://github.com/googleapis/googleapis/blob/master/google/rpc/code.proto">google.rpc.Code</a>.</p> 
error.<br>message | **string**<br><p>Текст ошибки.</p> 
error.<br>details[] | **object**<br><p>Список сообщений с подробными сведениями об ошибке.</p> 
response | **object** <br> включает только одно из полей `error`, `response`<br><br><p>Результат операции в случае успешного завершения. Если исходный метод не возвращает никаких данных при успешном завершении, например метод Delete, поле содержит объект <a href="https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#empty">google.protobuf.Empty</a>. Если исходный метод — это стандартный метод Create / Update, поле содержит целевой ресурс операции. Если метод возвращает ресурс Operation, в описании метода приведена структура соответствующего ему поля <code>response</code>.</p> 