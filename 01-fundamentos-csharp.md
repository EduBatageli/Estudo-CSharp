# Fundamentos de C#

## 1. C# x .NET x ASP.NET Core

Antes de tudo, é importante separar os conceitos:

- **C#** → linguagem de programação.
- **.NET** → plataforma/runtime utilizada para executar aplicações.
- **ASP.NET Core** → framework usado principalmente para aplicações Web e APIs.

```text
C#              → linguagem
.NET            → plataforma
ASP.NET Core    → desenvolvimento Web e APIs
```

## 2. Variáveis e tipos

C# é uma linguagem **fortemente tipada**.

```csharp
int idade = 21;
```

```text
int    → tipo
idade  → nome da variável
21     → valor
```

Uma variável `int` não pode receber diretamente uma `string`.

```csharp
int idade = "21"; // incorreto
int idade = 21;   // correto
string idade = "21"; // correto, mas "21" é texto
```

## 3. Tipos básicos

### int

```csharp
int idade = 21;
int quantidade = 10;
```

### string

```csharp
string nome = "Eduardo";
```

### bool

```csharp
bool ativo = true;
bool bloqueado = false;
```

### double

```csharp
double preco = 19.90;
```

### decimal

Muito usado para valores financeiros.

```csharp
decimal saldo = 1500.75m;
decimal valorProduto = 1299.90m;
```

Para dinheiro, normalmente preferimos `decimal` em vez de `double`.

## 4. var

O `var` permite que o compilador descubra automaticamente o tipo.

```csharp
var idade = 21;
```

É equivalente a:

```csharp
int idade = 21;
```

Outro exemplo:

```csharp
var nome = "Eduardo";
```

É equivalente a:

```csharp
string nome = "Eduardo";
```

`var` não significa que o tipo pode mudar.

```csharp
var idade = 21;

idade = 30;       // OK
idade = "trinta"; // ERRO
```

Regra mental:

```text
var = "descubra o tipo para mim"
```

## 5. Conversão de tipos

```csharp
string idadeTexto = "21";
int idade = int.Parse(idadeTexto);
```

```text
"21" → string
21   → int
```

## 6. if e else

```csharp
decimal saldo = 1000m;
decimal compra = 800m;

if (saldo >= compra)
{
    Console.WriteLine("Compra aprovada");
}
else
{
    Console.WriteLine("Saldo insuficiente");
}
```

O bloco do `if` é executado quando a condição for `true`.

## 7. Operadores lógicos

### && — E

As duas condições precisam ser verdadeiras.

```csharp
if (saldo >= compra && cartaoAtivo)
{
    Console.WriteLine("Compra aprovada");
}
```

### || — OU

Basta uma condição ser verdadeira.

```csharp
if (saldo >= compra || possuiLimiteExtra)
{
    Console.WriteLine("Compra aprovada");
}
```

### ! — NÃO

Inverte um valor booleano.

```csharp
bool ativo = true;
bool inativo = !ativo;
```

Resumo:

```text
&& → E
|| → OU
!  → NÃO
```

## 8. Métodos

Em C#, utilizamos muito o termo **método**. O conceito é semelhante ao de uma função em JavaScript.

JavaScript:

```javascript
function somar(a, b) {
    return a + b;
}
```

C#:

```csharp
static int Somar(int a, int b)
{
    return a + b;
}
```

## 9. Estrutura de um método

```csharp
static int Somar(int a, int b)
{
    return a + b;
}
```

```text
int      → tipo de retorno
Somar    → nome do método
int a    → primeiro parâmetro
int b    → segundo parâmetro
return   → retorna o resultado
```

Ainda não precisamos nos preocupar com o significado de `static`.

## 10. Parâmetros

Os parâmetros são valores que um método recebe.

```csharp
static int Somar(int a, int b)
{
    return a + b;
}
```

Nesse caso, `a` e `b` são parâmetros do tipo `int`.

## 11. Tipo de retorno

```csharp
static string ObterNome(int id)
{
    return "Eduardo";
}
```

```text
recebe  → int
retorna → string
```

Outro exemplo:

```csharp
static bool UsuarioExiste(int id)
{
    return id > 0;
}
```

```text
recebe  → int
retorna → bool
```

## 12. return

O `return` devolve um valor para quem chamou o método.

```csharp
static int Somar(int a, int b)
{
    return a + b;
}

int resultado = Somar(2, 3);
```

`resultado` receberá `5`.

## 13. void

`void` significa que um método **não retorna nenhum valor**.

```csharp
static void ExibirMensagem(string mensagem)
{
    Console.WriteLine(mensagem);
}
```

## 14. void x null

```text
void → o método não retorna nenhum valor
null → ausência de valor
```

São conceitos diferentes.

# Resumo rápido

```csharp
int idade = 21;
```

```text
int    → tipo
idade  → variável
21     → valor
```

```csharp
var nome = "Eduardo";
```

O compilador entende como `string`.

```text
&& → E
|| → OU
!  → NÃO
```

```csharp
static string ObterNome(int id)
{
    return "Eduardo";
}
```

```text
string    → retorno
ObterNome → nome do método
int id    → parâmetro
return    → devolve um valor
```

```csharp
static void ExibirMensagem(string mensagem)
{
    Console.WriteLine(mensagem);
}
```

```text
void → não retorna valor
```

## Próximo assunto

Ainda não estudado:

```text
Classes
Objetos
new
Propriedades
get e set
```
