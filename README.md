# Rec.FALAE

Instância da **Rec.FALAE**, uma "Arquitetura Baseada em **Rec**onhecimento de **FAL**a para **A**cessibilidade de Conteúdos **E**ducacionais". Tecnicamente, o projeto [bancolombia/scaffold-clean-architecture](https://github.com/bancolombia/scaffold-clean-architecture) foi utilizado para a geração de um projeto inicial aderente aos princípios da **_[Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)_**. Pra isso, os seguintes passos foram executados:

1. Criação de um projeto gradle simples, aplicando apenas o plugin `co.com.bancolombia.cleanArchitecture`;
2. Com o plugin devidamente ativo em um projeto vazio, a seguinte sequencia de comandos `gradle` foi executada:
    - `cleanArchitecture --package=br.usp.icmc.rec.falae --name=rec.falae --type=imperative --coverage=jacoco --lombok=false --metrics=false --language=JAVA --javaVersion=VERSION_17`: Gera uma estrutura de projeto baseada na _Clean Architecture_, com os seguintes módulos ativos:
        - **`applications/app-service` _(Main & Configuration Layer)_**
        - **`domain/model` _(Enterprise Business Rules Layer)_**
        - **`domain/usecase` _(Application Business Rules Layer)_**
    - `generateModel --name=[modelName]`: Cria um modelo e uma interface de _[Repository](https://www.martinfowler.com/eaaCatalog/repository.html)_ no módulo `domain/model`, responsável pelas regras de negócio do domínio educacional;
    - `generateUseCase --name=[useCaseName]`: Cria caso de uso  no módulo `domain/usecase`, responsável pelas regras de negócio da aplicação, como por exemplo a transcrição de vídeos;
    - `generateDrivenAdapter --type=mongodb --secret=false`: Cria uma implementação concreta do _Repository_ usando MongoDB, tal comando gera o seguinte novo módulo:
        - **`infrastructure/driven-adapters` _(Interface Adapters)_**
    - `generateEntryPoint --type=restmvc`: Cria um controlador imperativo usando a implementação concreta do Spring Framework para o Estilo Arquitetural REST, gerando o seguinte novo módulo:
        - **`infrastructure/entry-points` _(Frameworks & Drivers)_**
