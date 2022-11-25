# React GraphQL with end-to-end type safety

This project is referred to [this article](https://www.prisma.io/blog/e2e-type-safety-graphql-react-1-I2GxIfxkSZ)

## GraphQL-server

1. `cp .env.example .env` and provide PostgreSQL database url to `DATABASE_URL`
2. `npm i` (it will run `prisma generate` after installation automatically to generate `@prisma/client` and `@pothos/plugin-prisma/generated`)
3. (optional if tables already exists) `npm run prisma:push` to generate tables in the database
4. (optional) seed database with `npm run prisma:seed`
5. `npm run dev` to start server in port 4000

### Note

1. Generate GraphQL entity types from Prisma schema with `@pothos/plugin-prisma`
2. Entity fields to be exposed, query and mutation types need to be defined in js way, with `@pothos/core` `SchemaBuilder`
3. `pothos` provides type-safe resolver
4. Customized scalar type `Date` defined by `graphql-scalars`

## React-client

1. `npm i`
2. edit `codegen.yml`, provide graphql server url
3. start GraphQL server so that codegen can fetch schema
4. `npm run codegen` to generate `./graphql/generated.ts`
5. `npm run dev` to start server

### Note

1. `graphql-codegen` fetch schema from server, so generated type will always be correct (if it is up to date)
2. generate typescript from `.graphql` schema file
