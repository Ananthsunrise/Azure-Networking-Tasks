# Azure-Networking-Tasks

Task 1 : **Create Vnet,subnet in azure**

Go to azure portal->search virtual networks->click create->give subscription,resource group,region->give name of vnet->give cidr range(for ex:10.0.0.0/24)-click save
Go to azure portal->search virtual networks->select 1 vnet->go to subnet option->click create->give cidr range

Task 2 : **Create and attach additional NIC card in virtual machine**

Bydefault, virtual machine have one NIC card. If many users are login vm through NIC card, to reduce workload we can attach another NIC card.

Go to azure portal->search Network Interface card->click create->select subscription,resource group,region,vnet,subnet->give name of NIC card->select public ip as dynamic or static->click create

Go to azure portal->search virtual machines->select 1 vm->go to network setting->click attach network interface->select your newly created NIC->click attach

Note:while attching NIC card, Virtual machine should be in stopped state.

Task 3: **To associate and deassociate public ip of Virtaul machine**

for virtual machine, both public and private ip's are assingned in it's NIC card only. So we can associate public ip through NIC card

Go to azure portal->search virtual machine->click 1 vm ->go to network setting->select NIC card-> here you can associate and deassociate public ip

Task 4 : **To add additioanl private ip to virtual machine in azure portal and os level** 

Go to azure portal->search virtual machine->click 1 vm ->go to network setting->select NIC card->go to ip configurations in NIC->click add ->select private ip as dynamic or static

Login azure vm->search settings->click adaptor change options->double click ethernet(NIC card)->click properties->double click internet protocol v4->click use the following ip address->give your primare ip details such as ip,subnetmask,default gateway->then click advanced->click add ip address->give secondary ip details->click ok

Note: to get primary ip and secondary ip details, you can type ipcongig in command prompt inside your vm.
      Always choose private ip as static. because if you choose dynamic, there may be a chance to assign that ip to another vm when you stop that vm for 2 days.

Task 5 : **Move virtual machine from one subnet to another subnet**

If your subnet can take only few ip's remaing or your virtual machine needs to troubleshoot, you can change your virtual machine into another subnet.

Go to azure portal->search virtual machine->click 1 vm ->go to network setting->select NIC card->go to ip configurations in NIC->slect subnet you want to change

Task 6 : **Enable or disable Accelerated networking**
Accelerated networking used to increase the speed of virtual machine communication. Bydefault, azure enables accelerated networking.

Go to azure portal->search virtual machine->click 1 vm ->go to network setting->select NIC card->click overviwe->here you can enable or disable accelerated networking

Task 7 : **Adding Virtual machine into PPG(proximity placement group)**

PPG is used for increase the spped of virtual machine communication by grouping of vm's into single ppg group.

Go to azure portal->search proximity placement group->create group
Go to azure portal->search virual machines->click 1 vm->go to configuration->here you can add this vm into PPG group.

note : virtual machine should be in stopped state while adding into PPG.
       You can also add virtual machine into PPG while you creating a vm. you can find ppg in advanced tab.

**Task 8 : Login virtual machine using DNS name instead of using public ip**

Go to azure portal->search virtual machines->click 1 vm->go to configuration->click dns name configure->give proper name->click save.

Task 9 : **Create NAT gateway and assign it it multiple vm's**

go to azure portal->search NAT Gateway->click create->Give name of NAT,subscription,resource group,region->create new public ip(NAT Gateway ip)->give vnet,subnet->click create

Go to azure portal->search subnet->click 1 subnet->select NAT Gateway ip->click save(Instead of assingning NAT ip to multiple vm's onebyone, you can assign ip to the particular subnet which consist of multiple vm's)

Task 10 : **create NSG(Network Security Group) and assign it to vrtual machine**

Go to azure portal->search NSG->Click create->here you can give port number,protocol,priority number-click save

Go to azure portal->search virtual machines->click 1 vm->go to network setting->click 1 NIC card->here you can attach NSG(If you want to assign NSG to single VM, you can attach it on the NIC card)
Go to azure portal->search subnet->click 1 subnet->here you can attach NSG(If you want to attach NSG to multiple vm's, you can attach it on the subnet)

Task 11 : **Add Peering Connection between vnets**

Local vnet peering used to communicate resources from one vnet to another vnet in same region
Global vnet peering used to communicate resources from one vnet to another vnet in different region.

Local peering:
create 2 vnets in same region and create 2 virtual machines and assign 1 vm in 1 vnet, assign another vm in another vnet.
Go to azure portal->search virtual networks->select vnet1->select peering connection->click add->give name of peering->select vnet2 to connect peering->click save

global peering:
create 2 vnets in different region and create 2 virtual machines and assign 1 vm in 1 vnet, assign another vm in another vnet.
Go to azure portal->search virtual networks->select vnet1->select peering connection->click add->give name of peering->select vnet2 to connect peering->click save
