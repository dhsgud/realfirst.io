Raspberry Pi에서 Apache, MySQL, PHP, phpMyAdmin 설치하기
이 글은 Raspberry Pi에서 Apache, MySQL, PHP, phpMyAdmin을 설치하는 방법을 설명합니다.
fishpoint.tistory.com을 참조하였습니다.

시작하기 전에
먼저 apt-get 명령어로 최신 버전의 패키지 목록을 받아옵니다.

bash


Copy code
sudo apt-get update
sudo apt-get upgrade
설치 순서는 다음과 같습니다:

Apache
MySQL
PHP
phpMyAdmin
1. Apache 설치
아래 명령어로 Apache2를 설치합니다. 디스크 사용 여부를 묻는 메시지가 나오면 Y를 누르세요.

bash


Copy code
sudo apt-get install apache2
pi 사용자가 /var/www 디렉토리에 쓰기 권한을 갖도록 합니다.

bash


Copy code
sudo chown pi -R /var/www/html
부팅 시 Apache2가 자동으로 실행되게 하려면 다음 명령어를 입력하세요.

bash


Copy code
sudo update-rc.d apache2 defaults
설치가 완료되면 재부팅합니다.

bash


Copy code
reboot -n
크롬 브라우저에서 라즈베리파이의 localhost 주소로 접속하면 Apache 기본 페이지가 나타납니다.

2. MySQL 설치
MySQL 서버와 클라이언트를 설치합니다.

bash


Copy code
sudo apt-get install mysql-server mysql-client libmysqlclient-dev
만약 위 명령어가 동작하지 않으면 apt search 명령어로 사용 가능한 MySQL 패키지를 찾아 설치하세요.

bash


Copy code
sudo apt search mysql
3. PHP 설치
apt search 명령어로 설치 가능한 PHP 버전을 확인합니다.

bash


Copy code
sudo apt search php
여기서는 PHP 7.1을 설치하겠습니다.

bash


Copy code
sudo apt-get install php7.1
설치 후 PHP가 잘 동작하는지 확인해봅시다. 아래 내용을 phpinfo.php 파일로 저장합니다.

php


Copy code
<?php phpinfo(); ?>
웹 브라우저에서 http://localhost/phpinfo.php에 접속하면 PHP 정보 페이지가 나타납니다.

4. phpMyAdmin 설치
phpMyAdmin은 아래 명령어로 간단히 설치할 수 있습니다.

bash


Copy code
sudo apt-get install phpmyadmin
설치 후 http://localhost/phpmyadmin으로 접속해 봅니다.

오류 해결
phpMyAdmin 접속 시 오류가 발생한다면 다음 패키지를 추가로 설치해보세요.

bash


Copy code
sudo apt-get install php7.1-mysqlnd
sudo apt-get install libapache2-mod-php7.1
sudo apt-get install php7.1-mbstring
특히 "mysqli 확장기능이 설치되지 않았습니다" 오류가 나타난다면 php-mysqlnd 패키지를 꼭 설치해야 합니다.

bash


Copy code
sudo apt-get install php7.1-mysqlnd
이상으로 Raspberry Pi에 웹 서버 환경을 구축하는 방법을 알아보았습니다. 질문이나 오류가 있으시면 댓글 남겨주세요.
