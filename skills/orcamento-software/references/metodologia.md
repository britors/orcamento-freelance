# Metodologia de estimativa

## Checklist de itens esquecidos

Passe por cada item e decida: entra no escopo (vira tarefa), entra como premissa ("fornecido pelo cliente") ou entra como exclusão.

**Base do projeto:** setup do repositório e da arquitetura · ambientes (desenvolvimento, homologação, produção) · CI/CD · configuração de domínio, DNS e SSL · backups.

**Contas e acesso:** cadastro · login · recuperação de senha · confirmação de e-mail · perfis e permissões · painel administrativo · logout e expiração de sessão.

**Comunicação com o usuário:** e-mails transacionais (modelos e provedor) · notificações push · mensagens de erro e estados vazios · carregamento.

**Qualidade e conformidade:** responsividade · compatibilidade de navegadores · acessibilidade básica · LGPD (termos, política de privacidade, consentimento, exclusão de conta e de dados) · logs e monitoramento de erros · segurança básica (validação, rate limit, segredos).

**Dados:** importação/migração de dados existentes · seed inicial · relatórios e exportações (CSV/PDF).

**Mobile, quando houver:** contas de desenvolvedor · publicação e revisão nas lojas · ícones, splash e capturas de tela · atualização de versão.

**Encerramento:** documentação de implantação · treinamento ou sessão de handoff · transferência de contas e credenciais.

## Faixas de calibração (desenvolvedor sênior, sozinho)

Use para conferir se uma estimativa está fora da curva, não como tabela de preços. Ajuste quando o seu histórico real mostrar outros números.

| Item | Faixa provável (h) |
|---|---|
| Setup de projeto + ambientes + CI/CD básico | 8–16 |
| Autenticação completa (cadastro, login, recuperação, confirmação) | 12–24 |
| Perfis e permissões (RBAC simples) | 8–16 |
| CRUD simples com listagem, filtro e paginação | 6–12 |
| CRUD com regras de negócio, validações e relacionamentos | 12–24 |
| Dashboard com 4–6 indicadores e gráficos | 12–24 |
| Integração com gateway de pagamento (checkout + webhooks) | 16–40 |
| Integração com API de terceiro bem documentada | 8–16 |
| Integração com API mal documentada ou legada | 24–60 |
| Upload de arquivos com armazenamento em nuvem | 6–12 |
| Relatório exportável (PDF ou CSV) | 6–16 |
| Tela de front-end a partir de design pronto | 4–10 |
| Tela de front-end sem design (inclui decisões visuais) | 8–16 |
| Publicação de app nas duas lojas | 8–16 |

## Critérios de risco

Some um ponto por critério presente:
- Escopo descrito sem telas, protótipo ou regras de negócio escritas.
- Integração com sistema legado, API sem documentação ou sem ambiente de testes.
- Tecnologia nova para o freelancer.
- Prazo do cliente abaixo do prazo calculado.
- Muitos decisores do lado do cliente, ou decisor indisponível.
- Dependência de entregas do cliente (conteúdo, design, acessos) no caminho crítico.

**0–1 ponto:** risco baixo · **2–3 pontos:** risco médio · **4 ou mais:** risco alto — considere propor descoberta paga em vez de preço fechado direto.

Registre na planilha quais critérios pontuaram; isso justifica a contingência se o usuário questionar.

## Prazo do cliente menor que o prazo calculado

Não comprima as horas para caber no prazo. Ofereça, nesta ordem: reduzir escopo para um MVP que caiba no prazo, entregar em fases, ou cobrar adicional de urgência (sugestão: +25% a +50% sobre o preço) se o freelancer puder realmente dedicar mais horas por semana.
