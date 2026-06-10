# 63 - GitHub GraphQL Basics

GraphQL allows you to request exactly the data you need in a single request.

## Key Concepts
- **Endpoint:** `https://api.github.com/graphql`
- **Method:** `POST`
- **Authentication:** `Bearer ${{ secrets.GITHUB_TOKEN }}`

## Example Query
```graphql
query {
  repository(owner: "octocat", name: "Hello-World") {
    name
    description
    stargazerCount
  }
}
```

## Usage in Actions
```yaml
- name: GraphQL Query
  run: |
    curl -H "Authorization: bearer ${{ secrets.GITHUB_TOKEN }}" \
         -X POST \
         -d '{"query": "query { viewer { login } }"}' \
         https://api.github.com/graphql
```

## Exam Tips
- Use GraphQL when you need to fetch nested data efficiently.
- `actions/github-script` also supports GraphQL via `github.graphql()`.
- You can test queries in the [GitHub GraphQL Explorer](https://docs.github.com/en/graphql/overview/explorer).
