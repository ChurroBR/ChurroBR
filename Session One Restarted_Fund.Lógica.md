# Session One Restarted/Fund.Lógica

autor: Nilton da Silva Moreira
turma: INFO-A
número: ?? 


## Exercício 1

Crie uma função que implemente a lógica para
calcular a média de 4 notas de um aluno.

```csharp=
public class NotasAluno 
{
	public double n1;
	public double n2;
	public double n3;
	public double n4;
}
	

public double Media (NotasAluno notas)
{
	double m = (notas.n1 + notas.n2 + notas.n3 + notas.n4) / 3;
	return m;
}
	
NotasAluno notas = new NotasAluno();
notas.n1 = 5;
notas.n2 = 9;
notas.n3 = 10;
notas.n4 = 7.5;

double x = Media(notas);
x


//10.5
```



## Exercicio 2

Crie uma função que implemente a lógica para
calcular a área do Retângulo.

```csharp=
public class Retangulo
{
	public int alt;
	public int bas;
}


public double Area (Retangulo ret)
{
	double r = ret.alt * ret.bas;
	return r;
}

Retangulo ret = new Retangulo();
ret.alt = 10;
ret.bas = 5;


double x = Area(ret);
x


//50
```

## Exercício 3

Crie uma função que a partir da base e altura de dois
triângulos diferentes, crie uma função que verifique se o
[Triângulo-1] possui a área igual ao [Triângulo-2], retorne
verdadeiro se forem iguais e falso se forem diferentes.

```csharp=
public class Triangulo
{
	public double bas;
	public double alt;
}

public bool AreasIguais(Triangulo tri1, Triangulo tri2)
{
	double a1 = (tri1.alt * tri1.bas)/ 2;
	double a2 = (tri2.alt * tri2.bas)/ 2;
	
	bool iguais = a1 == a2;
	return iguais;
}

Triangulo t1 = new Triangulo();
t1.alt = 10;
t1.bas = 2;

Triangulo t2 = new Triangulo();
t2.alt = 10;
t2.bas = 2;




bool x = AreasIguais(t1, t2);
x


//true
```


## Exercício 4

Crie uma função que a partir da quantidade de açaí
pequenos, médios e grandes comprados por um cliente,
calcule o total a pagar sabendo que os valores do açaí são
R$ 10,00, R$ 12,00 e R$ 14,00 respectivamente e não
sofrerão alteração de preço.

```csharp=
public class PedidoAcai
{
	public int qtdP;
	public int qtdM;
	public int qtdG;
}



public double VendaAcai (PedidoAcai qtd)
{
	double q1 = qtd.qtdP * 10;
	double q2 = qtd.qtdM * 12;
	double q3 = qtd.qtdG * 14;
	double c = q1 + q2 + q3;
	return c;
}

PedidoAcai qtd = new PedidoAcai();
qtd.qtdP = 2;
qtd.qtdM = 1;
qtd.qtdG = 1;

double x = VendaAcai(qtd);
x


//46
```

## Exercício 5

Crie uma função que a partir do preço de um veículo e o
total de parcelas que será financiado, calcule o valor final
pago considerando uma taxa de 5% por mês.

```csharp=
using System;

public class CompraVeiculo
{
	public int parcela;
	public double preco;
}


public double CalcularTotalVeiculo (CompraVeiculo info)
{
	double m = ((info.preco + info.preco)*(0.05 * info.parcela));
	return m;
}

CompraVeiculo info = new CompraVeiculo();
info.preco = 48000;
info.parcela = 12;


double x = CalcularTotalVeiculo(info);
x


//57600
```

## Exercício 6

Crie uma função que a partir do nome de uma pessoa e
um CEP, verifique se o CEP contém o caractere hífen (-) e
possui um total de 9 caracteres.

Se o CEP for válido, retorne:
“XXX, o resultado da validação de seu CEP é: true”
ou
“XXX, o resultado da validação de seu CEP é: false”.

```csharp=
public class Endereco
{
	public string nomeCompleto;
	public string cep;
}

public bool ValidarCEP (Endereco info)
{
	bool a = info.cep.Contains("-");
	int b = info.cep.Length;
    bool c = b == 9;
	return a && c;
}

Endereco info = new Endereco();
info.nomeCompleto = "Nilton da Silva Moreira";
info.cep = "048-51804";
string n = info.nomeCompleto + ", o resultado da validação do seu CEP é :";

string x = n + ValidarCEP(info);
x


//Nilton da Silva Moreira, o resultado da validação do seu CEP é :True
```

## Exercício 7

Crie uma função composta que a partir de três nomes
completos, retorne verdadeiro/falso se as pessoas são da
mesma família, comparando o último nome das três
pessoas

```csharp=
public class Pessoa
{
	public string nomeCompleto;
}

public bool MesmaFamilia(Pessoa p1, Pessoa p2, Pessoa p3)
{
	string s1 = ExtrairSobrenome(p1.nomeCompleto);
	string s2 = ExtrairSobrenome(p2.nomeCompleto);
	string s3 = ExtrairSobrenome(p3.nomeCompleto);
	bool b = s1 == s2;
	b = s1 == s3;
	return b;
}

public string ExtrairSobrenome (string p)
{
	int e = p.LastIndexOf(" ");
	string a = p.Substring(e);
	return a;
}

Pessoa p1 = new Pessoa();
p1.nomeCompleto = "João Santos";

Pessoa p2 = new Pessoa();
p2.nomeCompleto = "Felipe Santos";

Pessoa p3 = new Pessoa();
p3.nomeCompleto = "Thomas Cabrito";

bool x = MesmaFamilia(p1, p2, p3);
x


//False
```



## Exercício 8

Crie uma função composta que a partir dos valores
'a', 'b' e 'c', calcule o valor de xi e xii baseado na equação de segundo grau.

```csharp=
public class Equacao
{
	public int a;
	public int b;
	public int c;
}

public class resultado
{
	public double x1;
	public double x2;
}

Equacao valores = new Equacao();
valores.a = 1;
valores.b = 1;
valores.c = -12;


public double Delta (Equacao parametros)
{
	return Math.Pow(parametros.b,2) - 4 * parametros.a * parametros.c;
}

public resultado  Conta (Equacao valores)
{
	double x11 =(-valores.b + Math.Sqrt(Delta(valores))) / 2 *valores.a;
	double x22 = (-valores.b - Math.Sqrt(Delta(valores))) / 2 *valores.a;
	
	resultado resposta = new resultado();
	resposta.x1 = x11;
	resposta.x2 = x22;
	return resposta;	
}


resultado resu = Conta(valores);
Console.WriteLine("Resposta 8 = o x1 vale: " + resu.x1);
Console.WriteLine("Resposta 8 = x2 vale: " + resu.x2);
```



## Exercício 9




## Exercício 10