# dw-vestibular

Projeto de Dataware House para o curso de Sistemas de Informação da UFSC - Universidade Federal de Santa Catarina.

## Pré Requisitos

* [Docker](https://www.docker.com/)
* [Kettle](http://community.pentaho.com/projects/data-integration/)
* [Tableau](https://www.tableau.com/pt-br)

## Instalando

### Banco de dados vestibular 2008-2012 UFSC
Para executar o banco de dados, deve-se utilizar o docker abaixo:

MySQL com dados de vestibular de 2008-2012.
Para executar:

```sh
docker run -d -p 3306:3306 --name my-mysql-name -e MYSQL_ROOT_PASSWORD=root -v /opt/data:/var/lib/mysql thiagods/vestibular2008-2012
```
Se após o comando acima der o erro: Cannot connect to the Docker daemon. Is the docker daemon running on this host?
Pode ser que vocẽ precise executar o comando acima como root ou utilizando sudo.

OBS: pode trocar /opt/data por outro diretório aonde deseja guardar os dados.

Mais detalhes em https://hub.docker.com/_/mysql/

### Kettle

* Instalar o Kettle utilizando o endereço: http://community.pentaho.com/projects/data-integration/
* Importar e executar em ordem os arquivos abaixo para dentro do kettle:
[dm_evento.ktr](https://github.com/thiagodsti/dw-vestibular/blob/master/Data%20Integration/dm_evento.ktr) - Dimensão evento.
[dm_regiao.ktr](https://github.com/thiagodsti/dw-vestibular/blob/master/Data%20Integration/dm_regiao.ktr) - Dimensão região.
[dm_curso.ktr](https://github.com/thiagodsti/dw-vestibular/blob/master/Data%20Integration/dm_curso.ktr) - Dimensão  curso.
[dm_candidato.ktr](https://github.com/thiagodsti/dw-vestibular/blob/master/Data%20Integration/dm_candidato.ktr) - Dimensão candidato.
[dm_socioeconomico.ktr](https://github.com/thiagodsti/dw-vestibular/blob/master/Data%20Integration/dm_socioeconomico.ktr) - Dimensão socioeconomico.
[fato_desempenho.ktr](https://github.com/thiagodsti/dw-vestibular/blob/master/Data%20Integration/fato_desempenho.ktr) - Fato desempenho.
[fato_agregado.ktr](https://github.com/thiagodsti/dw-vestibular/blob/master/Data%20Integration/fato_agregado.ktr) - Fato agregado.

### Tableau

* Instalar o Tableau utilizando o endereço: https://www.tableau.com/pt-br
* Importar e executar em ordem os arquivos abaixo para dentro do Tableau:
[fato_desempenho.tde](https://github.com/thiagodsti/dw-vestibular/blob/master/Tableau/fato_desempenho.tde) - Extração do BD.
[trabalho_dw.twb](https://github.com/thiagodsti/dw-vestibular/blob/master/Tableau/trabalho_dw.twb) - Gráficos.

## Autores

* **Thiago Diniz da Silveira** - [Git](https://github.com/thiagodsti)
* **Otávio Augusto Corrêa**
* **Diogo Bach**

## License

This project is licensed under the GNU General Public License - see the [LICENSE.md](LICENSE.md) file for details
