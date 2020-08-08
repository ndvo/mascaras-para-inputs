# Máscaras para inputs

Pequena coleção de máscaras simples para inputs comuns.

Não se trata de uma biblioteca ou framework. O código está copiado no README. O arquivo `index.html` oferece um exemplo de uso.

### CPF

Altera o atributo value de um elemento removendo caracteres não numéricos e acrescentando os separadores usados no CPF.

```javascript
    function mascaraCPF(el) {
      // Remove caracteres não numéricos
      var numeros = el.value.replace(/[^\d]/g, '');
      // Cria grupos de algorismos com mesmo separador
      var grupos = numeros.match(/(\d{1,3})?(\d{1,3})?(\d{1,3})?(\d{1,2})?/);
      var trios = [];
      if (grupos[1]) trios.push(grupos[1])
      if (grupos[2]) trios.push(grupos[2])
      if (grupos[3]) trios.push(grupos[3])
      var resultado = trios.join(".")
      if (grupos[4]) resultado += "-"+grupos[4]
      el.value = resultado;
    }
```

### CNPJ
Altera o atributo value de um elemento removendo caracteres não numéricos e acrescentando os separadores usados no CNPJ.

```javascript
    function mascaraCNPJ(el) {
      // Remove caracteres não numéricos
      var numeros = el.value.replace(/[^\d]/g, '');
      // Cria grupos de algorismos com mesmo separador
      var grupos = numeros.match(/(\d{1,2})?(\d{1,3})?(\d{1,3})?(\d{1,4})?(\d{1,2})?/);
      var pontos = [];
      var hifens = [];
      // Junta grupos com ponto
      if (grupos[1]) pontos.push(grupos[1])
      if (grupos[2]) pontos.push(grupos[2])
      if (grupos[3]) pontos.push(grupos[3])
      var resultado = pontos.join(".")
      // Junta grupos com hifen
      if (grupos[4]) hifens.push(grupos[4])
      if (grupos[5]) hifens.push(grupos[5])
      // Junta os grupos com barra
      if (hifens.length) resultado += "/" + hifens.join("-")
      el.value = resultado;
    }
```

# Perguntas e Reclamações Frequentes

#### Por que não usar uma biblioteca de máscara de input?
Nenhum motivo. Vá em frente, procure a biblioteca ideal e use.

#### E quanto ao DRY? Você repete linhas de código!
Pois é.

#### Este código utiliza antipatterns, como o onkeyup. Por quê?
Assim foi mais rápido.

#### Faltou o linting. Vários statements não terminam com o ponto e vírgula.
Esqueci de pôr.

#### Faltou o linting. Vários statements terminam com o ponto e vírgula.
Esqueci de tirar.
