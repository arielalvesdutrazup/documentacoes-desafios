# Como criar um Realm no keycloak

O keycloak tem um conceito de Realm, que na prática é um grupo de divisão lógico. Neste grupo 
contém usuários, credenciais, perfis e grupos.

Uma parte bastante importante é que um Realm é totalmente isolado de outro Realm, dessa maneira
você só consegue gerenciar usuários que o próprio Realm controla.

## Criando um Realm


Vamos lá. Depois de você logar no Keycloak devemos utilizar a opção "Add Realm". Como mostra a figura abaixo

![add realm](../../images/keycloak/add-realm.png "criação do realm")


Você será redirecionado para a página de inclusão de Realm o procedimento é bastante simples, precisamos
somente configurar um nome.

![realm name](../../images/keycloak/realm-name.png "configurar nome do realm")

Preenchido o nome podemos clicar em **Create**

Pronto!!!

Simples assim, você deverá ser redirecionado para a tela de configurações do Realm.

Verifique se seu novo Realm está com a opção **Enabled** marcado e os Endpoints esteja selecionado
a opção **OpenID Endpoint Configuration**

## Informações de suporte

* [**KeyCloak - Zup Academy - Login**](keycloak-login.md)

* [**KeyCloak - Server Admin**](https://www.keycloak.org/docs/latest/server_admin/#admin-console)

* [**KeyCloak - Criar Realm**](https://www.keycloak.org/docs/latest/server_admin/#_create-realm) 
