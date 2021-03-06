# Recomendação de utilização para o grant type _client_credentials_


Para aplicações que não precisam de usuários finais no fluxo, o grant type _client_credentials_ é recomendado para interações
de sistemas. 

Por exemplo o **sistema C** possui habilitada segurança por OAuth2, para que o **sistema B** possa acessar o **sistema
C**, ele precisa obter um token. Perceba que não há um **Resource Owner** envolvido.  

Neste caso nosso **sistema B**, precisa de um **client_id** e um **client_secret**, é muito importante que
o **client_secret** seja mantido sob segurança, ele atua como senha da sua aplicação. Sugerimos fortemente
que esse client_secret seja armazenado encriptado ou em ferramentas como Vault, por exemplo.

Isto é muito importante, proteja seu secret à qualquer custo!!

![oauth 2 basics](../../images/oauth2-flows-client.png "fluxo básico oauth2")

Note que no fluxo não encontramos o Resource Owner, porque ele não é envolvido neste processo,
por este motivo este fluxo é recomendado para interação entre sistemas.

## Informações de Suporte  

* [**Client Credentials**](https://www.oauth.com/oauth2-servers/access-tokens/client-credentials/)

* [**RFC 6749 - 1.3.4. Client Credentials**](https://tools.ietf.org/html/rfc6749#section-1.3.4)
