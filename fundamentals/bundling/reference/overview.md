# 핵심 개념

**웹팩**(Webpack) 여러 JavaScript 파일과 리소스를 분석하고, 이를 하나의 번들로 묶어서 최적화하는 대표적인 모듈 번들러예요. 덕분에 개발자는 복잡한 빌드 과정에 신경 쓰지 않고, 다양한 언어와 모듈을 자유롭게 사용하며 개발에 집중할 수 있어요.

웹팩의 핵심 개념들을 중심으로 하나씩 알아봐요.

## 웹팩의 번들링

웹팩은 애플리케이션의 여러 파일을 분석하고, 필요한 리소스를 하나의 파일로 번들링해요.<br />
이 과정은 **진입점**(Entry Point)에서 시작해, **의존성을 분석**(Resolution)한 후, **출력** 파일(Output)을 만드는 순서로 진행돼요.

::: info 번들링이란
번들링 개념이 궁금하다면, [번들링 개념을 설명하는](/overview) 문서를 참고하세요.
:::

## 번들링 과정

1. 웹팩은 [진입점](../reference/entry)에서 애플리케이션 실행에 필요한 모든 모듈을 추적하기 시작해요

2. 각 모듈이 실제로 어떤 파일을 가리키는지 찾고 결정하는 [모듈 해석](../reference/resolution)하는 과정을 거쳐요.

3. [로더](../reference/loader)를 적용해 JavaScript뿐만 아니라 CSS, 이미지, 폰트 같은 파일도 해석하고 변환할 수 있게 해요

4. [플러그인](../reference/plugin)을 사용해 번들 최적화, 환경 변수 설정, 추가적인 파일 생성 등 빌드 과정에서 다양한 기능을 확장할 수 있어요.

5. 웹팩이 최종으로 [출력](../reference/output)할 번들 파일을 지정된 경로에 저장해요.

## 번들링 최적화

웹팩은 번들링 뿐만 아니라 다양한 최적화 기능을 제공해요.

## 웹팩이 제공하는 개발환경

웹팩은 편리한 [개발환경](../reference/dev/overview)을 구성하는 데 필요한 다양한 기능을 제공해요.

- [개발 서버](../reference/dev/dev-server): 코드 변경 사항을 실시간으로 반영해서 개발 속도를 높일 수 있어요. 개발 중 페이지를 새로고침하지 않아도 최신 상태를 유지할 수 있어요.
- [HMR(Hot Module Replacement)](../reference/dev/hmr): 전체 페이지를 새로고침하지 않고, 수정된 모듈만 빠르게 업데이트해서 상태가 초기화되지 않고 작업을 지속할 수 있어요.
- [소스맵(Source Map)](../reference/dev/source-map): 코드와 빌드된 파일 간의 매핑 정보를 제공해서, 브라우저 디버거에서 원본 코드를 보며 디버깅할 수 있어요.
- [환경 변수](../reference/dev/env-variable): 개발, 테스트, 배포 등 다양한 환경에 따라 설정을 쉽게 변경할 수 있어서 유연하고 효율적인 개발이 가능해요.
