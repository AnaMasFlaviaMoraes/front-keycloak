
# 🔐 Autenticação com Keycloak em uma Aplicação React

Este projeto demonstra como integrar o **Keycloak** com uma aplicação **React** básica para proteger rotas e acessar dados do usuário autenticado.

---

## ✅ Pré-requisitos

- Node.js (v18 ou superior)
- Yarn ou npm
- Keycloak em execução (pode ser via Docker)
- Conta de administrador no Keycloak

---

## ⚙️ 1. Subindo o Keycloak com Docker (opcional)

```
docker run -p 8080:8080 \
-e KEYCLOAK_ADMIN=admin \
-e KEYCLOAK_ADMIN_PASSWORD=admin \
quay.io/keycloak/keycloak:24.0.3 start-dev
```

Acesse: http://localhost:8080

---

## 🏗️ 2. Configurando o Keycloak

### 2.1 Criar um Realm

- Acesse o painel de admin (`http://localhost:8080/admin`)
- Vá em **Realm settings > Add Realm**
- Nomeie como: `ReactRealm`

### 2.2 Criar um Cliente

- Vá em **Clients > Create client**
- `Client ID`: `react-client`
- `Client type`: `Public`
- `Root URL`: `http://localhost:3000`
- Salvar

Na aba “Settings” do cliente:
- `Valid redirect URIs`: `http://localhost:3000/*`
- `Web origins`: `*`

Salvar novamente.

### 2.3 Criar um Usuário

- Vá em **Users > Add user**
- Defina um nome de usuário e email
- Salvar
- Vá na aba **Credentials**, defina uma senha e desmarque “Temporary”

---

## ⚛️ 3. Criando a aplicação React

### 3.1 Criar o projeto

```
npx create-react-app nome-aplicacao

```

### 3.2 Instalar dependências

```
npm install @react-keycloak/web keycloak-js
```

---

## 🧩 4. Integrando Keycloak ao React


## 🚀 5. Rodando o projeto

```
npm start
```

A aplicação abrirá em `http://localhost:3000`. Você será redirecionado para o Keycloak para login.

---

## 🛠️ Dicas

- O Keycloak salva o token no `sessionStorage` por padrão.
- É possível proteger rotas com `PrivateRoute` se for usar `react-router-dom`.

---

## 📚 Referências

- [Documentação oficial do Keycloak](https://www.keycloak.org/documentation)
- [react-keycloak GitHub](https://github.com/react-keycloak/react-keycloak)
