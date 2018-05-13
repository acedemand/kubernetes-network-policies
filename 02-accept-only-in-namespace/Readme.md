NetworkPolicy leri yazarken dikkat edilmesi gereken kısım eğer deny-all derseniz hiç bir pod birbiryle konuşmayacaktır. Istediğim buysa o zaman aynı namespace üzerinde sadece belirli podlar birbirine erişsin diyorsak spec kısmında hangi pod erişim istiyoruz. ingress / from kısmında ise hangi podların bu namespace içerisinde erişebileceği tanımlanıyor

```yaml
spec:
  podSelector:
    matchLabels:
      app: nginx
  ingress:
  - from:
      - podSelector:
          matchLabels:
            app: ingress
```