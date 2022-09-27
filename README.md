# Rec.FALAE

Instância da **Rec.FALAE**, uma "Arquitetura Baseada em **Rec**onhecimento de **FALA** para *A*cessibilidade de Conteúdos **E**ducacionais". Tecnicamente, o projeto [bancolombia/scaffold-clean-architecture](https://github.com/bancolombia/scaffold-clean-architecture) foi utilizado para a geração de um projeto inicial aderente aos princípios da **_[Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)_**.

Para isso, como primeiro passo, criamos um projeto gradle simples, contendo apenas um arquivo `build.gradle` com o plugin `co.com.bancolombia.cleanArchitecture` declarado (versão de referência: `2.4.5`). Com o plugin devidamente ativo, a seguinte sequencia de comandos `gradle` foi executada:

```console
cleanArchitecture --package=br.usp.icmc.rec.falae --name=rec.falae --type=imperative 
--coverage=jacoco --lombok=false --metrics=false --language=JAVA --javaVersion=VERSION_17
```

O comando acima gera a estrutura de projeto baseada na _Clean Architecture_, com os seguintes módulos ativos:
  - **`applications/app-service` _(Main & Configuration Layer)_**
  - **`domain/model` _(Enterprise Business Rules Layer)_**
  - **`domain/usecase` _(Application Business Rules Layer)_**

```console
generateModel --name=[modelName]
```

Cria um modelo e uma interface de _[Repository](https://www.martinfowler.com/eaaCatalog/repository.html)_ no módulo `domain/model`, responsável pelas regras de negócio do domínio educacional.

```console
generateUseCase --name=[useCaseName]
```

Cria caso de uso  no módulo `domain/usecase`, responsável pelas regras de negócio da aplicação, como por exemplo a transcrição de vídeos.

```console
generateDrivenAdapter --type=mongodb --secret=false
```

Cria uma implementação concreta do _Repository_ usando MongoDB, tal comando gera o seguinte novo módulo:
  - **`infrastructure/driven-adapters` _(Interface Adapters)_**

```console
generateEntryPoint --type=restmvc
```

Cria um controlador imperativo usando a implementação concreta do Spring Framework para o Estilo Arquitetural REST, gerando o seguinte novo módulo:
  - **`infrastructure/entry-points` _(Frameworks & Drivers)_**
