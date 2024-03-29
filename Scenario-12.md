# Сценарий "Формирование заказа"

<!-- К сожалению, сценарии были описаны в апреле прошлого года на Confluence, и аккаунт там конечно блокнули. 
  За прошедшее время я и работу поменял, и добраться до текстовых копий сценария представляет некоторую проблему...
  Моя новая должность - технический писатель, основной инструмент - markdown в VSCode :)
  Описание сценария я сейчас могу дать несколько "фантазийное": я плохо помню как выглядели рабочие сценарии.
  Надеюсь, что для этого конкретного модуля логика сценария не очень важна; если я заблуждаюсь - я готов позже переделать документ 
  -->
  
## Акторы в сценарии

* Авторизованный клиент (*Клиент*).
* Функциональная подсистема оформления заказа (*Система*).

## Основной сценарий

  1. *Система* предоставляет *Клиенту* возможность сформировать корзину заказов.
  2. *Клиент* сообщает *Системе* о завершении формирования корзины.
  3. *Система* предлагает *Клиенту* выбрать время/дату доставки.
  4. *Клиент* выбирает дату доставки заказа.
     * Альтернативный сценарий 4а.
     * Прерывание сценария 4б.
  5. *Система* предлагает *Клиенту* выбрать адрес доставки.
  6. *Клиент* выбирает адрес доставки.
     * Альтернативный сценарий 6а.
     * Прерывание сценария 6б.
  8. *Система* предлагает *Клиенту* выбрать способ оплаты.
  9. *Клиент* выбирает способ оплаты "картой при получении".
     * Альтернативный сценарий 8а.
     * Альтернативный сценарий 8б.
     * Прерывание сценария 8в. 
  11. *Система* выводит информирующее окно, финализирует заказ и завершает работу сценари.

## Альтернативные сценарии

### 4а. *Клиент* выбрал отложенную доставку 

1. *Система* вносит в CRM информацию об отсроченном заказе.
2. Переход к п.5 Основного сценария.

### 6а. *Клиент* хочет добавить новый адрес доставки

1. *Система* вызывает Модуль добавления адреса.
2. Переход к п.6 основного сценария.

### 8а. *Клиент*  выбрал оплату наличными

1. *Система* вызывает модуль расчёта и подготовки сдачи.
2. Переход к п.9 основного сценария.

### 8б. *Клиент* выбрал предварительную оплату

1. *Система* вызывает универсальный модуль расчётов по картам (расчёты через эквайрера или локально).
2. Переход к п.9 основного сценария.
   * Альтернативный сценарий 8г.

### 8г. Оплата по карте не проведена

1. *Система* выводит сообщение о неоплате.
2. Переход к п.8 сценария.

   
## Прерывания сценария 

### 4б. *Клиент* прервал сеанс или прекратил оформление

1. *Система* финализирует запись о незавершённом заказе в CRM.
2. Прерывание сценария.

### 6б. *Клиент* прервал сеанс или прекратил оформление

1. *Система* финализирует запись о незавершённом заказе в CRM.
2. Прерывание сценария.

### 8в. *Клиент* прервал сеанс или прекратил оформление

1. *Система* финализирует запись о незавершённом заказе в CRM.
2. Прерывание сценария.
