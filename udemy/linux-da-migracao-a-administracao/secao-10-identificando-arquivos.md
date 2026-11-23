# Seção 10 - Identificando arquivos

- Como descobrir o formato de um arquivo sem extensão?
- `ls -l nomearquivo`
  - apresenta informações do arquivo, mas não inclui formato ou extensão
- `file nomearquivo`: mostra o formato do arquivo
- Sistemas Unix não precisam de extensão para saber o formato do arquivo
- O sistema lê o início do arquivo (a assinatura, também chamada de magic number) e, através dessa informação, identifica o formato
