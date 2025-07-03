# Deploy React App no AWS Amplify - FIAP

Este repositório contém uma aplicação React básica que exibe "Hello World" na tela, desenvolvida para demonstrar o processo de deploy utilizando o AWS Amplify.

## 📋 Sobre a Aplicação

Esta é uma aplicação React simples criada com `create-react-app` que serve como exemplo prático para aprender sobre deploy e hospedagem de aplicações web na AWS.

### Tecnologias Utilizadas

- **React** ^18.2.0
- **React DOM** ^18.2.0
- **React Scripts** 5.0.1
- **AWS Amplify** (para deploy e hospedagem)

## 🚀 Como Executar Localmente

### Pré-requisitos

- Node.js (versão 14 ou superior)
- npm ou yarn
- Git

### Passos para Executar

1. **Clone o repositório**
   ```bash
   git clone https://github.com/LeticiaRosa/deploy-amplify-fiap.git
   cd deploy-amplify-fiap
   ```

2. **Instale as dependências**
   ```bash
   npm install
   ```

3. **Execute a aplicação**
   ```bash
   npm start
   ```

4. **Acesse a aplicação**
   - Abra seu navegador em `http://localhost:3000`
   - Você verá a mensagem "Hello World" na tela

## 📦 Deploy no AWS Amplify

### O que é o AWS Amplify?

O AWS Amplify é uma plataforma de desenvolvimento que permite criar, deployar e hospedar aplicações web e mobile de forma rápida e segura. Ele oferece:

- **Hospedagem estática** para aplicações frontend
- **Deploy automático** a partir de repositórios Git
- **HTTPS por padrão**
- **CDN global** para melhor performance
- **Integração com outros serviços AWS**

### Passo a Passo para Deploy

#### 1. Preparação da Conta AWS

1. **Acesse o Console AWS**
   - Vá para [console.aws.amazon.com](https://console.aws.amazon.com)
   - Faça login com sua conta AWS (ou crie uma se não tiver)

2. **Acesse o Amplify**
   - No console AWS, procure por "Amplify" na barra de pesquisa
   - Clique em "AWS Amplify"

#### 2. Configuração do Projeto

1. **Criar Nova Aplicação**
   - Clique em "Get Started" na seção "Host your web app"
   - Selecione "GitHub" como provedor de código

2. **Conectar Repositório**
   - Autorize o Amplify a acessar sua conta GitHub
   - Selecione o repositório: `LeticiaRosa/deploy-amplify-fiap`
   - Escolha a branch `main`

#### 3. Configuração de Build

1. **Configurações de Build**
   - O Amplify detectará automaticamente que é uma aplicação React
   - Configuração padrão será aplicada:
   ```yaml
   version: 1
   frontend:
     phases:
       preBuild:
         commands:
           - npm install
       build:
         commands:
           - npm run build
     artifacts:
       baseDirectory: build
       files:
         - '**/*'
     cache:
       paths:
         - node_modules/**/*
   ```

2. **Configurações Avançadas (Opcional)**
   - Nome da aplicação: `deploy-amplify-fiap`
   - Environment: `main`
   - Habilitar full-stack deployments: **Não** (apenas frontend)

#### 4. Deploy e Monitoramento

1. **Iniciar Deploy**
   - Clique em "Save and Deploy"
   - O Amplify iniciará o processo de build automaticamente

2. **Etapas do Deploy**
   - **Provision**: Configuração da infraestrutura
   - **Build**: Instalação de dependências e build da aplicação
   - **Deploy**: Upload dos arquivos para o CDN
   - **Verify**: Verificação da aplicação

3. **Monitoramento**
   - Acompanhe o progresso em tempo real
   - Verifique logs de build em caso de erros

#### 5. Acesso à Aplicação

1. **URL da Aplicação**
   - Após o deploy, você receberá uma URL única
   - Formato: `https://main.dxxxxxx.amplifyapp.com`

2. **Configuração de Domínio Personalizado (Opcional)**
   - Vá para "Domain management"
   - Adicione seu domínio personalizado
   - Configure os registros DNS conforme indicado

## 🔄 Deploy Contínuo

### Configuração Automática

O AWS Amplify oferece **deploy contínuo** automaticamente:

- **Commits na branch main** disparam novo deploy
- **Build automático** a cada push
- **Rollback automático** em caso de falha
- **Preview de branches** para desenvolvimento

### Fluxo de Trabalho

1. **Desenvolvimento Local**
   ```bash
   # Fazer alterações no código
   git add .
   git commit -m "Nova funcionalidade"
   git push origin main
   ```

2. **Deploy Automático**
   - O Amplify detecta o push
   - Inicia build automaticamente
   - Atualiza a aplicação em produção

## 📊 Recursos Aprendidos

### Conceitos Importantes

1. **Hospedagem Estática**
   - Aplicações React são compiladas para arquivos estáticos
   - HTML, CSS e JavaScript são servidos por CDN

2. **Build Process**
   - `npm run build` cria versão otimizada
   - Minificação e otimização automática
   - Geração de arquivos estáticos na pasta `build/`

3. **CDN (Content Delivery Network)**
   - Distribuição global de conteúdo
   - Melhor performance para usuários
   - Cache automático de arquivos

4. **HTTPS e Segurança**
   - Certificado SSL/TLS automático
   - Conexão segura por padrão
   - Proteção contra ataques comuns

### Vantagens do AWS Amplify

- ✅ **Facilidade de uso**: Interface intuitiva
- ✅ **Deploy automático**: Integração com Git
- ✅ **Escalabilidade**: Suporta alto tráfego
- ✅ **Performance**: CDN global da AWS
- ✅ **Custo-benefício**: Pricing baseado em uso
- ✅ **Segurança**: HTTPS por padrão

## 🛠️ Comandos Úteis

```bash
# Instalar dependências
npm install

# Executar em desenvolvimento
npm start

# Criar build de produção
npm run build

# Executar testes
npm test

# Verificar build localmente
npx serve -s build
```

## 📝 Estrutura do Projeto

```
deploy-amplify-fiap/
├── public/
│   ├── index.html
│   └── manifest.json
├── src/
│   ├── App.js
│   ├── App.css
│   ├── index.js
│   └── index.css
├── package.json
├── README.md
└── Dockerfile (para containerização)
```

## 🔧 Troubleshooting

### Problemas Comuns

1. **Build Falha**
   - Verificar versão do Node.js
   - Limpar cache: `npm cache clean --force`
   - Deletar `node_modules` e reinstalar

2. **Deploy Não Atualiza**
   - Verificar se commit foi feito na branch correta
   - Aguardar alguns minutos para propagação
   - Verificar logs de build no console Amplify

3. **Erro 404**
   - Verificar configuração de redirecionamento
   - Para SPAs, configurar redirect rules

## 📚 Recursos Adicionais

- [Documentação AWS Amplify](https://docs.aws.amazon.com/amplify/)
- [AWS Amplify Console](https://console.aws.amazon.com/amplify/)
- [React Documentation](https://reactjs.org/docs/)

## 👥 Contribuição

Este projeto foi desenvolvido para fins educacionais na FIAP. Sinta-se à vontade para fazer fork e experimentar!

---

**Desenvolvido com ❤️ para aprender sobre deploy e AWS Amplify**
