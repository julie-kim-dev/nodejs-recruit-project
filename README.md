# 1. Class로 리팩토링 했을 때 장점이 무엇인지 설명해 주세요.
- 조각조각 나눠서 수정 및 관리가 용이하다.
  
# 2. 3-Layered Architecture의 장점과 단점을 아는대로 적어주세요.
- 장점: 각 계층을 명확하게 분리하여 역할 파악 및 관리가 쉽다.
- 단점: 데이터의 양이 많아질수록 관리가 힘들어진다.

# 3. 이번 과제에서 Prisma를 TypeORM로 교체할 때 3-Layered Architecture를 기반으로 프로젝트가 구성되어있으면 어떤 장점이 있었나요?

# 4. 테스트코드 작성의 장점과 단점을 아는대로 적어주세요.
- 장점: api 클라이언트로 하나하나 체크할 필요 없이 비교적 간단하게 테스트가 가능하다.

# 5. 테스트의 종류 3가지와 각각이 무엇인지 간단히 설명해 주세요. 
- 단위테스트: 가장 작은 규모의 기능 테스트
- 통합테스트:
- E2E테스트:

# 6. 서버가 2대 이상 있을경우 장점이 어떤게 있고, 무중단 서비스는 어떤 # 원리로 동작하는지 설명해주세요.



# 환경변수

- .env 파일에 어떤 환경변수가 추가되어야 하는지 작성합니다.
- key=value 형태에서 key만 나열합니다. value는 비밀!

- DB_URL
- JWT_SECRET
- 그 밖의 사용한 환경변수를 나열해 주세요.

# API 명세서 URL

- 구글 Docs 공유 URL 추가
- https://www.notion.so/julie-kim-dev/a0f290df91c44fe2af2e5c2fea7aad01?v=0bfdf1284e6d4dfeb1c6d4b5957ed433&pvs=4

# ERD URL

- ERD 작성한 위치 URL 추가
- https://drawsql.app/teams/julie-kims-team/diagrams/nodejs-recruit-project

# 더 고민해 보기

1. **암호화 방식**

   - 비밀번호를 DB에 저장할 때 Hash를 이용했는데, Hash는 단방향 암호화와 양방향 암호화 중 어떤 암호화 방식에 해당할까요?
   - 단방향입니다.
   - 비밀번호를 그냥 저장하지 않고 Hash 한 값을 저장 했을 때의 좋은 점은 무엇인가요?
   - 암호화된 상태로 저장되어 원래 값을 복구할 수 없지만, 입력된 비밀번호와 암호화된 문자열의 일치 여부는 가능합니다. 그렇기 때문에 보안과 검증을 동시에 할 수 있게 됩니다.

2. **인증 방식**

   - JWT(Json Web Token)을 이용해 인증 기능을 했는데, 만약 Access Token이 노출되었을 경우 발생할 수 있는 문제점은 무엇일까요?
   - 도용한 사람이 Access Token을 사용하더라도, 기존에 발급받은 사용자와 비교하여 알아낼 수 있는 방법이 없습니다.
   - 해당 문제점을 보완하기 위한 방법으로는 어떤 것이 있을까요?
   - refresh token을 함께 발급합니다.

3. **인증과 인가**

   - 인증과 인가가 무엇인지 각각 설명해 주세요.
   - 인증 : 서비스를 이용하려는 사용자에게 권한을 부여해주기 위해 신분을 검증하는 작업. 로그인 = 인증
   - 인가 : 이미 인증된 사용자가 어떤 일을 하려고 할때 권한 여부를 확인하는(검증) 작업. (로그인된 사용자만 게시글 작성 가능 = 인가)

   - 과제에서 구현한 Middleware는 인증에 해당하나요? 인가에 해당하나요? 그 이유도 알려주세요.
   - 인증에 해당합니다. 로그인 여부 자체만 확인한 것이기 때문입니다.

4. **Http Status Code**

   - 과제를 진행하면서 사용한 Http Status Code를 모두 나열하고, 각각이 의미하는 것과 어떤 상황에 사용했는지 작성해 주세요.
   - 200 로그인 성공, 유저 상세정보 조회, 게시글 목록 조회
   - 201 게시글 생성

   - 409 이미 존재하는 이메일, 비밀번호가 6자리보다 적음
   - 401 존재하지 않는 이메일, 비밀번호가 일치하지 않음, 토큰 만료, 토큰 조작, 비정상적인 요청

   - 500 서버내부에러

5. **리팩토링**

   - MySQL, Prisma로 개발했는데 MySQL을 MongoDB로 혹은 Prisma 를 TypeORM 로 변경하게 된다면 많은 코드 변경이 필요할까요? 주로 어떤 코드에서 변경이 필요한가요?
     - 만약 이렇게 DB를 변경하는 경우가 또 발생했을 때, 코드 변경을 보다 쉽게 하려면 어떻게 코드를 작성하면 좋을 지 생각나는 방식이 있나요? 있다면 작성해 주세요.

6. **API 명세서**
   - notion 혹은 엑셀에 작성하여 전달하는 것 보다 swagger 를 통해 전달하면 장점은 무엇일까요?
