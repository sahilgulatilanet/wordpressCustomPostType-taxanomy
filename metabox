/**
 * Custom meta boxes
 */
//adding meta boxes
add_action( 'add_meta_boxes', 'cd_meta_box_add' );
function cd_meta_box_add()
{
    add_meta_box( 'my-meta-box-id', 'My First Meta Box', 'cd_meta_box_cb', array('post','movies'), 'normal', 'high' );
}
//
function cd_meta_box_cb($object)
{
    ?>
    <label for="meta-box-text">Text Label</label>
    <input type="text" name="meta-box-text" id="meta-box-text" value="<?php echo get_post_meta($object->ID, "meta-box-text", true); ?>" />
    <?php
}
//saving it to database
add_action( 'save_post', 'cd_meta_box_save' );
function cd_meta_box_save( $post_id )
{
    // Bail if we're doing an auto save
    if( defined( 'DOING_AUTOSAVE' ) && DOING_AUTOSAVE ) return;

    // if our nonce isn't there, or we can't verify it, bail
    if( !isset( $_POST['meta_box_nonce'] ) || !wp_verify_nonce( $_POST['meta_box_nonce'], 'my_meta_box_nonce' ) ) return;

    // if our current user can't edit this post, bail
    //if( !current_user_can( 'edit_post' ) ) return;
    if(isset($_POST["meta-box-text"]))
    {
        $meta_box_text_value = $_POST["meta-box-text"];
    }
    update_post_meta($post_id, "meta-box-text", $meta_box_text_value);
}
