# Guardando nossos segredos! Como criar um secret no Kubernetes!

Quando falamos de aplicações cloud-native applications sempre devemos ter em mente o manifesto
do 12 Factor Apps!

Esse manifesto nos ajuda a construir aplicações portáveis entre provedores de nuvem dentre
outras características importantes.

Um dos pilares é o da configuração, que diz que a configuração da aplicação deve ser provida pelo ambiente.

O Kubernetes provê uma série de primitivas, elementos que estão presentes em todas instalações do Kubernetes,
que nos ajudam a lidar com problemas de deployments de aplicações.

Uma delas é o **ConfigMap**, que nos ajuda a manipular informações relacionadas a configuração da aplicação de maneira 
separada, seguindo o pilar do 12 Factor Apps, porém, quando precisamos armazenar informações sensíveis e de forma segura, 
precisamos utilizar uma outra primitiva denominada **Secrets**.

Essa primitiva permite que consigamos armazenar informações sensíveis como senhas, tokens, chaves SSH, etc.

Vamos ver como podemos declarar um arquivo de configuração de um **Secret**

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: my-secret
type: Opaque
data:
  username: YWRtaW4=
  password: YWRtaW5AMjYtMjAwLTAtQEA=
```

Você pode salvar um arquivo com qualquer nome com extensão **.yaml** e então ele está apto à ser declarado no Kubernetes!

Demais né!?

Note que temos um nó **data**, qualquer entrada desse nó pode se tornar uma variável de ambiente a ser injetada no [Pod](https://kubernetes.io/docs/concepts/workloads/pods/) 
que for utilizá-la. Dessa maneira se tivermos um sistema que utilize a variável de ambiente **username** ela será 
preenchida com o valor aberto em **Base64**.

Demais né!? Vamos criá-la?

Para criar a Secret no Kubernetes, precisamos executar o seguinte comando:

```shell script
$ kubectl apply -f <NOME DO SEU ARQUIVO>.yaml -n <NAMESPACE>
```

Eba! Você criou sua primeira Secret no Kubernetes!


## Associando Secret ao [PODs](https://kubernetes.io/docs/concepts/workloads/pods/)

Uma vez que declaramos nossas variáveis de ambiente no **Secret**, podemos utilizá-la em nossos PODs, onde efetivamente
rodam nossas aplicações. Para fazer isso devemos adicionar a seguinte configuração no arquivo de configuração de deployments,
conforme exemplo abaixo:

```yaml
## restante omitido
spec:
  containers:
    - image: zupacademy/proposta
      imagePullPolicy: Always
      env:
        - name: USERNAME
          valueFrom:
            secretKeyRef:
              name: my-secret
              key: username
## restante omitido
``` 

A associação acontece pela configuração do nó **valueFrom** perceba que referenciamos o **Secret** pelo atributo
**secretKeyRef**.

Demais né!?

# Informação de Suporte

* [Base64 - Wikipedia](https://pt.wikipedia.org/wiki/Base64)
* [Kubernetes - Secret](https://kubernetes.io/docs/concepts/configuration/secret/)
* [Kubernetes - Secrets como variáveis de ambiente](https://kubernetes.io/docs/concepts/configuration/secret/#using-secrets-as-environment-variables)

