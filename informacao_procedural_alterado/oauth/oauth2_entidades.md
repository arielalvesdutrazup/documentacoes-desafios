# Afinal, quais são as 4 entidades presentes no OAuth2!!!

Para o perfeito entendimento da especificação OAauth2 é recomendado entender o papel de
cada entidade no fluxo de autenticação.

As 4 entidades são Resource Owner, Resource Server, Client e Authorization Server cada um deles
executa uma atividade bem definida no processo de autenticação.

De uma maneira bastante simplificada as entidades principais interagem da seguinte forma, uma parte bastante 
relevante é que o oauth permite alguns modelos de autenticação com mais ou menos interações entre o cliente
e o authorization server, mas não se preocupe vamos cobrir todos os detalhes.

![oauth 2 basics](../../images/oauth2.png "fluxo básico oauth2")

## Informações de suporte

### OAuth2

* [**O que é Resource Server**](https://www.oauth.com/oauth2-servers/the-resource-server/)

* [**Resource Server e Documentação Spring Boot**](https://docs.spring.io/autorepo/docs/spring-security-oauth2-boot/2.0.0.RC2/reference/html/boot-features-security-oauth2-resource-server.html)
  

* [**Spring Authorization Server**](https://github.com/spring-projects-experimental/spring-authorization-server)  
  
* [**RFC 8414 - OAuth 2.0 Authorization Server Metadata**](https://tools.ietf.org/html/rfc8414)
  
* [**RFC 8414 - 1. Introdução. Compatibilidade com OpenID Connect Discovery 1.0**](https://tools.ietf.org/html/rfc8414#section-1)
   
### KeyCloak

* O Keycloak cria uma separação de usuários, credencias, grupos e permissões por Realm, então cada Realm tem seus metadados.
  
* [**O que é um Realm?**](https://www.keycloak.org/docs/latest/server_admin/#core-concepts-and-terms)

*  [**Como criar um Realm**](../../informacao_suporte_alterado/keycloak/keycloak-realm.md)     
    
* [**Link para consultar os metadados do Authentication Server**](http://localhost:18080/auth/realms/nosso-cartao/.well-known/openid-configuration)
      
* [**RFC 8615 - Wll-Known Uniform Resource Identifiers (URIs)**](https://tools.ietf.org/html/rfc8615)

* [**Rascunho - OAuth v2 - 1.1. Roles. Resource Owner, Client, Resource Server e Authorization Server**](https://tools.ietf.org/html/draft-ietf-oauth-v2-16#section-1.1)
  
* [**Zup Academy - Papel do Resource Owner**](oauth2_resource_owner.md)
