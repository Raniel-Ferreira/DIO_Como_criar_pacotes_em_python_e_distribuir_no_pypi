# DIO_Como_criar_pacotes_em_python_e_distribuir_no_pypi

Aula explicando como elaborar seus próprios pacotes e distribuir no Pypi

# Resumo

A criação de pacotes em python facilita o trabalho de programadores proporcionando uma forma de automatizar a instalação de pacotes popularmente usados (pandas, seaborn e etc...) em um único pacote que você pode criar e distibuir de forma gratúita no Pypi.

> Pypi = repositório público oficial (semelhante ao github) de pacotes python

A criação do pacote segue diversas estruturas, neste repositório utilizamos uma estrutura simples de pacote:


` project_name/
      README.md
      setup.py
      requirements.txt
      package_name/
        __init__.py
        file1_name.py
        file2_name.py `
        
Cada arquivo precisa segue uma estrutura

1. README.md = a descrição do pacote que será disponibilizada no site do Pypi, o arquivo é semelhante a este do github
2. setup.py = a descrição do pacote e o processo de instalação ao ser executado na linha de comando
3. requirements.txt = a lista de dependências que o pacote precisa, por exemplo, se ele precisa de uma versão específica do python para ser executado ou de algum outro pacote (exemplo = só pode ser exeutado com a versão 0.8 do pandas e com python 3.9).
4. package name = é a pasta que leva o nome do seu pacote contendo os módulos que precisam ser executados
    - __init__.py = arquivo que vai importar os módulos
    - file1_name ou file2_name = o código (modularizado) necessário pra executar o pacote.

Para subir o pacote, criar uma distribuição binária ou distribuição de código fonte. Ambos serão colocados no Pypi, as versões mais recentes do pip instalam primeiramente a binária e usam a distribuição de código fonte, apenas se necessário pois a binária é muito mais rápida para instalar

Os comandos de instalação são

> `python -m pip install --upgrade pip` `python -m pip install --user twine` `python -m pip install --user setuptools`

Já o comando para criar distribuições é o:

> `python setup.py sdist bdist_wheel `

Após toda a configuração do seu pacote é necessário criar uma conta no Pypi e no Test Pypi:

https://pypi.org/account/register/
https://test.pypi.org/account/register/

> O Test Pypi é um repositório para testar seus pacotes antes de distribuir eles publicamente no Pypi

Para publicar no test Pypi utilizamos o Twine, um pacote utilizado para publicar seus pacotes no Pypi e TestPypi

> Comando de publicação ` python -m twine upload --repository-url https://test.pypi.org/legacy/ dist/* `

> Como instalar o pacote de teste ` pip install –-index-url https://test.pypi.org/simple/ image-processing`

> Como publicar no Pypi `python -m twine upload --repository-url https://upload.pypi.org/legacy/ dist/* `

> Comando para instalar o pacote `python -m pip install package_name`



    

