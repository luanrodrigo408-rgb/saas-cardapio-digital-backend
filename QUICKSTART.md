# Quick Start - SaaS Cardápio Digital Backend

## Setup Local (Development)

### 1. Pré-requisitos
- Node.js 20+
- PostgreSQL 14+ (local ou Docker)
- Git

### 2. Clone e Instale

```bash
git clone https://github.com/luanrodrigo408-rgb/saas-cardapio-digital-backend.git
cd saas-cardapio-digital-backend
npm install
```

### 3. Configure o Ambiente

```bash
cp .env.example .env
```

Edite o `.env` com suas configurações:
```env
DATABASE_URL="postgresql://user:password@localhost:5432/saas_cardapio?schema=public"
JWT_SECRET="seu-segredo-jwt-com-32-caracteres"
PORT=3000
NODE_ENV=development
FRONTEND_URL="http://localhost:3000"
```

### 4. Setup Banco de Dados

```bash
npx prisma generate
npx prisma migrate dev --name init
```

### 5. Rode o Servidor

```bash
npm run dev
```

Servidorestá em `http://localhost:3000`

### 6. Teste os Endpoints

**Health Check:**
```
GET http://localhost:3000/health
```

**Registrar usuário:**
```bash
curl -X POST http://localhost:3000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"email":"user@example.com","password":"password123","name":"John Doe","tenantSlug":"meu-restaurante"}'
```

**Login:**
```bash
curl -X POST http://localhost:3000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"user@example.com","password":"password123","tenantSlug":"meu-restaurante"}'
```

## Deploy no Railway

### 1. Prepare o Repo
```bash
git add .
git commit -m "Ready for Railway deployment"
git push
```

### 2. No Railway.app
1. Clique em "New Project"
2. Selecione "Deploy from GitHub"
3. Escolha este repositório
4. Railway detectará Node.js automaticamente

### 3. Configure Variáveis
No Dashboard do Railway, configure:
- `DATABASE_URL` - Railway PostgreSQL Plugin (auto-linkado)
- `JWT_SECRET` - Valor seguro e aleatório
- `NODE_ENV` - "production"
- `FRONTEND_URL` - URL do seu frontend

### 4. Deploy
Railway faz deploy automático quando você faz push ao main.

## Arquitetura

- **Server**: `src/server.js` - Setup Express com middlewares
- **Routes**: `src/routes/` - Rotas de auth, restaurants, categories, products
- **Database**: `prisma/schema.prisma` - Schema multi-tenant
- **Config**: `.env.example` - Template de variáveis

## Endpoints Principais

### Auth
- `POST /api/auth/register` - Registrar novo usuário/tenant
- `POST /api/auth/login` - Login

### Restaurants (CRUD)
- `GET /api/restaurants` - Listar todos
- `POST /api/restaurants` - Criar
- `GET /api/restaurants/:id` - Detalhe
- `PUT /api/restaurants/:id` - Atualizar
- `DELETE /api/restaurants/:id` - Deletar

### Categories (CRUD)
- `GET /api/categories/restaurant/:restaurantId`
- `POST /api/categories`
- `PUT /api/categories/:id`
- `DELETE /api/categories/:id`

### Products (CRUD)
- `GET /api/products/category/:categoryId`
- `POST /api/products`
- `PUT /api/products/:id`
- `DELETE /api/products/:id`

## Próximos Passos

1. ✅ Schema Prisma multi-tenant
2. ✅ Rotas de auth, restaurants, categories, products
3. ⏳ Middleware de autenticação (JWT validation)
4. ⏳ Testes com Postman/Thunder Client
5. ⏳ Frontend React/Next.js
6. ⏳ Webhook de pedidos
7. ⏳ Integração com Stripe/payment

## Suporte

Para dúvidas, abra uma issue no repositório!
