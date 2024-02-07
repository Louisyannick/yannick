
<?php
$catalogues = new PDO('mysql:host=localhost;dbname=catalogue', 'root', '');

$requete= "SELECT reference, prix, description, libtype FROM articles JOIN types ON articles.typeid=types.typeid";
$resultat= $catalogues-> query($requete);
?>
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Affiche</title>
    <style>
        table, tr, td,th{
            border: 2px solid black;
            border-collapse: collapse;
            text-align: center;
        }
        table{
            width: 600px;
            height: 200px;
        }
    </style>
</head>
<body>
    <table>
        <tr>
            <th>reference</th>
            <th>prix</th>
            <th>Description</th>
            <th>type</th>
        </tr>
        <?php
            while($article=$resultat->fetch()){?>
            <tr>
                <td><?php echo $article['reference']; ?></td>
                <td><?php echo $article['prix']; ?></td>
                <td><?php echo $article['description']; ?></td>
                <td><?php echo $article['libtype']; ?></td>
            </tr>
            <?php
            }
        ?>
    </table>
</body>
</html>
