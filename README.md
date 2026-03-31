# Exercícios de JavaScript - Arrays e Métodos

---

## 1 - Lista de compras simples

### HTML

```html
<input id="item">
<button onclick="adicionar()">Adicionar</button>
<ul id="lista"></ul>
```

### JS

```javascript
let itens = [];

function adicionar() {
    let valor = item.value;
    itens.push(valor);
    render();
}

function remover(index) {
    itens.splice(index, 1);
    render();
}

function render() {
    lista.innerHTML = "";

    itens.forEach((i, index) => {
        let li = document.createElement("li");
        li.innerHTML = `${i} <button onclick="remover(${index})">Remover</button>`;
        lista.appendChild(li);
    });
}
```

---

## 2 - Gerenciador de alunos

### HTML

```html
<input id="nome">
<input id="nota">
<button onclick="addAluno()">Adicionar</button>
<button onclick="filtrar()">Aprovados</button>

<ul id="lista"></ul>
```

### JS

```javascript
let alunos = [];

function addAluno() {
    alunos.push({ nome: nome.value, nota: Number(nota.value) });
    mostrar(alunos);
}

function mostrar(arr) {
    lista.innerHTML = "";
    arr.forEach(a => {
        let li = document.createElement("li");
        li.textContent = `${a.nome} - ${a.nota}`;
        lista.appendChild(li);
    });
}

function filtrar() {
    let aprovados = alunos.filter(a => a.nota >= 7);
    mostrar(aprovados);
}
```

---

## 3 - Lista de tarefas com prioridade

### HTML

```html
<input id="titulo">
<select id="prioridade">
    <option value="alta">Alta</option>
    <option value="normal">Normal</option>
</select>
<button onclick="add()">Adicionar</button>

<ul id="lista"></ul>
```

### JS

```javascript
let tarefas = [];

function add() {
    let tarefa = { titulo: titulo.value, prioridade: prioridade.value };

    if (tarefa.prioridade === "alta") {
        tarefas.unshift(tarefa);
    } else {
        tarefas.push(tarefa);
    }

    render();
}

function render() {
    lista.innerHTML = "";
    tarefas.forEach(t => {
        let li = document.createElement("li");
        li.textContent = `${t.titulo} (${t.prioridade})`;
        lista.appendChild(li);
    });
}
```

---

## 4 - Transformando dados com map

### HTML

```html
<button onclick="mostrar()">Mostrar produtos</button>
<ul id="lista"></ul>
```

### JS

```javascript
const produtos = [
    { nome: "Mouse", preco: 50 },
    { nome: "Teclado", preco: 100 },
    { nome: "Monitor", preco: 800 }
];

function mostrar() {
    let desconto = produtos.map(p => {
        return { nome: p.nome, preco: p.preco * 0.9 };
    });

    lista.innerHTML = "";

    desconto.forEach(p => {
        let li = document.createElement("li");
        li.textContent = `${p.nome} - ${p.preco}`;
        lista.appendChild(li);
    });
}
```

---

## 5 - Carrinho de compras

### HTML

```html
<button onclick="add()">Adicionar produto</button>
<button onclick="remover()">Remover último</button>

<ul id="lista"></ul>
```

### JS

```javascript
let carrinho = [];

function add() {
    carrinho.push({ nome: "Produto", preco: 10 });
    render();
}

function remover() {
    carrinho.pop();
    render();
}

function render() {
    lista.innerHTML = "";
    carrinho.forEach(p => {
        let li = document.createElement("li");
        li.textContent = p.nome;
        lista.appendChild(li);
    });
}
```

---

## 6 - Filtro de usuários

### HTML

```html
<button onclick="mostrar()">Mostrar todos</button>
<button onclick="filtrar()">Maiores de 18</button>

<ul id="lista"></ul>
```

### JS

```javascript
let usuarios = [
    { nome: "Ana", idade: 20 },
    { nome: "João", idade: 15 }
];

function mostrar() {
    render(usuarios);
}

function filtrar() {
    let maiores = usuarios.filter(u => u.idade >= 18);
    render(maiores);
}

function render(arr) {
    lista.innerHTML = "";
    arr.forEach(u => {
        let li = document.createElement("li");
        li.textContent = `${u.nome} - ${u.idade}`;
        lista.appendChild(li);
    });
}
```

---

## 7 - Salvando tarefas no LocalStorage

### HTML

```html
<input id="tarefa">
<button onclick="add()">Adicionar</button>

<ul id="lista"></ul>
```

### JS

```javascript
let tarefas = JSON.parse(localStorage.getItem("tarefas")) || [];

function add() {
    tarefas.push(tarefa.value);
    salvar();
    render();
}

function salvar() {
    localStorage.setItem("tarefas", JSON.stringify(tarefas));
}

function render() {
    lista.innerHTML = "";
    tarefas.forEach(t => {
        let li = document.createElement("li");
        li.textContent = t;
        lista.appendChild(li);
    });
}

render();
```

---

## 8 - Editar item da lista

### HTML

```html
<input id="tarefa">
<button onclick="add()">Adicionar</button>

<ul id="lista"></ul>
```

### JS

```javascript
let tarefas = [];

function add() {
    tarefas.push(tarefa.value);
    render();
}

function editar(index) {
    let novo = prompt("Novo valor:");
    tarefas.splice(index, 1, novo);
    render();
}

function render() {
    lista.innerHTML = "";
    tarefas.forEach((t, i) => {
        let li = document.createElement("li");
        li.innerHTML = `${t} <button onclick="editar(${i})">Editar</button>`;
        lista.appendChild(li);
    });
}
```

---

## 9 - Catálogo de filmes

### HTML

```html
<input id="titulo">
<input id="genero">
<input id="ano">
<button onclick="add()">Adicionar</button>
<button onclick="filtrar()">Filtrar gênero</button>

<ul id="lista"></ul>
```

### JS

```javascript
let filmes = [];

function add() {
    filmes.push({
        titulo: titulo.value,
        genero: genero.value,
        ano: ano.value
    });

    render(filmes);
}

function filtrar() {
    let g = prompt("Digite o gênero:");
    let filtrados = filmes.filter(f => f.genero === g);
    render(filtrados);
}

function render(arr) {
    lista.innerHTML = "";
    arr.forEach(f => {
        let li = document.createElement("li");
        li.textContent = `${f.titulo} - ${f.genero}`;
        lista.appendChild(li);
    });
}
```

---

## 10 - Ranking de jogadores

### HTML

```html
<input id="jogador">
<input id="pontos">
<button onclick="add()">Adicionar</button>

<ul id="lista"></ul>
```

### JS

```javascript
let ranking = [];

function add() {
    ranking.push({
        jogador: jogador.value,
        pontos: Number(pontos.value)
    });

    mostrar();
}

function mostrar() {
    let ordenado = ranking.sort((a, b) => b.pontos - a.pontos);

    let posicoes = ordenado.map((j, i) => {
        return `${i + 1}º ${j.jogador} - ${j.pontos} pontos`;
    });

    lista.innerHTML = "";

    posicoes.forEach(p => {
        let li = document.createElement("li");
        li.textContent = p;
        lista.appendChild(li);
    });
}
```
