<?php include 'includes/session.php'; ?>
<?php include 'includes/header.php'; ?>

<?php
// Sécurité : Utilisation de requêtes préparées pour éviter les injections SQL
$where = '';
$catid = 0;

if (isset($_GET['category']) && is_numeric($_GET['category'])) {
    $catid = (int)$_GET['category'];
    $where = 'WHERE category_id = ?';
}

// Recherche (optionnelle)
$search = isset($_GET['search']) ? trim($_GET['search']) : '';
?>

<body class="hold-transition skin-blue layout-top-nav">
<div class="wrapper">

    <?php include 'includes/navbar.php'; ?>

    <div class="content-wrapper">
        <div class="container">

            <!-- Main content -->
            <section class="content">
                <div class="row">
                    <div class="col-sm-8 col-sm-offset-2">
                        <?php
                        // Gestion des messages d'erreur
                        if (isset($_SESSION['error'])) {
                            echo "
                                <div class='alert alert-danger'>
                                    {$_SESSION['error']}
                                </div>
                            ";
                            unset($_SESSION['error']);
                        }
                        ?>
                        <div class="box">
                            <!-- Commenter la section de la barre de recherche -->
                            <!--
                            <div class="box-header with-border">
                                <form method="GET" class="form-inline">
                                    <div class="input-group">
                                        <input type="text" class="form-control input-lg" name="search" id="searchBox" 
                                               placeholder="Rechercher ISBN, Titre ou Auteur" 
                                               value="<?php echo htmlspecialchars($search); ?>">
                                        <span class="input-group-btn">
                                            <button type="submit" class="btn btn-primary btn-flat btn-lg">
                                                <i class="fa fa-search"></i>
                                            </button>
                                        </span>
                                    </div>
                                    <div class="input-group col-sm-5">
                                        <span class="input-group-addon">Catégorie :</span>
                                        <select class="form-control" name="category" id="catlist" onchange="this.form.submit();">
                                            <option value="0" <?php echo ($catid == 0) ? 'selected' : ''; ?>>TOUTES</option>
                                            <?php
                                            // Afficher les catégories dynamiquement
                                            $sql = "SELECT * FROM category";
                                            $query = $conn->query($sql);
                                            while ($catrow = $query->fetch_assoc()) {
                                                $selected = ($catid == $catrow['id']) ? 'selected' : '';
                                                echo "
                                                    <option value='{$catrow['id']}' {$selected}>{$catrow['name']}</option>
                                                ";
                                            }
                                            ?>
                                        </select>
                                    </div>
                                </form>
                            </div>
                            -->
                            <div class="box-body">
                                <table class="table table-bordered table-striped" id="booklist">
                                    <thead>
                                        <th>ISBN</th>
                                        <th>Titre</th>
                                        <th>Auteur</th>
                                        <th>Statut</th>
                                    </thead>
                                    <tbody>
                                        <?php
                                        // Utilisation de requêtes préparées pour les livres
                                        $sql = "SELECT * FROM books ";
                                        $params = [];
                                        $types = '';

                                        if (!empty($where)) {
                                            $sql .= $where;
                                            $params[] = $catid;
                                            $types .= 'i';
                                        }

                                        if (!empty($search)) {
                                            $sql .= (!empty($where) ? ' AND ' : 'WHERE ') . "(isbn LIKE ? OR title LIKE ? OR author LIKE ?)";
                                            $params[] = "%$search%";
                                            $params[] = "%$search%";
                                            $params[] = "%$search%";
                                            $types .= 'sss';
                                        }

                                        $stmt = $conn->prepare($sql);
                                        if ($params) {
                                            $stmt->bind_param($types, ...$params);
                                        }
                                        $stmt->execute();
                                        $result = $stmt->get_result();

                                        // Afficher les résultats
                                        if ($result->num_rows > 0) {
                                            while ($row = $result->fetch_assoc()) {
                                                $status = ($row['status'] == 0) 
                                                    ? '<span class="label label-success">Disponible</span>' 
                                                    : '<span class="label label-danger">Non disponible</span>';
                                                echo "
                                                    <tr>
                                                        <td>{$row['isbn']}</td>
                                                        <td>{$row['title']}</td>
                                                        <td>{$row['author']}</td>
                                                        <td>{$status}</td>
                                                    </tr>
                                                ";
                                            }
                                        } else {
                                            echo "
                                                <tr>
                                                    <td colspan='4' class='text-center'>Aucun livre trouvé.</td>
                                                </tr>
                                            ";
                                        }
                                        ?>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

        </div>
    </div>

    <?php include 'includes/footer.php'; ?>
</div>

<?php include 'includes/scripts.php'; ?>

<script>
$(function(){
    $('#catlist').on('change', function(){
        $(this).closest('form').submit();
    });
});
</script>

</body>
</html>
