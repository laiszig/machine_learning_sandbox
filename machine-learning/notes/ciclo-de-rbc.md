### O Ciclo de Raciocinio Baseado em Casos (RBC)

1. **`Recuperacao`**: recuperacao do caso armazenado na BC (base de casos) mais similar ao novo problema apresentado.
2. **`Reutilizacao`**: adaptacao da parte de solucao do caso recuperado. A solucao do problema recuperado e geralmente utilizadaa como ponto de partida para propor uma solucao para o novo problema. Essa etapa tambem e denominada adaptacao de casos
3. **`Revisao`**: a solucao adaptada e revisada pelo usuario para validar sua relevancia para resolver o novo problema.
4. **`Retencao`**: caso, apos a etapa de revisao, a solucao adaptada seja considerada relevante, o novo problema, junto com essa solucao, sera armazenado na BC.

Situacoes em que RBC nao constitui a solucao mais adequada:
- Problemas com Alta Complexidade e Escalabilidade
- Problemas em Ambientes Dinamicos e de Rapida Mudanca
- Problemas com Dados Insuficientes ou de Baixa Qualidade
- Problemas que Exigem Raciocinio Abstrato ou Criatividade
- Problemas que Exigem Modelagem Formal ou Algoritmos Precisos