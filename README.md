# 🧠 Estimador de Idade com Debounce usando SvelteKit

Este é um pequeno projeto feito com **SvelteKit** e **JavaScript**, que permite ao usuário digitar um nome e consultar a idade estimada para ele usando a API pública [Agify.io](https://agify.io).  
A requisição só é feita com **debounce de 1000ms**, evitando chamadas excessivas.  
O campo de busca é sincronizado com a URL via query string (`?name=joao`), utilizando a função `load()` do SvelteKit para pré-carregar os dados da API.

---

## 🚀 Tecnologias usadas

- **SvelteKit**
- **JavaScript**
- **API pública Agify.io**

---

## 🔓 API usada

Endpoint: https://api.agify.io?name=SEUNOME

---

## 🖼️ Preview

<img src="https://drive.google.com/uc?export=view&id=1KpjmEcLyJX4RJacEOM6kjy2PsCKqF2N9" alt="Preview do Estimador de Idade" width="700" />
