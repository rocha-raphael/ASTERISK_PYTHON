# ASTERISK_PYTHON
#Esse script identifica o ip externo usando o "curl" e troca no arquivo do sip.conf o externip,
#Adicionar abaixo no crontab -e para verificar de 2 em 2 minutos
#*/2 * * * * /usr/bin/python3 /usr/src/cache.py

#Necessário ter o "curl" e python3.
#
#Caso o ip externo esteja igual o externip do sip.conf nada é feito.
#
#
#Serve para quando o servidor local possui duas rotas de saidas ou algum failover de rede ativo.
