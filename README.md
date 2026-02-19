# SaaS Cardápio Digital - Backend

Backend Node.js + Express + Prisma + PostgreSQL para SaaS de Cardápio Digital com arquitetura multi-tenant.

## 🚀 Stack Tecnológica

- **Runtime**: Node.js 20+
- **Framework**: Express.js
- **ORM**: Prisma
- **Banco de Dados**: PostgreSQL
- **Autenticação**: JWT (JSON Web Tokens)
- **Segurança**: Helmet, CORS, bcryptjs

## 📂 Estrutura do Projeto

```
.
├── package.json
├── prisma/
│   └── schema.prisma
├── src/
│   ├── server.js
│   ├── config/
│   │   └── database.js
│   ├── middlewares/
│   │   └── auth.js
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── usersController.js
│   │   ├── restaurantsController.js
│   │   ├── categoriesController.js
│   │   └── productsController.js
│   └── routes/
│       ├── auth.js
│       ├── users.js
│       ├── restaurants.js
│       ├── categories.js
│       └── products.js
├── .env.example
├── .gitignore
├── Dockerfile
└── docker-compose.yml
```

## 📝 Código Completo

**TODOS os arquivos com código completo estão disponíveis no Perplexity:**

🔗 **Link**: https://www.perplexity.ai/search/crie-a-estrutura-completa-de-a-DZA.2zofSLmTV5YzzYbfsA

Copie e cole todos os arquivos do Perplexity neste repositório:

1. ✅ `package.json` (já criado)
2. `prisma/schema.prisma`
3. `src/server.js`
4. `src/middlewares/auth.js`
5. `src/controllers/authController.js`
6. `src/controllers/usersController.js`
7. `src/controllers/restaurantsController.js`
8. `src/controllers/categoriesController.js`
9. `src/controllers/productsController.js`
10. `src/routes/auth.js`
11. `src/routes/users.js`
12. `src/routes/restaurants.js`
13. `src/routes/categories.js`
14. `src/routes/products.js`
15. `src/config/database.js`
16. `.env.example`
17. `Dockerfile`
18. `docker-compose.yml`

## ⚙️ Instalação Local

```bash
# 1. Clone o repositório
git clone https://github.com/luanrodrigo408-rgb/saas-cardapio-digital-backend.git
cd saas-cardapio-digital-backend

# 2. Instale as dependências
npm install

# 3. Configure as variáveis de ambiente
cp .env.example .env
# Edite .env com suas credenciais

# 4. Configure o Prisma
npx prisma generate
npx prisma migrate dev --name init

# 5. Inicie o servidor
npm run dev
```

## 📦 Variáveis de Ambiente

Crie um arquivo `.env` na raiz do projeto:

```env
DATABASE_URL="postgresql://user:password@localhost:5432/saas_cardapio?schema=public"
JWT_SECRET="seu-jwt-secret-super-seguro-aqui-min-32-chars"
NODE_ENV=development
PORT=3000
```

## 🚀 Deploy no Railway

1. Faça push do código completo para este repositório
2. Acesse [railway.app](https://railway.app)
3. Clique em "New Project" → "Deploy from GitHub repo"
4. Selecione este repositório
5. Adicione PostgreSQL: "New" → "Database" → "PostgreSQL"
6. Configure as variáveis:
   - `DATABASE_URL` (copiado automaticamente do PostgreSQL)
   - `JWT_SECRET` (gere um segredo forte)
   - `NODE_ENV=production`
7. Build Command: `npm install && npx prisma generate`
8. Start Command: `npm start`
9. Deploy!

## 📚 Documentação da API

### Autenticação

**POST** `/api/auth/register`
```json
{
  "name": "Luan Marques",
  "email": "luan@panzeroni.com",
  "password": "senha123"
}
```

**POST** `/api/auth/login`
```json
{
  "email": "luan@panzeroni.com",
  "password": "senha123"
}
```
Resposta:
```json
{
  "token": "eyJhbGciOiJIUzI1NiIs...",
  "user": { "id": "...", "role": "OWNER" }
}
```

**GET** `/api/auth/me`
Headers: `Authorization: Bearer {token}`

### Restaurants

**POST** `/api/restaurants` (auth)
```json
{
  "name": "Panzeroni",
  "description": "Melhor pizzaria de Fortaleza",
  "address": "Rua X, 123"
}
```

**GET** `/api/restaurants` (auth)
**GET** `/api/restaurants/:id` (auth)
**PUT** `/api/restaurants/:id` (auth)
**DELETE** `/api/restaurants/:id` (auth)

### Categories

**POST** `/api/categories` (auth)
```json
{
  "name": "Pizzas",
  "restaurantId": "...",
  "position": 0
}
```

**GET** `/api/categories/restaurant/:restaurantId`
**PUT** `/api/categories/:id` (auth)
**DELETE** `/api/categories/:id` (auth)

### Products

**POST** `/api/products` (auth)
```json
{
  "name": "Pizza Margherita",
  "description": "Tomate, mussarela, manjericão",
  "price": 42.90,
  "categoryId": "...",
  "image": "https://...",
  "position": 0
}
```

**GET** `/api/products/category/:categoryId`
**PUT** `/api/products/:id` (auth)
**DELETE** `/api/products/:id` (auth)

## 🔒 Segurança

- ✅ Autenticação JWT
- ✅ Senhas criptografadas com bcryptjs
- ✅ Helmet para headers HTTP seguros
- ✅ CORS configurado
- ✅ Validação de entrada
- ✅ Rate limiting (implementar)

## 📊 Próximos Passos

- [ ] Adicionar todos os arquivos do Perplexity
- [ ] Testar localmente
- [ ] Deploy no Railway
- [ ] Integrar com frontend
- [ ] Adicionar testes unitários
- [ ] Implementar rate limiting
- [ ] Adicionar logs com Winston
- [ ] Cache com Redis

## 📄 Links Úteis

- **Código Completo**: https://www.perplexity.ai/search/crie-a-estrutura-completa-de-a-DZA.2zofSLmTV5YzzYbfsA
- **Guia de Deploy**: https://www.perplexity.ai/search/crie-um-guia-completo-de-deplo-UjUBkKfYQV.cZvD6gRzkBQ
- **Documentação Completa**: [Google Docs](https://docs.google.com/document/d/1_2fjGRqwl5V8gsUBPR-pdAatTucV1AUUMyn9N2QNuPE/edit)

## 👤 Autor

**Luan Marques** - Fortaleza, CE

Criado em: 19/02/2026
