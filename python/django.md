---
description: "장고\U0001F600 - 정리중입니다..."
---

# Django

### pipenv

 파이선파일 환경설정

```text
// mac
brew install pipenv
brew upgread pipenv

// window
pip install --user pipenv

```

```text
pipenv --three

pipenv shell
```

##  장고설치

```text
pip install Django==2.2.5

// pip install Django==3.0.5
```

```text
django-admin

잘나오는지 확
```

## Python PEP

{% embed url="https://www.python.org/dev/peps/pep-0008/" %}

```text
// vsc 에서
Python: Select Linter 선택후

flake8 선

// formatter
pipenv install black --dev --pre


// vsc - 설정
format on save
```

## 프로젝트 시작

```text
// cofig컨피그를 설치하는것은 아니다
django-admin startproject config

> config 폴더안에 config 폴더와, manage.py 를 루트로 가져온다

// 실행
python manage.py runserver

// 아래주소 접속
http://127.0.0.1:8000/admin/

// 에러나면
python manage.py migrate

// 슈퍼유저 만들기
python manage.py createsuperuser

// 어플리케이션만들
django-admin startapp lists
```

