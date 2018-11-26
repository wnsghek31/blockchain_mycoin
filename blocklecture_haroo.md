# Blockchain - Lecture

## Geth 과정에 사용되는 명령어들

> 교재의 Code 를 Copy&Paste 할 때 마다
> PDF Reader 에 따라 값이 달라지는 경우 발생 (줄바뀜 및 띄어쓰기 발생)
> 아래 코드를 사용하세요


```
// 폴더 만들고 이동하기
mkdir MyNetwork
cd MyNetwork

// puppeth 통해서 제네시스 블록 셋팅하기
puppeth
// 이후 설정은 교재 참조

#### puppeth 실행이 안되는 경우 - Windows
- geth-alltools 설치시 자동으로 Path 에 추가 됩니다
- CMD 창을 닫았다 새로 열어보세요
#### puppeth 실행이 안되는 경우 - macOS
- 편집기 열고 : vi ~/.bash_profile
- 다음 내용 추가(JongKwang 경로 수정필요) : export PATH=$PATH:/Users/JongKwang/bin/geth-alltools-1.8.15
- terminal 을 새로 엽니다

// MyNetwork.json 으로 블록 생성하기
geth --datadir . init MyNetwork.json

// Account 생성 및 조회
geth --datadir . account new
geth --datadir . account list

// 비밀번호 파일 생성하기
code password.txt
12341234

// 블록체인 시작 파일 생성
code startblockchain.bat
geth --datadir . --networkid 9999 --nodiscover --rpc --rpcport 8545 --rpccorsdomain "*" --rpcapi "eth,web3,personal,net" --nat any --unlock 0 --password ./password.txt
#### macOS의 경우
- 파일 생성 : code startblockchain.sh
- 권한 부여 : chmod 755 startblockchain.sh


// 블록체인 시작
startblockchain.bat
#### macOS의 경우 : startblockchain.sh

// Geth Console 배치파일 생성
code startgethconsole.bat
geth attach ipc:\\.\pipe\geth.ipc
#### macOS의 경우
- 파일 생성 : code startgethconsole.sh
- 권한 부여 : chmod 755 startgethconsole.sh

// Geth Console 시작
startgethconsole.bat #### macOS의 경우 : startgethconsole.sh

// Mist 실행 파일 생성
code startmist.bat
"c:\Program Files\Mist\Mist.exe" --ipc \\\\.\\pipe\\geth.ipc
#### macOS의 경우
- code startmist.sh
- /Applications/Mist.app/Contents/MacOS/Mist --ipc \\\\.\\pipe\\geth.ipc

// Mist 실행
startmist.bat #### macOS의 경우 : startmist.sh
```

## Geth 주요 명령어

#### 계정 관련
- 계정 목록 : <code>eth.accounts</code>
- 1번째 계정 주소 : <code>eth.accounts[0]</code>
- 신규 계정 생성 : <code>personal.newAccount()</code>
- 계정 잠금 해제 : <code>personal.unlockAccount</code>

#### 채굴
- 채굴 시작 : <code>miner.start(1)</code>
- 채굴 중지 : <code>miner.stop()</code>

#### 조회
- 대기중인 트랜젝션 : <code>eth.pendingTransactions</code>
- 트랜젝션 ID 로 상세조회 : <code>eth.getTransaction("트랜잭션ID")</code>
- 현재 블록 넘버 : <code>eth.blockNumber</code>
  - web3.eth.getBlock('latest') // 마지막 블록 정보

#### 기타
- debug.verbosity(2) // (0=silent, 1=error, 2=warn, 3=info, 4=core, 5=debug, 6=debug detail)


## Solidity Code

- solidity 폴더의 파일들을 사용하세요
  - 바로가기 : https://github.com/jongkwang/blockchain-lecture/tree/master/solidity