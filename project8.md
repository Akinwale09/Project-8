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
`sudo vi /etc/apache2/sites-available/000-default.conf`
#### I added the below configuration 

![ScreenShot_20_07_2022_19_57_39](https://user-images.githubusercontent.com/19933457/181347420-91dabc83-531e-42a4-ab2d-63cd4cedf952.png)

#### I restart my apache2 server
`sudo systemctl restart apache2`

![ScreenShot_20_07_2022_19_58_54](https://user-images.githubusercontent.com/19933457/181347675-17dfd742-3f42-4dbe-bc62-a7f55dba4f66.png)

![ScreenShot_20_07_2022_19_59_35](https://user-images.githubusercontent.com/19933457/181347722-c51da24d-c6d9-45ee-bb1b-c7af8e623800.png)

#### And now I have my web page served on both serever

![ScreenShot_20_07_2022_20_00_31](https://user-images.githubusercontent.com/19933457/181347866-0679e614-bbc9-4d68-82ac-8183c84fd249.png)

![ScreenShot_20_07_2022_20_00_38](https://user-images.githubusercontent.com/19933457/181347879-f5114c51-23fe-4a55-bdde-b02da35943ac.png)

![ScreenShot_20_07_2022_20_00_58](https://user-images.githubusercontent.com/19933457/181347911-67044e0b-b662-4519-8852-5896fef82d51.png)

### I Configure Local DNS Names Resolution
#### I got served locally on my system
![ScreenShot_20_07_2022_20_07_15](https://user-images.githubusercontent.com/19933457/181348265-f00bfe23-2d1d-47d7-8dd2-eb5d5eae4310.png)

![ScreenShot_20_07_2022_20_07_30](https://user-images.githubusercontent.com/19933457/181348273-e50fc0da-30e1-4fe3-831d-5c00e5200cc4.png)

![ScreenShot_20_07_2022_20_07_50](https://user-images.githubusercontent.com/19933457/181348310-3889a4e9-dd3e-4237-864b-e1a95c9c0079.png)


![ScreenShot_20_07_2022_20_17_18](https://user-images.githubusercontent.com/19933457/181348335-0dda07fa-b921-4b58-ac99-40d6bbb17db1.png)

![ScreenShot_20_07_2022_20_18_04](https://user-images.githubusercontent.com/19933457/181348373-77566494-05fb-4b3b-a550-49f0d30dc390.png)


![ScreenShot_20_07_2022_20_18_04](https://user-images.githubusercontent.com/19933457/181348412-e7dc700e-8e30-471f-afb9-1352ebc317c7.png)

![ScreenShot_20_07_2022_20_20_39](https://user-images.githubusercontent.com/19933457/181348420-dad9f091-1b1b-4cd9-a2db-a7975b79484f.png)

![ScreenShot_20_07_2022_20_20_56](https://user-images.githubusercontent.com/19933457/181348436-4919f0e3-a5d3-4efc-85d2-52df9e46ba2f.png)

![ScreenShot_20_07_2022_20_22_30](https://user-images.githubusercontent.com/19933457/181348464-e8569e85-470c-4efb-a579-522cd4436e5f.png)


![ScreenShot_20_07_2022_20_23_01](https://user-images.githubusercontent.com/19933457/181348481-f1606952-d785-4f4a-8312-0b24a4882936.png)







