# AI SDK - GitHub Models

The GitHub Models provider for the [AI SDK](https://ai-sdk.dev/docs) gives you access to the [GitHub Models][feature] catalog of large language models, designed for building modern web applications.
GitHub Models has support for multiple model families, like [xAI](https://github.com/marketplace?publisher=xAI&type=models), [OpenAI](https://github.com/marketplace?publisher=OpenAI&type=models) and [Meta](https://github.com/marketplace?publisher=Meta&type=models).

> [!IMPORTANT]
> GitHub Models is currently in pre-release and subject to [GitHub Pre-release License Terms](https://docs.github.com/en/site-policy/github-terms/github-pre-release-license-terms).

To learn more about integrating GitHub Models into your projects, visit the [GitHub Models documentation](https://docs.github.com/en/github-models).

## Setup

The GitHub Models provider is available in the `@github/models` NPM package. You can install it with:

```bash
npm i @github/models
```

## Quick Start

To get started, you'll need a [GitHub PAT (personal access token)](https://github.com/settings/tokens).

```ts
import {githubModels} from '@github/models'
import {generateText} from 'ai'

const result = await generateText({
  model: githubModels('meta/meta-llama-3.1-8b-instruct'),
  prompt: 'Write a haiku about programming.',
})

console.log(result.text)
```

> [!TIP]
> GitHub Models includes [free usage](https://gh.io/models-rate-limits) for all accounts. For higher usage limits, you can opt into [paid usage](https://gh.io/github-models-pricing).

If you need a customized setup, you can import `createGithubModels` from `@github/models` and create a provider instance with your settings:

```ts
import {createGithubModels} from '@github/models'

const githubModels = createGithubModels({
  org: 'my-organization',
})
```

### Configuration Options

- **apiKey** _string_

  Your GitHub [Personal Access Token](https://github.com/settings/tokens) or [Fine-Grained Token](https://github.com/settings/personal-access-tokens) with `read:models` scope.
  Defaults to the `GITHUB_TOKEN` environment variable.

- **org** _string_

  Organization to attribute API usage to (optional).

- **baseURL** _string_

  Custom API endpoint URL.
  Defaults to `https://models.github.ai/inference`.

- **headers** _Record<string, string>_

  Additional headers to include with requests.

- **fetch** _(input: RequestInfo, init?: RequestInit) => Promise<Response>_

  Custom [fetch](https://developer.mozilla.org/en-US/docs/Web/API/fetch) implementation.
  Defaults to the global `fetch` function.
  You can use it as a middleware to intercept requests,
  or to provide a custom fetch implementation for e.g. testing.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of GitHub's trademarks or logos is subject to and must follow [GitHub's Brand Toolkit](https://brand.github.com/). Use of GitHub's trademarks or logos in modified versions of this project must not cause confusion or imply GitHub sponsorship. Any use of third-party trademarks or logos are subject to those third-party’s policies.

## License

Distributed under the MIT License. See [LICENSE](./license.txt) for more information.

<!-- LINKS -->

[feature]: https://github.com/features/models
