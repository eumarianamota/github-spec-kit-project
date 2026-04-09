# github-spec-kit
Esse é um repositório para armazenar os meus estudos relacionados ao Spec Kit do Github, um conjunto de ferramentas open-source que permite focar na criação de cenários antes do cesenvolvimento.

### 1. O que é spec driven development?
Spec driven development, em português, desenvolvimento orientado a especificações, inverte a lógica do desenvolvimento. Antes, as especificações eram uma base para a codificação, hoje, a as especificações são executáveis que podem gerar implementações funcionais automaticamente.

### 2. Por onde começar?
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

### 3. Definindo os princípios do projeto 



### the spec command 
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

### the clarify command 
- the clarify command instructs the coding agent to read through the current spec file to find any ambiguities edge cases or areas that might need further clarification. And it asks us about them and then we can provide feedback for each one of those which the agent will then bake into the spec file. This spec inst required, but it a good idea if you have any clarification marks in you current specs. 
- O prompt vai ler o spec file em usca de areas pouco especificadas, se tiver, ele vai nos fazer perguntas e nos dar opções para responder. Uma vez que tiver respondido todas as perguntas, eles vai atualizar o spec file 
- è só rodar o comando /speckit.clarify + enter
- Esse é o momento para ler todas as especificações ate o momento porque ainda dá pra mudar, a partir do proximo step o negócio vai ficar mais complicado pra fazer mudanças, read over, if you find anything you wanna change, change it mannually before you go to planning step  


### the plan command 
- Nessa etapa, você pode definir as tecnologieas, as versões, os frameworks, as bibliotecas, os serviços e as APis que serão consumidas. The planning stage is the time to lay all that out. 
- Primeiro ele run the script set up plan 
- 

### Dúvidas 
- constitution, specify, plan, tasks, implement, clarify, analyse
- Add principle e os outros lá uma explicação? 

### Referências 
- []()

