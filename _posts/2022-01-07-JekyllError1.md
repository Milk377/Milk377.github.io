---
title: About Post Error
categories: [Jekyll,JekyllError]
tags: [jekyll] #lowercase    
---

# 새로운 포스트를 작성하였으나 업데이트가 되지 않는경우

![image](https://user-images.githubusercontent.com/37606666/148405096-3bfc66c8-0c0d-46c8-a929-33f00595602b.png)
![image](https://user-images.githubusercontent.com/37606666/148405138-05174b0b-0009-42c8-8c7e-15f086302e5b.png)

## 증상
- post 를 새롭게 작성하였으나 업데이트가 되지 않음



## 분석
- 헤드에 포함된 categories: [ , ] 에 띄어쓰기가 문제인가?
- 파일 경로에 똑같은 파일 이름을 가지고 있어서 그런것인가?
- bundle exec jekyll serve 명령어를 실행한 경로가 맞는가?

## 해결
- 파일 제목에 날짜가 맞지 않아서 발생한 오류
- 오류가 발생해서 새롭게 수정한 내용이 적용되지 않았던 것
- 새롭게 수정하였을때 적용되지 않는다면, 무언가 오류를 냈기 때문임.