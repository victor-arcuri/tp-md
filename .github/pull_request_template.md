## Descrição
- Resolve a questão X do Tópico Y.
- Adiciona a explicação teórica sobre Z.

## Tipo de Alteração
- [X] ✨ `feat`: Nova funcionalidade ou resolução de questão.
- [ ] 🐛 `fix`: Correção de bug no código ou erro na explicação.
- [ ] 📝 `docs`: Modificação exclusiva em documentação ou texto explicativo.
- [ ] ♻️ `refactor`: Otimização ou refatoração de código sem mudar o comportamento.

## Checklist de Qualidade e Padrões
- [ ] **A branch de destino está correta?** (O PR deve ser apontado para a `develop`, NUNCA direto para a `main`).
- [ ] **Limpou o Notebook?** As saídas do Jupyter (`.ipynb`) foram limpas (*Kernel > Clear All Outputs*) para evitar conflitos de metadados.
- [ ] O código foi testado localmente e executa sem erros (ex: `ZeroDivisionError`).
- [ ] As variáveis não estão sendo utilizadas de questões anteriores de maneira indevida e atrapalhando o resultado.

## Revisores
@B-DuarteS @maciel-vinicius @victor-arcuri

---
*Lembrete: Pelo menos UM integrante precisa aprovar este PR para que o merge seja liberado na branch develop.*