# Web-Development-Notes

## Credits

- [The Complete Junior to Senior Web Developer Roadmap](https://www.udemy.com/course/the-complete-junior-to-senior-web-developer-roadmap/)

## 1. General

- [Browser Rendering](General/browserRendering.md)
- [Optimising Javascript](General/optimisingJavascript.md)
- [Progressive Web App](General/progressiveWebApp.md)
- [Statically vs Dynamically Typed Languages](General/staticVsDynamic.md)
- [Setting up Window Subsystem for Linux](General/settingUpWSL.md)
- [Some Bash Tips](General/bashTips.md)

## 2. Frameworks And Libaries

- [Server-side vs Client-side Routing](FrameworksAndLibraries/serverSideVsClientSideRouting.md)

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

## 4. Testing

- [Introduction to Testing](testingIntro.md)

## 5. UI Resources

- [Material Design](https://material.io/)

## 6. FAQS

### [why does if(“string”) evaluate “string” as true but if (“string”==true) does not?](https://stackoverflow.com/questions/4923631/why-does-ifstring-evaluate-string-as-true-but-if-string-true-does-not)

It is being cast to Boolean. Any non-empty string evaluates to true.
