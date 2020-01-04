# [yenarue.github.io](https://yenarue.github.io)

Jeklly 블로그 프레임워크를 사용한 개인 블로그.

## 로컬 테스트
### 최초 실행 [#](https://nachwon.github.io/jekyllblog/)

```bash
$ gem install bundler
$ gem install github-pages
$ gem install jekyll
```

Gemfile 생성 및 적용

```bash
$ vi Gemfile
gem "github-pages", group: :jekyll_plugins
$ bundle install
$ bundle update
```

### 테스트

1. 아래의 커멘드를 실행한다.
```bash
$ bundle exec jekyll serve --livereload --draft
```

* `--draft` : 초안을 함께 표시. (`_draft` 디렉토리 하위의 문서들 표시)
* `--livereload` : 문서 수정 시 자동으로 새로고침. (`_config.yml` 제외)

2. `localhost:4000` 으로 접속하여 확인한다.

------
# Codinfox-Lanyon

This is a jekyll template based on [Lanyon](https://github.com/poole/lanyon). See a live demo [here](http://codinfox.github.io).

**If you like this project, PLEASE give it a star.**

Lanyon is an unassuming [Jekyll](http://jekyllrb.com) theme that places content first by tucking away navigation in a hidden drawer. It's based on [Poole](http://getpoole.com), the Jekyll butler.

All the configurations are inside either `_config.yml` or `_config.scss`. The options are fairly straightforward. 

The theme supports: 

1. Theme colors: you can choose your favorite theme color
2. Changable sidebar locations
3. Integration of FontAwesome, MathJax, Disqus and Google Analytics
4. and numerous improvements over original Lanyon


## License

Open sourced under the [MIT license](LICENSE.md).

<3
