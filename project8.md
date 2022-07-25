## LOAD BALANCER SOLUTION WITH APACHE
#### I will Deploy and configure an Apache Load Balancer for Tooling Website solution on a separate Ubuntu EC2 intance. I Make sure that users can be served by Web servers through the Load Balancer. 

### Configure Apache As A Load Balancer
#### I Create an Ubuntu Server 20.04 EC2 instance and name it Project-8.

![ScreenShot_20_07_2022_19_33_44](https://user-images.githubusercontent.com/19933457/180858639-2a51f37a-f1a5-4c4c-ad29-9658bfe1320a.png)

#### I Open TCP port 80 on Project-8 by creating an Inbound Rule in the Security Group.

#### I Install Apache Load Balancer on Project-8-apache server and configure it to point traffic coming to LB to both Web Servers:

`sudo apt update`
![ScreenShot_20_07_2022_19_37_19](https://user-images.githubusercontent.com/19933457/180859024-d85cc2e8-7136-4d47-aa2c-d7f0485f7b24.png)

`sudo apt install apache2 -y`
![ScreenShot_20_07_2022_19_37_45](https://user-images.githubusercontent.com/19933457/180859129-3a477962-e15c-41c4-8602-d61021752b41.png)

`sudo apt-get install libxml2-dev`

![ScreenShot_20_07_2022_19_38_25](https://user-images.githubusercontent.com/19933457/180859143-30093b46-2a8e-4cc5-a202-08944ca4c8ec.png)
![ScreenShot_20_07_2022_19_39_26](https://user-images.githubusercontent.com/19933457/180862751-f3de174d-f83f-4a08-9bc2-a21a15c24fde.png)

`sudo a2enmod rewrite`
![ScreenShot_20_07_2022_19_39_52](https://user-images.githubusercontent.com/19933457/180862852-c03c6e32-ddc1-4869-8672-f52723ef18c1.png)

`sudo a2enmod proxy`
![ScreenShot_20_07_2022_19_39_52](https://user-images.githubusercontent.com/19933457/180862915-71380460-7891-4f88-b2ff-db8d968dd460.png)

`sudo a2enmod proxy_balancer`
![ScreenShot_20_07_2022_19_40_05](https://user-images.githubusercontent.com/19933457/180862954-625739ff-c58c-41b8-bf0f-46b031baa9d0.png)

`sudo a2enmod proxy_http`

![ScreenShot_20_07_2022_19_40_05](https://user-images.githubusercontent.com/19933457/180862999-8fbb3b1d-a52c-4280-92a5-ada483aa343a.png)

`sudo a2enmod headers`
![ScreenShot_20_07_2022_19_40_05](https://user-images.githubusercontent.com/19933457/180863029-d31f1aab-a0ab-4880-9823-0417b620349a.png)

`sudo a2enmod lbmethod_bytraffic`

![ScreenShot_20_07_2022_19_40_05](https://user-images.githubusercontent.com/19933457/180863175-d5a39f9f-727f-4cab-bd6f-f302f3358cbe.png)

`sudo systemctl restart apache2`

![ScreenShot_20_07_2022_19_40_28](https://user-images.githubusercontent.com/19933457/180863296-414eaed5-bf4c-4e25-8f4d-70c203053631.png)

### Make sure apache2 is up and running
`sudo systemctl status apache2`
![ScreenShot_20_07_2022_19_40_51](https://user-images.githubusercontent.com/19933457/180863462-bb785b2c-69de-4e32-82a3-c302f41d08e7.png)

### Configure load balancing


