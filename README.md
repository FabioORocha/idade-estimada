🧠 Estimador de Idade com Debounce usando SvelteKit
Este é um pequeno projeto feito com SvelteKit e JavaScript, que permite ao usuário digitar um nome e consultar a idade estimada para ele usando a API pública Agify.io. A requisição só é feita com debounce de 1000ms, evitando chamadas excessivas. O campo de busca é sincronizado com a URL via query string (?name=joao), utilizando a função load() do SvelteKit para pré-carregar os dados da API.

🚀 Tecnologias usadas
SvelteKit
JavaScript
API pública Agify.io

📦 Instalação e execução
1.Instale as dependências
npm install

2. Rode o projeto localmente
npm run dev
Acesse http://localhost:5173 no navegador.

🔓 API usada
Endpoint: https://api.agify.io?name=SEUNOME
