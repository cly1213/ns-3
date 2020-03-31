# myfirst

```bash
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
