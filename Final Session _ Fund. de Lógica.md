# Final Session / Fund. de Lógica 
autor: Nilton da Silva Moreira
turma: Info D
número: 36

## Nível 1

### Exercício 1
Faça uma função ÚNICA que a partir da base e altura, calcule a área do
triângulo.

```csharp=
public double AreaTriangulo (double alt, double bas)
{
	return alt * bas;
}

double x = AreaTriangulo (10, 5);
x

//25
```
### Exercício 2

Faça uma função ÚNICA que a partir do lado, calcule o perímetro do
octógono.

```csharp=
public double PerimetroOctagono(double lado)
{
	return lado * 8;
}

double x = PerimetroOctagono (10);
x

//80
```


### Exercício 3


Faça uma função ÚNICA que a partir da base maior, base menor e altura,
calcule a área do trapézio.

```csharp=
public double AreaTrapezio(double bma, double bme, double alt )
{
	 return bma + bme * alt / 2;
}
 
double x = AreaTrapezio (15, 5, 8);

x

//35
```

### Exercício 4

Faça uma função ÚNICA que a partir da diagonal maior e menor, calcule a
área do losango.

```csharp=
public double AreaLosango(double diagma, double diagme)
{
	 return diagma * diagme / 2;
}
 
double x = AreaLosango (8 , 6);

x

//24
```


## Nível 2

### Execício 1

Faça uma função ÚNICA que a partir do cateto oposto e adjacente, calcule
a hipotenusa. Arredonde a resposta para uma casa decimal.

```csharp=
public double Hip( double oposto, double adjcente)
{
	double total = (Math.Sqrt((oposto * oposto) + (adjcente * adjcente)));
	total = Math.Round(total,1);
	return total;
}
 

double x = Hip(8, 10);
x

//12.8
```

### Exercício 2

Faça uma função ÚNICA que a partir de um peso e altura de uma pessoa,
calcule o IMC. Arredonde a resposta para duas casas decimais.

```csharp=
public double Imc( double kg, double alt)
{
	 double total = (kg / (alt * alt));
	 total = Math.Round(total,2);
	 return total;
}
							  
 

double x = Imc(45.90, 1.40);
x

//23.42
```

### Exercício 3

Faça uma função ÚNICA que a partir de um capital, parcelas e taxa de
juros, calcule o juros compostos. Arredonde a resposta para uma casa
decimal.

```csharp=
public double jurosCompostos (double capital, double juros, double parcela)
{
	double num1 = Math.Pow(1 + juros / 100, parcela);
	double mentente = (capital * num1);
 	mentente = Math.Round(mentente, 1);
	return mentente;
}


double x = jurosCompostos (4000, 5, 12);
x

//7183.4
```

### Exercício 4

Faça uma função ÚNICA que a partir da massa e velocidade, calcule a
energia cinética. Obrigatório o uso da função Math.Pow.

```csharp=
public double EnergiaCinetica (double massa, double velo)
{
	double a = Math.Pow(velo, 2);
	double b = (massa * a / 2);
	return b;
}

double x = EnergiaCinetica(5, 2);
x
	
//10
```

## Nível 3

### Exercício 1

Faça uma função ÚNICA que a partir de um nome completo de uma
pessoa, extraia o primeiro nome.

```csharp=
public string primeiroNome (string nome)
{
	int espaco = nome.IndexOf(" ");
	string primeiro = nome.Substring(0, espaco);
	return primeiro;
}

string a = "Nilton da Silva Moreira";
string x = primeiroNome(a);
x

//"Nilton"
```

### Exercício 2

Faça uma função ÚNICA que a partir de um nome completo de uma
pessoa, extraia o último nome.

```csharp=
public string ultimoNome (string nome)
{
 	int espaco = nome.LastIndexOf(" ");
	string ultimo = nome.Substring(espaco);
	return ultimo;
}

string nome = "Nilton da Silva Moreira";
string x = ultimoNome(nome);
x

//"Moreira"
```
### Exercício 3

Faça uma função ÚNICA que a partir de um e-mail de uma pessoa, extraia
o domínio do e-mail.

```csharp=
public string Dominio (string email)
{
	int a = email.LastIndexOf("@");
	string c = email.Substring(a);
	return c;
}

string e = "nmoreira407@gmail.com";
string x = Dominio(e);
x

//"@gmail.com"
```

### Exercício 4

Faça uma função ÚNICA que a partir de um telefone com máscara e DDD
incluído ex. (11) 94343-0808, retorne apenas os números do telefone
ex. 11943430808.

```csharp=
public string Telefone (string num)
{
	num = num.Replace("(", "");
	num = num.Replace(")", "");
	return num;
}

string n = "(11)952157786";
string x = Telefone(n);
x

//"11952157786"
```

## Nível 4

### Exercício 1

Faça uma função ÚNICA que a partir de uma data, descubra o último dia
do mês a partir dessa data.

```csharp=
public DateTime ultimoDia (DateTime data)
{
 	DateTime ult = data.AddMonths(1).AddDays(-data.Day);
	return ult;
}

DateTime nasc = new DateTime(1989, 2, 22);
DateTime dia =  ultimoDia(nasc);
dia

// 2, 28, 1989
```

### Exercício 2

Faça uma função ÚNICA que a partir de uma data, descubra o primeiro
dia do próximo mês a partir dessa data.

```csharp=
public DateTime primeiroDia (DateTime data)
{
 	DateTime prm = data.AddMonths(1).AddDays(-data.Day + 1);
	return prm;
}

DateTime nasc = new DateTime(1989, 2, 22);
DateTime dia = primeiroDia(nasc);
dia
		        
//3, 1, 1989
```

### Exercício 3

Faça uma função ÚNICA que a partir de uma data, retorne
verdadeiro/falso se a data pertence ao segundo trimestre do ano.

```csharp=
public bool secondTrim (DateTime date)
{
	bool check = date.Month == 6;
	return check;
}

DateTime d = new DateTime(1998, 6, 22);
bool x = secondTrim(d);
x

//true		
```

### Exercício 4

Faça uma função ÚNICA que a partir de uma data, retorne
verdadeiro/falso se a pessoa tem mais de 18 anos a partir do dia atual.

```csharp=
public bool quinzenaMes (DateTime date)
{
	bool check = date.Day <= 15;
	return check;
}

DateTime d = new DateTime(1998, 6, 10);
bool x = quinzenaMes(d);
x

//true
```

## Nível 5 

### Exercício 1

Faça uma função COMPOSTA que a partir dos valores 'a', 'b' e 'c’, calcule
o valor de 'x’ baseado na equação de segundo grau.

```csharp=
public double equacao2grau (double a, double b, double c)
{
	double delta = (Math.Pow(b, 2) - 4 * a * c);
	double total = formulaDB( a, b, delta);
	return total;
}

public double formulaDB (double a, double b, double delta)
{
	double plus = (-b + Math.Sqrt(delta)) /(2 * a);
	double less = (-b - Math.Sqrt(delta)) /(2 * a);
	return less ;
}

double x = equacao2grau(5, -3, -2);
x

// 1
```

### Exercício 2

Faça uma função COMPOSTA que encontre um termo de uma PA
(Progressão Aritmética), a partir do primeiro termo, razão e posição do termo que deseja encontrar.

```csharp=
public double PA (double termo, double razao, double posicao)
{
	return formulaTM (termo, razao, posicao);
}

public double formulaTM (double a, double b, double c)
{
	return a + (c - 1) * b;	
}

double x = PA(1, 2, 5);
x

// 9
```

### Exercício 3

Faça uma função COMPOSTA que encontre um termo de uma PG
(Progressão Geométrica), a partir do primeiro termo, razão e posição do termo que deseja encontrar.

```csharp=
public double PG (double termo, double razao, double posicao)
{
	return formulaTM (termo, razao, posicao);
}


public double formulaTM (double a, double b, double c)
{
 	c = c - 1;
	return Math.Pow((a * b), c);
	
}


double x = PG (3, 2, 3);
x

//36
```

### Exercício 4

Faça uma função COMPOSTA que a partir de dois nomes completos,
retorne verdadeiro/falso se as pessoas são da mesma família,
comparando o último nome das duas pessoas.

```csharp=
public bool mesmaFamilia (string nome1, string nome2)
{
	int espaco = nome1.LastIndexOf(" ");
	string ultimoNome = nome1.Substring(espaco);
	bool sera = nome2.Contains(ultimoNome);
	return sera;
}


bool x = mesmaFamilia("Nilton Silva", "Miriam da Silva");
x

// true
```