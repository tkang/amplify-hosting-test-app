# Deploy a Next.js app to Amplify Hosting

[English](README.md)

본 가이드는 Next.js app 을 [Amplify Hosting](https://aws.amazon.com/amplify/hosting/) 로 배포하는 방법을 알려드립니다.

우리가 만들 앱은 Next.js 의 data fetching methods 를 이용한 server-side rendered application 이 될 것입니다.

> Next.js 의 data fetching 관련 문서 (https://nextjs.org/docs/basic-features/data-fetching#getserversideprops-server-side-rendering)

본 가이드를 마치면, AWS 위에 배포된 web application 을 확인하실수 있습니다.


## Overview

[Create Next App](https://nextjs.org/docs/api-reference/create-next-app) 을 이용하여 새로운 next.js 프로젝트를 생성합니다.
그리고 Amplify hosting 에 연결할 새로운 git repository 를 만듭니다.
이후, Amplify console 을 이용하여 Amplify hosting 을 셋업한후, 우리가 만든 git repository 를 연결해서 CI/CD 를 구성합니다.

본 가이드는 20분 정도 걸릴것으로 예상됩니다.

### Required Background / Level

본 워크샾은 front-end 개발자들을 위해 만들어졌습니다.

React 에 대한 지식이 있다면 도움이 되지만 필수는 아닙니다.

### Topics we will cover

- Next.js application
- Web application Hosting
- Deleting the resources

### Development Environment

시작하기전에, 다음 패키지를 설치해주세요.

- Node.js v10.x or later
- npm v5.x or later
- git v2.14.1 or later

### AWS Account

아직 AWS 어카운트가 없거나, 새로운 어카운트가 필요하다면, 다음 문서를 참조하세요.
[link](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/).

### Create a Next.js application

[Create Next App](https://nextjs.org/docs/api-reference/create-next-app) 를 이용하여 새로운 프로젝트를 만듭니다.

```sh
$ npx create-next-app amplify-hosting-test-app
```

`amplify-hosting-test-app` directory 로 이동합니다.

```sh
$ cd amplify-forum
```

### Testing application

dev server 를 실행해봅시다.

```bash
npm run dev
# or
yarn dev
```

브라우저를 열고 [http://localhost:3000](http://localhost:3000) 주소에서 화면이 잘 나오는지 확인해봅시다.

![localhost](localhost.png)

`pages/index.js` 파일을 변경해봅시다. 화면이 자동으로 업데이트 되는것을 확인할수 있을것입니다.

