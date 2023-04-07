4/6


vscode (1.77.1) 설치
node js (18.15.0) 설치
-> 설치 옵션 : also install chocolatey 체크
-> node js 설치시 python도 설치됨

패키지 매니저
window - chocolatey
mac - homebrew
linux - apt

node - npm

 




https://velog.io/@songyouhyun/Package.json%EA%B3%BC-Package-lock.json%EC%9D%98-%EC%B0%A8%EC%9D%B4
npm install package 시 기본으로 저장되는 경로 : 사용자 > tustu > node-modules
사용자 > tustu > package.json : install 된 패키지 정보
사용자 > tustu > package-lock.json : 정확한 버전의 패키지를 다운받기 위해 package.json보다 버전정보가 정확하게 명시되어있음
package-lock.json이 존재할 때에는 package.json을 사용하여 node_modules를 생성하지않고 package-lock.json을 사용하여 node_modules를 생성





https://blog.outsider.ne.kr/1041
npm 버전
틸드(~) : 현재 지정한 버전의 마지막 자리 내의 범위에서만 자동으로 업데이트
~0.0.1 : >=0.0.1 <0.1.0
~0.1.1 : >=0.1.1 <0.2.0
~0.1 : >=0.1.0 <0.2.0
~0 : >=0.0 <1.0

Semantic Versioning(보통 SemVer라고 부른다.)
MAJOR.MINOR.PATCH의 버저닝
MAJOR 버전은 API의 호환성이 깨질만한 변경사항을 의미하고
MINOR 버전은 하위호환성을 지키면서 기능이 추가된 것을 의미하고
PATCH 버전은 하위호환성을 지키는 범위내에서 버그가 수정된 것을 의미한다.

캐럿(^) : Node.js 모듈이 이 SemVer의 규약을 따른다는 것을 신뢰한다는 가정하에서 동작한다.
그래서 MINOR나 PATCH버전은 하위호환성이 보장되어야 하므로 업데이트를 한다.

^1.0.2 : >=1.0.2 <2.0
^1.0 : >=1.0.0 <2.0
^1 : >=1.0.0 <2.0

하지만 여기에 예외사항이 있다. 다음 내용을 보자.

^0.1.2 : >=0.1.2 <0.2.0
^0.1 : >=0.1.0 <0.2.0
^0 : >=0.0.0 <1.0.0
^0.0.1 : ==0.0.1

버전이 1.0.0 미만인 경우(SemVer에서는 pre-release라고 부른다.)에는 상황이 다르다.
소프트웨어 대부분에서 1.0버전을 내놓기 전에는 API 변경이 수시로 일어난다.
그래서 0.1을 쓰다가 0.2를 사용하면 API가 모두 달라졌을 수 있다.
그래서 캐럿(^)을 사용할 때 0.x.x에서는 마치 틸드처럼 동작해서 지정한 버전 자릿수 내에서만 업데이트한다.(앞에 예시와 비교해보면 차이점을 알 수 있다.)
그리고 0.0.x인 경우에는 하위호환성 유지가 안 될 가능성이 더 높으므로 위의 마지막 예시처럼 지정한 버전만을 사용한다.



https://seizemymoment.tistory.com/106
package.json : 모듈 설치시 자동으로 생성되는 node.js 버전 관리 파일
node_modules : 모든 모듈의 저장공간
React : 많은 모듈들로 구성된 라이브러리로 이들 간의 상호작용이 중요하다.
따라서 npm으로 모듈 설치, node.js로 개발 작업환경을 구성한다.

npm란?
node.js의 자동화 된 의존성과 패키지 관리를 위한 패키지 매니저이다.

1) 패키지 설치
프로젝트를 할 때 필요한 모든 의존성 패키지는 package.json 파일 안 에서 지정할 수 있다.
npm intall를 실행하기만 하면 원하는 패키지를 로컬(node_modules)에 설치할 수 있다.

2) 버전관리 제공
npm은 패키지의 버전을 선택할 수 있기 때문에 패키지 버전 차이로 생기는 문제를 방지할 수 있다.

* npm install 모듈이름 -g
-g 옵션을 사용하면 프로젝트마다 모듈을 설치할 필요없이 글로벌한 공간에 설치되어 모듈을 공유할 수 있다.

(유의해야할 점)
- 한번 설치한 모듈을 계속 사용하기 때문에 업데이트 확인이 어렵다.
- 같은 모듈을 사용해도 프로젝트마다 다른 버전이 필요할 수 있기 때문에 버전 문제가 발생할 수 있다.
- 위와 같은 문제로 모듈 변경사항이 잦은 create-react-app 같은 보일러플레이트에서는 최신버전 설치를 매번 해줘야 하기 때문에 번거롭다.


npx란?
npm 5.2.0버전부터 추가된 node.js 패키지를 실행시키는 하나의 도구이다.

1) 패키지 실행 
패키지의 최신버전 파일을 불러와 설치하여 실행시키고 실행된 이후에 해당 패키지를 제거하는 방식입니다.

(과정)
- 실행시킬 패키지가 로컬에 저장되어 있는지 먼저 확인한다.
- 존재한다면 실행시킨다.
- 존재하지 않는다면 npx가 가장 최신 버전을 설치하고 실행시킨다.


npx는 결국 npm을 더욱 편리하게 사용하기 위해 나온 도구이다.
npx이 아닌 npm을 사용한다면
my-package (패키지 예시) 를 실행시킬 때
로컬에서 패키지가 위치한 ./node_modules/.bin/my-package의 경로로 실행시켜야하거나
package.json의 script로 my-package의 경로를 정의해주어야한다.

{
  "name": "myPackage",
  "version": "1.0.0",
  "scripts": {
    "my-package": "./node_modules/.bin/my-package"
  }
}

업데이트의 경우에도 npm는 일일히 업데이트를 해줘야하기 때문에
모듈이 많아 업데이트가 잦은 create-react-app의 경우 npx를 이용해 설치하는 것을 권장한다는 것을 알게 되었다.




https://joonfluence.tistory.com/659
NPM이란 node.js 환경에서 사용되는 패키지 관리자입니다.
패키지 매니저(Package manager)는 패키지를 다루는 작업을 편리하고 안전하게 수행하기 위해 사용되는 툴이며,
라이브러리가 코드의 작성을 위해 사용되는 코드의 묶음이라면 패키지는 코드의 배포를 위해 사용되는 코드의 묶음입니다.

또한 많은 패키지들은 다른 패키지들이 설치되어야만 제대로 동작하는데,
기존 패키지를 제대로 동작시키기 위해 필요한 다른 패키지들을 dependency(의존성)라고 한다.
따라서 패키지를 사용하고자 할 때, 의존성을 갖는 다른 패키지들을 전부 설치해 줄 필요가 있다.
다만, 이는 패키지가 늘어갈 때마다 다른 패키지의 의존성을 체크하고 또 설치해줘야 하는 번거로움이 발생하는 원인이 됩니다.
이 때, packge.json 파일에 의존성에 대한 정보를 확인할 수 있도록 저장하면 사용자가 사용하고자 하는 패키지의 dependency를 패키지 매니저를 통해 쉽게 설치하도록 도울 수 있습니다.


NPX란 아래 3가지 역할을 합니다.
NPX로 실행하고자 하는 패키지가 현재 실행 경로에 존재하는지 파악합니다.
만약 존재한다면, 패키지를 실행해줍니다.
없다면, 패키지가 존재하지 않는다는 의미이므로 패키지의 최신 버젼을 설치하고 실행해준 뒤 자동으로 삭제해줍니다.

NPX가 나온 배경

NPX는 npm 버젼 5.2.0부터 가능하게 됐습니다.
NPX가 하는 역할은 참 직관적입니다.
그냥 '패키지를 실행'해줍니다. 정말 간단합니다.
예를 들어, NPX가 없던 시절에는 패키지를 실행하기 위해선 다음과 같이, 해당 모듈 경로로 직접 찾아가야 했습니다.
./node_modules/.bin/my-package

그런데 이젠 그럴 필요가 없습니다. NPX가 설치한 경로를 찾아서 실행해주거든요!
npx my-package


CRA에서 NPX를 사용하는 이유
create-react-app 같은 경우에는 글로벌 모듈에 설치하면 좋습니다.
왜냐면 프로젝트 셋팅 도구이기에, 자주 사용될 수 있습니다. 따라서 로컬에 매번 설치하면 용량도 많이 차지합니다.
(우리의 용량은 소중하잖아요?) 그런데, 글로벌 모듈로 설치할 경우 문제가 발생될 수 있습니다.

모듈이 업데이트 되었는지 안되었는지 파악 하기 불가능합니다.
그래서 글로벌 모듈로 설치된 모듈은 설치 당시 버젼을 사용하므로 버젼 파악을 따로 해줘야 하는 번거로움이 있습니다.
업데이트를 진행했을 때 변동사항이 생겨 다른 프로젝트에도 영향을 끼칠 수 있습니다.
프로젝트를 3개를 운영하는데, 같은 모듈의 각각 다른 버전이 필요한 상황이 있을 수 있습니다. 이럴 때 글로벌 모듈의 버전은 당연히 한 개이기 때문에 문제가 발생하게 됩니다.
create-react-app 같은 보일러플레이트코드(최소한의 변경으로 여러곳에서 재사용되며, 반복적으로 비슷한 형태를 띄는 코드 getter/setter 같은 단순노동코드)에는 치명적입니다.
리액트 프로젝트 생성 도구인 create-react-app 같은 모듈의 경우, 변경사항이 꽤나 잦은 모듈입니다.
그렇기 때문에 매 설치 전마다 npm으로 재 설치를 하지 않는 경우에는 이전 버전을 사용할 여지가 꽤 있습니다.
이런 프로젝트 생성 모듈은 매 업데이트마다 새로운 기능과 다양한 버그들이 고쳐집니다.
그리고 이런 보일러플레이트 같은 경우에는, 항상 최신 버전을 유지해 주는 것이 좋은데, 매번 설치하는 것이 꽤나 귀찮은 일입니다.





4/7
https://ux.stories.pe.kr/238
https://ffoorreeuunn.tistory.com/200
https://velog.io/@mannmae/React%EB%A5%BC-%EC%9C%84%ED%95%9C-%EC%83%88-%EC%9E%91%EC%97%85%ED%99%98%EA%B2%BD%EC%97%90-VSCode-%EC%84%B8%ED%8C%85%ED%95%98%EA%B8%B0





https://velog.io/@stella6767/React%EC%99%80-Node.js%EC%9D%98-%EA%B4%80%EA%B3%84
Node.js는 chrome v8 javascript엔진으로 빌드된 javascript 런타임환경
React는 Dom을 조작할 수 있는 프론트엔드 프레임워크
Node.js는 React.js를 더 쓰기 편하게 해주는 도구를 제공하는 오픈소스





https://velog.io/@eungook/React%EC%99%80-Node.js%EC%9D%98-%EA%B4%80%EA%B3%84%EB%8A%94-%EC%AB%8C-%EA%B1%B4%EB%84%88%EA%B1%B4%EB%84%88%EC%97%90%EC%9A%94
사실 React는 jQuery랑 더 닮았답니다.
Node.js는 자바스크립트 런타임일 뿐, 결코 UI 혹은 HTML을 표현하지는 않습니다.
React는 가상 DOM을 통해 UI를 만드는 라이브러리

Node.js와 React 사이에는 webpack과 Babel이 있습니다.
React를 통한 대규모 SPA(어떠한 웹 사이트의 전체 페이지를 하나의 페이지에 담아 동적으로 화면을 변경해 표시하는 기술) 개발을 위해서는

몹시 많은 정적 파일이 필요하고, (.js, .css, .png 등) 이를 번들링할 필요가 있습니다.
→ webpack을 사용합니다.

ES6를 해석할 수 없는 IE11 등 비非 모던 웹 브라우저에 대한 지원이 필요합니다.
→ Babel을 사용합니다.

그럼 Node.js는 무엇인가요?
Node.js는 자바스크립트 런타임 입니다. 그리고 어떤 라이브러리를 갖고 있습니다.

웹브라우저에서 JavaScript가 해석되면, Web API를 통해서 웹브라우저에서 결과가 나타납니다.
Node.js에서 JavaScript가 해석되면, libuv(비동기 입출력, 이벤트 기반에 초점을 맞춘 라이브러리)를 통해서 OS에서 결과가 나타납니다.

그래서 Node.js를 통해 webpack과 Babel을 사용하면
(이 과정을 보통 빌드한다고 하죠)
React 코드가 compatible version of JavaScript로 바뀌고, 다시 bundle되어
브라우저에 올리기만 하면 되는 결과물이 나타납니다.

React의 의존성 관리는 npm을 사용하는게 가장 일반적 입니다.
따라서 npm을 쓰려면 역시 Node.js가 필요하게 됩니다!

그리고 React의 부트스트랩인 create-react-app을 사용하기 위해서!
역시 Node.js가 필요합니다.




https://chucoding.tistory.com/86
결론부터 말하자면, React를 사용하기 위해 Node.js가 반드시 필요한 것은 아닙니다.
그럼에도 왜 항상 React 뒤에는 Node.js가 따라 붙는 것일까요?
그 이유는 Node.js가 React를 사용하기 더 쉽게 해주는 도구들을 내장하고 있는 오픈소스이자 JavaScript runtime environment이기 때문입니다.

더 자세하게 설명하자면 Node.js는 설치하는 경우 NPM(Node Package Manager)이 같이 설치되는데
이 NPM이란 것을 통해 React 개발에 필요한 다양한 모듈들을 다운받아 사용할 수 있습니다.

그렇기 때문에 React개발자들은 다른 개발자들이 구현해 놓은 간편하고 필요한 모듈 및 라이브러리들을 다운받기 위해서 node.js를 설치해서 사용하는 것입니다.
그렇다면 npm만 설치하면 되지 왜 굳이 번거롭게 node.js를 통해 npm을 설치하는 것일까요??
물론, react는 클라이언트 기반 라이브러리기 때문에 npm만 설치하여도 react와 react-dom라이브러리를 사용할 수 있습니다.

그러나 node.js가 있으면 바벨이라는 컴파일러 도구를 추가로 다운받아 자바스크립트 대신 JSX를 사용하는 것이 가능하기 때문입니다. 그렇다면 JSX가 무엇인가??
JSX는 JavaScript를 확장한 문법

jsx코드 (우리에게 익숙한 html코드로 개발할 수 있기 때문에 코딩이 쉬워진다)
class Hello extends React.Component {
  render() {
    return <div>Hello world</div>;
  }
}

js코드
class Hello extends React.Component {
  render() {
    return React.createElement('div', null, `Hello world`);
  }
}

바벨은 자바스크립트 es6 문법을 es5로 변환하는 기능을 갖고 있습니다.
따라서 우리는 바벨을 통해 React를 다양한 브라우저 환경에서 실행시키는 것이 가능해집니다.





# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

The page will reload when you make changes.\
You may also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can't go back!**

If you aren't satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you're on your own.

You don't have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn't feel obligated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)
