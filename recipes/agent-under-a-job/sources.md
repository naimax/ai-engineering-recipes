# Опорные документы

Три породы: ваши файлы, документация инструмента, внешняя статья про уровень «агент vs чат» и agent engineering как дисциплина.

## Внешняя опора

### Дисциплина (что такое agent engineering)

[What is agent engineering?](https://agentengineering.org/articles/what-is-agent-engineering/) (AgentEngineering.org, 2026): bounded autonomy, пять jobs: autonomy, context, tools, trajectory eval, operate. Промпт 0a в [`prompts.md`](prompts.md).

Не копировать фреймворки: только граница «чат / агент / workflow».

### Построение агентов (вендор)

[Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) (Anthropic): augmented LLM, agent vs workflow, Appendix 2 (tool design). Промпт 0 в [`prompts.md`](prompts.md).

### Prompt vs agent (короткая таблица)

[Prompt Engineering vs Agent Engineering](https://gantz.ai/blog/post/prompt-vs-agent-engineering/): один turn vs multi-turn; responder vs actor. Опционально для самопроверки перед charter.

## Документация, вариации и ваши файлы

| Инструмент | Agent / tools | Роли / subagents |
|---|---|---|
| Cursor | [Agent overview](https://cursor.com/docs/agent/overview) | [Rules](https://cursor.com/docs/context/rules) |
| Claude Code | [Sub-agents](https://docs.anthropic.com/en/docs/claude-code/sub-agents) | [Memory](https://docs.anthropic.com/en/docs/claude-code/memory) |
| Codex | [AGENTS.md](https://github.com/openai/codex/blob/main/docs/agents.md) | OpenAI best practices |
| Anthropic API | [Managed Agents overview](https://platform.claude.com/docs/en/managed-agents/overview) | Agent object vs Session |

Перед charter: агент читает строки для вашего инструмента, не все четыре.

Шаблоны charter A–D по типу процесса: [`variations.md`](variations.md) (внутренняя матрица рецепта, не внешний URL).

Минимум ваших файлов:

1. Описание проекта: что агент может трогать.
2. Журнал сбоев: «описал действие, trace пустой» или «destructive при Never».
3. Список необратимых операций: deploy, push main, деньги, удаление данных.
4. Один пример успешной задачи с выводом tool, не пересказ.

Порядок сборки:

1. Промпт 0a (agent engineering) или 0 (Anthropic agent vs workflow).
2. Прочитать [`variations.md`](variations.md), выбрать A/B/C/D.
3. Доки инструмента (таблица выше).
4. Ваши 4 файла.
5. Промпт 1 → `agent-charter.md`.
6. Промпт 2 на реальной задаче.

## Связки с другими рецептами

Правила ([`rule-under-a-job/`](rule-under-a-job/)) задают что удерживать. Этот рецепт задаёт кто исполнитель и чем трогает систему. Maker ≠ checker: charter Never «не ставить себе PASS»; несколько агентов: `many-agents/`.

| Практика | Рецепт (план) | Что добавляет поверх agent charter |
|----------|---------------|-----------------------------------|
| Harness | `environment-around-agent/` | гейты, журнал, ratchet |
| Context | `context-under-a-job/` | что в окне, progressive disclosure |
| Loop | `loop-under-a-job/` | кто инициирует повтор без «проверь ещё» |
