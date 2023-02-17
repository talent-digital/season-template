# talent::digital season template

Use this template to create a new season for the [talent::digital](https://www.talentdigital.eu) platform and to get any changes automatically installed through a [Github action](https://github.com/talent-digital/deploy-season) and [Netlify](https://www.netlify.com/). Please note that you need an own Netlify account. Free plans are available.

## 🐎 Getting Started

0. Contact support@talentdigital.eu to request an **episode provisioner client password**. The password will permit deployment of new content into your talent::digital tenant using the Github action.
1. Create a repository using this template.
2. Run `npm install` or `pnpm install` or `yarn install` to install the [@talentdigital/season](https://www.npmjs.com/package/@talentdigital/season) package.
3. Add your **tenant id** into an [enviroment actions variable](https://docs.github.com/en/actions/learn-github-actions/variables) as `TENANT_ID`. The tenant ID is the first part of your talent::digital URL. E.g., if you URL is *mytenant.talentdigital.eu*, the tenant ID is *mytenant*.
4. Add your **episode provisioner client password** into an [actions secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets) under `EPISODES_PROVISIONER_CLIENT_PASSWORD`.
5. Replace [assets/season.svg](/assets/season.svg) with your own season image.
6. [Add your new repository to your Netlify account](https://www.netlify.com/blog/2016/09/29/a-step-by-step-guide-deploying-on-netlify/).
7. Optional: Customise your _site name_ on Netlify to get a custom Netlify URL. 
8. Add your season configuration into the [season.yaml](/season.yaml) file, adding your **Netlify URL** under the key **assetsURL**.
9. Commit and push your changes to the **main** branch to deploy the season to the platform.

Note: Pull requests and changes on branches will not be deployed to your talent::digital tenant. This way, you can safely test your changes without interferring with deployed content. See [talentkit](https://github.com/talent-digital/talentkit) for more information.

## Configuration

_Example season.yaml_

```yaml
title:
  de: Season Title in German
  en: Season Title in German
info:
  de: Season Description in German
  en: Season Description in English
assetsURL: the netlify url of for the season https://{season id}.netlify.app
competenceAreas:
  "Competence Area 1": # Competence Area Id (string)
    competences:
      "Competence 1": # Competence Id (string)
        subCompetences:
          "Sub Competence 1": # Sub Competence Id (string)
            name:
              de: Name of Subcompetence in German
              en: Name of Subcompetence in English
            testItems: # Tests that belong to this sub competence
              "Test Item 1" # Test Id (string)
                level: FOUNDATION # Level of the test FOUNDATION, INTERMEDIATE, ADVANCED, HIGHLY_SPECIALISED
                episode: "Episode 1" # Id of the episode this test item is used in
                documentation:
                  de: Test description # German description of the skill this test measures
                  en: Test description # English description of the skill this test measures
                search:
                  de:
                    generic:
                      - search term in German # German searches that are carried out by the scraper
                  en:
                    generic:
                      - search term in English # English searches that are carried out by the
            feedbackQuestions: # Feedback that is collected for this sub competence
              "Feedback Question 1": # Feedback Question Id (string)
                episode: "Episode 1" # Id of the episode this feedback question is used in
                question: # The question to ask
                  de: German Question
                  en: English Question
                answers: # The answers, ordered from assumed good to bad.
                  "0":
                    de: Option in German
                    en: Option in English
                  "1":
                    de: Option in German
                    en: Option in English
                  "2":
                    de: Option in German
                    en: Option in English

episodes:
  "Episode 1": # The episode Id
    title: # The episode title
      de: Title in German
      en: Title in English
    description:
      de: Episode description in German
      en: Episode description in English
    maturity: PUBLIC #
    imageUrl: filename # The filename of the images, base is the assetsUrl
    format: formatId # The id of the format this episode uses
    formatConfiguration: filename # The filename of the configuration for this format, supports json, yaml, toml & markdown
    badges: # A list of badges
      "Badge 1":
        name:
          de: Badge name in German
          en: Badge name in English
        image: filename # The filename of the image used for this badge, base is the assetsUrl

seasonEndMessage: # The message displayed when the last episode in this season is played
  de: Message in German
  en: Message in English
```
