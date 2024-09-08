# my-work-setup-node
Aqui fica minhas configurações de trabalho que me ajudam a otimizar meu trabalho com vscode. 


Aqui esta os plugins e configurações que uso para trabalhar com Node.js e NestJS no VSCode:

Plugins que recomendados:

ESLint
Ajuda a manter a consistência no código e detectar problemas em tempo de desenvolvimento. Para NestJS, é altamente recomendável configurar regras de lint específicas para TypeScript.

Prettier - Code formatter
Um formatador de código que se integra com o ESLint para garantir que o código fique limpo e consistente.

NestJS Snippets
Oferece snippets para gerar código mais rapidamente, como módulos, controladores e serviços, otimizando o desenvolvimento.

Path Intellisense
Fornece autocompletar para caminhos de arquivos, ajudando a evitar erros ao importar arquivos no projeto.

Debugger for Chrome
Para testar suas APIs ou aplicações frontend que se comunicam com NestJS diretamente no VSCode com debugging.

REST Client
Permite testar as rotas da API diretamente do VSCode, sem a necessidade de utilizar ferramentas externas como Postman.

Docker
Facilita o gerenciamento e integração com containers Docker, especialmente se você estiver usando Docker no desenvolvimento de suas aplicações.

GitLens
Melhora a integração do Git com o VSCode, mostrando histórico de commits, autores de cada linha, e mais, facilitando o versionamento do código.

Configurações que faço:
ESLint + Prettier integração: No arquivo settings.json do VSCode, configuro a integração entre ESLint e Prettier:
para abrir o settings.json faça:

para ir diretamente ao arquivo, pode pressionar Ctrl + Shift + P (ou Cmd + Shift + P no macOS) para abrir a paleta de comandos, digitar Preferences: Open Settings (JSON) e selecionar a opção.

a configuração fica da seguinte forma 

settings.json

{
  "editor.formatOnSave": true,
  "eslint.autoFixOnSave": true,
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    "typescript",
    "typescriptreact"
  ]
}

Debugging NestJS no VSCode: Adiciono uma configuração de depuração personalizada para NestJS no arquivo .vscode/launch.json:

launch.json:
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Launch NestJS",
      "skipFiles": ["<node_internals>/**"],
      "program": "${workspaceFolder}/src/main.ts",
      "outFiles": ["${workspaceFolder}/dist/**/*.js"],
      "sourceMaps": true
    }
  ]
}
Configuração de Docker:
 (caso se for usar containers): Certifico de ter um arquivo .devcontainer/devcontainer.json para configurar do ambiente de desenvolvimento dentro do Docker, algo como:

json
{
  "name": "NestJS Dev Container",
  "dockerFile": "Dockerfile",
  "appPort": [3000, 9229],
  "settings": {
    "terminal.integrated.shell.linux": "/bin/bash"
  },
  "extensions": [
    "dbaeumer.vscode-eslint",
    "esbenp.prettier-vscode"
  ],
  "postCreateCommand": "npm install"
}
Essas são as configurações e plugins que me ajudão a otimizar meu fluxo de trabalho com Node.js e NestJS no VSCode.
