# [yenarue.github.io](https://yenarue.github.io)

Jeklly 블로그 프레임워크를 사용한 개인 블로그.

## 로컬 테스트
### 최초 실행
```bash
$ bundle
```

### 테스트
1. 아래의 커멘드를 실행한다.
```bash
$ jekyll serve --livereload --draft
```

* `--draft` : 초안을 함께 표시. (`_draft` 디렉토리 하위의 문서들 표시)
* `--livereload` : 문서 수정 시 자동으로 새로고침. (`_config.yml` 제외)

2. `localhost:4000` 으로 접속하여 확인한다.

## 설정
### Navigation
`_data/navigation.yml` 수정

```yaml
main:
  - title: "About"
    url: /about/
```

* url은 `_pages` 디렉토리 안의 `html` 파일내 `permalink` 필드를 참조한다.
