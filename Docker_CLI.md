# Docker CLI Cheat Sheet

Docker 명령어 요약 정리입니다. 주로 사용되는 Docker CLI 명령어를 간단히 정리해 두었습니다.

---

## 🐳 Image 다운로드

```bash
docker pull nginx:stable-alpine3.20-perl
# nginx: 이미지 이름
# stable-alpine3.20-perl: 태그(버전)
```

---

## 🧹 이미지 삭제

```bash
docker image rm 0d2d
# image id 앞 4자리만 입력 가능

docker image rm 0d2d -f
# 실행중인 컨테이너가 사용 중일 경우 강제 삭제 필요

docker image rm $(docker images -q)
# 사용되지 않는 모든 이미지 삭제

docker image rm -f $(docker images -q)
# 사용 중인 이미지 포함 전체 삭제

docker rm 0d2d 0d2b
# 여러 개 동시 삭제 가능

docker rm $(docker ps -qa)
# 모든 중지된 컨테이너 삭제
```

---

## 📦 이미지 목록 조회

```bash
docker image ls
```

---

## 🧐 실행 중인 컨테이너 조회

```bash
docker ps
docker ps -a
# -a 옵션: 중단된 컨테이너까지 포함
```

---

## 🛠 컨테이너 생성

```bash
docker create nginx
# 실행하지 않고 컨테이너만 생성 (잘 사용되지 않음)
```

---

## ▶️ 컨테이너 시작

```bash
docker start b8b
# 컨테이너 ID 사용
```

---

## 🚀 Run (Create + Start)

```bash
docker run --name webserver -d -p 4000:80 nginx
# -d: 백그라운드 실행
# --name: 컨테이너 이름 설정
# 4000: 호스트 포트
# 80: 컨테이너 포트
```

---

## 🛑 컨테이너 중지

```bash
docker stop webserver
```

---

## 💀 컨테이너 강제 종료

```bash
docker kill webserver
# 파일 손상 가능성 있음
```

---

## 📄 컨테이너 로그 확인

```bash
docker logs ee6
# ee6: 컨테이너 ID

docker logs --tail 3 d806
# 마지막 3줄

docker logs -f d806
# 실시간 로그 보기

docker logs --tail 0 -f d806
# 현재 시점 이후부터 실시간 로그 보기
```

---

## 🔍 컨테이너 내부 접속

```bash
docker exec -it [컨테이너명 또는 ID] bash

# 예시:
docker run -d nginx
docker exec -it <컨테이너 ID> bash
cd /etc/nginx
cat nginx.conf
```

---

> 이 문서는 개인적인 참고용으로 작성된 Docker 명령어 요약본입니다.
