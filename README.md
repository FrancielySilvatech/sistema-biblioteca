import json

# Lista global para armazenar os livros em memória
livros = []


def exibir_menu():
  print("\n--- SISTEMA DE CADASTRO DE BIBLIOTECA ---")
  print("1. Cadastrar Livro")
  print("2. Listar Livros")
  print("3. Buscar Livro (Título ou Autor)")
  print("4. Realizar Empréstimo")
  print("5. Realizar Devolução")
  print("6. Sair")


def cadastrar_livro():
  print("\n--- Cadastro de Novo Livro ---")
  titulo = input("Digite o título do livro: ")
  autor = input("Digite o autor do livro: ")
  ano = input("Digite o ano de publicação: ")

  # Criando o dicionário do livro com status inicial disponível ("Sim")
  livro = {"titulo": titulo, "autor": autor, "ano": ano, "disponivel": "Sim"}

  livros.append(livro)
  print(f"Livro '{titulo}' cadastrado com sucesso!")


def listar_livros():
  # Etapa 3: Listagem geral
  pass


def buscar_livro():
  # Etapa 3: Busca por filtro
  pass


def emprestar_livro():
  # Etapa 4: Empréstimo
  pass


def devolver_livro():
  # Etapa 4: Devolução
  pass


# --- Loop Principal do Programa (Etapa 1) ---
while True:
  exibir_menu()
  opcao = input("Escolha uma opção (1-6): ")

  if opcao == "1":
    cadastrar_livro()
  elif opcao == "2":
    listar_livros()
  elif opcao == "3":
    buscar_livro()
  elif opcao == "4":
    emprestar_livro()
  elif opcao == "5":
    devolver_livro()
  elif opcao == "6":
    print("Saindo do sistema... Até logo!")

    import json

# Lista global para armazenar os livros em memória
livros = []


def exibir_menu():
  print("\n--- SISTEMA DE CADASTRO DE BIBLIOTECA ---")
  print("1. Cadastrar Livro")
  print("2. Listar Livros")
  print("3. Buscar Livro (Título ou Autor)")
  print("4. Realizar Empréstimo")
  print("5. Realizar Devolução")
  print("6. Sair")


def cadastrar_livro():
  print("\n--- Cadastro de Novo Livro ---")
  titulo = input("Digite o título do livro: ")
  autor = input("Digite o autor do livro: ")
  ano = input("Digite o ano de publicação: ")

  livro = {"titulo": titulo, "autor": autor, "ano": ano, "disponivel": "Sim"}

  livros.append(livro)
  print(f"Livro '{titulo}' cadastrado com sucesso!")


def listar_livros():
  print("\n--- Acervo da Biblioteca ---")
  if not livros:
    print("Nenhum livro cadastrado no momento.")
    return

  # Percorre a lista e exibe os detalhes de cada livro
  for i, livro in enumerate(livros):
    print(f"[{i}] Título: {livro['titulo']} | Autor: {livro['autor']} | Ano: {livro['ano']} | Disponível: {livro['disponivel']}")


def buscar_livro():
  print("\n--- Buscar Livro ---")
  termo = input("Digite parte do título ou do autor que deseja buscar: ").lower()
  
  encontrados = []
  for livro in livros:
    # Compara o termo digitado (em minúsculas) com o título ou autor do livro
    if termo in livro['titulo'].lower() or termo in livro['autor'].lower():
      encontrados.append(livro)

  if encontrados:
    print(f"\nLivros encontrados ({len(encontrados)}):")
    for livro in encontrados:
      print(f"- Título: {livro['titulo']} | Autor: {livro['autor']} | Ano: {livro['ano']} | Disponível: {livro['disponivel']}")
  else:
    print("Nenhum livro encontrado com esse termo.")


def emprestar_livro():
  print("\n--- Realizar Empréstimo ---")
  listar_livros()
  if not livros:
    return

  try:
    indice = int(input("Digite o número (índice) do livro que deseja emprestar: "))
    if 0 <= indice < len(livros):
      if livros[indice]['disponivel'] == "Sim":
        livros[indice]['disponivel'] = "Não"
        print(f"Empréstimo do livro '{livros[indice]['titulo']}' realizado com sucesso!")
      else:
        print("Este livro já está emprestado!")
    else:
      print("Número de livro inválido.")
  except ValueError:
    print("Por favor, digite um número válido.")


def devolver_livro():
  print("\n--- Realizar Devolução ---")
  listar_livros()
  if not livros:
    return

  try:
    indice = int(input("Digite o número (índice) do livro que deseja devolver: "))
    if 0 <= indice < len(livros):
      if livros[indice]['disponivel'] == "Não":
        livros[indice]['disponivel'] = "Sim"
        print(f"Devolução do livro '{livros[indice]['titulo']}' realizada com sucesso!")
      else:
        print("Este livro já consta como disponível na biblioteca.")
    else:
      print("Número de livro inválido.")
  except ValueError:
    print("Por favor, digite um número válido.")


# --- Loop Principal do Programa ---
while True:
  exibir_menu()
  opcao = input("Escolha uma opção (1-6): ")

  if opcao == "1":
    cadastrar_livro()
  elif opcao == "2":
    listar_livros()
  elif opcao == "3":
    buscar_livro()
  elif opcao == "4":
    emprestar_livro()
  elif opcao == "5":
    devolver_livro()
  elif opcao == "6":
    print("Saindo do sistema... Até logo!")
    break
  else:
    print("Opção inválida! Por favor, escolha um número de 1 a 6.")

    import json
import os

# Nome do arquivo JSON onde os dados serão salvos
ARQUIVO_DADOS = "biblioteca.json"

# Lista global para armazenar os livros em memória
livros = []


def carregar_dados():
  """Lê os dados do arquivo JSON ao iniciar o programa (Etapa 5)"""
  global livros
  if os.path.exists(ARQUIVO_DADOS):
    try:
      with open(ARQUIVO_DADOS, "r", encoding="utf-8") as arquivo:
        livros = json.load(arquivo)
    except Exception:
      livros = []


def salvar_dados():
  """Salva a lista atual de livros no arquivo JSON (Etapa 5)"""
  try:
    with open(ARQUIVO_DADOS, "w", encoding="utf-8") as arquivo:
      json.dump(livros, arquivo, ensure_ascii=False, indent=4)
  except Exception as e:
    print(f"Erro ao salvar os dados: {e}")


def exibir_menu():
  print("\n--- SISTEMA DE CADASTRO DE BIBLIOTECA ---")
  print("1. Cadastrar Livro")
  print("2. Listar Livros")
  print("3. Buscar Livro (Título ou Autor)")
  print("4. Realizar Empréstimo")
  print("5. Realizar Devolução")
  print("6. Exibir Contador de Acervo (Melhoria)")
  print("7. Remover Livro do Acervo (Melhoria)")
  print("8. Sair")


def cadastrar_livro():
  print("\n--- Cadastro de Novo Livro ---")
  titulo = input("Digite o título do livro: ")
  autor = input("Digite o autor do livro: ")
  ano = input("Digite o ano de publicação: ")

  livro = {"titulo": titulo, "autor": autor, "ano": ano, "disponivel": "Sim"}

  livros.append(livro)
  salvar_dados()  # Salva automaticamente no arquivo JSON
  print(f"Livro '{titulo}' cadastrado com sucesso!")


def listar_livros():
  print("\n--- Acervo da Biblioteca ---")
  if not livros:
    print("Nenhum livro cadastrado no momento.")
    return

  for i, livro in enumerate(livros):
    print(
        f"[{i}] Título: {livro['titulo']} | Autor: {livro['autor']} | Ano:"
        f" {livro['ano']} | Disponível: {livro['disponivel']}"
    )


def buscar_livro():
  print("\n--- Buscar Livro ---")
  termo = input("Digite parte do título ou do autor que deseja buscar: ").lower()

  encontrados = []
  for livro in livros:
    if (
        termo in livro["titulo"].lower()
        or termo in livro["autor"].lower()
    ):
      encontrados.append(livro)

  if encontrados:
    print(f"\nLivros encontrados ({len(encontrados)}):")
    for livro in encontrados:
      print(
          f"- Título: {livro['titulo']} | Autor: {livro['autor']} | Ano:"
          f" {livro['ano']} | Disponível: {livro['disponivel']}"
      )
  else:
    print("Nenhum livro encontrado com esse termo.")


def emprestar_livro():
  print("\n--- Realizar Empréstimo ---")
  listar_livros()
  if not livros:
    return

  try:
    indice = int(
        input("Digite o número (índice) do livro que deseja emprestar: ")
    )
    if 0 <= indice < len(livros):
      if livros[indice]["disponivel"] == "Sim":
        livros[indice]["disponivel"] = "Não"
        salvar_dados()  # Atualiza o arquivo JSON
        print(
            f"Empréstimo do livro '{livros[indice]['titulo']}' realizado com"
            " sucesso!"
        )
      else:
        print("Este livro já está emprestado!")
    else:
      print("Número de livro inválido.")
  except ValueError:
    print("Por favor, digite um número válido.")


def devolver_livro():
  print("\n--- Realizar Devolução ---")
  listar_livros()
  if not livros:
    return

  try:
    indice = int(
        input("Digite o número (índice) do livro que deseja devolver: ")
    )
    if 0 <= indice < len(livros):
      if livros[indice]["disponivel"] == "Não":
        livros[indice]["disponivel"] = "Sim"
        salvar_dados()  # Atualiza o arquivo JSON
        print(
            f"Devolução do livro '{livros[indice]['titulo']}' realizada com"
            " sucesso!"
        )
      else:
        print("Este livro já consta como disponível na biblioteca.")
    else:
      print("Número de livro inválido.")
  except ValueError:
    print("Por favor, digite um número válido.")


def contador_acervo():
  """Melhoria 1: Mostra estatísticas do acervo"""
  total = len(livros)
  disponiveis = sum(1 for l in livros if l["disponivel"] == "Sim")
  emprestados = total - disponiveis

  print("\n--- Contador de Acervo ---")
  print(f"Total de livros cadastrados: {total}")
  print(f"Livros disponíveis: {disponiveis}")
  print(f"Livros emprestados: {emprestados}")


def remover_livro():
  """Melhoria 3: Permite excluir um livro do sistema"""
  print("\n--- Remover Livro ---")
  listar_livros()
  if not livros:
    return

  try:
    indice = int(input("Digite o número (índice) do livro que deseja remover: "))
    if 0 <= indice < len(livros):
      removido = livros.pop(indice)
      salvar_dados()  # Atualiza o arquivo JSON
      print(f"Livro '{removido['titulo']}' removido com sucesso!")
    else:
      print("Número de livro inválido.")
  except ValueError:
    print("Por favor, digite um número válido.")


# --- Inicialização do Programa ---
carregar_dados()

# --- Loop Principal do Programa ---
while True:
  exibir_menu()
  opcao = input("Escolha uma opção (1-8): ")

  if opcao == "1":
    cadastrar_livro()
  elif opcao == "2":
    listar_livros()
  elif opcao == "3":
    buscar_livro()
  elif opcao == "4":
    emprestar_livro()
  elif opcao == "5":
    devolver_livro()
  elif opcao == "6":
    contador_acervo()
  elif opcao == "7":
    remover_livro()
  elif opcao == "8":
    print("Saindo do sistema... Até logo!")
    break
  else:
    print("Opção inválida! Por favor, escolha um número de 1 a 8.")
    
    break
  else:
    print("Opção inválida! Por favor, escolha um número de 1 a 6.")
