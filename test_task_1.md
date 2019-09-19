Реализовать API сервис обработки ipv4-адресов, решающий следующие задачи:
========================================================================
 * получение диапазона адресов по cidr, например:
 ``` python
    GET: /cidr_range/192_168_10_0/24
    return rest: {
      'first_ip': '192.168.10.1',
      'last_ip': '192.168.10.255'
      }
    GET: /cidr_range/192_168_10_11_0/24 
    return rest: {
      'error': 'Invalid cidr',
      }
```
 * проверка попадания ip-адреса в cidr, например:
 ``` python
    GET: /cidr/ip/192_168_10_1/in_range/192_168_10_0/24 
    return rest: {
      'result': 'True',
      }
    GET: /cidr/ip/192_168_20_1/in_range/192_168_10_0/24 
    return rest: {
      'result': 'False',
      }
```
