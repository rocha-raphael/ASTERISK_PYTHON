import os
from time import sleep

#Data atual
date=os.popen('date \'+%Y-%m-%d %H:%M\'').read().strip()

#Procura o externip configurado no sip.conf
ip_sip_antigo = os.popen('cat /etc/asterisk/sip.conf | grep externip').read().strip().split('\n')
for i in ip_sip_antigo:
#Aqui ele busca a linha do externip se ela não estiver comentada.
    if ';' not in i:
        ip_sip_antigo=i
        ip_sip=i.split('=')
        ip_sip=ip_sip[1].strip()
        
#verifica o ip externo do servidor
ip_externo = os.popen('curl ifconfig.me').read().strip()
#muda o externip caso esteja diferente do ip externo pego com o curl
if ip_sip != ip_externo:
    os.system(f'sed -i \'s/{ip_sip_antigo}/externip={ip_externo}/\' /etc/asterisk/sip.conf')
    sleep(2)
    os.system('asterisk -rx \'sip reload\'')
    #Criar log da troca do IP
    os.system(f'echo \'externip trocado de {ip_sip_antigo} para {ip_externo} em {date}\' >> /tmp/externip.log')
