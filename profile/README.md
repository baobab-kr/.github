<h1 align="center">
 🌴 Baobab 🌴
</h1>
</p>
<div align="center">

`개발자를 위한 블로그-채용 연계 플랫폼 서비스! Baobab 플랫폼입니다.`

</div>
<p>

<p align="center">
<table align="center">
  <tbody>
    <tr>
      <td>
        <div align="center">
        블로그 서비스 메인 페이지
        </div>
      </td>
      <td>
        <div align="center">
        채용 서비스 메인 페이지
        </div>
      </td>
    </tr>
    <tr>
      <td>
        <img src="https://user-images.githubusercontent.com/79235021/201961288-1e8150c8-2550-430c-a9c2-173dd320db36.png" alt="screenshot" width="500" />
      </td>
      <td>
        <img src="https://user-images.githubusercontent.com/79235021/201961156-f3dff9a0-b5d2-4093-8689-c9bcdb5bd42d.png" alt="screenshot" width="500" />
      </td>
    </tr>
  </tbody>
</table>
<br/>

## 해당 서비스의 개발 동기는?
- 개발자들에게 필수가 되어버린 블로그 서비스, 이를 위한 개발자 전용 블로그 서비스
- 이직이 잦은 개발자의 특성들을 고려하여 블로그-채용 연계 플랫폼 서비스 구현
<br/>

## 해당 서비스는 어떻게 사용하나요?
https://baobab.blog 에 접속하시면 바로 사용해 보실 수 있습니다.  
다만, Azure Resoruce 비용이 부족해 AKS가 중지된 경우 사용이 원활하지 않을 수 있습니다.
<br/>
<br/>

## 어떻게 서비스가 구성되어 있나요? 
해당 섹션은 서비스의 전체적인 흐름 정도만 설명합니다.  
- Baobab 플랫폼은 다양한 서비스들이 각각의 마이크로서비스로 구분돼 API 게이트웨이를 통해 상호작용함.
- 분리된 마이크로서비스는 각 서비스에 적합한 프레임워크, 언어 등을 선택해 개발할 수 있어 생산성이 향상됨. 
- 마이크로서비스는 Azure Kubernetes Service의 Kubernetes Cluster를 통해 제공.
- 데이터베이스는 Master-Slave 디자인 패턴 형식으로 구성되어 이중화됨.
- Gabia DNS Service와 Azure DNS Service 간의 DNS 위임 설정을 통해 Azure 내부 서비스의 DNS를 제공하고, 실제 사용자(외부 접근)들이 baobab.blog 도메인을 통해 접속할 수 있도록 구성함.
- 회원가입 인증 메일 등 메일 서비스를 위해 SaaS 형태의 클라우드 서비스인 Exchange Online 연동.
- HTTPS 트래픽을 통해 사용자가 안전하게 서비스를 사용할 수 있도록 Let’s Encrypt 인증서 생성 및 Nginx Reverse Proxy 구성.
- 사용자는 일반 HTTP 헤더를 통해 서비스를 사용하는 것이 아니라 TLS를 적용한 보안 헤더를 씌운 채로 서비스를 사용함.
- 한국어 욕설 데이터 수집 후, 머신 러닝을 통해 AI 모델을 생성 및 추출하였고 이를 통해 댓글 비속어 필터링 API 구현
- 리소스 부하량에 따라 Azure Node Pool를 자동으로 확장(축소)함.
- Azure Blob Storage를 통해 업로드된 이미지들을 별도로 관리함.
- Azure Storage 를 통해 Database에 저장된 DB 데이터 파일을 관리함.
- Nginx Load Balancer 를 통해 Resource Request를 각 노드에 분산하여 전달함.
- Cert Manager (인증서) 는 Private Container Image Registry (Azure Container Instance)를 통해서 Container Image를 제공 받음.
- 일반적인 서비스들은 Public Container Image Registry (Github Container Registry)를 통해서 Container Image를 제공 받음.
<br/>
<td>
  <img src="https://user-images.githubusercontent.com/79235021/201963351-78b7270a-ae4c-42e5-b104-277744df5d27.png" alt="screenshot" />
</td>
<br/>
<br/>

## 더 자세한 내용들이 궁금하다면?
[baobab-kr info](https://baobab-tree.notion.site/baobab-kr-Information-29be9ac32f0743559b26552c6129785c) 사이트를 통해 더욱 자세하게 살펴보실 수 있습니다.
