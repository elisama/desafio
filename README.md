# Faria Lima - Coworking Spaces

> status: em desenvolvimento 👷🏿

## 1  Objetivo

Projeto de desafio técnico como etapa do processo seletivo de uma instituição financeira brasileira. O desafio foi proposto dia 11 de março de 2024 para ser entregue no dia 26.

O desafio consiste na construção de uma plataforma completa onde os usuários possam encontrar e reservar espaços de trabalho em diferentes locais de coworking pelo Brasil e pelo Mundo. Além disso, haverá a necessidade de aprovação pelo proprietário do espaço antes que a reserva seja confirmada, o que exige que a plataforma tenha dois perfis de acesso (usuário comum e proprietário de espaço), sendo obrigatório o login para acesso às funcionalidades. Tudo acima deve ser implementado com uma aplicação de interface front-end web que forneça uma interface amigável aos usuários.

E, como condição imposta pela banca avaliadora, o projeto deve utilizar no back-end .NET Core 8, tendo como liberdade de escolha o uso do ORM Entity Framework Core ou do Dapper para acesso aos dados.

    

## 2  Descrição

As seguintes questões técnicas foram abordadas com a banca avaliadora:

**1** Haverá um banco de dados prévio com o registro de alguns espaços de coworking já previamente cadastrados?

- R: Pode se utilizar alguma biblioteca fake para gerar os nomes e localização (lat, long) ou pega alguns que estejam na região da Faria Lima, Av. Paulista em SP mesmo.

**2** Haverá alguma "lógica" ou critério para que ocorra a aprovação do proprietário? Como alguma tabela de checklist que deva ser previamente preenchida pelos usuários? Se sim, também quais informações do usuário deverão ser disponíveis para preenchimento.

- R: Acredita-se que para facilitar para o aprovador, podemos aprovar automaticamente via sistema se o número de usuários da equipe for menor que a lotação máxima do coworking, e se o pagamento já foi realizado no agendamento.

**3.** Quais as informações sobre um espaço de coworking devem constar para cadastro?
    - endereço?
    - número máximo de usuários?
    - custo?

- R: Endereço completo, coordenadas geográficas, máximo de usuários (lotação máxima), horário de abertura e fechamento, dias de funcionamento (ex. : abre de final de semana?), modelo de cobrança (diária, por hora, mensal, todos)

**4.** Quando na especificação é dito "uma interface amigável ao usuário", isso envolveria exibição de mapas? 

- R: Mapas facilitarão o cadastro e para que o usuário também encontre o espaço.

**5.** Há um tempo máximo para resposta do proprietário? Se sim, qual seria ou é algo aberto?

- R: Pode ser definido pelo desenvolvedor.

**6.** Qual o tempo máximo de duração de uma sessão inativa?

- R: Fica à escolha do desenvolvedor.

**7.** A integração de pagamentos é para ser com alguns dos players já existentes, como MercadoPago, etc?

- R: Esta parte será mockada.

**8.** Para a apresentação final, o sistema poderá rodar na minha máquina, para que seja exibido para vocês, ou posso colocá-lo online em um provedor comercial, como Locaweb, etc?

- R: Disponibilizar que a aplicação esteja em um serviço de provedor é um diferencial.

### 2.1 Funcionamento e Lógica da Aplicação

Inicialmente temos dois tipos de usuários:
* usuário
* proprietário 

O **usuário** comum pode apenas acessar a plataforma



### 2.2 Fluxo de funcionamento do usuário

* **Passo 1:** Independente do usuário desejar ou não realizar alguma reserva, ele terá a permissão de entrar no site e visualizar os espaços disponíveis;
* **Passo 2:** Caso ele então se interesse por um espaço específico e deseje então reservá-lo, ele será conduzido à pagina de login;
* **Passo 3:** Caso ainda não seja cadastrado, ele então terá que se cadastrar, e após isso retorna à página inicial onde os espaços encontram-se disponíveis;
* **Passo 4:** Após reservar o espaço, o usuário deverá aguardar a sinalização de aprovação do proprietário. Nessa parte aqui, a sinalização dar-se-á por uma mensagem que aparecerá na página do usuário;
* **Passo 5:** Caso ocorra a aprovação do proprietário, o usuário seguirá para a realização de pagamento;
* **Passo 6:** Caso não possua nenhum meio de pagamento cadastrado, o usuário seguirá para a página de cadastro de meio de pagamento;
* **Passo 7:** Uma vez com um meio de pagamento registrado, o pagamento é então realizado. Havendo sucesso no pagamento, a reserva é confirmada e o usuário pode sair da plataforma ou continuar navegando;
* **Passo 8:** Caso o pagamento não seja aprovado, o usuário poderá registrar outro meio e então retornar ao passo 6.


![Fluxograma_do_Usuario_Desafio](https://github.com/elisama/desafio/assets/7691281/a3d8de0c-7523-4e77-82a9-6821925886f4)


### 2.3 Fluxo de funcionamento do proprietário

![Fluxograma_Proprietario_Desafio](https://github.com/elisama/desafio/assets/7691281/e448c128-3a55-4561-877b-374ae547151a)

### Tabelas e banco de dados

**Tabela:** user

<table>
    <tr>
        <td> id_user </B> </td>
        <td> chave primária </td>
    </tr>
    <tr>
        <td> user_type </td>
        <td> usuario = 1 ; proprietário = 2 </td>
    </tr>
    <tr>
        <td> CPF </td>
        <td> XXX.XXX.XXX.-XX </td>
    </tr>
    <tr>
        <td> phone </td>
        <td> (xx) xxxxx-xxxx </td>
    </tr>
</table>

![banco_dados_desafio](https://github.com/elisama/desafio/assets/7691281/496d763b-c055-4635-808b-c4685a38e534)

## 3    Tecnologias utilizadas

As tecnogias abaixo foram impostas como condições do desafio, sendo que o ORM

<table>
    <tr>
        <td> <B> Tecnologia </B> </td>
        <td> Versão </td>
    </tr>
    <tr>
        <td> DotNet </td>
        <td> 8.01 </td>
    </tr>
    <tr>
        <td> Entity Framework Core </td>
        <td> 8.0.3 </td>
    </tr>
</table>

Serviço de disponibilização de mapas

Serviço de Pagamento

## 4  Dependências e Versões Necessárias

Blazor
Bootstrap
Servidor de serviço de mapas
Provedor Externo


## 5  Como rodar a aplicação

> área em construção

## 6 Como rodar os testes

> Área em construção

## 7    Problemas e questões enfrentadas

> Área em desenvolvimento

7.1 Uso de qual ORM?

7.2 Uso de qual solução Blazor?

7.3 Qual plataforma online para deploy?

## 9  Material de suporte utilizado
- Principal material utilizado:
[Crie aplicativos Web com o blazor](https://learn.microsoft.com/pt-br/training/paths/build-web-apps-with-blazor/)
- Documentação oficial do Dot Net:
    - [ASP.NET Core 8.0](https://learn.microsoft.com/pt-br/aspnet/core/?view=aspnetcore-8.0)

- Documentação oficial do Razor:
    - [ASP.NET Core Blazor](https://learn.microsoft.com/pt-br/aspnet/core/blazor/?view=aspnetcore-8.0)
    - [Ferramentas para ASP.NET Core Blazor](https://learn.microsoft.com/pt-br/aspnet/core/blazor/tooling?view=aspnetcore-8.0&pivots=windows)
- Documentação do Entity Framework:
    - [Hub de documentação do Entity Framework](https://learn.microsoft.com/pt-br/ef/)
- Documentação oficial do Boostrap:
    - [Documentação](https://getbootstrap.com.br/docs/4.1/getting-started/introduction/)
- Documentação oficial do Google Maps:
    - [Sdks e APIs](https://developers.google.com/maps/documentation?hl=pt-br)


## 10   Agradecimentos

Sabemos que, atualmente, a documentação necessária para a construção completa de qualquer aplicação dev já se encontra totalmente disponível online, desde um Readme à uma API completa, inclusive nos sites dos proprietários das tecnologias, como da Microsoft, do Bootstrap e do próprio GitHub. Contudo, é importante reconhecer aqueles que nos ajudam a dar um *start* inicial, o ponta pé, quando ficamos indecisos ou desorientados antes mesmo de saber qual opção utilizar dentre aquelas disponíveis pelas documentações oficiais.

Devido a isso, faço aqui um reconhecimento e agradecimento especial a:

* André Baltieri, do lendário canal [balta.io](https://www.youtube.com/@baltaio) e da platforma homônima [balta.io](https://balta.io/), que possui material abundante sobre diversas tecnologias do **.NET Core**, inclusive ensinando a construção de diversos CRUDs do zero. Devo ser sincero que alguns dos seus vídeos me salvaram literalmente para esse desafio 😅;
* À [Jose Carlos Macoratti](https://www.youtube.com/@josecarlosmacoratti), detentor de um excelente canal com ampla cobertura da plataforma **Dot NET**, passando desde a criação de CRUD's, API's à elaboração de diversos testes;
* À desenvolvedora [Stephanie Cardoso](https://www.youtube.com/@dev_steph), com o melhor material para a elaboração de uma documentação de portfólio e repositório, dicas essas utilizadas no presente documento;
* Ao Tiago Matos do canal [Tiago Matos](https://www.youtube.com/@tiagomatosweb), com sua playlist fenomenal de uso profissional do *git* e do **GitHub**, importante para qualquer desenvolvedor que esteja em qualquer nível;

* E claro, ao fenomenal casal dev, Gabriel Fróes e Vanessa Weber, do icônico canal [Código Fonte TV](https://www.youtube.com/@codigofontetv), que hoje é o mais completo repositório em língua portuguesa, versando qualquer assunto imaginável de programação, passando do Assembly e Fortran até às Large Language Models (LLM).