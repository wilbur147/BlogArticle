WordPress删除文章时，文章内所上传到媒体库的图片等附件不仅不会自动删除，还占用了网站空间。

因此下面将通过几行代码的简单方式实现在删除文章时自动删除缩略图以及图片附件，这样就不用手动去媒体库寻找并删除，准确而且效率高。

## 实现代码

- 将下面代码复制到主题根目录 `functions.php`添加即可



```php
/* 删除文章时删除图片附件 */  
function delete_post_and_attachments($post_ID) {  
        global $wpdb;  
        //删除特色图片  
        $thumbnails = $wpdb->get_results( "SELECT * FROM $wpdb->postmeta WHERE meta_key = '_thumbnail_id' AND post_id = $post_ID" );  
        foreach ( $thumbnails as $thumbnail ) {  
        wp_delete_attachment( $thumbnail->meta_value, true );  
        }  
        //删除图片附件  
        $attachments = $wpdb->get_results( "SELECT * FROM $wpdb->posts WHERE post_parent = $post_ID AND post_type = 'attachment'" );  
        foreach ( $attachments as $attachment ) {  
        wp_delete_attachment( $attachment->ID, true );  
        }  
        $wpdb->query( "DELETE FROM $wpdb->postmeta WHERE meta_key = '_thumbnail_id' AND post_id = $post_ID" );  
}  
add_action('before_delete_post', 'delete_post_and_attachments');
```

## 注意事项

当你在删除文章时先执行函数内容，删除特色图片以及图片附件，但是如果在使用 `action delete_post` 而不是 `before_delete_post` 将导致删除文章后因媒体附件与文章关联已取消而无法正确删除。

