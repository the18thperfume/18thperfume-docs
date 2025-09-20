# Deployment Architecture

## CI/CD Pipeline

Mỗi repository sẽ có một pipeline GitHub Actions riêng.

### Backend Deploy Pipeline (`18thperfume-backend/.github/workflows/deploy.yaml`)
```yaml
name: Deploy Backend
on:
  push:
    branches:
      - main
jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '20.x'
      - name: Install Dependencies
        run: npm install
      - name: Configure AWS Credentials
        uses: aws-actions/configure-aws-credentials@v2
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: ap-southeast-1
      - name: Deploy with Serverless
        run: npx serverless deploy --stage prod
```

### Frontend Deploy Pipeline (`18thperfume-frontend/.github/workflows/deploy.yaml`)
```yaml
name: Deploy Frontend
on:
  push:
    branches:
      - main
jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '20.x'
      - name: Install Dependencies
        run: npm install
      - name: Build
        run: npm run build
      - name: Configure AWS Credentials
        # ... (tương tự backend)
      - name: Sync to S3
        run: aws s3 sync ./out s3://${{ secrets.S3_BUCKET_NAME }} --delete
      - name: Invalidate CloudFront
        run: aws cloudfront create-invalidation --distribution-id ${{ secrets.CLOUDFRONT_DIST_ID }} --paths "/*"
```

## Environments

| Environment | Frontend URL | Backend URL | Purpose |
| :--- | :--- | :--- | :--- |
| Development | `http://localhost:3000` | `http://localhost:3001` | Local development |
| Production | `https://18thperfume.com` | `https://api.18thperfume.com/v1` | Live environment |
