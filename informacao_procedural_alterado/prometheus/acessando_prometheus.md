# Acessando Prometheus pela primeira vez!

O Prometheus é uma ferramenta bastante importante em um ambiente de aplicações distribuídas, ele nos
ajuda a realizar a coleta de métricas dos nossos serviços de uma maneira bastante aderente aos 
padrões de computação na nuvem.

Para nosso uso vamos _"subir"_ uma instância para que ele possa coletar nossas métricas. Vale a pena notar
que estamos rodando em ambiente de desenvolvimento, quando estamos em ambiente produtivo precisamos de provavelmente
mais de uma instância para garantir alta disponibilidade e resiliência. Isso é muito importante!

Se você usou nosso [docker compose](../ops/docker-compose.yaml) você poderá verificar
que temos um elemento chamado **prometheus**. Abaixo segue o fragmento

```yaml
    ##
    ## restante omitido
    ##
  prometheus:
    image: prom/prometheus
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml
      - prometheus-volume:/etc/prometheus/
    ports:
      - 9090:9090
    ##
    ## restante omitido
    ##
```

Temos algumas configurações de volumes que serão utilizadas para configuração
da ferramenta, mas não é importante para esse momento.

Neste momento atente-se à porta que está mapeada para [localhost:9090](http://localhost:9090/) então vamos nos conectar
na aplicação!

Poderemos ver que a tela do prometheus é bastante _"pobrezinha"_, não vamos encontrar muitas opções, afinal esta é uma ferramenta
para monitoramento.

Você deve ser apresentado à seguinte tela

![home prometheus](../../images/prometheus.png "home prometheus")

Temos alguns menus na barra que são muito importante para checarmos as configurações do prometheus, as configurações relacionados ao 
sistema estão no menu **Status**, uma parte importante legal é que o prometheus também conta com um sistema de alertas que pode ser instalado
junto a solução, as configurações de alertas estão no menu **Alertas**, atente-se que o módulo deve estar instalado.

Outra parte importante na parte central da tela, é o combo para seleção das métricas, neste combo **todas** as métricas que os sistemas conectados
ao prometheus estão listadas, perceba que precisamos trabalhar com bastante rigor nas nomenclaturas das métricas.

## Explorando o menu Status

O menu Status é um menu que conta com diversos sub-menus relacionados a configuração do prometheus, podemos encontrar a versão do sistema, 
configurações de runtime, os parâmetros de inicialização da ferramentas entre outras informações.

Os pontos bastante importante relacionados à coleta de métricas são **Targets** e **Service Discovery**, estes são relacionados à como o prometheus está operando
em relação a obtenção dos valores da métricas. 

Vamos entender isso agora!

### Targets

**Targets** são "alvos", no nosso contexto são os nossos sistemas que estão configurados para que o prometheus faça a coleta das métricas. Essas
configurações são realizadas através do arquivo de configuração _prometheus.yaml_, mas este pode ser um trabalho de infra, para nosso contexto basta
entendermos que precisamos avisar o prometheus que ele precisa buscar métricas.

Essa tela nos ajuda bastante a entender como estão nossos sistemas em relação ás coletas, ela mostra se o endpoint de coleta está ok, e podemos
ver informações da última coleta e quanto tempo demorou. Quando há erro também conseguimos identificar o motivo.

Então esta tela nos ajuda muito, vale a pena lembrar dela....algum momento ela pode te salvar!

Vamos dar uma olhada nela.

![home targets](../../images/prometheus_targets.png "home targets")

Olha que legal, com um simples olhar já podemos perceber que nosso sistema de contas está com problema, olhe o campo State está marcado
como **DOWN**, neste caso precisaríamos dar uma olhada nele.

Também temos algumas informações sobre atributos do sistema também como endpoint de coleta e IPs por exemplo 

### Service Discovery

Service Discovery é a maneira que o prometheus vai usar para descobrir seus serviços, no nosso ambiente de desenvolvimento informamos esses os serviços
arbitrariamente, mas imagine quando nossos sistemas tiverem dezenas de instâncias ou talvez milhares, já pensou em cada nova instância tivermos
que informar o prometheus, esta tarefa se tornaria inviável. Para isto o prometheus é capaz de se conectar com implementações de Service Discovery
mais usadas no mercado como kubernetes e Consul por exemplo. Essas implementações são capazes de fornecer informações das instâncias para o prometheus.

Olha que massa hein!

Vamos dar uma olhada na tela
   
![home service discovery](../../images/prometheus_service_discovery.png "home service discovery")

Olha que legal, o prometheus é capaz de agrupar nossos targets por "nomes" e ainda mais consegue contá-los isso é muito útil quando contamos com algumas 
instâncias de um mesmo serviço! Também é possível saber como eles foram descobertos, note que ele consegue mostrar as labels descobertas e as
labels do "alvo".

### Fazendo uma consulta de Métrica

Na home do prometheus escolha uma métrica qualquer e depois clique na tab **Graph**. 

Veja no exemplo, escolhemos a métrica de coletas de log do logback por nível. Cada linha de log é um evento, essa métrica visa mostrar quantos deles
utilizamos.

Nome da métricas:

**transacoes_logback_events_total**

Veja abaixo

![home metrics](../../images/sample_prometheus.png "metrics sample")

Olha que legal, parece que nossas métricas estão sendo armazenadas corretamente. Sucesso!

Quer dizer mais ou menos sucesso, na verdade colocamos métricas mas parece que esse gráfico do prometheus tem algumas limitações.
Não consigo criar agregações e "juntar" métricas, e é por isso que outra ferramenta aparece em cena. O **Grafana** é uma ferramenta feita
para renderizar gráficos e adivinha ele tem uma fortíssima integração com o prometheus...

[Zup Academy - Grafana](../informacao_procedural_alterado/../grafana/acessando_grafana.md)

## Informações de suporte

* [Prometheus - Site](https://prometheus.io/)

* [Prometheus - Iniciando](https://prometheus.io/docs/prometheus/latest/getting_started/)

* [Prometheus - Nomenclaturas](https://prometheus.io/docs/practices/naming/)

* [Prometheus - Mais informações sobre configuração](https://prometheus.io/docs/prometheus/latest/configuration/configuration/)

* [Zup Academy - Prometheus](prometheus.md)

* [Docker - Volumes](https://docs.docker.com/storage/volumes/)

* [Docker - Redes de container](https://docs.docker.com/config/containers/container-networking/)


* [Service Discovery em uma arquitetura de microserviços](https://www.nginx.com/blog/service-discovery-in-a-microservices-architecture/)

* [Service Discovery e Kubernetes ](https://kubernetes.io/docs/concepts/services-networking/service/#cloud-native-service-discovery)

* [O que é um serviço em Kubernates](https://kubernetes.io/docs/concepts/services-networking/service/)

* [Consul é eletrodoméstico?](https://www.consul.io/use-cases/service-discovery-and-health-checking)
