# Sistema para Gerenciamento de Projetos
# Funcionalidades
- Alocação e remoção de usuários dos tipos alunos de graduação, mestrado e doutorado, professores, pesquisadores, profissionais (desenvolvedor, testador e analista) e técnico.
- Alocação e remoção de produções, isto é, projetos e atividades na unidade acadêmica, além de edição de informações.
- Apresentação de relatório de produção da unidade acadêmica.
- Consulta de informações de: usuário, projeto, ou atividade.
# Classes e distribuição de métodos
- System: Nesta classe main, temos o loop onde o sistema roda em runtime, também é onde existe a opção de adicionar usuários e produções, que leva a métodos de outras classes; seus atributos (Array List de Person 'users', Array List de Project 'projects' e Array List de Activity 'activies') funcionam como banco de dados do sistema; o método 'consult' permite a consulta das informações de um usuário, projeto ou atividade mediante o número de identificação; o método 'report' fornece um relatório de projeto e atividades da unidade acadêmica.
- Person: Super-classe com os atributos comuns 'name' e 'id'; possui o método 'removePerson' que recebe um Array List de Person e o método abstrato 'addPerson' que é implementado nas subclasses. Da classe Person derivam por herança as subclasses:
    
    -> Student: A classe Student possui como atributo um int 'type' que informa o grau de graduação do aluno: graduação(1), mestrado(2) e doutorado(3). Implementa 'addPerson' com as especificações de alunos.
    
    -> ProjectCoordenator: Essa classe abrange os tipos de usuários professor e pesquisador, poís são os únicos que podem ser coordenadores de projetos. O atributo 'type' informa se trata-se de um professor(1) ou um pesquisador(2). Implementa 'addPerson' com as especificações de professores e pesquisadores.
    
    -> Professional: Essa classe abrange os tipos de usuários profissionais (desenvolvedor, testador e analista) e técnico, uma vez que não há nenhuma especificação para estes usuários. O atributo 'job' informa se trata-se de um desenvolvedor(1), testador(2), analista(3) ou técnico(4). Implementa 'addPerson' com as especificações de profissionais e técnicos.
    
- Production: Super-classe que abrange os atributos em comuns das subclasses Project e Activity: 'id', 'description', 'startDay', 'startMonth', 'startYear', 'startTime', 'endDay', 'endMonth', 'endYear', 'endTime', e um Array List de Person 'collaborators' com todos os usuários atribuídos ao projeto ou atividade. Possui o método abstrato 'startProduction' que é implementado nas subclasses, o método 'editBasicInfo' que, dado o número de id de uma produção já incorporada no sistema, permite a edição de suas informações, e os métodos 'removeProduction' e 'addCollaborator'. Da classe Production derivam por herança as classes:

    -> Project: Além dos atributos herdados de Production, possui os atributos 'status', 'coordenator' do tipo ProjectCoordenator e um Array List 'activities'. Possui todos os métodos relacionados a gerenciamento de projetos, implementa 'startProduction' com as especificações de um projeto, possui o método addActivity que adiciona uma atividade do "banco de dados" ao Array List 'activities' desta classe. Além disso, possui o método 'loginProjectCoordenator', em que o coordenador de um certo projeto deve informar sua id para ter acesso à edição e outras ações específicas em um projeto, como o método 'changeStatus'. Os métodos 'isCoordenatorAttributed' e 'isBasicInfoSet' servem como booleanas para verificação de certas etapas.
    
    -> Activity: Além dos atributos herdados de Production, essa subclasse possui os atributos 'coordenator' do tipo Person e um Array List 'works' do tipo Work. Possui o método 'assignWork' que dado um colaborador que já esteja atribuído à atividade, adiciona um objeto do tipo Work ao Array List 'works', além de implementar o método 'startProduction' com as especificações de uma atividade. 

- Work: Esta classe possui apenas atributos, que são 'id', 'description' e 'responsable' do tipo Person que o responsável pela tarefa e é atribuido no método 'assignWork' da classe Activity.
#Tratamento de exceção
Apesar de não estar no diagrama de classes, todas as situações em que podem ocorrer erro de exceção, como input inválido, devem receber tratamento de exceção do tipo "try (...) catch"
