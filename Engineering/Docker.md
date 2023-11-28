Docker is an [[open-source]] platform for developing, shipping, and running applications. It uses OS-level [[virtualization]] to package applications and services as lightweight, portable, self-sufficient [[container]]s. Docker [[container]]s leverage the operating system's [[kernel]] to isolate applications and services from each other, making it possible to run multiple [[container]]s on the same machine without conflicts.

> **Comparison with [[virtualization]]**
> 
> - 가상화를 통해 생성된 서버는 운영체제나 소프트웨어 선택이 자유로움, Docker는 [[container]]에서 [[Linux]]가 동작하는것 처럼 보이지만 실제 [[Linux]]가 동작하는 것은 아니다. [[OS (Operating System)]]의 기능 중 일부를 호스트 역할을 하는 물리 서버에 맡겨 부담을 덜어 둔 형태. 따라서 [[container]]는 운영체제의 일부 기능을 호스트 컴퓨터에 의존하기 때문에 물리 서버에도 [[Linux]] 기능이 필요하며, 내용도 [[Linux]]로 한정됨
> - [[AWS (Amazon Web Services)]] [[Amazon Elastic Compute Cloud (EC2)]] 역시 같은 가상화 기술을 기반으로 하기 때문에 위와 같은 특징과 차이를 가지고 있음

#### Solutions

1. [[AWS (Amazon Web Services)]] [[Amazon Elastic Container Service (ECS)]]: [[container]] 호스팅 서비스로, 별도로 가상 서비스를 만들지 않아도 컨테이너 이미지를 그대로 실행할 수 있음

## Installation

1. [[macOS]]
	> Homebrew is more recommendable due to no need to divide your Mac’s CPU architecture
	``` bash
	brew install --cask docker’
	```
2. [[Windows]] ([[Micorosoft]])
3. [[Linux]]