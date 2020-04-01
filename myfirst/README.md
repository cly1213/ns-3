# myfirst

```c
Device = Helper.Install(Node);
/* 生成網卡
    Device是網卡
    Helper是網路類型，
    Node是要來連接的節點
*/

Interface = Address.Assign(Device);
/*
    綁定IP
    Interface是網路接口接口，供後續Application使用
    Address是網路地址，是一個網段
    Device是網卡
*/

Ipv4GlobalRoutingHelper::PopulateRoutingTables ();
/*
    用拓撲幫助構建路由
*/
```
P2P nework

```c
NodeContainer c;
c.create(2);

NodeContainer n0n1 = NodeContainer(c.Get(0), c.Get(1));

PointToPointHelper p2p;
p2p.SetDeviceAttribute ("DataRate", StringValue ("5Mbps"));
p2p.SetChannelAttribute ("Delay", StringValue ("2ms"));
NetDeviceContainer d0d1 = p2p.Install (n0n1);

Ipv4AddressHelper address;
address.SetBase ("10.1.1.0", "255.255.255.0");
xxx = address.Assign (d0d1);
// 為d0d1裡2個節點分配ip, 10.1.1.1 -------10.1.1.2

Ipv4GlobalRoutingHelper::PopulateRoutingTables ();
```
Ethernet network

```c
NodeContainer c;
c.create(4);

CsmaHelper n0n1n2n3 = NodeContainer(c.Get(0), c.Get(1), c.Get(2), c.Get(3));
//CsmaHelper n0n1n2n3 = NodeContianer(c);
csma.SetChannelAttribute ("DataRate", StringValue ("100Mbps"));
csma.SetChannelAttribute ("Delay", TimeValue (NanoSeconds (6560)));
NetDeviceContainer d0d1d2d3 = csma.Install (n0n1n2n3);

Ipv4AddressHelper address;
address.SetBase ("10.1.2.0", "255.255.255.0");
xxx = address.Assign (d0d1d2d3);
// 為d0d1d2d3中的節點分別分配ip
// 10.1.2.1----10.1.2.2----10.1.2.3----10.1.2.4

Ipv4GlobalRoutingHelper::PopulateRoutingTables ();
```
Wireless newwork

```c
NodeContainer c;
c.create(3);

//讓第一個節點做為AP，其他的連接這個AP
NodeContainer ApNode = c.Get(0);

//其他的做無線設備，連接AP(節點)路由器
NodeContainer StaNode = NodeContainer(c.Get(1), c.Get(2));

WifiHelper wifi;
wifi.SetRemoteStationManager ("ns3::AarfWifiManager");

WifiMacHelper mac;
Ssid ssid = Ssid ("ns-3-ssid");


//設置AP節點網路
mac.SetType ("ns3::ApWifiMac",
           "Ssid", SsidValue (ssid));
NetDeviceContainer apDevices = wifi.Install (phy, mac, wifiApNode);

//設置無線設備網路
mac.SetType ("ns3::StaWifiMac",
           "Ssid", SsidValue (ssid),
           "ActiveProbing", BooleanValue (false));
NetDeviceContainer staDevices = wifi.Install (phy, mac, wifiStaNodes);

Ipv4AddressHelper address;
address.SetBase ("10.1.2.0", "255.255.255.0");
address.Assign (staDevices);
address.Assign (apDevices);
```

