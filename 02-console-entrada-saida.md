# C# — Entrada e Saída no Terminal

## 1. Escrevendo no terminal

Em aplicações de console, usamos a classe `Console`.

### Console.WriteLine

Escreve algo no terminal e pula para a próxima linha.

```csharp
Console.WriteLine("Olá, mundo!");
```

Também podemos imprimir variáveis:

```csharp
string nome = "Eduardo";
Console.WriteLine(nome);
```

## 2. Console.Write

`Console.Write` escreve no terminal, mas não pula de linha.

```csharp
Console.Write("Digite seu nome: ");
```

Exemplo:

```csharp
Console.Write("Digite seu nome: ");
string nome = Console.ReadLine();
```

## 3. Diferença entre Write e WriteLine

```text
Write     → escreve e continua na mesma linha
WriteLine → escreve e pula de linha
```

## 4. Interpolação de strings

Podemos misturar texto e variáveis usando `$`.

```csharp
string nome = "Eduardo";
int idade = 21;

Console.WriteLine($"Meu nome é {nome} e tenho {idade} anos.");
```

As variáveis ficam dentro de `{}`.

## 5. Lendo dados do terminal

Para ler algo digitado pelo usuário:

```csharp
Console.ReadLine();
```

Exemplo:

```csharp
Console.Write("Digite seu nome: ");
string nome = Console.ReadLine();

Console.WriteLine($"Olá, {nome}!");
```

## 6. ReadLine retorna texto

`Console.ReadLine()` retorna uma `string`.

```csharp
var idade = Console.ReadLine();
```

O tipo inferido de `idade` será `string`.

Mesmo que o usuário digite:

```text
21
```

o programa inicialmente recebe:

```text
"21"
```

## 7. Por que isso não funciona?

```csharp
int idade = Console.ReadLine();
```

Porque:

```text
Console.ReadLine() → string
idade              → int
```

Existe incompatibilidade de tipos.

## 8. Convertendo string para int

```csharp
string idadeTexto = Console.ReadLine();
int idade = int.Parse(idadeTexto);
```

Fluxo:

```text
Usuário digita "21"
        ↓
Console.ReadLine()
        ↓
string "21"
        ↓
int.Parse()
        ↓
int 21
```

Também pode ser escrito diretamente:

```csharp
int idade = int.Parse(Console.ReadLine());
```

## 9. Problema do Parse

Funciona:

```csharp
int idade = int.Parse("21");
```

Mas:

```csharp
int idade = int.Parse("abc");
```

gera erro em tempo de execução.

## 10. TryParse

Para entradas do usuário, normalmente é mais seguro usar `TryParse`.

```csharp
bool sucesso = int.TryParse("30", out int numero);
```

Nesse caso:

```text
sucesso = true
numero  = 30
```

## 11. O que é out?

O `out` permite que um método coloque um valor dentro de uma variável passada como parâmetro.

```csharp
bool sucesso = int.TryParse("30", out int numero);
```

O método produz:

```text
return → true
out    → 30
```

Uma forma simples de pensar:

> além do retorno principal, coloque outro resultado nessa variável.

## 12. Entrada inválida

```csharp
bool sucesso = int.TryParse("abc", out int numero);
```

A conversão falha e `sucesso` recebe `false`.

## 13. Usando TryParse com if

```csharp
Console.Write("Digite sua idade: ");

string entrada = Console.ReadLine();

if (int.TryParse(entrada, out int idade))
{
    Console.WriteLine($"Idade válida: {idade}");
}
else
{
    Console.WriteLine("Valor inválido.");
}
```

## 14. Parse x TryParse

### Parse

```csharp
int idade = int.Parse(entrada);
```

```text
Converte ou gera erro.
```

### TryParse

```csharp
bool sucesso = int.TryParse(entrada, out int idade);
```

```text
Tenta converter.
Retorna true ou false.
```

Resumo mental:

```text
Parse    → converte ou quebra
TryParse → tenta converter e informa se deu certo
```

Para dados vindos do usuário, `TryParse` costuma ser mais seguro.

# Exemplo completo

```csharp
Console.Write("Digite seu nome: ");
string nome = Console.ReadLine();

Console.Write("Digite sua idade: ");
string entrada = Console.ReadLine();

if (int.TryParse(entrada, out int idade))
{
    Console.WriteLine($"Olá, {nome}!");
    Console.WriteLine($"Você tem {idade} anos.");
}
else
{
    Console.WriteLine("A idade informada é inválida.");
}
```

# Resumo rápido

```text
Console.Write     → escreve sem pular linha
Console.WriteLine → escreve e pula linha
Console.ReadLine  → lê uma entrada como string
int.Parse         → converte string para int e pode gerar erro
int.TryParse      → tenta converter e retorna true/false
out               → recebe um resultado adicional do método
```

Regra mental:

```text
Console.Write / WriteLine
        ↓
programa fala com o usuário

Console.ReadLine
        ↓
usuário fala com o programa
```
