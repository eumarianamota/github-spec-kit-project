# Desenvolvimento Orientado a Especificações - GitHub SpecKit
Esse é um repositório para armazenar os meus estudos relacionados ao desenvolvimento orientado a especificações com as ferramentas de spec do github. 

O desenvolvimento orientado a especificações, inverte a lógica do desenvolvimento. Antes, as especificações eram uma base para a codificação, hoje, as especificações são executáveis que geram implementações funcionais automaticamente. O desenvolvimento orientado a especificações é um processo que enfatiza:
- **Desenvolvimento orientado a inteções:** as especificações definem primeiro "o quê" antes do "como".
- **Criação de especificações detalhadas:** as especificações são criadas respeitando as diretrizes e princípios organizacionais. 
- **Refinamento em várias etapas:** as especificações passam por diversas etapas de refinamento antes de começar a codificação.
- **Inteligência artificial:** forte dependência dos recursos de IA para a definição e interpretação das especificações.

Para trabalhar com spec driven usando as ferramentas do github, seguimos uma metodologia para definição definição e aprimoramento das especificações até o desenvolvimento de fato, veja as etapas:
1. **Definição dos princípios:** define-se os princípios inegóciáveis do projeto.
2. **Definição das especificações:** define-se as especificações alto nível do projeto.
3. **Etapa de clarificação:** refina-se as especificações por meio de questionários.
4. **Definição do planejamento:** define-se o planejamento do projeto por meio das especificações.
5. **Definição das tarefas:**
6. **Etapa de análise:**
7. **Implementação das tarefas:**

### 1. Começando
**1. Instale o Specify CLI**
``` 
    uv tool install specify-cli --from git+https://github.com/github/spec-kit.git@vX.Y.Z

    # ou 

    uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```

**2. Inicialize o projeto** 
```
# Criar novo projeto
specify init <PROJECT_NAME>

# Inicializar em um projeto existente
specify init . 
# or
specify init . --ai claude
# or
specify init --here --ai claude

# Verificar ferramentas instaladas
specify check
```

### 2. Os princípios



### 3. As especificações 
- to make a high level spec of a new feature 
- A feature não deve ser muito grande porque isso abre espaço para o modelo viajar na maionese, mas ela tambem não pode ser muito pequena porque se nao vai ser over kill over engineering e over tudo 
- This should focus on the what and the why intead of the how.
- Not details about the underlying technologies or the architecture, well be focusing on the user experience  
- Para definir as especificações, na janela do copilot ou qualquer ferramenta que esteja usando, selecione o /speckit.specify e digite o prompt
- O arquivo do spec vai ser criado assim na raiz do projeto:
```
|  specs 
    | nome-da-branch
        | spec.md
```
- Se tiver partes no documento com "[NEED CLARIFICATION]" é porque você precisa rodar o /clarify para clarear essas ideias.
- Esse negócio em cima tá errado, ainda nao entendi o que são os clarification tokens que ele tá falando  
- Aqui o prompt que a gente usou para fazer a definição do spec.md 
```
/speckit.specify initial page setup - this application should be a goal tracking web app called "doit". There should be two columns - a left one where current goals are shown, along with how many days left the user has to achieve the goal, and a right one where completed goals are. Each goal can be "checked" using a checkbox, and the either moved to the completed column or permanently deleted. To add new goals, a user can click on a button to open a new goal form in a modal (title and end date fields). Goals reaching their end date (within 3 days) are highlighted. Lets use a modern light theme with fun pastel colors.  
```

- O que dveria ter no documento de spec.md está definido no prompt em agents 
- 

### 4. A clarificação 
- the clarify command instructs the coding agent to read through the current spec file to find any ambiguities edge cases or areas that might need further clarification. And it asks us about them and then we can provide feedback for each one of those which the agent will then bake into the spec file. This spec inst required, but it a good idea if you have any clarification marks in you current specs. 
- O prompt vai ler o spec file em usca de areas pouco especificadas, se tiver, ele vai nos fazer perguntas e nos dar opções para responder. Uma vez que tiver respondido todas as perguntas, eles vai atualizar o spec file 
- è só rodar o comando /speckit.clarify + enter
- Esse é o momento para ler todas as especificações ate o momento porque ainda dá pra mudar, a partir do proximo step o negócio vai ficar mais complicado pra fazer mudanças, read over, if you find anything you wanna change, change it mannually before you go to planning step  


### 5. O planejamento
- Nessa etapa, você pode definir as tecnologieas, as versões, os frameworks, as bibliotecas, os serviços e as APis que serão consumidas. The planning stage is the time to lay all that out. 
- Primeiro ele run the script set up plan 

### 6. A tarefa 
- takes the plan documents and from those makes an actionable set of tasks for the coding agents to work on to implement that plan 
- É só rodar o comando tasks e não precisa escrever mais nada no input 
- Turn the plan into a series of tasks for the AI model to follow  

### Dúvidas 
- constitution, specify, plan, tasks, implement, clarify, analyse
- Add principle e os outros lá uma explicação? 

### Referências 
- [Spec Kit - Github](https://github.com/github/spec-kit)
- [Spec Kit - Tutorial](https://youtube.com/playlist?list=PL4cUxeGkcC9h9RbDpG8ZModUzwy45tLjb&si=1nRTHqr4rsshat_k)
- [Spec Kit - Documentação](https://github.github.com/spec-kit/index.html)

