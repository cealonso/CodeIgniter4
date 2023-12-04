# Proyecto en CodeIgniter 4

### En app/Config/App.php 


```php
public string $baseURL = 'http://localhost/app-ci';
```

### En app/Config/Database.php 

```php
public array $default = [
        'hostname'     => 'localhost',
        'username'     => 'root',
        'password'     => '',
        'database'     => 'commerce',
    ];

```

### En app/Models/ProductsModel.php

```php

<?php
namespace App\Models;
use CodeIgniter\Model;
class ProductsModel extends Model
{
    protected $table = 'products';
    protected $returnType = 'array';
    protected $allowedFields =    
    ['id_product','product_name','price','id_category'];
}   

```

### En app/Controllers/Demo.php

```php

<?php

namespace App\Controllers;

use App\Models\ProductsModel;

class Demo extends BaseController
{
    public function index()
    {
        $productsModel = new ProductsModel();
        $data['products'] = $productsModel->findAll();
        return view('demo/index', $data);
    }
}

```

### En app/Views/demo/index.php 

```php

<!DOCTYPE html>
<html lang="en">

	<head>
		<title>Listado de Productos</title>
        <link rel="stylesheet"
      href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css"
      integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk"
      crossorigin="anonymous">
    </head>

	<body>
		<h3>Lista de Productos</h3>
		<table class="table table-bordered">
			<tr>
                <th>ID</th>
				<th>Price</th>
				<th>Description</th>
                <th>ID Category</th>
			</tr>
			<?php foreach ($products as $product) { ?>
				<tr>
                    <td><?= $product['id_product'] ?></td>
					<td><?= $product['price'] ?></td>
					<td><?= $product['product_name'] ?></td>
                    <td><?= $product['id_category'] ?></td>
				</tr>
			<?php } ?>
		</table>
	</body>
</html>

```

