Düşünce tarzımızı biraz vlanlara çevirelim. DMZ / DB / Web gibi vlanlarımızın olduğunu düşünelim. Bu mantıkla o zaman bu isimlerde namespace yaratacağız. Bu namespacelerde ise podlarımı yaratıp hepsine deny-all deyip daha sonradan güvenlik açısından düşünerek teker teker açacağız. 
Eğer Web namespace'i DB namespace'indeki bir pod 3306 portundan erişmesini istitorsak aşağdaki gibi tanım yapmamız yeterli olacaktır.

```yaml
spec:
  podSelector:
    matchLabels:
      app: mysql
  ingress:
  - ports:
    - port: 3306
  - from:
    - namespaceSelector:
        matchLabels:
          purpose : web
          env: prod
    - podSelector:
        matchLabels:
          color: blue      
```