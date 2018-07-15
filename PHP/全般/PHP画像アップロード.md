# PHP画像アップロード

## HTML

```html
<form action="test.php" method="post" enctype="multipart/form-data">
<input type="hidden" name="MAX_FILE_SIZE" value="200000" />
<input name="image1" type="file" />
<input name="image2" type="file" />
</form>
```

## PHP

```php
try {
    $id = 100;
    $image_dir = '/var/www/image';
    $errs = array(
        UPLOAD_ERR_OK         => 'There is no error, the file uploaded with success.',
        UPLOAD_ERR_INI_SIZE   => 'The uploaded file exceeds the upload_max_filesize directive in php.ini.',
        UPLOAD_ERR_FORM_SIZE  => 'The uploaded file exceeds the MAX_FILE_SIZE directive that was specified in the HTML form.',
        UPLOAD_ERR_PARTIAL    => 'The uploaded file was only partially uploaded.',
        UPLOAD_ERR_NO_FILE    => 'No file was uploaded.',
        UPLOAD_ERR_NO_TMP_DIR => 'Missing a temporary folder.',
        UPLOAD_ERR_CANT_WRITE => 'Failed to write file to disk.',
        UPLOAD_ERR_EXTENSION  => 'File upload stopped by extension.',
    );
    foreach (array('image1','image2') as $k) {
        while (true) {
            if (!isset($_FILES[$k])) break;
            if (!isset($_FILES[$k]['type'])) break;
            list($type) = split('/',$_FILES[$k]['type']);
            if ($type != 'image') break;
            if (isset($_FILES[$k]['error']) && $_FILES[$k]['error'] !== UPLOAD_ERR_OK) {
                throw new Exception('ファイルアップロードに失敗しました（'.$errs[$_FILES[$k]['error']].'）：'.$_FILES[$k]['name']);
            }
            $suffix = strtolower(substr($_FILES[$k]['name'], strrpos($_FILES[$k]['name'],'.') + 1));
            if (!in_array($suffix,array('jpg','jpeg','gif','png'))) break;
            if (!is_dir("$image_dir/$id")) {
                mkdir("$image_dir/$id");
                chmod("$image_dir/$id",0777);
            }
            foreach (array('jpg','jpeg','gif','png') as $v) {
                if (file_exists("$image_dir/$id/$k.$v")) unlink("$image_dir/$id/$k.$v");
            }
            move_uploaded_file($_FILES[$k]['tmp_name'], "$image_dir/$id/$k.$suffix");
            chmod("$image_dir/$id/$k.$suffix",0666);
            break;
        }
    }
} catch (Exception $e) {
    die($e->getMessage());
}
```
