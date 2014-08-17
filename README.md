#simple-php-Shopping-Cart

An easy to use shopping cart that is backed by a database and lets you add, update and remove items from a session based cart 

##configure

items must be added to a mysql database in order to use the cart.
make sure you run the cart.sql and add your database user details to the db class located in the core/classes file

##Add
To add an item to the shopping cart call the addToCart method and supply an item id and quantity you wish to add

```
$cart->addToCart(1, 1);
```

If the item is already in the cart this method will automatically add the items quantity given it is not more than the quantity in the database

##Total
```
$cart->Total();
```
This will let you know the total price of items in the cart 

##number of items
```
$cart->numbitems();
```
Will return the number of items that have been added to the cart 

##update 
```
$cart->update()
```
Lets you update an item quantity in the cart, if a value is non numeric or is zero the items will automatically be removed from the cart 

#Items

##output items
```
if($cart->cart())
{
  foreach(sessions::get('cart') as $key => $value)
  {
    $prods = $items->getDetails($key);
      
      echo $prods->name(). '<br>';
      echo '&pound'.$cart->itemPrice($key).'<br>';
  }
} 
else 
{
  ..............
}
```
If you wish to output the items in the cart use the above code and of cause you can easliy add your own styling to this

##check

```
$items->getItems(tablename)
```
will check if there are items in the database and will return the results in an object and can be output by 

```
foreach($items->getItems(tablename) as $prods)
{
  echo $prods->fields
} 
else {
  no items
}
```

To check if a spesific item exists and its details call 
```
$items->getDetails($id)->quantity()
```
This will get the quantity available of the given item

##Other 
The sessions and db classes a not only tied to this project and can easily be used in any other

#ToDo

1. Add and calculate the taxes
2. look for security loop holes 
3. Make cart much more flexible 
4. Gain more followers on github :-)


