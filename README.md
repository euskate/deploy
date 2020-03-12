# deploy
deploy

# 세팅 절차
- deploy = 저장소
- git에 새로운 deploy 생성
  - https://github.com/아이디/deploy
- 로컬 PC에서 aws폴더를 vs code에 오픈
- terminal 오픈
  - $ git clone https://github.com/아이디/deploy.git
- cd deploy

# 파일 세팅 (~/deploy)
- fabfile.py, deploy.json 파일을 위치
- 서버파일을 생성
- wsgi.py(엔트리포인트), run.py 생성
- 코드 작성
- 배포 관련 환경변수 파일 수정 ( deploy.json )
  - git 주소, 서버의 IP, 도메인은 향후 IP와 연결(호스팅쪽), 리눅스 접속 계정 ID 등을 설정
- requirements.txt : 본 서비스를 구동하기 위해 사용된 모든 파이썬 패키지를 기술한다.

# 구동
- python3 버전 기반으로 수행
- 운영체계 및 서버 세팅 및 배포, 업데이트 관리 등등을 자동화하는 모듈 -> fabric3
  -  pip3 install fabric3
- git에 최종 소스 반영 
- $ fab new_server
  - 중간에 y, git로그인 등등이 나올 수 없다.
- 브라우저 가동
  - 서버 아이피로 접속 테스트
- 접속 로그 확인 (리눅스에서 진행)
  - $ tail -f /var/apache2/access.log

# 잘 안된다.
  - 소스 코드상의 파일명, 설정값 등 오타가 없어야 함.
  - git에 최종 소스 모드가 반영되어야 함
  - 리눅스에서 기존의 흔적을 모두 제거
    - 현재 위치 : /home/ubuntu
    - 프로젝트 삭제 $ rm -r -f deploy
    - 가상환경 삭제 $ ls -a
      - $ rm -rf .virtualenvs/
  - 로컬PC
    - $ fab new_server