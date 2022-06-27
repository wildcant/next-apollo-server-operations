## Goal

Generate apollo client functions that can be used to make request to a graphql server within `getServerSideProps`, `getStaticProps` etc.

## Configuration

## Example config

```
overwrite: true
schema:
    - 'https://myschema/graphql'
documents:
    - 'src/**/*.graphql'
generates:
  temp/operations.ts:
    plugins:
      - 'typescript'
      - 'typescript-operations'
      - 'typescript-react-apollo'
    config:
      withHooks: true
      withHOC: false
      withComponent: false
  temp/server-operations.ts:
    config:
      documentMode: external
      importDocumentNodeExternallyFrom: ./operations
      reactApolloVersion: 3
      contextType: 'ApolloClientContext'
      contextTypeRequired: false
      # excludePatterns: 'getComments'
      # excludePatternsOptions: 'i'
      # customDataIdFromObjectName: 'test'
      # customDataIdFromObjectImport: 'abc'
      apolloClientInstanceImport: './withApollo'
      # apolloStateKey: '__APOLLO_STATE__'
    preset: import-types
    presetConfig:
      typesPath: ./operations
    plugins:
      - build/src/index.js # replace with this plugin build location.

```

Forked from graphql-codegen-apollo-next-ssr.
