# Swifters

The Swifters iOS app lets you browse [Swift](https://swift.org/) users on [GitHub](https://github.com). Its purpose is to explore [GraphQL](https://graphql.org) with [Apollo iOS](https://www.apollographql.com/docs/ios/), a strongly-typed, caching GraphQL client. Swifters queries GitHub’s [GraphQL API v4](https://developer.github.com/v4/). If your new to GraphQL, you might want to read my [introduction](https://troubled.pro/2019/02/graphql.html).

The Swifters iOS app lets you browse [Swift](https://swift.org/) users on [GitHub](https://github.com). Its purpose is to explore [GraphQL](https://graphql.org) with [Apollo iOS](https://www.apollographql.com/docs/ios/), a strongly-typed, caching GraphQL client. Swifters queries GitHub’s [GraphQL API v4](https://developer.github.com/v4/).

![Screenshot 1](./screenshots/1.jpg) ![Screenshot 2](./screenshots/2.jpg)

Swifters progressively populates its [cache](https://www.apollographql.com/docs/ios/watching-queries.html), while users scroll a list of Swift developers on GitHub, loading two to three handfuls of Swifters at a time. Tapping a developer in the list shows details.

## Objectives

- Explore GraphQL building a *modern* application with Apollo and [UICollectionView](https://developer.apple.com/documentation/uikit/uicollectionview)
- Compare the imperative and procedural REST approach to the declarative GraphQL
- Paginate with [UICollectionViewDataSourcePrefetching](https://developer.apple.com/documentation/uikit/uicollectionviewdatasourceprefetching)

## Dependencies

- [Apollo iOS](https://github.com/apollographql/apollo-ios) – A strongly-typed, caching GraphQL client
- [DeepDiff](https://github.com/onmyway133/DeepDiff) – Amazingly incredible extraordinary lightning fast diffing
- [Nuke](https://github.com/kean/Nuke) – Image loading and caching
- [Ola](https://github.com/michaelnisi/ola) – Check reachability of host

## Installation

### Accessing GitHub

Swifters needs a personal access token to communicate with [GitHub’s GraphQL server](https://developer.github.com/v4/guides/forming-calls/#authenticating-with-graphql).

These scopes are required:

- `read:user`
- `user:email`

### Preparing the Workspace

```
$ GITHUB_TOKEN=<token> make
```

#### What this does

- Clone repositories of framework dependencies into `./deps`
- Generate `./apollo.config.js` with your GitHub token
- Copy `./apollo.config.js` to `./Swifters/github/apollo.config.json`

## Running the app

```
$ open Swifters.xcworkspace
```

- Select Swifters scheme
- Run ⌘R

🙌

## Onwards

If you want to modify GraphQL queries to develop this app further, you need code generation tooling. [Apollo GraphQL](https://www.apollographql.com) tools are written in [TypeScript](https://www.typescriptlang.org) and run on [Node.js](https://nodejs.org).

### Apollo CLI

```
$ npm i -g apollo
```

### Generating Swift files from GraphQL queries

After you have adjusted `*.graphql` queries to your needs, you must generate the GraphQL related Swift source files. Apollo recommends adding a [Run Script Phase](https://www.apollographql.com/docs/ios/installation#adding-build-step) to your Xcode target, but I find using the command line interface directly less opaque.

```
$ apollo client:codegen --target=swift ./Swifters/github
```

## License

[MIT License](https://github.com/michaelnisi/swifters/blob/master/LICENSE)
