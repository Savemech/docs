# Метод attachDisk
Присоединяет диск к виртуальной машине.
 

 
## HTTP-запрос
`POST /compute/v1/instances/{instanceId}:attachDisk`
 
## Path-параметры {#path_params}
 
Name | Description
--- | ---
instanceId | Обязательное поле. Идентификатор виртуальной машины для подключения диска. Чтобы получить идентификатор виртуальной машины, используйте запрос [list](/docs/compute/api-ref/Instance/list).  Максимальная длина — 50 символов.
 
## Параметры в теле запроса {#body_params}
 
```json 
 {
  "attachedDiskSpec": {
    "mode": "string",
    "deviceName": "string",
    "autoDelete": true,

    // `attachedDiskSpec`включает только одно из полей `diskSpec`, `diskId`
    "diskSpec": {
      "name": "string",
      "description": "string",
      "typeId": "string",
      "size": "string",

      // `attachedDiskSpec.diskSpec`включает только одно из полей `imageId`, `snapshotId`
      "imageId": "string",
      "snapshotId": "string",
      // конец списка возможных полей`attachedDiskSpec.diskSpec`

    },
    "diskId": "string",
    // конец списка возможных полей`attachedDiskSpec`

  }
}
```

 
Поле | Описание
--- | ---
attachedDiskSpec | **object**<br><p>Обязательное поле. Диск, который должен быть подключен.</p> 
attachedDiskSpec.<br>mode | **string**<br><ul> <li>READ_ONLY: Доступ на чтение.</li> <li>READ_WRITE: Доступ на чтение и запись.</li> </ul> 
attachedDiskSpec.<br>deviceName | **string**<br><p>Задает уникальный серийный номер, который на виртуальной машине с операционной системой Linux отображается в директории /dev/disk/by-id/.</p> <p>Это значение может использоваться для ссылки на устройство внутри виртуальной машины при монтировании, изменении размера и т. д. Если не указано, будет сгенерировано случайное значение.</p> <p>Значение должно соответствовать регулярному выражению <code>[a-z][a-z0-9-_]{,19}</code>.</p> 
attachedDiskSpec.<br>autoDelete | **boolean** (boolean)<br><p>Указывает, должен ли диск автоматически удалиться при удалении виртуальной машины.</p> 
attachedDiskSpec.<br>diskSpec | **object** <br>`attachedDiskSpec` включает только одно из полей `diskSpec`, `diskId`<br><br>
attachedDiskSpec.<br>diskSpec.<br>name | **string**<br><p>Имя диска.</p> <p>Значение должно быть длиной от 3 до 63 символов и соответствовать регулярному выражению <code>^[a-z][-a-z0-9]{1,61}[a-z0-9]$</code>.</p> 
attachedDiskSpec.<br>diskSpec.<br>description | **string**<br><p>Описание диска.</p> <p>Максимальная длина — 256 символов.</p> 
attachedDiskSpec.<br>diskSpec.<br>typeId | **string**<br><p>Идентификатор типа диска. Чтобы получить список доступных типов дисков, используйте запрос <a href="/docs/compute/api-ref/DiskType/list">list</a>.</p> <p>Максимальная длина — 50 символов.</p> 
attachedDiskSpec.<br>diskSpec.<br>size | **string** (int64)<br><p>Обязательное поле. Размер диска в байтах.</p> <p>Допустимые значения — от 4194304 до 4398046511104 включительно.</p> 
attachedDiskSpec.<br>diskSpec.<br>imageId | **string** <br>`attachedDiskSpec.diskSpec` включает только одно из полей `imageId`, `snapshotId`<br><br><p>Идентификатор образа для создания диска из него.</p> <p>Максимальная длина — 50 символов.</p> 
attachedDiskSpec.<br>diskSpec.<br>snapshotId | **string** <br>`attachedDiskSpec.diskSpec` включает только одно из полей `imageId`, `snapshotId`<br><br><p>Идентификатор снимка для восстановления диска из него.</p> <p>Максимальная длина — 50 символов.</p> 
attachedDiskSpec.<br>diskId | **string** <br>`attachedDiskSpec` включает только одно из полей `diskSpec`, `diskId`<br><br><p>ID диска, который должен быть подключен.</p> <p>Максимальная длина — 50 символов.</p> 
 
## Ответ {#responses}
**HTTP Code: 200 - OK**

Ресурс Operation. Дополнительные сведения см. в разделе
[Объект Operation](/docs/api-design-guide/concepts/operation).
 
Поле | Описание
--- | ---
id | **string**<br><p>Идентификатор операции.</p> 
description | **string**<br><p>Описание операции. Длина описания должна быть от 0 до 256 символов.</p> 
createdAt | **string** (date-time)<br><p>Время создания ресурса в формате в <a href="https://www.ietf.org/rfc/rfc3339.txt">RFC3339</a>.</p> 
createdBy | **string**<br><p>Идентификатор пользователя или сервисного аккаунта, инициировавшего операцию.</p> 
modifiedAt | **string** (date-time)<br><p>Время, когда ресурс Operation последний раз обновлялся. Значение в формате <a href="https://www.ietf.org/rfc/rfc3339.txt">RFC3339</a>.</p> 
done | **boolean** (boolean)<br><p>Если значение равно <code>false</code> — операция еще выполняется. Если <code>true</code> — операция завершена, и задано значение одного из полей <code>error</code> или <code>response</code>.</p> 
metadata | **object**<br><p>Метаданные операции. Обычно в поле содержится идентификатор ресурса, над которым выполняется операция. Если метод возвращает ресурс Operation, в описании метода приведена структура соответствующего ему поля <code>metadata</code>.</p> 
error | **object** <br> включает только одно из полей `error`, `response`<br><br><p>Описание ошибки в случае сбоя или отмены операции.</p> 
error.<br>code | **integer** (int32)<br><p>Код ошибки. Значение из списка <a href="https://github.com/googleapis/googleapis/blob/master/google/rpc/code.proto">google.rpc.Code</a>.</p> 
error.<br>message | **string**<br><p>Текст ошибки.</p> 
error.<br>details | **object**<br><p>Список сообщений с подробными сведениями об ошибке.</p> 
response | **object** <br> включает только одно из полей `error`, `response`<br><br><p>Результат операции в случае успешного завершения. Если исходный метод не возвращает никаких данных при успешном завершении, например метод Delete, поле содержит объект <a href="https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#empty">google.protobuf.Empty</a>. Если исходный метод — это стандартный метод Create / Update, поле содержит целевой ресурс операции. Если метод возвращает ресурс Operation, в описании метода приведена структура соответствующего ему поля <code>response</code>.</p> 