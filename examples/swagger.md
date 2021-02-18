### Авторизация

Авторизация передаётся в HTTP-заголовке запроса "Authorization", например,  
`Authorization: Basic <authToken>`  
Где `authToken` — закодированная в base64 пара Идентификатор отправителя (id) и Токен отправителя (token), разделенная двоеточием" `(id:token)`

## Letters List Controller Impl :id=letters-list-controller-impl
### <span class='req GET'>GET</span> /api/v1/letters/inbox
Получение списка врученных писем.

##### URL для отправки запроса
`https://erl-partners.test.russianpost.ru/api/v1/letters/inbox`
##### HTTP-заголовки

```
Authorization: Basic <authToken>  
Content-type: application/json
```

##### Параметры запроса

| Наименование            | Расположение | Описание                | Обязательный | Схема данных |
| ----------------------- | ------------ | ----------------------- | ------------ | ------------ |
| hid                     | query        | hid                     | **Да**       | string       |
| externalUserId          | query        | externalUserId          | **Да**       | string       |
| externalSystemMnemonics | query        | externalSystemMnemonics | **Да**       | string       |
| quantity                | query        | quantity                | **Да**       | integer      |
| pagingState             | query        | pagingState             | Нет          | string       |

##### Пример запроса

```bash  
curl --  
```

##### Ответы сервера

| Код | Описание                  | Схема данных                          |
| --- | ------------------------- | ------------------------------------- |
| 200 | OK                        | [LettersListModel](#letterslistmodel) |
| 401 | Unauthorized              |                                       |
| 403 | Forbidden                 |                                       |
| 404 | Пользователь не найден    |                                       |
| 500 | Внутренняя ошибка сервиса |                                       |

##### Пример ответа сервера

```javascript  
{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
```

<hr />

### <span class='req GET'>GET</span> /api/v1/letters/inbox/single/{letterId}
Получение письма по его идентификатору.

##### URL для отправки запроса
`https://erl-partners.test.russianpost.ru/api/v1/letters/inbox/single/{letterId}`
##### HTTP-заголовки

```
Authorization: Basic <authToken>  
Content-type: application/json
```

##### Параметры запроса

| Наименование            | Расположение | Описание                | Обязательный | Схема данных |
| ----------------------- | ------------ | ----------------------- | ------------ | ------------ |
| letterId                | path         | letterId                | **Да**       | string       |
| externalUserId          | query        | externalUserId          | **Да**       | string       |
| externalSystemMnemonics | query        | externalSystemMnemonics | **Да**       | string       |

##### Пример запроса

```bash  
curl --  
```

##### Ответы сервера

| Код | Описание                         | Схема данных                |
| --- | -------------------------------- | --------------------------- |
| 200 | OK                               | [LetterModel](#lettermodel) |
| 400 | Некорректные данные пользователя |                             |
| 401 | Unauthorized                     |                             |
| 403 | Пользователь не найден           |                             |
| 404 | Письмо не найдено                |                             |

##### Пример ответа сервера

```javascript  
{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
```

<hr />

## Settings Controller Impl :id=settings-controller-impl
### <span class='req GET'>GET</span> /api/v1/findUser
Получение параметров пользователя.

##### URL для отправки запроса
`https://erl-partners.test.russianpost.ru/api/v1/findUser`
##### HTTP-заголовки

```
Authorization: Basic <authToken>  
Content-type: application/json
```

##### Параметры запроса

| Наименование            | Расположение | Описание                | Обязательный | Схема данных |
| ----------------------- | ------------ | ----------------------- | ------------ | ------------ |
| hid                     | query        | hid                     | **Да**       | string       |
| externalSystemMnemonics | query        | externalSystemMnemonics | **Да**       | string       |
| externalUserId          | query        | externalUserId          | **Да**       | string       |

##### Пример запроса

```bash  
curl --  
```

##### Ответы сервера

| Код | Описание                  | Схема данных            |
| --- | ------------------------- | ----------------------- |
| 200 | OK                        | [UserModel](#usermodel) |
| 401 | Unauthorized              |                         |
| 403 | Forbidden                 |                         |
| 404 | Пользователь не найден    |                         |
| 500 | Внутренняя ошибка сервиса |                         |

##### Пример ответа сервера

```javascript  
{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
```

<hr />

### <span class='req PUT'>PUT</span> /api/v1/settings/addresses
Обновление адресов пользователя

##### URL для отправки запроса
`https://erl-partners.test.russianpost.ru/api/v1/settings/addresses`
##### HTTP-заголовки

```
Authorization: Basic <authToken>  
Content-type: application/json
```

##### Параметры запроса

| Наименование        | Расположение | Описание            | Обязательный | Схема данных                                |
| ------------------- | ------------ | ------------------- | ------------ | ------------------------------------------- |
| updateAddressesData | body         | updateAddressesData | **Да**       | [UpdateAddressesData](#updateaddressesdata) |

##### Пример запроса

```bash  
curl --  
```

##### Ответы сервера

| Код | Описание                                                  | Схема данных                    |
| --- | --------------------------------------------------------- | ------------------------------- |
| 200 | OK                                                        |                                 |
| 201 | Created                                                   |                                 |
| 400 | Некорректный запрос или адреса не валидны или дублируются | [ErrorResponse](#errorresponse) |
| 401 | Unauthorized                                              |                                 |
| 403 | Forbidden                                                 |                                 |
| 404 | Not Found                                                 |                                 |
| 500 | Внутренняя ошибка сервиса                                 |                                 |

##### Пример ответа сервера

```javascript  
{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
```

<hr />

### <span class='req POST'>POST</span> /api/v1/settings/addresses/validation
Валидация адресов пользователя

##### URL для отправки запроса
`https://erl-partners.test.russianpost.ru/api/v1/settings/addresses/validation`
##### HTTP-заголовки

```
Authorization: Basic <authToken>  
Content-type: application/json
```

##### Параметры запроса

| Наименование          | Расположение | Описание              | Обязательный | Схема данных                                    |
| --------------------- | ------------ | --------------------- | ------------ | ----------------------------------------------- |
| validateAddressesData | body         | validateAddressesData | **Да**       | [ValidateAddressesData](#validateaddressesdata) |

##### Пример запроса

```bash  
curl --  
```

##### Ответы сервера

| Код | Описание                                  | Схема данных                                            |
| --- | ----------------------------------------- | ------------------------------------------------------- |
| 200 | Адреса валидны                            | [ValidateAddressesResponse](#validateaddressesresponse) |
| 201 | Created                                   |                                                         |
| 400 | Некорректный запрос или адреса не валидны | [ErrorResponse](#errorresponse)                         |
| 401 | Unauthorized                              |                                                         |
| 403 | Forbidden                                 |                                                         |
| 404 | Not Found                                 |                                                         |
| 413 | Превышен допустимый размер входных данных | [ErrorResponse](#errorresponse)                         |
| 414 | Превышена допустимая длина запроса        | [ErrorResponse](#errorresponse)                         |
| 500 | Внутренняя ошибка сервиса                 |                                                         |

##### Пример ответа сервера

```javascript  
{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
```

<hr />

### <span class='req POST'>POST</span> /api/v1/settings/subscribe
Включение услуги электронной доставки писем

##### URL для отправки запроса
`https://erl-partners.test.russianpost.ru/api/v1/settings/subscribe`
##### HTTP-заголовки

```
Authorization: Basic <authToken>  
Content-type: application/json
```

##### Параметры запроса

| Наименование     | Расположение | Описание         | Обязательный | Схема данных                          |
| ---------------- | ------------ | ---------------- | ------------ | ------------------------------------- |
| subscriptionData | body         | subscriptionData | **Да**       | [SubscriptionData](#subscriptiondata) |

##### Пример запроса

```bash  
curl --  
```

##### Ответы сервера

| Код | Описание                  | Схема данных                    |
| --- | ------------------------- | ------------------------------- |
| 200 | OK                        |                                 |
| 201 | Created                   |                                 |
| 400 | Некорректный запрос       | [ErrorResponse](#errorresponse) |
| 401 | Unauthorized              |                                 |
| 403 | Forbidden                 |                                 |
| 404 | Not Found                 |                                 |
| 409 | Услуга уже включена       | [ErrorResponse](#errorresponse) |
| 500 | Внутренняя ошибка сервиса |                                 |

##### Пример ответа сервера

```javascript  
{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
```

<hr />

### <span class='req POST'>POST</span> /api/v1/settings/unsubscribe
Выключение услуги электронной доставки писем

##### URL для отправки запроса
`https://erl-partners.test.russianpost.ru/api/v1/settings/unsubscribe`
##### HTTP-заголовки

```
Authorization: Basic <authToken>  
Content-type: application/json
```

##### Параметры запроса

| Наименование     | Расположение | Описание         | Обязательный | Схема данных                          |
| ---------------- | ------------ | ---------------- | ------------ | ------------------------------------- |
| subscriptionData | body         | subscriptionData | **Да**       | [SubscriptionData](#subscriptiondata) |

##### Пример запроса

```bash  
curl --  
```

##### Ответы сервера

| Код | Описание                  | Схема данных                    |
| --- | ------------------------- | ------------------------------- |
| 200 | OK                        |                                 |
| 201 | Created                   |                                 |
| 400 | Некорректный запрос       | [ErrorResponse](#errorresponse) |
| 401 | Unauthorized              |                                 |
| 403 | Forbidden                 |                                 |
| 404 | Not Found                 |                                 |
| 409 | Услуга уже отключена      | [ErrorResponse](#errorresponse) |
| 500 | Внутренняя ошибка сервиса |                                 |

##### Пример ответа сервера

```javascript  
{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
```

<hr />

## Letter Download Pdf Controller Impl :id=letter-download-pdf-controller-impl
### <span class='req GET'>GET</span> /api/v1/download/letter/{letterId}
Доступ к письму по ссылке

##### URL для отправки запроса
`https://erl-partners.test.russianpost.ru/api/v1/download/letter/{letterId}`
##### HTTP-заголовки

```
Authorization: Basic <authToken>  
Content-type: application/json
```

##### Параметры запроса

| Наименование            | Расположение | Описание                | Обязательный | Схема данных |
| ----------------------- | ------------ | ----------------------- | ------------ | ------------ |
| hids                    | query        | hids                    | **Да**       | [ string ]   |
| externalSystemMnemonics | query        | externalSystemMnemonics | **Да**       | string       |
| externalUserId          | query        | externalUserId          | **Да**       | string       |
| letterId                | path         | letterId                | **Да**       | string       |
| code                    | query        | code                    | **Да**       | string       |
| storageId               | query        | storageId               | **Да**       | string       |

##### Пример запроса

```bash  
curl --  
```

##### Ответы сервера

| Код | Описание                                       | Схема данных |
| --- | ---------------------------------------------- | ------------ |
| 200 | OK                                             | object       |
| 400 | Некорректный запрос                            |              |
| 401 | Unauthorized                                   |              |
| 403 | Пользователь не имеет доступа к данному письму |              |
| 404 | Not Found                                      |              |
| 500 | Внутренняя ошибка сервиса                      |              |

##### Пример ответа сервера

```javascript  
{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
```

<hr />

## Registration Controller Impl :id=registration-controller-impl
### <span class='req POST'>POST</span> /api/v1/bindingUser
Включить услугу электронной доставки госпочты через REST-API. Получить идентификатор пользователя в системе почты.

##### URL для отправки запроса
`https://erl-partners.test.russianpost.ru/api/v1/bindingUser`
##### HTTP-заголовки

```
Authorization: Basic <authToken>  
Content-type: application/json
```

##### Параметры запроса

| Наименование | Расположение | Описание     | Обязательный | Схема данных                  |
| ------------ | ------------ | ------------ | ------------ | ----------------------------- |
| bindUserData | body         | bindUserData | **Да**       | [BindUserData](#binduserdata) |

##### Пример запроса

```bash  
curl --  
```

##### Ответы сервера

| Код | Описание                                        | Схема данных                    |
| --- | ----------------------------------------------- | ------------------------------- |
| 200 | Идентификатор пользователя в системе почты      | string                          |
| 201 | Created                                         |                                 |
| 400 | Некорректный запрос                             | [ErrorResponse](#errorresponse) |
| 401 | Пользователь не зарегистрирован в системе почты | [ErrorResponse](#errorresponse) |
| 403 | Forbidden                                       |                                 |
| 404 | Not Found                                       |                                 |
| 500 | Внутренняя ошибка сервиса                       |                                 |

##### Пример ответа сервера

```javascript  
{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
```

<hr />

### <span class='req GET'>GET</span> /api/v1/client/registration/prepare
Подключение Госпочты. Регистрация пользователя в системе почты через Web-авторизацию в ЕСИА.

##### URL для отправки запроса
`https://erl-partners.test.russianpost.ru/api/v1/client/registration/prepare`
##### HTTP-заголовки

```
Authorization: Basic <authToken>  
Content-type: application/json
```

##### Параметры запроса

| Наименование            | Расположение | Описание                | Обязательный | Схема данных |
| ----------------------- | ------------ | ----------------------- | ------------ | ------------ |
| externalUserId          | query        | externalUserId          | **Да**       | string       |
| externalSystemMnemonics | query        | externalSystemMnemonics | **Да**       | string       |
| requestId               | query        | requestId               | Нет          | string       |
| redirectUrl             | query        | redirectUrl             | **Да**       | string       |

##### Пример запроса

```bash  
curl --  
```

##### Ответы сервера

| Код | Описание                  | Схема данных                      |
| --- | ------------------------- | --------------------------------- |
| 200 | OK                        | [ResponseEntity](#responseentity) |
| 400 | Некорректный запрос       |                                   |
| 401 | Unauthorized              |                                   |
| 403 | Forbidden                 |                                   |
| 404 | Not Found                 |                                   |
| 500 | Внутренняя ошибка сервиса |                                   |

##### Пример ответа сервера

```javascript  
{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
```

<hr />

### <span class='req GET'>GET</span> /api/v1/client/registration/prepare/fio
Подключение Госпочты. Регистрация пользователя в системе почты через Web-авторизацию в ЕСИА с предоставлением ФИО.

##### URL для отправки запроса
`https://erl-partners.test.russianpost.ru/api/v1/client/registration/prepare/fio`
##### HTTP-заголовки

```
Authorization: Basic <authToken>  
Content-type: application/json
```

##### Параметры запроса

| Наименование            | Расположение | Описание                | Обязательный | Схема данных |
| ----------------------- | ------------ | ----------------------- | ------------ | ------------ |
| externalUserId          | query        | externalUserId          | Нет          | string       |
| externalSystemMnemonics | query        | externalSystemMnemonics | Нет          | string       |
| lastName                | query        | lastName                | Нет          | string       |
| firstName               | query        | firstName               | Нет          | string       |
| middleName              | query        | middleName              | Нет          | string       |
| redirectUrl             | query        | redirectUrl             | Нет          | string       |

##### Пример запроса

```bash  
curl --  
```

##### Ответы сервера

| Код | Описание                  | Схема данных                      |
| --- | ------------------------- | --------------------------------- |
| 200 | OK                        | [ResponseEntity](#responseentity) |
| 400 | Некорректный запрос       |                                   |
| 401 | Unauthorized              |                                   |
| 403 | Forbidden                 |                                   |
| 404 | Not Found                 |                                   |
| 500 | Внутренняя ошибка сервиса |                                   |

##### Пример ответа сервера

```javascript  
{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
```

<hr />

### <span class='req GET'>GET</span> /api/v1/client/registration/prepare/passport
Подключение Госпочты. Регистрация пользователя в системе почты через Web-авторизацию в ЕСИА с предоставлением паспортных данных.

##### URL для отправки запроса
`https://erl-partners.test.russianpost.ru/api/v1/client/registration/prepare/passport`
##### HTTP-заголовки

```
Authorization: Basic <authToken>  
Content-type: application/json
```

##### Параметры запроса

| Наименование            | Расположение | Описание                | Обязательный | Схема данных |
| ----------------------- | ------------ | ----------------------- | ------------ | ------------ |
| externalUserId          | query        | externalUserId          | Нет          | string       |
| externalSystemMnemonics | query        | externalSystemMnemonics | Нет          | string       |
| series                  | query        | series                  | Нет          | string       |
| number                  | query        | number                  | Нет          | string       |
| redirectUrl             | query        | redirectUrl             | Нет          | string       |

##### Пример запроса

```bash  
curl --  
```

##### Ответы сервера

| Код | Описание                  | Схема данных                      |
| --- | ------------------------- | --------------------------------- |
| 200 | OK                        | [ResponseEntity](#responseentity) |
| 400 | Некорректный запрос       |                                   |
| 401 | Unauthorized              |                                   |
| 403 | Forbidden                 |                                   |
| 404 | Not Found                 |                                   |
| 500 | Внутренняя ошибка сервиса |                                   |

##### Пример ответа сервера

```javascript  
{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
```

<hr />

### <span class='req GET'>GET</span> /api/v1/client/registration/prepare/snils
Подключение Госпочты. Регистрация пользователя в системе почты через Web-авторизацию в ЕСИА с предоставлением СНИЛС.

##### URL для отправки запроса
`https://erl-partners.test.russianpost.ru/api/v1/client/registration/prepare/snils`
##### HTTP-заголовки

```
Authorization: Basic <authToken>  
Content-type: application/json
```

##### Параметры запроса

| Наименование            | Расположение | Описание                | Обязательный | Схема данных |
| ----------------------- | ------------ | ----------------------- | ------------ | ------------ |
| externalUserId          | query        | externalUserId          | Нет          | string       |
| externalSystemMnemonics | query        | externalSystemMnemonics | Нет          | string       |
| snils                   | query        | snils                   | Нет          | string       |
| redirectUrl             | query        | redirectUrl             | Нет          | string       |

##### Пример запроса

```bash  
curl --  
```

##### Ответы сервера

| Код | Описание                  | Схема данных                      |
| --- | ------------------------- | --------------------------------- |
| 200 | OK                        | [ResponseEntity](#responseentity) |
| 400 | Некорректный запрос       |                                   |
| 401 | Unauthorized              |                                   |
| 403 | Forbidden                 |                                   |
| 404 | Not Found                 |                                   |
| 500 | Внутренняя ошибка сервиса |                                   |

##### Пример ответа сервера

```javascript  
{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
```

<hr />

### <span class='req POST'>POST</span> /api/v1/unbindingUser
Отключить услугу электронной доставки почты во внешнюю систему через REST-API. Получить идентификатор пользователя в системе почты.

##### URL для отправки запроса
`https://erl-partners.test.russianpost.ru/api/v1/unbindingUser`
##### HTTP-заголовки

```
Authorization: Basic <authToken>  
Content-type: application/json
```

##### Параметры запроса

| Наименование   | Расположение | Описание       | Обязательный | Схема данных                      |
| -------------- | ------------ | -------------- | ------------ | --------------------------------- |
| unbindUserData | body         | unbindUserData | **Да**       | [UnbindUserData](#unbinduserdata) |

##### Пример запроса

```bash  
curl --  
```

##### Ответы сервера

| Код | Описание                                                          | Схема данных                    |
| --- | ----------------------------------------------------------------- | ------------------------------- |
| 200 | Идентификатор пользователя в системе почты                        | string                          |
| 201 | Created                                                           |                                 |
| 400 | Некорректный запрос                                               | [ErrorResponse](#errorresponse) |
| 401 | Пользователь не зарегистрирован в системе почты                   | [ErrorResponse](#errorresponse) |
| 403 | Forbidden                                                         |                                 |
| 404 | Not Found                                                         |                                 |
| 409 | У пользователя уже отключена услуга электронной доставки госпочты | [ErrorResponse](#errorresponse) |
| 500 | Внутренняя ошибка сервиса                                         |                                 |

##### Пример ответа сервера

```javascript  
{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
```

<hr />

## Схемы данных

### BankRequisites

Реквизиты банка получателя платежа

| Наименование         | Тип    | Описание               | Обязательное |
| -------------------- | ------ | ---------------------- | ------------ |
| bankName             | string | Наименование банка     | **Да**       |
| bik                  | string | БИК                    | **Да**       |
| correspondingAccount | string | Корреспондентский счёт | Нет          |

### Address

Адрес

| Наименование | Тип    | Описание            | Обязательное |
| ------------ | ------ | ------------------- | ------------ |
| address      | string | Адрес в виде строки | **Да**       |
| hid          | string | Hid адреса          | Нет          |

### UpdateAddressesData

Параметры обновления адресов пользователя

| Наименование            | Тип                     | Описание                                      | Обязательное |
| ----------------------- | ----------------------- | --------------------------------------------- | ------------ |
| addresses               | [ [Address](#address) ] | Список адресов                                | **Да**       |
| externalSystemMnemonics | string                  | Мнемоника внешней системы                     | **Да**       |
| externalUserId          | string                  | Идентификатор пользователя во внешней системе | **Да**       |
| hid                     | string                  | Идентификатор пользователя в системе почты    | **Да**       |
| requestId               | string                  | Идентификатор запроса                         | Нет          |

### BindUserData

Параметры для обновления данных, получения почтового идентификатора

| Наименование            | Тип    | Описание                                      | Обязательное |
| ----------------------- | ------ | --------------------------------------------- | ------------ |
| externalSystemMnemonics | string | Мнемоника внешней системы                     | **Да**       |
| externalUserId          | string | Идентификатор пользователя во внешней системе | **Да**       |

### ValidateAddressesResponse

Результат валидации адресов

| Наименование     | Тип                                   | Описание                                              | Обязательное |
| ---------------- | ------------------------------------- | ----------------------------------------------------- | ------------ |
| allValid         | boolean                               | Являются ли все адреса валидными<br>_Пример:_ `false` | Нет          |
| invalidAddresses | [ [InvalidAddress](#invalidaddress) ] | Невалидные адреса                                     | Нет          |
| validAddresses   | [ [Address](#address) ]               | Валидные адреса                                       | Нет          |

### ErrorResponse

Ошибки выполнения запроса

| Наименование | Тип        | Описание                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Обязательное |
| ------------ | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ |
| errors       | [ string ] | Описание ошибок                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Нет          |
| message      | string     | Сообщение                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Нет          |
| redirectUrl  | string     | Урл возврата во внешнюю систему                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Нет          |
| status       | string     | Статус<br>_Перечисление:_ `"100"`, `"101"`, `"102"`, `"103"`, `"200"`, `"201"`, `"202"`, `"203"`, `"204"`, `"205"`, `"206"`, `"207"`, `"208"`, `"226"`, `"300"`, `"301"`, `"302"`, `"303"`, `"304"`, `"305"`, `"307"`, `"308"`, `"400"`, `"401"`, `"402"`, `"403"`, `"404"`, `"405"`, `"406"`, `"407"`, `"408"`, `"409"`, `"410"`, `"411"`, `"412"`, `"413"`, `"414"`, `"415"`, `"416"`, `"417"`, `"418"`, `"419"`, `"420"`, `"421"`, `"422"`, `"423"`, `"424"`, `"426"`, `"428"`, `"429"`, `"431"`, `"451"`, `"500"`, `"501"`, `"502"`, `"503"`, `"504"`, `"505"`, `"506"`, `"507"`, `"508"`, `"509"`, `"510"`, `"511"` | Нет          |

### UserModel

Модель пользователя

| Наименование    | Тип                     | Описание                                                         | Обязательное |
| --------------- | ----------------------- | ---------------------------------------------------------------- | ------------ |
| addresses       | [ [Address](#address) ] | Список адресов                                                   | **Да**       |
| deliveryEnabled | boolean                 | Статус услуги<br>_Пример:_ `false`                               | **Да**       |
| hid             | string                  | Уникальный идентификатор пользователя                            | **Да**       |
| isUserBound     | boolean                 | Статус услуги для указанной внешней системы<br>_Пример:_ `false` | **Да**       |

### UnbindUserData

Параметры для отключения электронной доставки госпочты

| Наименование            | Тип    | Описание                                      | Обязательное |
| ----------------------- | ------ | --------------------------------------------- | ------------ |
| externalSystemMnemonics | string | Мнемоника внешней системы                     | **Да**       |
| externalUserId          | string | Идентификатор пользователя во внешней системе | **Да**       |

### Payment

Атрибуты платежа

| Наименование        | Тип    | Описание                                    | Обязательное |
| ------------------- | ------ | ------------------------------------------- | ------------ |
| amount              | number | Первоначальная сумма платежа                | Нет          |
| deadline            | string | Срок оплаты                                 | **Да**       |
| discountEndTime     | string | Срок истечения скидки                       | Нет          |
| discountPercentages | number | Процент скидки (от первоначальной суммы)    | Нет          |
| discountSumm        | number | Сумма скидки                                | Нет          |
| dueDate             | string | Срок оплаты                                 | Нет          |
| inn                 | string | ИНН                                         | **Да**       |
| kbk                 | string | КБК                                         | **Да**       |
| kpp                 | string | КПП                                         | **Да**       |
| name                | string | Наименование платежа                        | **Да**       |
| oktmo               | string | ОКТМО                                       | **Да**       |
| operatingAccount    | string | Расчётный счёт                              | **Да**       |
| paidSumm            | number | Оплаченная сумма                            | Нет          |
| period              | string | Период оплаты платежа                       | Нет          |
| receiver            | string | Получатель платежа                          | **Да**       |
| status              | string | Статус оплаты                               | **Да**       |
| statusUniteller     | string | Статус оплаты в системе оплаты Uniteller    | Нет          |
| totalSumm           | number | Сумма итоговая, с учетом скидок и предоплат | **Да**       |
| type                | string | Тип платежа                                 | Нет          |
| uniqueNumber        | string | УИН платежа                                 | **Да**       |

### ResponseEntity

| Наименование    | Тип     | Описание                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Обязательное |
| --------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| body            | object  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Нет          |
| statusCode      | string  | _Перечисление:_ `"100"`, `"101"`, `"102"`, `"103"`, `"200"`, `"201"`, `"202"`, `"203"`, `"204"`, `"205"`, `"206"`, `"207"`, `"208"`, `"226"`, `"300"`, `"301"`, `"302"`, `"303"`, `"304"`, `"305"`, `"307"`, `"308"`, `"400"`, `"401"`, `"402"`, `"403"`, `"404"`, `"405"`, `"406"`, `"407"`, `"408"`, `"409"`, `"410"`, `"411"`, `"412"`, `"413"`, `"414"`, `"415"`, `"416"`, `"417"`, `"418"`, `"419"`, `"420"`, `"421"`, `"422"`, `"423"`, `"424"`, `"426"`, `"428"`, `"429"`, `"431"`, `"451"`, `"500"`, `"501"`, `"502"`, `"503"`, `"504"`, `"505"`, `"506"`, `"507"`, `"508"`, `"509"`, `"510"`, `"511"` | Нет          |
| statusCodeValue | integer |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Нет          |

### GibddData

Атрибуты писем от ГИБДД

| Наименование     | Тип    | Описание                                           | Обязательное |
| ---------------- | ------ | -------------------------------------------------- | ------------ |
| address          | string | Адрес нарушения                                    | Нет          |
| carNumber        | string | Номер машины                                       | **Да**       |
| date             | string | Дата нарушения                                     | **Да**       |
| deadline         | string | Срок оплаты штрафа                                 | Нет          |
| description      | string | Описание нарушения                                 | Нет          |
| photoUrl         | string | Фото нарушения                                     | Нет          |
| sts              | string | Свидетельство о регистрации транспортного средства | Нет          |
| violation        | string | Нарушение                                          | Нет          |
| violationAddress | string | Адрес нарушения                                    | Нет          |
| violationDate    | string | Дата нарушения                                     | Нет          |

### InvalidAddress

 Невалидный адрес

| Наименование | Тип                                     | Описание             | Обязательное |
| ------------ | --------------------------------------- | -------------------- | ------------ |
| address      | string                                  | Адрес в виде строки  | **Да**       |
| errors       | [ [ValidationError](#validationerror) ] | Список ошибок        | **Да**       |
| hid          | string                                  | Идентификатор адреса | Нет          |

### PaperData

Атрибуты писем от Ф22

| Наименование       | Тип        | Описание                          | Обязательное |
| ------------------ | ---------- | --------------------------------- | ------------ |
| deliveryDate       | string     | Дата вручения                     | Нет          |
| expiryDate         | string     | Срок хранения отправления         | Нет          |
| latitude           | double     | Широта                            | Нет          |
| longitude          | double     | Долгота                           | Нет          |
| mailType           | string     | Тип посылки                       | Нет          |
| postOfficeAddress  | string     | Адрес почтового отделения         | Нет          |
| postOfficeContacts | [ string ] | Телефоны почтового отделения      | Нет          |
| postOfficeSchedule | string     | График работы почтового отделения | Нет          |
| postOfficeType     | string     | Тип отделения                     | Нет          |
| returnDate         | string     | Дата возврата                     | Нет          |
| senderName         | string     | Имя отправителя                   | **Да**       |
| summCashOnDelivery | long       | Сумма оплаты                      | Нет          |
| summInsured        | long       | Сумма страховки                   | Нет          |
| trackNumber        | string     | Трек-номер посылки                | Нет          |
| weightGr           | integer    | Вес посылки в граммах             | Нет          |
| weightKg           | integer    | Вес посылки в килограммах         | Нет          |

### SubscriptionData

Параметры для подключения, отключения услуги

| Наименование            | Тип    | Описание                                      | Обязательное |
| ----------------------- | ------ | --------------------------------------------- | ------------ |
| externalSystemMnemonics | string | Мнемоника внешней системы                     | **Да**       |
| externalUserId          | string | Идентификатор пользователя во внешней системе | **Да**       |
| hid                     | string | Идентификатор пользователя в системе почты    | **Да**       |
| platform                | string | Платформа (ОС)                                | Нет          |
| requestId               | string | Идентификатор запроса                         | Нет          |

### LettersListModel

Модель списка писем

| Наименование      | Тип                             | Описание                                   | Обязательное |
| ----------------- | ------------------------------- | ------------------------------------------ | ------------ |
| letters           | [ [LetterModel](#lettermodel) ] | Список писем                               | Нет          |
| moreDataAvailable | boolean                         | Имеются ли ещё письма<br>_Пример:_ `false` | **Да**       |
| pagingState       | string                          | Статус паджинации                          | Нет          |

### LetterModel

Модель письма

| Наименование           | Тип                               | Описание                                                                                                                                                                     | Обязательное |
| ---------------------- | --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| attention              | boolean                           | Непрочитанное<br>_Пример:_ `false`                                                                                                                                           | Нет          |
| code                   | string                            | Код для получения PDF письма                                                                                                                                                 | **Да**       |
| documentNumber         | string                            | Номер исходящего электронного документа у отправителя                                                                                                                        | **Да**       |
| finalStatus            | string                            | Финальный статус письма (Вручено либо возвращено)                                                                                                                            | **Да**       |
| finalStatusTimestamp   | string                            | Дата получения финального статуса письма PDF во внутреннем хранилище                                                                                                         | **Да**       |
| gibddData              | [GibddData](#gibdddata)           | Атрибуты писем от ГИБДД                                                                                                                                                      | Нет          |
| hid                    | string                            | Идентификатор пользователя в системе почты                                                                                                                                   | **Да**       |
| id                     | string                            | Идентификатор карточки письма, включает в себя трек-номер письма                                                                                                             | **Да**       |
| issueDate              | string                            | Дата поступления письма в ИС ЭПС(по ней идет сортирвка данных )                                                                                                              | **Да**       |
| paperData              | [PaperData](#paperdata)           | Атрибуты для извещений Ф22                                                                                                                                                   | Нет          |
| payment                | [Payment](#payment)               | Атрибуты платежа                                                                                                                                                             | Нет          |
| pdfStorageId           | string                            | Идентификатор PDF во внутреннем хранилище                                                                                                                                    | **Да**       |
| provider               | string                            | Идентификатор отправителя письма<br>_Перечисление:_ `"GIBDD"`, `"FSSP"`, `"PR"`, `"OTHER"`, `"SMEV"`, `"EZP"`                                                                | **Да**       |
| receiverBankRequisites | [BankRequisites](#bankrequisites) | Реквизиты банка получателя платежа                                                                                                                                           | Нет          |
| recipient              | string                            | Получатель                                                                                                                                                                   | **Да**       |
| recipientAddress       | string                            | Адрес получателя                                                                                                                                                             | **Да**       |
| recipientIndex         | string                            | Индекс получателя                                                                                                                                                            | **Да**       |
| registeredDate         | string                            | Дата регистрации исходящего электронного документа у отправителя                                                                                                             | **Да**       |
| senderAddressIndex     | string                            | Индекс отправителя                                                                                                                                                           | Нет          |
| senderName             | string                            | Имя отправителя полное                                                                                                                                                       | **Да**       |
| shortSenderTitle       | string                            | Имя отправителя сокращенное                                                                                                                                                  | Нет          |
| title                  | string                            | Заголовок письма                                                                                                                                                             | Нет          |
| trackNumber            | string                            | Трек-номер письма. Может быть в форматах: 1) РТМ0001 (внутрироссийский), напр. '80080152000048';2) S10 (международный), напр. 'RN000005011RU';3) UUID (простые отправления); | **Да**       |
| type                   | string                            | Тип письма<br>_Перечисление:_ `"REGISTERED"`, `"REGULAR"`, `"F22"`                                                                                                           | **Да**       |

### ValidateAddressesData

Параметры валидации адресов пользователя

| Наименование            | Тип                     | Описание                                      | Обязательное |
| ----------------------- | ----------------------- | --------------------------------------------- | ------------ |
| addresses               | [ [Address](#address) ] | Список адресов                                | **Да**       |
| externalSystemMnemonics | string                  | Мнемоника внешней системы                     | **Да**       |
| externalUserId          | string                  | Идентификатор пользователя во внешней системе | **Да**       |

### ValidationError

Ошибка валидации

| Наименование | Тип    | Описание        | Обязательное |
| ------------ | ------ | --------------- | ------------ |
| errorCode    | string | Код ошибки      | Нет          |
| message      | string | Описание ошибки | Нет          |
| validString  | string | Подсказка       | Нет          |
