# Projeto-final-algoritmo
projeto que simula matricula de alunos. 

import random

cont = True
matriz_alunos = []

def nome_aluno():
    nome = input('Digite o nome do aluno: ')
    return nome


def adicionar_dados_aluno(nome):
    nome_da_mae = input('Digite o nome da mãe do aluno: ')
    nome_do_pai = input('Digite o nome do pai do aluno: ')
    identidade_aluno = int(input('Digite o RG do aluno: '))
    cpf_aluno = int(input('Digite o CPF do aluno: '))
    titulo_aluno = input('Digite o número do título de eleitor do aluno: ')
    email = input('Digite o seu e-mail: ')
    telefone = int(input('Digite o seu número de telefone: '))
    return nome_da_mae, nome_do_pai, identidade_aluno, cpf_aluno, titulo_aluno, email, telefone


def adicionar_dados_endereco():
    cidade = input('Digite a cidade: ')
    cep = int(input('Digite o CEP: '))
    bairro = input('Digite o bairro: ')
    rua = int(input('Digite a rua: '))
    numero = int(input('Digite o número: '))
    return cidade, cep, bairro, rua, numero


def adicionar_dados_curso():
    curso = input('Digite o curso que deseja realizar a matrícula: ')
    turno = input('Digite o turno do seu curso: ')
    numero_matricula = random.randint(100000, 999999)
    codigo_formatado = f'{numero_matricula:06d}'
    print('Número Matrícula:', codigo_formatado)
    return curso, turno, numero_matricula, codigo_formatado


def editar_dados_aluno():
    nome_pesquisa = input('Digite o nome do aluno que deseja editar: ')
    for aluno in matriz_alunos:
        if aluno[0] == nome_pesquisa:
            print('Dados atuais do aluno:')
            print('Nome:', aluno[0])
            print('Nome da mãe:', aluno[1])
            print('Nome do pai:', aluno[2])
            print('RG:', aluno[3])
            print('CPF:', aluno[4])
            print('Título de eleitor:', aluno[5])
            print('E-mail:', aluno[6])
            print('Telefone:', aluno[7])
            print('Cidade:', aluno[8])
            print('CEP:', aluno[9])
            print('Bairro:', aluno[10])
            print('Rua:', aluno[11])
            print('Número:', aluno[12])
            print('Curso:', aluno[13])
            print('Turno:', aluno[14])
            print('Número Matrícula:', aluno[15])
            print('Código formatado:', aluno[16])
            print('-' * 80)
            print('Digite os novos dados do aluno:')
            nome_da_mae, nome_do_pai, identidade_aluno, cpf_aluno, titulo_aluno, email, telefone = adicionar_dados_aluno(nome_pesquisa)
            aluno[1], aluno[2], aluno[3], aluno[4], aluno[5], aluno[6], aluno[7] = nome_da_mae, nome_do_pai, identidade_aluno, cpf_aluno, titulo_aluno, email, telefone
            print('\033[32m Dados do aluno atualizados com sucesso!\033[0m')
            return
    print('\033[31m Aluno não encontrado!\033[0m')


def remover_matricula():
    nome_pesquisa = input('Digite o nome do aluno que deseja remover a matrícula: ')
    for aluno in matriz_alunos:
        if aluno[0] == nome_pesquisa:
            matriz_alunos.remove(aluno)
            print('\033[32m Matrícula removida com sucesso!\033[0m')
            return
    print('\033[31m Aluno não encontrado!\033[0m')


while cont:
    print('=' * 80)
    print('INSTITUTO FEDERAL DO PIAUÍ-CAMPUS CORRENTE')
    print('=' * 80)

    print('1- MATRICULAR ALUNOS')
    print('2- EXIBIR ALUNOS MATRICULADOS')
    print('3- EDITAR DADOS DO ALUNO')
    print('4- REMOVER MATRÍCULA')
    print('5- BUSCAR ALUNO POR NOME')
    print('6- SAIR')

    opcao = input('Digite a opção que deseja realizar: ')

    if opcao == '1':
        nome = nome_aluno()
        nome_da_mae, nome_do_pai, identidade_aluno, cpf_aluno, titulo_aluno, email, telefone = adicionar_dados_aluno(nome)
        cidade, cep, bairro, rua, numero = adicionar_dados_endereco()
        curso, turno, numero_matricula, codigo_formatado = adicionar_dados_curso()

        dados_aluno = [nome, nome_da_mae, nome_do_pai, identidade_aluno, cpf_aluno, titulo_aluno, email, telefone, cidade, cep, bairro, rua, numero, curso, turno, numero_matricula, codigo_formatado]
        matriz_alunos.append(dados_aluno)
        print('\033[32m Aluno matriculado com sucesso!\033[0m')

    elif opcao == '2':
        print('Alunos matriculados:')
        for aluno in matriz_alunos:
            print('Nome:', aluno[0])
            print('Nome da mãe:', aluno[1])
            print('Nome do pai:', aluno[2])
            print('RG:', aluno[3])
            print('CPF:', aluno[4])
            print('Título de eleitor:', aluno[5])
            print('E-mail:', aluno[6])
            print('Telefone:', aluno[7])
            print('Cidade:', aluno[8])
            print('CEP:', aluno[9])
            print('Bairro:', aluno[10])
            print('Rua:', aluno[11])
            print('Número:', aluno[12])
            print('Curso:', aluno[13])
            print('Turno:', aluno[14])
            print('Número Matrícula:', aluno[15])
            print('Código formatado:', aluno[16])
            print('-' * 80)

    elif opcao == '3':
        editar_dados_aluno()

    elif opcao == '4':
        remover_matricula()

    elif opcao == '5':
        buscar_aluno_por_nome()

    elif opcao == '6':
        cont = False
        print('Programa encerrado.')

    else:
        print('\033[31mOpção inválida!\033[0m')
