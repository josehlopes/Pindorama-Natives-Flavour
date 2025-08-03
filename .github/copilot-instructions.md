# Instruções para GitHub Copilot

## Contexto do Projeto

Este repositório contém arquivos para o desenvolvimento de um **mod para Europa Universalis IV (EU4)**, um jogo de grande estratégia da Paradox Interactive. O objetivo é criar conteúdos personalizados como eventos, decisões, ideias nacionais, modificadores e outras funcionalidades usando a **linguagem de script da Paradox**.

## Linguagem Utilizada

Este projeto utiliza a **linguagem de scripts da Paradox** (geralmente arquivos `.txt` com sintaxe própria), conforme documentado na wiki oficial:

📖 https://eu4.paradoxwikis.com/Modding

Essa linguagem tem uma estrutura baseada em blocos aninhados, chave-valor, lógica booleana, operadores condicionais, gatilhos e efeitos.

Exemplo típico:
```plaintext
country_event = {
    id = my_mod.1
    title = "My Custom Event"
    desc = "This is a description for a custom event."

    trigger = {
        tag = FRA
        stability = 3
    }

    option = {
        name = "Great!"
        add_stability = -1
    }
}