# Droneboga

## Instalação de dependencias

### ROS

Instale o [ROS Kinetic](http://wiki.ros.org/kinetic/Installation/Ubuntu) caso seu sistema seja o Ubuntu 16.04 ou o [ROS Melodic](http://wiki.ros.org/melodic/Installation/Ubuntu) caso seja o Ubuntu 18.04:
```shell
export ROS_VERSION=kinetic
```
ou
```shell
export ROS_VERSION=melodic
```

### MAVROS

```shell
sudo apt-get install ros-$ROS_VERSION-mavros ros-$ROS_VERSION-mavros-extras
```

### GerographicLib

```shell
wget https://raw.githubusercontent.com/mavlink/mavros/master/mavros/scripts/install_geographiclib_datasets.sh
sudo chmod +x install_geographiclib_datasets.sh
./install_geographiclib_datasets.sh
```

### ROS Workspace

Para criar um workspace com este pacote (droneboga), crie um diretório com uma pasta src, por exemplo:
```shell
mkdir -p ~/catkin_ws/src
```
Vá a pasta src, clone este repositório, volte ao diretório deste workspace e compile o pacote
```shell
cd ~/catkin_ws/src
git clone https://github.com/PEQUI-MEC/DRONEBOGA.git
cd ..
catkin_make
```
## Configurando o firmware da pixhawk

TODO: ñ lembro o nome das variáveis alteradas no QGroundControl


## Rodando o script

Conecte a pixhawk via usb, abra um terminal e inicie o nó do MAVROS na porta correta para que ele crie a interface pela qual controlaremos o drone, exemplo caso ele inicie na porta **/dev/ttyACM0**:
```shell
roslaunch mavros px4.launch fcu_url:=///dev/ttyACM0:921600
```

Em outro terminal ative workspace criado colocando-o em suas variáveis de ambiente:
```shell
source ~/catkin_ws/src/devel/setup.bash
```
E execute este nó:
```shell
rosrun droneboga droneboga_node
```
