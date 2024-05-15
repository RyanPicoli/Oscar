# Oscar

1. Quantas vezes *Natalie Portman* foi indicada ao Oscar?
```mysql
SELECT COUNT(*) 
FROM indicados_ao_oscar 
WHERE nome_do_indicado  = "Natalie Portman";
```
## Resposta do Banco
|3|
|---|
### Resposta:
>*Natalie Portman* foi indicada ao Oscar 3 vezes
---

2. Quantos Oscars *Natalie Portman* ganhou?
```mysql
SELECT COUNT(*)
FROM indicados_ao_oscar
WHERE nome_do_indicado = "Natalie Portman" 
AND vencedor = "sim"
LIMIT 1;
```
## Resposta do Banco
|0|
|---|

### Resposta:
> *Natalie Portman* não ganhou nenhum Oscar.
---

3. *Amy Adams* já ganhou algum Oscar?
```mysql
SELECT COUNT(*) 
FROM indicados_ao_oscar 
WHERE nome_do_indicado = "Amy Adams"
AND vencedor = "sim"; 
```
## Resposta do Banco
|0|
|---|
### Resposta:
> *Amy Adams* não ganhou nenhum Oscar, mas concorreu 6 vezes.
---
