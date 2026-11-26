# Meu Portfólio

Página de portfólio simples, responsiva e fácil de personalizar, feita com **HTML**, **CSS** e **JavaScript puro**.  
Toda a estrutura de dados, cores e seções da página fica centralizada em um objeto no `app.js`, permitindo adicionar ou alterar conteúdos sem precisar mexer no HTML.

---

## Como rodar localmente

Você pode testar o projeto no seu computador de duas formas:

1. **Direto no navegador:** dê um duplo clique no arquivo `index.html` para abri-lo.
2. **Usando VS Code (opcional):** se tiver a extensão *Live Server*, clique com o botão direito no `index.html` e escolha **Open with Live Server**.

---

## Onde editar o site

A maior parte da personalização acontece no arquivo **`app.js`**, dentro do objeto principal de configuração (ex.: `portfolioData`).

### 1. Alterar cores e estilo (`tema`)
Dentro de `tema`, você pode trocar as cores principais da página usando códigos hexadecimais (ex.: `#2563eb`):

```js
tema: {
  corPrimaria: "#2563eb", // Destaques, botões, bordas e links ativos
  corFundo: "#0f172a",    // Fundo geral da página
  corCard: "#1e293b",     // Fundo dos cartões e tags
  corTexto: "#f8fafc"     // Cor principal do texto
}
```

Também é possível ajustar detalhes visuais adicionais (como espaçamentos, fontes ou bordas) diretamente no arquivo `styles.css`.

---

### 2. Alterar seus dados pessoais (`perfil`)
No bloco `perfil`, atualize suas informações principais, foto e links:

```js
perfil: {
  nome: "Seu Nome Completo",
  cargo: "Desenvolvedor(a) / Estudante de Tecnologia",
  resumo: "Um parágrafo curto sobre o que você faz, aprende e quer construir.",
  foto: "./assets/avatar-placeholder.svg", // Pode ser um arquivo local ou URL de imagem
  links: [
    { rotulo: "GitHub", url: "[https://github.com/seu-usuario](https://github.com/seu-usuario)" },
    { rotulo: "LinkedIn", url: "[https://linkedin.com/in/seu-usuario](https://linkedin.com/in/seu-usuario)" }
  ]
}
```

> **Dica para imagens:** se colocar uma imagem dentro da pasta `assets/` (ex.: `assets/minha-foto.jpg`), referencie como `"./assets/minha-foto.jpg"`.

---

### 3. Alterar ou criar novas seções (`secoes`)

O menu superior e o corpo da página são gerados automaticamente a partir da lista `secoes`.  
Cada item dentro de `secoes` representa uma seção na página e deve ter:

* `id`: identificador único sem espaços e sem acentos (ex.: `"sobre"`, `"experiencias"`, `"contato"`). Usado para o link de navegação (`#id`).
* `titulo`: nome da seção que aparece no menu e no título do bloco.
* `tipo`: define como o conteúdo será exibido. Os tipos suportados são:
  * `"texto"`: um bloco de texto corrido (usa o campo `conteudo`).
  * `"lista"`: uma lista de itens/tags (usa o campo `itens` com um array de textos).
  * `"cards"`: grade de cartões com título, descrição, tags e link opcional (usa o campo `itens` com objetos).

#### Exemplo: editando uma seção existente
Para mudar o texto da seção *"Sobre mim"*, basta alterar o valor de `conteudo`:

```js
{
  id: "sobre",
  titulo: "Sobre mim",
  tipo: "texto",
  conteudo: "Escreva aqui a sua apresentação atualizada."
}
```

#### Exemplo: criando uma nova seção (`tipo: "lista"`)
Para adicionar uma seção de **Formação** ou **Idiomas**, basta incluir um novo objeto no array `secoes`:

```js
{
  id: "formacao",
  titulo: "Formação",
  tipo: "lista",
  itens: [
    "Curso Técnico / Graduação em TI",
    "Inglês Técnico"
  ]
}
```

#### Exemplo: criando uma seção com cartões (`tipo: "cards"`)
Ótima opção para **Projetos**, **Experiências** ou **Certificados**:

```js
{
  id: "certificados",
  titulo: "Certificados",
  tipo: "cards",
  itens: [
    {
      titulo: "Nome do Certificado",
      descricao: "Resumo do que foi aprendido ou desenvolvido no curso.",
      tags: ["Cloud", "Git"],
      link: "[https://exemplo.com/certificado](https://exemplo.com/certificado)"
    }
  ]
}
```

---

## Cuidados importantes ao editar o `app.js`

* **Vírgulas:** separe elementos de listas (`[...]`) e propriedades de objetos (`{...}`) por vírgula `,`.
* **Aspas:** mantenha textos entre aspas (`"..."` ou `'...'`). Se o texto tiver aspas duplas dentro, prefira usar aspas simples por fora ou escapar (`\"`).
* **IDs únicos:** evite repetir o mesmo `id` em duas seções diferentes para não quebrar a navegação da página.