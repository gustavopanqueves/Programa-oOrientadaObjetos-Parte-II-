# Atividade 1

***TypeScript***
```typescript
class Pessoa {
    constructor(public nome: string) {}
}

class Aluno extends Pessoa {
    estudar(): void {
        console.log(`${this.nome} está estudando.`);
    }
}

class Professor extends Pessoa {
    lecionar(): void {
        console.log(`O(A) professor(a) ${this.nome} está lecionando.`);
    }
}

const aluno = new Aluno("Carlos");
aluno.estudar();
```

# Atividade 2

***TypeScript***
```typescript
class ContaBancaria {
    protected _saldo: number;

    constructor(saldoInicial: number) {
        this._saldo = saldoInicial;
    }

    depositar(valor: number): void {
        if (valor > 0) {
            this._saldo += valor;
            console.log(`Depositado: R$${valor}`);
        }
    }

    sacar(valor: number): void {
        if (valor > 0 && valor <= this._saldo) {
            this._saldo -= valor;
            console.log(`Sacado: R$${valor}`);
        } else {
            console.log("Saldo insuficiente ou valor inválido.");
        }
    }

    consultarSaldo(): number {
        return this._saldo;
    }
}

const conta = new ContaBancaria(1000);
conta.depositar(500);
conta.sacar(200);
console.log(`Saldo atual: R$${conta.consultarSaldo()}`);

```

# Atividade 3

***TypeScript***
```typescript
class Animal {
    emitirSom(): void {
        console.log("O animal emite um som genérico.");
    }
}

class Cachorro extends Animal {
    override emitirSom(): void {
        console.log("O cachorro late: Au Au!");
    }
}

class Gato extends Animal {
    override emitirSom(): void {
        console.log("O gato mia: Miau!");
    }
}

const animais: Animal[] = [new Cachorro(), new Gato()];
animais.forEach(animal => animal.emitirSom());

```
# Atividade 4

***TypeScript***
```typescript
abstract class Forma {
    abstract calcularArea(): number;
}

class Retangulo extends Forma {
    constructor(private largura: number, private altura: number) {
        super();
    }

    calcularArea(): number {
        return this.largura * this.altura;
    }
}

class Circulo extends Forma {
    constructor(private raio: number) {
        super();
    }

    calcularArea(): number {
        return Math.PI * Math.pow(this.raio, 2);
    }
}

const retangulo = new Retangulo(10, 5);
console.log(`Área do Retângulo: ${retangulo.calcularArea()}`);

```
# Atividade 5

***TypeScript***
```typescript
abstract class UsuarioSistema {
    constructor(protected nome: string, protected email: string) {}

    abstract executarAcaoPrincipal(): void;

    exibirDados(): void {
        console.log(`Nome: ${this.nome} | Email: ${this.email}`);
    }
}

class AlunoIntegrado extends UsuarioSistema {
    private _matricula: string;

    constructor(nome: string, email: string, matricula: string) {
        super(nome, email);
        this._matricula = matricula;
    }

    get matricula(): string {
        return this._matricula;
    }

    executarAcaoPrincipal(): void {
        console.log(`O aluno ${this.nome} (Matrícula: ${this._matricula}) está assistindo às aulas.`);
    }
}

class ProfessorIntegrado extends UsuarioSistema {
    private _salario: number;

    constructor(nome: string, email: string, salarioInicial: number) {
        super(nome, email);
        this._salario = salarioInicial;
    }

    darAumento(percentual: number): void {
        if (percentual > 0) {
            this._salario += this._salario * (percentual / 100);
            console.log(`Novo salário de ${this.nome}: R$${this._salario.toFixed(2)}`);
        }
    }

    executarAcaoPrincipal(): void {
        console.log(`O professor ${this.nome} está lançando as notas e ministrando conteúdo.`);
    }
}

const usuarios: UsuarioSistema[] = [
    new AlunoIntegrado("Ana Silva", "ana@escola.com", "20261001"),
    new ProfessorIntegrado("Dr. Roberto", "roberto@escola.com", 5000)
];

usuarios.forEach(usuario => {
    usuario.exibirDados();
    usuario.executarAcaoPrincipal();
});


```
