# Shopify-Fall-2022-Challenge

## Build an inventory tracking web application for a logistics company with the following features

* Basic CRUD Functionality. You should be able to:
    * Create inventory items
    * Edit Them
    * Delete Them
    * View a list of them

* Along with one additional feature:
    * Ability to create “shipments” and assign inventory to the shipment, and adjust inventory appropriately

# For a video demonstration visit
-  [Youtube Video](https://www.youtube.com/watch?v=U19rjLJybpw)

# Table of Contents
- [Installations](#installations)
- [CRUD Functionality](#CRUD-Functionality)
- [Images](#images)
- [Future Features](#future-features)
- [Note For Shopify Developers](#note-for-shopify-developers)
- [Contact Me](#contact-me)


<p align="center">
    <u><h2 align="center">Installations</h2></u>
</p>

- First create a Firebase Project
-  Generate an serviceAccountkey for your firebase project. Go to your ```Firebase project -> Project Settings -> Service Accounts``` and download the firebase SDK by clicking ```Generate New Private Key``` button
- Rename the file to ``` serviceAccountKey.json ``` and put it in the root folder. The file will look like this
```
 {
  "type": ,
  "project_id": ,
  "private_key_id": ,
  "private_key": ,
  "client_email": ,
  "client_id": ,
  "auth_uri": ,
  "token_uri": ,
  "auth_provider_x509_cert_url": ,
  "client_x509_cert_url": 
}
```
- To install all the dependencies run 
```bash
npm i
```

<p align="center">
    <u><h2 align="center">How to Run it</h2></u>
</p>

- To run the application, start up your terminal /command prompt ,and go to the project folder and then run the following command
```bash
node index.js
```

## Features
<p align="center">
    <u><h2 align="center">CRUD Functionality</h2></u>
</p>


- All the inventry items are stored in the Firebase Database
- **Create inventory items** : POST {/api/inventory/add}
   - Sample body request:
   ```
   {
      "item_name" : "sanitizer",
      "qunatity" : 4,
      "desc" : "disinfectnant"
   }
   ```
   - Sample Postman Request:
    ![Screen Shot 2022-01-19 at 6 47 41 PM](https://user-images.githubusercontent.com/60456975/150245325-9d0f7855-158b-412e-bad6-661e12678fda.png)
    
- **View inventory** : GET {/api/inventory/view}
   - Sample Postman Request:
   ![Screen Shot 2022-01-19 at 6 48 57 PM](https://user-images.githubusercontent.com/60456975/150245621-8b61ef05-b4db-4a1f-b2c3-a46430c12bb3.png)

- **Edit inventory item** : PUT {/api/inventory/edit}
   - Sample body request:
   ```
   {
      "item_id" : item_id,
      "qunatity" : 9
   }
   ```
   - Sample Postman Request:
   ![Screen Shot 2022-01-19 at 6 50 27 PM](https://user-images.githubusercontent.com/60456975/150245424-81ee4c21-b97b-4b9d-adc6-183291e7f425.png)

- **Delete inventory item** : DELETE {/api/inventory/delete/$item_id}
   - In the request url replace $item_name with the item you want to delete from the inventory
   - Sample Request:
   ![Screen Shot 2022-01-19 at 6 51 51 PM](https://user-images.githubusercontent.com/60456975/150245497-1c9ba362-b10f-4192-a47f-2bdb0addaf5d.png)


<p align="center">
    <u><h2 align="center">Shipment</h2></u>
</p>

- Once images are uploaded, a thumbnail is generated which is then stored in the Firebase Storage that can be later downloaded using the download url 
   genrated by Firebase
- Create a Shipment: POST {/api/shipment/create}
  - Sample body request:
   ```
   {
      "shipment_to" : test2.png,
      "shipment_from" : test2.png,
      "courrier_service" : test2.png,
      "user_name" :
   }
   ```
  - Sample Postamn Request:
  ![Screen Shot 2022-01-19 at 8 32 56 PM](https://user-images.githubusercontent.com/60456975/150246429-2e202895-b122-4d09-962d-b75f192b033e.png)

  
- Assign Inventory items to Shipment : PUT {/api/shipment/assign}
  - The file's download url is generated using firebase
  - Security during download:
    - The download url is an unique url generated by firebase
    - Since we have made some chnages in the security rules of the firesbase storage,any body for now can download the images
  - Sample body request:
   ```
   {
      "shipment_id" : test2.png,
      "item_id" : "",
      "qunatity" : 4
   }
   ```
  - Sample Postman Request:
  ![Screen Shot 2022-01-19 at 8 33 13 PM](https://user-images.githubusercontent.com/60456975/150246468-379b50c5-3e94-4bd8-afbb-5a514ef9c176.png)

- View all Shipments : GET {/api/shipment/view}
  - The file's download url is generated using firebase
  - Security during download:
    - The download url is an unique url generated by firebase
    - Since we have made some chnages in the security rules of the firesbase storage,any body for now can download the images
  - Sample Postman Request:
  ![Screen Shot 2022-01-19 at 8 33 13 PM](https://user-images.githubusercontent.com/60456975/150246468-379b50c5-3e94-4bd8-afbb-5a514ef9c176.png)

- Delete a Shipment : DELTE {/api/shipment/delete/$shipment_id}
  - The file's download url is generated using firebase
  - Security during download:
    - The download url is an unique url generated by firebase
    - Since we have made some chnages in the security rules of the firesbase storage,any body for now can download the images
  - Sample Postman Request:
  ![Screen Shot 2022-01-19 at 8 33 13 PM](https://user-images.githubusercontent.com/60456975/150246468-379b50c5-3e94-4bd8-afbb-5a514ef9c176.png)

<p align="center">
    <u><h2 align="center">Future Features</h2></u>
</p>

- Make the UI interface for the app
- Update the create inventory request so that it accepts images as well.


<p align="center">
    <u><h2 align="center">Note for Shopify Developers</h2></u>
</p>

- If required I will migrate to aws or gcp in the future releases.
-  Currently the create inventory request only accepts two body parameters which are `item name` and `quantity`, if required i can update it and store more metadata such as expirty date, product_condition,shipment date,etc

<p align="center">
    <u><h2 align="center">Contact Me</h2></u>
</p>

Email : pritish.panda@mail.utoronto.ca
