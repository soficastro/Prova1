# Sistema para Gerenciamento de Projetos
# Funcionalidades
- Alocação e remoção de usuários dos tipos alunos de graduação, mestrado e doutorado, professores, pesquisadores, profissionais (desenvolvedor, testador e analista) e técnico, além de edição de informações destes.
- Alocação e remoção de produções, isto é, projetos e atividades na unidade acadêmica, além de edição de informações.
- Apresentação de relatório de produção da unidade acadêmica.
- Consulta de informações de: usuário, projeto, ou atividade.
# Classes e distribuição de métodos
- System: Nesta classe main, temos o loop onde o sistema roda em runtime, também é onde existe a opção de adicionar usuários e produções, que leva a métodos de outras classes; seus atributos (Array List de Person 'users', Array List de Project 'projects' e Array List de Activity 'activies') funcionam como banco de dados do sistema; o método 'consult' permite a consulta das informações de um usuário, projeto ou atividade mediante o número de identificação; o método 'report' fornece um relatório de projeto e atividades da unidade acadêmica.
- Person: Super-classe com os atributos comuns 'name' e 'id'; possui o método 'removePerson' que recebe um Array List de Person e o método abstrato 'addPerson' que é implementado nas subclasses. Da classe Person derivam as subclasses:
    
    -> Student: A classe Student possui como atributo um int 'type' que informa o grau de graduação do aluno: graduação(1), mestrado(2) e doutorado(3). Implementa 'addPerson' com as especificações de alunos.
    
    -> ProjectCoordenator: Essa classe abrange os tipos de usuários professor e pesquisador, poís são os únicos que podem ser coordenadores de projetos. O atributo 'type' informa se trata-se de um professor(1) ou um pesquisador(2). Implementa 'addPerson' com as especificações de professores e pesquisadores.
    
    -> 
