# Web-Development-Notes

## Credits

- [The Complete Junior to Senior Web Developer Roadmap](https://www.udemy.com/course/the-complete-junior-to-senior-web-developer-roadmap/)

## 1. General

- [Browser Rendering](General/browserRendering.md)
- [Optimising Javascript](General/optimisingJavascript.md)
- [Progressive Web App](General/progressiveWebApp.md)
- [Statically vs Dynamically Typed Languages](General/staticVsDynamic.md)

## 2. Frameworks And Libaries

### Typescript

- Initialise project as typescript

```bash
tsc --init
```

- [Interface vs Type](FrameworksAndLibraries/interfaceVsType.md)
- [Typescript Deep Dive](https://basarat.gitbook.io/typescript/)

### React

- [Deploying Create-React-App](FrameworksAndLibraries/deployingReactApp.md)

## 3. Git

- [Difference between git reset --soft, --hard and --mixed](gitReset.md)

## 4. Bash

### Quick Setup of package.json

  ```bash
  npm init -y
  ```

### Upgrading Node with NVM

Check current node version

```bash
nvm ls
```

Installing latest node

```bash
nvm install node
```

Migrating globally installed packages

```bash
nvm reinstall-packages v13.12.0
```

Check list of globally installed packages

```bash
npm list -g --depth 0
```

## 5. Testing

- [Introduction to Testing](testingIntro.md)

## 6. FAQS

### [why does if(“string”) evaluate “string” as true but if (“string”==true) does not?](https://stackoverflow.com/questions/4923631/why-does-ifstring-evaluate-string-as-true-but-if-string-true-does-not)

It is being cast to Boolean. Any non-empty string evaluates to true.