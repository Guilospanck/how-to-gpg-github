# how-to-gpg-github
How to create your GPG key and import it and sign your commits.

### [Generate your GPG keys]
You can easily generate your GPG keys using the gpg bundle.
It'll all depend on the type of system you're working on. For MacOS, download [GPG Suite](https://gpgtools.org/) and generate your keys following the steps.
Choose at least 4096 bytes and RSA.

After that, run the following command and copy the fingerprint of your public key.
```bash
gpg --list-secret-keys --keyid-format=long
```

Then, add it to your `.gitconfig` global:
```bash
git config --global user.signingKey {fingerprint}
```

To sign all your commits automatically (and not rely on `-S`):
```bash
git config --global commit.gpgsign true 
```

### [Adding GPG key to your Github account](https://docs.github.com/en/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account)

## Using GPG
- Search for keys from other people:
```bash
gpg --search-keys <email>
```

- Get your complete public key:
```bash
gpg --armor --export <fingerprint> 
```

- Get GPG key from another GitHub user:
```bash
curl https://api.github.com/users/Guilospanck/gpg_keys | jq ".[0].raw_key" -r | gpg --import 
```

- Decrypt file
```bash
gpg --decrypt hello.go.gpg > hello.go
```
