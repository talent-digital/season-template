# talent::digital season template

Use this template to create a new season for the [talent::digital](https://www.talentdigital.eu) platform.

You will need to obtain a **tenant id**, and a **episode provisioner client password** from talent::digital.

The [deploy season](https://github.com/talent-digital/deploy-season) github action is preconfigured to deploy your season to the talent::digital platform.

## 🐎 Getting Started

1. Create a repository using this template.
2. Run `npm install` or `pnpm install` or `yarn install` to install the [@talentdigital/season](https://www.npmjs.com/package/@talentdigital/season) package.
3. Add your **tenant id** into an [enviroment actions variable](https://docs.github.com/en/actions/learn-github-actions/variables) as `TENANT_ID`.
4. Add your **episode provisioner client password** into an [actions secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets) under `EPISODES_PROVISIONER_CLIENT_PASSWORD`.
5. Replace [assets/season.svg](/assets/season.svg) with your own season image.
6. Add your season configuration into the [season.yaml](/season.yaml) file.
7. Commit and push your changes to the **main** branch.
