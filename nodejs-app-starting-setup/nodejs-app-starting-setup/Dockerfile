FROM node 
#docker hub, 혹은 로컬에 있는 node 불러오기

WORKDIR /app
#추후에 실행되는 명령은 모두 app폴더에서 진행
#만약 이걸 추가 안하면 디폴트인 루트폴더에서 명령이 진행된다.

COPY . /app
#첫번쨰 . : 하위 디렉토리 혹은 동일 디렉토리내 파일들 모두 이미지 포함시키기
#두번째 . : 파일들을 저장할 이미지 내부의 경로(이미지 내부에도 자체 파일 시스템이 있음..)
#현재는 이미지에 실리는 모든 파일들이 이미지 내부의 ./app 폴더에 저장 된다. ./도 가능.

RUN npm install

EXPOSE 80
#포트 개방

#RUN node server.js 이건 안돼...이미지는 실행파일이 아니야...!

CMD ["node", "server.js"]

#이걸 사용해야 컨테이너에서 실행 된다
#docker run 을 할 때 -p 3000:80를 삽입해야 컨테이너에게 오픈된 로컬 포트를 알려줄 수 있음 
#앞의 3000은 마음대로 할 수 있으나 80은 우리가 도커에게 노출한 포트이므로 80써줘야함

FROM node 
WORKDIR /app
COPY package.json /app
RUN npm install
COPY . /app
EXPOSE 80
CMD ["node", "server.js"]
#이렇게 최적화하면 빌드속도 훨씬 더 빨라짐 왜? 리빌드하는게 더 적어지잖아!