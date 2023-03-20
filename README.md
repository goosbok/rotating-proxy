# TorProxy
## Источник

Эта репа [форк](https://github.com/mattes/rotating-proxy) данного технологического чуда.

## Что умеет

Поднимаем сервер для маршрутизации запросов через сервера TORа. Число серверов меняетя в переменной tors в compose.yaml.

При каждом запросе через сервер мы получаем один из путей маршрутизации, что означает что мы под каждый запрос получает новый IP.

## Как поднять

	make build
	make up
	# чтобы остановить:
	make stop

## Пример использования:
Пример приведу на python библиотека requests

	import requests

	scheme_proxy_map = {
	    'http': '127.0.0.1:5566',
	    'https': '127.0.0.1:5566',
	}
	
	
	response = requests.get('https://ip.oxylabs.io/ip', proxies=scheme_proxy_map)
	print(response.text)


При каждом выполнении запроса мы будем получать один из поднятых IP.
