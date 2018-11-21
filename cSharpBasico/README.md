# Estudos C# Clássico

Aqui estão alguns exemplos de lógica com C#.

  - os programas rodam somente em linha de comando
  - Criei todos os programas em linux
  - Para compilar digite dotnet build
  - Para rodar o programa digite dotnet run

# Variáveis no C#
As variáveis são utilizadas para armazenar informações na memória em tempo de execução da aplicação, isso significa que essas informações estarão disponíveis enquanto a aplicação estiver em execução e, mais precisamente, enquanto a classe ou método em que ela foi criada estiver em execução.

No C# toda variável deve ter: modificador de acesso, tipo de dados e nome.

A regra para nomear uma variável é que o nome dela sempre comece por uma letra ou _. No meio do nome podem-se usar números, mas não se devem usar caracteres especiais e também não pode ser uma palavra reservada. Entende-se por palavras reservadas os comandos do C# e que são facilmente identificadas quando digitadas, por ficarem da cor azul. Exemplos de palavras que não podem ser utilizadas são: if, for, while, string e etc.

Exemplo de variável:

```sh
int numero;
```
No exemplo, int é o tipo e numero é o nome da variável.

Como dito anteriormente, toda variável deve ter o modificador de acesso. No exemplo acima não tem um modificador porque no C# quando não há um modificador em uma variável e é atribuído a ele o modificador padrão private.

## Modificadores

No caso das varáveis, os modificadores definem a visibilidade delas, se elas poderão ser acessadas por outras classes que não seja a sua própria, se serão acessadas somente por classes derivadas a classe que ela está e assim por diante, como mostra a Listagem 1.

Listagem 1. Utilização de modificadores.
```sh
Public int numero;
```

##### No C# existem os seguintes modificadores:
#
| Modificador| Funcionamento |
| ------ | ------ |
|public |O acesso não é restrito.|
|protected |O acesso é limitado às classes ou tipos derivados da classe que a variável está.|
|Internal |O acesso é limitado ao conjunto de módulos (assembly) corrente.|
|protected internal |O acesso é limitado ao conjunto corrente ou tipos derivados da classe recipiente.|
|private|O acesso é limitado à classe que a variável está.|
**Tabela1:** Modificadores de acesso **-Fonte:** Adaptado de Microsoft

## Tipos de dados

C# é uma linguagem de programação fortemente tipada, isso significa que todas as variáveis e objetos devem ter um tipo declarado. Os tipos de dados são divididos em value types e reference types. Os value types são derivados de System.ValueType e reference types são derivados de System.Object.

## Variáveis Value Type
As variáveis value type contém dentro delas um valor, enquanto as reference type contém uma referência. Isso significa que se copiar uma variável do tipo value type para dentro de outra o valor é copiado e, se o mesmo for feito com uma do tipo reference type será copiado apenas a referência do objeto.

Dentro de Value Type existem duas categorias: struct e enum.

a) Struct: é dividida em tipos numéricos, bool e estruturas personalizadas pelo usuário.

Os tipos numéricos são os presentes na tabela abaixo:
|Tipo de dados|Intervalo|
| ------ | ------ |
|byte|0 ..255|
|sbyte|-128 ..127|
|short|-32,768 ..32,767|
|ushort|0 ..65,535|
|int|-2,147,483,648 ..2,147,483,647|
|uint|0 ..4,294,967,295|
|long|-9,223,372,036,854,775,808 ..9,223,372,036,854,775,807|
|ulong|0 ..18,446,744,073,709,551,615|
|float|-3.402823e38 ..3.402823e38|
|double|-1.79769313486232e308 ..1.79769313486232e308|
|decimal|-79228162514264337593543950335 ..79228162514264337593543950335|
|char|U+0000 .. U+ffff|
|float|-3.402823e38 ..3.402823e38|
|double|-1.79769313486232e308 ..1.79769313486232e308|

Tipo bool representa um valor que pode ser verdadeiro ou falso, o seu valor padrão é false.
b) **Enum**: permite criar um tipo que é formado por várias constantes. Normalmente é usada quando em algum momento existe a necessidade de um atributo que pode ter múltiplos valores, como por exemplo, em uma aplicação de venda que tem a tela de pedidos: cada pedido tem a sua situação que pode ser Aberto, Faturado e Cancelado. Para criar a classe Pedido, o tipo do atributo situação será int, conforme mostra a Listagem 2.

**Listagem 2.** Classe pedido.
```sh
class Pedido
    {
        public int numero;
        public DateTime dataHora;
        public int situacao;
  
    }
```
Agora é necessária a criação do Enum Situacao. Um Enum é criado da mesma porque se cria uma classe, mas ao invés de utilizar a palavra class usa-se enum, conforme mostra a Listagem 3.

**Listagem 3.** Enum Situacao.
```sh
enum Situacao
    {
        Aberto,
        Faturado,
        Cancelado
    }
}
```
Na Listagem 4 contém o código da utilização deste Enum que foi criado.

**Listagem 4.** Utilizando o Enum criado.
```sh
class Program
{
    static void Main(string[] args)
    {
        Pedido pedido = new Pedido();
 
        pedido.numero = 1;
        pedido.dataHora = DateTime.Now;
        pedido.situacao = (int) Situacao.Faturado;
 
        Console.WriteLine("Número do pedido: " 
         + pedido.numero.ToString());
        Console.WriteLine("Número do pedido: "
         + pedido.dataHora.ToString());
        Console.WriteLine("Número do pedido: " 
         + pedido.situacao.ToString());
 
        Console.ReadLine();
 
    }
}
```
O Enum por padrão retorna int e neste exemplo temos três opções, onde cada uma possui um índice. Então quando o valor de um Enum é atribuído a um outro atributo ,o que é atribuído é seu índice, no caso do exemplo da Listagem 4 é atribuído o valor 1.
## Variáveis Reference Types

As variáveis reference type armazenam apenas a referência do objeto. Os tipos de referência são: class, interface, delegate, object, string e Array.

a) Tipo object: todos os tipos são derivados da classe Object, sendo assim é possível converter qualquer tipo para object.

b) Tipo string: é utilizado para se armazenar caracteres e uma string deve estar entre aspas, como mostra a Listagem 5.

**Listagem 5.** Utilização de string
```sh
string nome = "Amarilis";
```
Para concatenar (juntar) uma ou mais strings é usando o sinal de +, como mostra a Listagem 6.
**Listagem 6.** Concatenando strings.

```sh
string a = "C#";
string b = ".net";
 
string c = a + b;
```
Outro recurso também é a possibilidade de se obter um determinado caractere de uma string, como mostra a Listagem 7.

**Listagem 7.** Pegando um caractere de uma string.

```sh
string a = "C#";
string b = ".net";
 
string c = a + b;
 
char d = c[3];
```
A variável d vai ficar com o valor da letra n que é a letra que está no índice 3, conforme informado no código.

Também é possível fazer a mesma coisa com uma palavra, como mostra a Listagem 8.

**Listagem 8.** Pegando um caractere de uma palavra.
```sh
char d = "C#.net"[3];
```
Existem muitas outras operações para fazer com variáveis, mas isso é assunto para um próximo artigo. O que foi mostrado nesse artigo são passos iniciais para entender como funcionam as variáveis no C#.