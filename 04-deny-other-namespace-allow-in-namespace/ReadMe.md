Bu policy tarzı aynı vlan gibi düşünebilirsiniz. Bir vlandaki her vm birbiriyle nasıl konuşuyorsa burda da her pod aynı namespacede birbiri ile konuşsun diyebiliyoruz.

```yaml
spec:
  podSelector:
    matchLabels:
  ingress:
  - from:
    - podSelector: {}
```