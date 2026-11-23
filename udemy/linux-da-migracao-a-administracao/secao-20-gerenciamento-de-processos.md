# Seção 20 - Gerenciamento de processos

## Aula 37 - Gerenciamento de processos

- `ps`: mostra processos, com ID do processo, terminal, tempo de execução e nome do comando em execução
  - `ps aux`: mostra todos os processos do sistema
- `pgrep processo`: mostra o número (PID) do processo
- `kill PID`: comando usado para encerrar processos
  - `kill -9 PID`: força o encerramento
- `pidof nomeprocesso`: mostra o PID do processo
  - caso haja mais de um PID, é possível usar `pgrep nomeprocesso` para filtrar o PID principal
- `top`: semelhante ao gerenciador de processos do Windows, se mantém atualizado
  - `L` (dentro do `top`): localiza processos

## Aula 38 - Números nice

- Números nice são como prioridades dos processos
- Variam de -20 a 19
- O número padrão é 0
- A prioridade aumenta à medida que o número diminui, indo para os números negativos
- `su -c "renice -n -1 -p PID"`: aumenta a prioridade do processo para -1 (como administrador); apenas o root pode atribuir valores negativos

## Aula 39 - Comando nice

- Como iniciar o programa já com uma prioridade definida?
- `nice --adjustment=-1 nomeprograma`: inicia o processo com prioridade -1
- Pode ser uma boa opção para tarefas pesadas, como backups: uma prioridade maior (número menor) faz a tarefa terminar mais rápido, e uma prioridade menor (por exemplo, `nice -n 10`) evita atrapalhar o resto do sistema
