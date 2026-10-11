# ObsidianRPG

Sistema de RPG de mesa autoral, escrito como um vault do [Obsidian](https://obsidian.md) e publicado como site estático com o [Quartz 4](https://quartz.jzhao.xyz).

A ideia do sistema é permitir ideias absurdas mantendo o jogo sob certo controle, com habilidades que criam interações, diálogos e disputas entre os jogadores.

## Estrutura

| Caminho | Conteúdo |
| --- | --- |
| `content/` | O vault do Obsidian: todas as regras do RPG. É o único lugar que você precisa editar para mudar o jogo. |
| `content/index.md` | Página inicial do site. |
| `content/1 - Conteudos do RPG/` | Regras gerais: atributos, raças, classes, perícias, armas e magias. |
| `content/Raças/` | Uma nota por raça. |
| `content/Classes/` | Uma nota por classe (`T1-*` iniciais, `T2-*` evoluções) e o índice. |
| `content/RPG/Dicionario.md` | Dicionário de termos, referenciado pelas outras notas. |
| `quartz/`, `docs/` | Código e documentação do Quartz (upstream), não do RPG. |
| `quartz.config.ts`, `quartz.layout.ts` | Configuração e layout do site. |

## Editando o conteúdo

Abra a pasta `content/` como vault no Obsidian e edite as notas normalmente.

### Convenções

- **Classes**: arquivo `T<tier>-<Nome>.md` em `content/Classes/`. Ao criar uma classe, adicione-a em `content/Classes/index.md`.
- **Raças**: arquivo `<Nome>.md` em `content/Raças/`. Ao criar uma raça, adicione-a em `1.2 - Raças.md`.
- **Termos do dicionário**: cada termo é um bloco em `content/RPG/Dicionario.md` terminado por uma âncora `^nome-do-termo`, em minúsculas, sem acento e com hífen.
- **Links para o dicionário**: `[[RPG/Dicionario#^nome-do-termo|Texto exibido]]`. O caminho e a âncora precisam bater exatamente com o arquivo, incluindo maiúsculas: o Obsidian tolera diferenças, mas o site publicado não.
- Trechos ainda não escritos são marcados com **Em construção**.

## Rodando localmente

Requer Node.js 22 ou superior e npm 10.9.2 ou superior.

```bash
npm ci
```

```bash
npx quartz build --serve
```

O site fica disponível em `http://localhost:8080` e é reconstruído a cada alteração.

Também é possível usar Docker:

```bash
docker build -t obsidianrpg .
```

```bash
docker run --rm -p 8080:8080 obsidianrpg
```

## Publicação

Cada push na branch `v4` dispara o workflow `.github/workflows/deploy.yml`, que gera o site e publica no GitHub Pages em <https://jdouglassilva.github.io/ObsidianRPG>.

## Licença

O Quartz é distribuído sob a licença MIT (ver `LICENSE.txt`).
