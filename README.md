# Trabalho Prático - Matemática Discreta

![GitHub repo size](https://img.shields.io/github/repo-size/iuricode/README-template?style=for-the-badge)
![GitHub language count](https://img.shields.io/github/languages/count/iuricode/README-template?style=for-the-badge)
![GitHub forks](https://img.shields.io/github/forks/iuricode/README-template?style=for-the-badge)
![Bitbucket open issues](https://img.shields.io/bitbucket/issues/iuricode/README-template?style=for-the-badge)
![Bitbucket open pull requests](https://img.shields.io/bitbucket/pr-raw/iuricode/README-template?style=for-the-badge)


Boas vindas ao repositório do **Trabalho Prático** para o curso de **Matemática Discreta de 2026/1**. As orientações gerais do projeto podem ser encontradads [AQUI](docs/orientacoes.md). Para as orientações de cada tópico:

- [Tópico 1](docs/topico-1.md) 
- [Tópico 2](docs/topico-2.md) 
- [Tópico 3](docs/topico-3.md) 
- [Tópico 4](docs/topico-4.md) 
- [Tópico 5](docs/topico-5.md) 

## 📋 Progresso

O **Trabalho Prático** ainda está em desenvolvimento e as próximas atualizações serão voltadas para as seguintes tarefas:

- [X] Tópico 1
- [ ] Tópico 2
- [ ] Tópico 3
- [ ] Tópico 4
- [ ] Tópico 5

## 💻 Pré-requisitos

Antes de começar, verifique se você atendeu aos seguintes requisitos:

- Você instalou a versão `3.10` ou superior de `python`.
- Você instalou localmente `git`.
- Você tem uma máquina `Windows / Linux / Mac`.
- Você leu toda a documentação do repositório.

## 🚀 Instalando o Repositório e Configurando o Ambiente
Para instalar o repositório do trabalho, siga estas etapas:

**Linux e macOS**:
```
git clone https://github.com/victor-arcuri/tp-md.git
cd tp-md
python -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```
**Windows**:

Abra o PowerShell ou o Prompt de Comando (CMD) e execute:
```
git clone https://github.com/victor-arcuri/tp-md.git
cd tp-md
python -m venv venv
```
Se estiver usando o PowerShell:
```
venv\Scripts\Activate.ps1
```
*(Se der erro de script desabilitado no PowerShell, execute antes: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process)`*

Se estiver usando o CMD comum:
```
venv\Scripts\activate.bat
```

Após ativar o ambiente virtual:

```
pip install --upgrade pip
pip install -r requirements.txt
```

## ☕ Configurando o Kernel e Rodando o Jupyter

Para garantir que o Jupyter encontre as bibliotecas instaladas no ambiente virtual, registre o kernel antes de rodar o painel.

### Registrar o Kernel (Passo único)

Com o ambiente virtual (venv) ativo no terminal, execute:

```
python -m ipykernel install --user --name=matematica-discreta --display-name="Matemática Discreta (Venv)"
```

### Executar o Jupyter Notebook

Inicie o painel interativo executando na raiz do projeto:

```
jupyter notebook
```

### Selecionar o Kernel no Documento

Ao abrir o arquivo `notebook.ipynb`, altere o ambiente de execução:

1. No menu superior, clique em *"Kernel"*.

2. Clique em *"Change kernel" (Alterar Kernel)*.

3. Selecione a opção *"Matemática Discreta (Venv)"*.

> [!WARNING]
> *Aviso importante*: Sempre vá em *Kernel > Clear All Outputs* antes de salvar e fazer `git commit` para evitar conflitos de merge no Git do grupo.

## 📫 Como Contribuir

As instruções de como contribuir com o projeto podem ser encontadas [AQUI](CONTRIBUTING.md).
## 🤝 Integrantes do Grupo

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/victor-arcuri" title="Github de Victor Romano Arcuri">
        <img src="https://avatars.githubusercontent.com/u/50268612?v=4" width="100px;" alt="Foto de Victor Romano Arcuri no GitHub"/><br>
        <sub>
          <b>Victor Romano Arcuri</b>
        </sub>
      </a>
    </td>
    <td align="center">
      <a href="https://github.com/B-DuarteS" title="Github de Breno Oliveira Duarte">
        <img src="https://avatars.githubusercontent.com/u/203674840?v=4" width="100px;" alt="Foto de Breno Oliveira Duarte"/><br>
        <sub>
          <b>Breno Oliveira Duarte</b>
        </sub>
      </a>
    </td>
    <td align="center">
      <a href="https://github.com/maciel-vinicius" title="Github de Vinícius Maciel Pimentel">
        <img src="https://avatars.githubusercontent.com/u/228737067?v=4" width="100px;" alt="Foto de Vinícius Maciel Pimentel"/><br>
        <sub>
          <b>Vinícius Maciel Pimentel</b>
        </sub>
      </a>
    </td>
  </tr>
</table>
