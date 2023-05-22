// trabalho de IVANEIDE E ANDREZA

workspace {
    model {
        // Passo 1: Definição das pessoas envolvidas
        Administrador = person "Orientador"
        professor = person "Professor"
        aluno = person "Aluno"

        // Passo 2: Criação do sistema de gestão de TCCs
        sistema = softwareSystem "Sistema de Gestão de TCC" {
            // Passo 3: Criação do container da aplicação web
            webapp = container "Aplicação web" "Aplicação para gerenciar TCCs do curso de Analise e Desenvolvimento de Sistemas do IFPA Campus Belém" {
                // Passo 4: Adição de relacionamentos entre as pessoas e a aplicação web
                Administrador -> this "Uses"
                professor -> this "Uses"
                aluno -> this "Uses"

                // Passo 5: Criação dos componentes da aplicação web
                webappController = component "WebApp Controller" "Controlador da aplicação web"
                webappService = component "WebApp Service" "Serviço da aplicação web"
                webappRepository = component "WebApp Repository" "Repositório da aplicação web"
            }

            // Passo 6: Criação do container do sistema de banco de dados
            database = container "Sistema de banco de dados" "O banco de dados Mysql amazena as informações dos alunos e professores assim como TCCs" {
                // Passo 7: Adição de relacionamento entre a aplicação web e o sistema de banco de dados
                webapp -> this "Lê de e escreve em"

                // Passo 8: Criação dos componentes do banco de dados
                databaseController = component "Database Controller" "Controlador do banco de dados"
                databaseService = component "Database Service" "Serviço do banco de dados"
                databaseRepository = component "Database Repository" "Repositório do banco de dados"
            }
        }
    }

    views {
        // Passo 9: Definição das visualizações do sistema - Diagrama de Contexto
        systemContext sistema {
            include *
            autolayout lr
        }

        // Passo 9: Definição das visualizações do sistema - Diagrama de Container
        container sistema {
            include *
            autolayout lr
        }

        // Passo 9: Definição das visualizações do sistema - Diagrama de Componentes (para o container "Aplicação web")
        component webapp {
            include *
            autolayout lr
        }

        theme default
    }
}
//O código acima descreve o seguinte passo a passo:

Definição das pessoas envolvidas: Administrador, professor e aluno.
Criação do sistema de gestão de TCCs.
Criação do container da aplicação web para gerenciar TCCs.
Adição de relacionamentos entre as pessoas (Administrador, professor, aluno) e a aplicação web.
Criação dos componentes da aplicação web: WebApp Controller, WebApp Service e WebApp Repository.
Criação do container do sistema de banco de dados para armazenar informações dos alunos, professores e TCCs.
Adição de relacionamento entre a aplicação web e o sistema de banco de dados.
Criação dos componentes do banco de dados: Database Controller, Database Service e Database Repository.
Definição das visualizações do sistema: Diagrama de Contexto, Diagrama de Container e Diagrama de Componentes (para o container "Aplicação web").
Definição do tema padrão.
