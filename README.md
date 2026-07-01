# Manual de Sobrevivência do 1º Ano Técnico

Atividade prática de Gitflow - ETEC Boituva.

## Objetivo da atividade

Demonstrar na prática:

- criação de um repositório Git;
- uso da branch `develop`;
- criação de features separadas por capítulo;
- merge com histórico preservado usando `--no-ff`;
- publicação de `develop` para `main`;
- criação de tags de versão;
- correção emergencial com `hotfix`.

## Estrutura usada

```text
main
  ├── release do manual completo
  └── hotfix aplicado

develop
  ├── feature/dicas-prazos
  ├── feature/mochila-aula-tecnica
  ├── feature/lanches-perto
  └── feature/regras-trabalho-equipe

hotfix/ajuste-cantina
  └── correção do nome e dos preços da cantina
```

## Branches

| Branch | Finalidade |
| --- | --- |
| `main` | versão publicada do manual |
| `develop` | integração dos capítulos |
| `feature/dicas-prazos` | capítulo 1 |
| `feature/mochila-aula-tecnica` | capítulo 2 |
| `feature/lanches-perto` | capítulo 3 |
| `feature/regras-trabalho-equipe` | capítulo 4 |
| `hotfix/ajuste-cantina` | correção da cantina |

## Manual

O arquivo [guia.md](guia.md) contém quatro capítulos:

1. Dicas para não esquecer os prazos das tarefas.
2. O que levar na mochila nos dias de aula técnica.
3. Onde encontrar os melhores salgados perto da escola.
4. Regras de ouro para trabalhar em equipe sem treta.

## Versões

| Tag | Descrição |
| --- | --- |
| `v1.0` | primeira publicação do manual completo |
| `v1.0.1` | hotfix com ajuste da cantina |

## Roteiro

O passo a passo completo está em [ROTEIRO_COMANDOS.md](ROTEIRO_COMANDOS.md).

## Autor

Victor E. Pereira
1º DS - ETEC Boituva
