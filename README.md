# Portfólio — Yasmin Macedo

Site de portfólio pessoal, de página única, feito com **Next.js**, **React** e **TypeScript**. Reúne quem eu
sou, o que faço, os projetos que desenvolvi e um formulário de contato, com layout responsivo para
computador, tablet e celular.

## Seções

- **Home:** foto, nome, cargo e uma breve apresentação;
- **Sobre Mim:** minha trajetória na Ciência da Computação (UFF), no desenvolvimento frontend e na área de dados;
- **Serviços:** cards com as áreas em que atuo (React, TypeScript, CSS, Ciência de Dados e Python);
- **Projetos:** galeria de projetos filtrada por tecnologia (React, CSS, Next, Python e Power BI), com o botão
  **Ver mais** para exibir além dos 6 primeiros;
- **Contato:** e-mail, redes sociais e formulário de contato;
- **Footer.**

O cabeçalho tem links que levam a cada seção por rolagem suave. Em telas pequenas, os links passam para um
menu sanduíche.

## Tecnologias

| Para quê | Tecnologia |
| --- | --- |
| Framework | [Next.js 15](https://nextjs.org/) (App Router) |
| Interface | React 19 + TypeScript |
| Estilo | CSS Modules (um `styles.module.css` por componente) |
| Estado global | [Zustand](https://zustand-demo.pmnd.rs/) |
| Requisições HTTP | [Axios](https://axios-http.com/) |
| API simulada | [json-server](https://github.com/typicode/json-server) |
| Ícones | [React Icons](https://react-icons.github.io/react-icons/) |

## Como os projetos são carregados

Os projetos não ficam fixos no código: eles estão em [`projetos.json`](projetos.json) e são servidos por uma
API REST simulada com o json-server. A store `useProjeto` (Zustand) busca a lista em
`http://localhost:5000/projetos` e filtra pela tecnologia escolhida nos botões da seção Projetos.

Cada projeto tem o formato:

```json
{
  "id": 1,
  "title": "Ecommerce de Livros",
  "tecnology": "React",
  "photo": "https://..."
}
```

Para adicionar um projeto, basta incluir um novo item em `projetos.json`. O valor de `tecnology` precisa ser
igual ao texto de um dos botões de filtro (`React`, `CSS`, `Next`, `Python` ou `Power BI`).

## Executando localmente

Requer **Node.js 18.18** ou mais recente.

```bash
git clone https://github.com/yasminmcedo11/Portfolio.git
cd Portfolio
npm install
```

O site precisa de dois processos rodando ao mesmo tempo, cada um em um terminal:

```bash
# terminal 1: API dos projetos em http://localhost:5000
npx json-server projetos.json --port 5000

# terminal 2: site em http://localhost:3000
npm run dev
```

Depois, abra [http://localhost:3000](http://localhost:3000) no navegador. Se a API não estiver rodando, o site
abre normalmente, mas a seção Projetos fica vazia.

### Scripts

| Comando | O que faz |
| --- | --- |
| `npm run dev` | inicia o servidor de desenvolvimento |
| `npm run build` | gera a versão de produção |
| `npm run start` | serve a versão de produção (depois do `build`) |
| `npm run lint` | roda o linter do Next.js |

## Estrutura do repositório

```
projetos.json          dados dos projetos, servidos pelo json-server
public/                imagens e ícones (foto de perfil, ícones das redes sociais etc.)
src/
  app/                 layout, página principal e estilos globais
  components/          uma pasta por seção ou componente (Header, Home, SobreMim, Servicos,
                       Projetos, CardProjeto, CardServico, Contato, Forms, Footer, Buttons)
  services/api.ts      instância do Axios apontando para a API
  stores/useProjeto.ts store do Zustand que busca e filtra os projetos
  types/Projeto.ts     tipo de um projeto
```

## Contato

- E-mail: yasminmacedo_11@outlook.com
- LinkedIn: [Yasmin Macedo](https://www.linkedin.com/in/yasmin-macedo-3ab01625a/)
- GitHub: [@yasminmcedo11](https://github.com/yasminmcedo11)
