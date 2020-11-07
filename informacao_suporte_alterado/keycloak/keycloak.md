# Entendendo conceitos de segurança para nossa aplicação!!!

## Contexto

Armazenar senhas e dados sensíveis sempre é uma missão crítica para sistemas. 
Essas informações são passíveis de auditoria e em alguns casos podemos ter vazamentos de informações 
dessas informações, pelo fato de não estarmos preparados para **todos** os tipos de ataques que estamos sujeitos.
Levamos isso em conta, então nosso processo de autenticação deve ser **delegado** à um sistema externo.

## Explicacao Necessária

Existe uma categoria de sistemas que lidam especificamente com gerenciamento e perfis de usuário. 
Nessa categoria esses sistemas implementam de maneira bastante efetiva controles de segurança, 
criptografia da informação, proteção contra ataques comuns no mundo virtual. 
Eles contam com uma vasta variedades de features que você pode gradualmente aumentando ou 
reduzindo a segurança de controle de seus usuários. 

Na nossa solução vamos usar a implementação do Keycloak, uma aplicação que pode nos ajudar a manter
os dados dos nossos usuários seguro além de prover uma maneira bem simples de integração com Spring Framework.
O produto é open-source então podemos usá-lo sem nenhum problema de licenciamento. Aliás esse é um ponto
de atenção sempre utilize software de acordo com a regulamentação da licensa

## Necessidades

Devemos "subir" nosso servidor de IAM e verificar se ele está operante e pronto para realizarmos
nossas integrações que serão realizadas no próximos passos.


## Resultado Esperado
- Identificar o serviço declarado no docker-compose.yaml
- Verificar a porta que o serviço esta exposto
- Logar no nosso IAM, escolhemos o Keycloak para este fim

## Informações de suporte

### IAM

* [**IAM - Identity and Access Management**](https://www.gartner.com/en/information-technology/glossary/identity-and-access-management-iam)
  
* [**IAM - Mais informações produzidas por uma companhia que criou uma implementação de IAM**](https://www.okta.com/identity-101/federated-identity-vs-sso/)
  
### SSO

* [**SSO - Single Sign-On**](https://searchsecurity.techtarget.com/definition/federated-identity-management) 

* [**SSO - Mais informações**](https://www.cloudflare.com/learning/access-management/what-is-sso/)


### KeyClock

* [**KeyCloak - Site**](https://www.keycloak.org/)
   
* [**KeyCloak - GitHub**](https://github.com/keycloak/keycloak)   
  
* [**KeyCloak - Primeiros passos**](https://www.keycloak.org/docs/latest/getting_started/index.html)  
    
* [**KeyCloak - Login**](keycloak-login.md) 

 
 * [**KeyCloak no CNFC**](https://landscape.cncf.io/selected=keycloak)
   
* [**O que é CNFC - Cloud Native Computing Foundation?**](https://www.cncf.io/)  

### Docker compose

* [**Docker compose para o desafio 3**](../../informacao_procedural_alterado/docker/nosso-compose.md)

* [**Docker compose - Documentação**](https://docs.docker.com/compose/) 


### Licenças Open Source

* [**Licenças Open Source**](https://opensource.org/licenses)        
