# Paramiko
Codigo de execução do Paramiko em ssh
# -*- coding: utf-8 -*-
import paramiko
try:
    ssh = paramiko.SSHClient()
    ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    ip = raw_input('digite seu ip: ')
    porta = int(raw_input('digite a porta: '))
    nome = raw_input('digite seu nome: ')
    senha = raw_input('digite sua senha: ')
    print("Conectando... por favor espere!\n")
    try:   
        ssh.connect(ip,port = porta, username=nome, password=senha)
        while True:
            comando = raw_input('digite o comando(sair): ')
            if comando!='sair':
                command = comando
                (stdin, stdout, stderr) = ssh.exec_command(command)
                for line in stdout.readlines():
                        print (line)
            else:
                print("Conexão foi terminada com sucesso!")
               ssh.close()
    except:
        print("Ops, algo deu errado! ")
        print("O usuario ou a senha estão corretos?")
        print(" ")
        print("Conexão encerrada - FATAL ERROR ")
except:
    print(" ")
    print("Ops, algo deu errado!")
    print("Verifique se o ip e a porta estão corretos!")
    print(" ")
    print("Conexão encerrada - FATAL ERROR ")
