# XPipe Vault (Keep this repository private!)

This repository contains all connection information that is designated to be shared.

You can sync with this repository in all XPipe application instances the same way, every change you make in one instance will be reflected in the repository. 

## Category list

- **Connections**
  - [**Total Tech Solutions**](categories/3916b391-9352-452f-84d3-321324956f84)
    - [**Production**](categories/51d7db05-2220-47c8-b671-ac73361cf99d)
    - [**Development**](categories/07d3d775-5ff3-4056-afe3-cebc08f0750a)
- **Scripts**
- **Identities**
- **Macros**

## Connection list

**All connections / Total Tech Solutions**

empty

**All connections / Total Tech Solutions / Production**

- [**TTS K8S**](stores/87fb1398-90f1-479c-a6ee-20c016e52c45)
  - [**Shell environments**](stores/d6069f55-f445-4f1a-a2b5-36ad0830b58f)
    - [**sudo**](stores/551c4426-f419-45a0-95bd-885217270e56)
- [**TTS-1721-SVR**](stores/c06106d3-31b3-46c7-bd9e-e2d315bd761c)
  - [**Shell environments**](stores/1daffdc9-b078-4ec8-a170-3e7d25d56ddf)
    - [**sudo**](stores/38298546-cbce-40b6-b1e7-bcb13de294a2)
- [**ttsunifi-2**](stores/a07367ac-aa09-4e6a-9c0f-c502338eec50)
  - [**Podman containers**](stores/953075ea-0cbd-4696-a5e5-0d160053818f)
  - [**Shell environments**](stores/af810d04-e17b-4f23-b650-209891aa3fd9)
    - [**sudo**](stores/719af986-744b-4ff4-8ee7-6ab83afa16bf)

**All connections / Total Tech Solutions / Development**

- [**TTS Portainer Dev Server**](stores/846e0f0b-eff4-4f14-a48d-c5c4aeeaef49)
  - [**Docker containers**](stores/c7178107-14f8-4c22-a760-5196635cc177)
    - [**default**](stores/fb87cad9-2f43-456d-9ebd-6c994970f383)
      - [**mssql-server**](stores/808677e1-308e-41fd-9830-883d911e3b03)
        - [**mssql**](stores/6ce592c3-5125-4c31-882f-25140b455bbb)
      - [**outline**](stores/569d5c18-caa6-44ad-8e80-bae9f55622d1)
        - [**outline-https-portal-1**](stores/edf07d5a-1ea7-415a-9e9a-d311d7377d30)
        - [**outline-outline-1**](stores/a01ad8e2-7430-485d-b088-9c8834fc21f2)
        - [**outline-postgres-1**](stores/0ee3cd36-c2ce-4577-b7d3-ea1f0b4d6dd8)
        - [**outline-redis-1**](stores/57d9ff85-8d17-475f-88f9-33e6ab815a34)
      - [**totaltech**](stores/607865f7-8157-4e55-8e8f-f70af9299265)
        - [**portainer**](stores/325d5452-7797-4820-b6df-0328e25ce3b3)
  - [**Shell environments**](stores/5bdb4cc2-2503-4f62-af91-c7f0d98f7390)
    - [**sudo**](stores/57c30fb5-c52b-4cfb-8327-c8f5f3b42556)
- [**TTS-CODE-SERVER**](stores/0249c8ff-f3b9-46ab-b62a-b91f9e4b41e1)



## Secret encryption

You have the option to fetch any sensitive information like passwords from outside sources like password managers or enter them at connection time through a prompt window. In that case, XPipe doesn't have to store any secrets itself.

In case you choose to store passwords and other secrets within XPipe, all sensitive information is encrypted when it is saved using AES with either:

- A dynamically generated key file `vaultkey` (The data can then only be decrypted with that file present)
- A custom passphrase that can be set for your user in the vault settings menu (This option can only as secure as the password you choose)

By default, general connection data is not encrypted, only secrets are.
So things like hostnames and usernames are stored without encryption, which is in line with many other tools.
There is an available setting in the vault settings menu to encrypt all connection data if you want to do that.

## Cloning the repository on other systems

Nowadays, most providers require a personal access token (PAT) to authenticate from the command-line instead of traditional passwords.
You can find common (PAT) pages here:
- **GitHub**: [Personal access tokens (classic)](https://github.com/settings/tokens)
- **GitLab**: [Personal access token](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)
- **BitBucket**: [Personal access token](https://support.atlassian.com/bitbucket-cloud/docs/access-tokens/)
- **Gitea**: `Settings -> Applications -> Manage Access Tokens section`
Set the token permission for repository to Read and Write. The rest of the token permissions can be set as Read.

Even if your git client prompts you for a password, you should enter your token unless your provider still uses passwords.

If you don't want to enter your credentials every time, you can use any git credentials manager for that.
For more information, see for example:
- https://git-scm.com/doc/credential-helpers
- https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git

Some modern git clients also take care of storing credentials automatically.

## Troubleshooting

### Adding connections to the repository

By default, no connection categories are set to sync so that you have explicit control on what connections to commit.

To have your connections of a category put inside your git repository, you first need to change its sync configuration.
In your `Connections` tab under the category overview on the left side, you can open the category configuration menu either by right-clicking the category or click on the `⚙️` icon when hovering over the category, and then clicking on the `🔧` configure button.

Then, set the `Sync with git repository` value to `Yes` to sync the category and connections to your git repository.
This will add all syncable connections in that category to the git repository.
The sync settings for a category are inherited by default from its parent if not explicitly set.

### Local connections are not synced

Any connection located under the local machine can not be shared as it refers to connections and data that are only available on the local system.
