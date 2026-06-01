# Como contribuir?

Este documento define os padrões de desenvolvimento e o fluxo de trabalho para os integrantes do grupo. Como estamos trabalhando em um repositório central compartilhado, seguir estas regras evita conflitos de código e perda de progresso. Em caso de dúvidas, [abra uma issue](https://github.com/victor-arcuri/tp-md/issues/new).

## 🔄 Fluxo de Desenvolvimento (GitFlow)

O fluxo é baseado em duas branches principais permanentes (`main` e `develop`) e branches de suporte temporárias (`feature/` e `fix/`).

### As Branches Principais

- `main`: Contém o código totalmente estável e pronto para entrega. **Ninguém faz commits aqui**. Ela só recebe merges da develop ao fim do desenvolvimento de cada etapa importante do trabalho.

- `develop`: Branch de integração. Todo o desenvolvimento do grupo se encontra aqui. É a partir dela que criamos novas tarefas e é nela que fazemos os merges.

### Passo a Passo para Desenvolver uma Tarefa
#### Atualize sua branch develop local

Antes de começar qualquer nova tarefa, certifique-se de que sua `develop` local está sincronizada com o GitHub para evitar conflitos:

```
git checkout develop
git pull origin develop
```

#### Crie uma branch de suporte partindo de develop

Dependendo da tarefa, crie uma branch de **Feature** (nova funcionalidade/tópico) ou de **Fix** (correção de bugs/erros):

Para novos tópicos ou funcionalidades (`feature/`):

```
git checkout -b feature/nome-da-tarefa
```

*Exemplo: `git checkout -b feature/topico-1-logica`*

Para correções de bugs ou erros de digitação (`fix/`):
```
git checkout -b fix/nome-da-correcao
```

*Exemplo: `git checkout -b fix/tabela-verdade`*

#### Desenvolva e faça o commit

Trabalhe no Jupyter Notebook. Ao commitar, utilize mensagens claras em português utilizando o padrão de commits simplificado.
```
git add .
git commit -m "feat: implementa a verificação de tabelas-verdade no tópico 1"
```

#### Envie sua branch para o GitHub
```
git push origin feature/nome-da-tarefa
```

*(ou `git push origin fix/nome-da-correcao`)*

#### Abra um Pull Request (PR) direcionado para develop

1. Vá até a página do repositório no GitHub.

2. Crie um novo Pull Request a partir da sua branch de tarefa.

3. **Atenção**: Defina a branch de destino (base) como `develop` (e **NÃO** `main`).

4. Adicione uma breve descrição das alterações e marque os outros dois integrantes como revisores.

#### Revisão e Merge na develop

Pelo menos um outro integrante do grupo deve revisar as alterações no código do Jupyter Notebook antes do PR ser aprovado. Após a aprovação, o merge na branch develop pode ser realizado.

### Fechamento de Versão (Merge na main)

Quando um o trabalho completo estiver 100% finalizado, testado na branch `develop` e pronto para a entrega final do professor:

1. Um dos integrantes abrirá um Pull Request de `develop` para `main`.

2. Após a aprovação do grupo, o merge é feito na `main`.

3. Recomenda-se criar uma tag na `main` para marcar a entrega:

```
git checkout main
git pull origin main
git tag -a v1.0 -m "Entrega do Trabalho"
git push origin v1.0
```

## 📌 Padrões de Commit

Para manter o histórico legível, adote o padrão **Conventional Commits** simplificado:

- `feat`: Quando adicionar novas funcionalidades ou resoluções de questões.

- `fix`: Para correção de bugs no código ou erros de digitação nas explicações.

- `docs`: Modificações exclusivas em documentações, arquivos markdown ou textos explicativos do notebook.

- `refactor`: Alterações de código que não mudam o comportamento final (otimizações).

## ⚠️ Atenção com Jupyter Notebooks (.ipynb)

Notebooks geram muitos metadados (como contadores de execução e saídas de imagens) que frequentemente causam conflitos de merge.

- **Boa Prática**: Sempre limpe as saídas do notebook (*Kernel > Clear All Outputs*) antes de dar `git add` e `git commit`, a menos que o output com os gráficos/resultados seja estritamente necessário para a entrega naquele commit.