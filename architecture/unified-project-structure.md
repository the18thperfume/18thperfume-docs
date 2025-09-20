# Unified Project Structure

Do kiến trúc là Polyrepo, chúng ta sẽ có hai cấu trúc dự án riêng biệt.

## Frontend (`18thperfume-frontend`)
```
/
├── .github/
│   └── workflows/
│       └── deploy.yaml
├── .next/
├── public/
├── src/
│   ├── app/                # Next.js App Router
│   ├── components/
│   ├── lib/
│   ├── services/
│   └── stores/
├── .eslintrc.json
├── next.config.mjs
├── package.json
└── tsconfig.json
```

## Backend (`18thperfume-backend`)
```
/
├── .github/
│   └── workflows/
│       └── deploy.yaml
├── src/
│   ├── handlers/
│   ├── core/
│   └── types/
├── tests/
│   ├── handlers/
│   └── integration/
├── .env.example
├── package.json
├── serverless.yml
└── tsconfig.json
```
