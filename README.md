<h2>Descrição do Projeto</h2>
<p>
    Este projeto tem como objetivo criar um banco de dados para gerenciar uma universidade. O modelo abrange diversas entidades e seus relacionamentos, como alunos, professores, cursos, disciplinas, coordenações, matrículas, inscrições em disciplinas, avaliações, entregas, formas de pagamento e cursos extras. O modelo é flexível e fácil de usar, atendendo às necessidades de uma instituição de ensino superior.
</p>

<h2>Entidades e Atributos</h2>
<ul>
    <li>
        <strong>Aluno</strong>
        <ul>
            <li><code>id_aluno</code> (INT, Primary Key)</li>
            <li><code>nome</code> (VARCHAR(45))</li>
            <li><code>tipo_conta</code> (ENUM('PF', 'PJ'))</li>
            <li><code>matricula</code> (VARCHAR(20))</li>
        </ul>
    </li>
    <li>
        <strong>Professor</strong>
        <ul>
            <li><code>id_professor</code> (INT, Primary Key)</li>
            <li><code>nome</code> (VARCHAR(45))</li>
            <li><code>coordenacao_id</code> (INT, Foreign Key)</li>
        </ul>
    </li>
    <li>
        <strong>Curso</strong>
        <ul>
            <li><code>id_curso</code> (INT, Primary Key)</li>
            <li><code>nome</code> (VARCHAR(45))</li>
            <li><code>coordenacao_id</code> (INT, Foreign Key)</li>
        </ul>
    </li>
    <li>
        <strong>Disciplina</strong>
        <ul>
            <li><code>id_disciplina</code> (INT, Primary Key)</li>
            <li><code>nome</code> (VARCHAR(45))</li>
            <li><code>professor_id</code> (INT, Foreign Key)</li>
            <li><code>semestre</code> (INT)</li>
        </ul>
    </li>
    <li>
        <strong>Coordenacao</strong>
        <ul>
            <li><code>id_coordenacao</code> (INT, Primary Key)</li>
            <li><code>nome</code> (VARCHAR(45))</li>
        </ul>
    </li>
    <li>
        <strong>Matricula</strong>
        <ul>
            <li><code>id_matricula</code> (INT, Primary Key)</li>
            <li><code>aluno_id</code> (INT, Foreign Key)</li>
            <li><code>curso_id</code> (INT, Foreign Key)</li>
            <li><code>data_matricula</code> (DATE)</li>
        </ul>
    </li>
    <li>
        <strong>Inscricao_Disciplina</strong>
        <ul>
            <li><code>id_inscricao</code> (INT, Primary Key)</li>
            <li><code>aluno_id</code> (INT, Foreign Key)</li>
            <li><code>disciplina_id</code> (INT, Foreign Key)</li>
            <li><code>semestre</code> (INT)</li>
        </ul>
    </li>
    <li>
        <strong>Pre_requisito</strong>
        <ul>
            <li><code>id_pre_requisito</code> (INT, Primary Key)</li>
            <li><code>disciplina_id</code> (INT, Foreign Key)</li>
            <li><code>pre_requisito_id</code> (INT, Foreign Key)</li>
        </ul>
    </li>
    <li>
        <strong>Avaliacao</strong>
        <ul>
            <li><code>id_avaliacao</code> (INT, Primary Key)</li>
            <li><code>disciplina_id</code> (INT, Foreign Key)</li>
            <li><code>aluno_id</code> (INT, Foreign Key)</li>
            <li><code>tipo</code> (ENUM('...'))</li>
            <li><code>nota</code> (DECIMAL(4,2))</li>
        </ul>
    </li>
    <li>
        <strong>Entrega</strong>
        <ul>
            <li><code>id_entrega</code> (INT, Primary Key)</li>
            <li><code>aluno_id</code> (INT, Foreign Key)</li>
            <li><code>status</code> (VARCHAR(45))</li>
            <li><code>codigo_rastreio</code> (VARCHAR(45))</li>
        </ul>
    </li>
    <li>
        <strong>Forma_Pagamento</strong>
        <ul>
            <li><code>id_pagamento</code> (INT, Primary Key)</li>
            <li><code>aluno_id</code> (INT, Foreign Key)</li>
            <li><code>tipo_pagamento</code> (VARCHAR(45))</li>
            <li><code>dados_pagamento</code> (VARCHAR(255))</li>
        </ul>
    </li>
    <li>
        <strong>Curso_Extra</strong>
        <ul>
            <li><code>id_curso_extra</code> (INT, Primary Key)</li>
            <li><code>nome</code> (VARCHAR(45))</li>
            <li><code>tipo</code> (ENUM('...'))</li>
            <li><code>horas_complementares</code> (INT)</li>
        </ul>
    </li>
    <li>
        <strong>Inscricao_Curso_Extra</strong>
        <ul>
            <li><code>id_inscricao_extra</code> (INT, Primary Key)</li>
            <li><code>aluno_id</code> (INT, Foreign Key)</li>
            <li><code>curso_extra_id</code> (INT, Foreign Key)</li>
        </ul>
    </li>
</ul>
    <h2>Relacionamentos</h2>
    <ul>
        <li><strong>Aluno</strong> se relaciona com <strong>Matricula</strong>, <strong>Inscricao_Disciplina</strong>, <strong>Avaliacao</strong>, <strong>Entrega</strong>, <strong>Forma_Pagamento</strong>, <strong>InscricaoCursoExtra</strong>.</li>
        <li><strong>Professor</strong> se relaciona com <strong>Disciplina</strong> e <strong>Coordenacao</strong>.</li>
        <li><strong>Curso</strong> se relaciona com <strong>Disciplina</strong> e <strong>Coordenacao</strong>.</li>
        <li><strong>Disciplina</strong> se relaciona com <strong>Professor</strong>, <strong>Pre-requisito</strong>, <strong>Inscricao_Disciplina</strong>, <strong>Avaliacao</strong>.</li>
        <li><strong>Coordenacao</strong> se relaciona com <strong>Professor</strong> e <strong>Curso</strong>.</li>
        <li><strong>Curso_Extra</strong> se relaciona com <strong>InscricaoCursoExtra</strong>.</li>
    </ul>
    <h2>Requisitos Adicionais</h2>
    <ul>
        <li><strong>Cliente PJ e PF</strong>: Uma conta pode ser PJ ou PF, mas não pode ter as duas informações ao mesmo tempo.</li>
        <li><strong>Pagamento</strong>: Pode ter mais de uma forma de pagamento cadastrada.</li>
        <li><strong>Entrega</strong>: Possui status e código de rastreio.</li>
    </ul>
    <h2>Instruções para Implementação</h2>
    <ol>
        <li><strong>Clone o Repositório</strong>:
            <pre><code>git clone &lt;URL_DO_REPOSITORIO&gt;</code></pre>
        </li>
        <li><strong>Navegue até o Diretório do Projeto</strong>:
            <pre><code>cd nome-do-projeto</code></pre>
        </li>
        <li><strong>Abra o MySQL Workbench</strong> e crie um novo esquema de banco de dados.</li>
        <li><strong>Implemente o Modelo</strong>: Utilize o script SQL fornecido no repositório para criar as tabelas e os relacionamentos conforme descrito.</li>
        <li><strong>Adicione a Descrição do Projeto ao README</strong>: Inclua a descrição conceitual do projeto no arquivo <code>README.md</code> para fornecer o contexto sobre o esquema.</li>
        <li><strong>Suba o Projeto para o GitHub</strong>:
            <pre><code>git add .<br>git commit -m "Adiciona modelo de banco de dados para sistema de universidade"<br>git push origin main</code></pre>
        </li>
    </ol>
    <h2>Conclusão</h2>
    <p>
        Este projeto fornece uma base sólida para a gestão de uma universidade, abrangendo todas as entidades e relacionamentos necessários para um sistema completo e funcional. Ao implementar este modelo, você estará criando um recurso valioso para seu portfólio de projetos no GitHub.
    </p>
</body>
</html>
