# FiLLTering Plugin
Wordpress Ajax Filtering Plugin


## HTML
### Classes Needed

|Classes					|    																		|
|---------------------------|---------------------------------------------------------------------------|
|.filltering-holder         | This is the container to hold all overlay and container                   |
|.fillter-ajax-overlay      | This is the overlay for while the ajax is loading                         |
|.fillter-ajax-animation    | This is the animation that runs in the overlay while the ajax is loading  |
|.fillter-ajax-container    | This is the container that receives the posts when ajax is completed      |
|.fillter-ajax-load         | This is the button that will load more posts                              |
|.fillter-ajax-form         | This is the container that receives the posts when ajax is completed      |

#### Examples

AJAX HTML Loading, Container, and Load More
```
<div class="filltering-holder">
	<div class="fillter-ajax-overlay">
		<div class="fillter-ajax-animation"></div>
	</div>
	<div class="fillter-ajax-container">
        <!-- Where the posts will be appended -->
	</div>
    <a class="button fillter-ajax-load">load more</a>
</div>
```


AJAX HTML Form to customize WP Query
```
<form class="fillter-ajax-form" action="portfolio" method="post">
	<input type="hidden" name="query-post_type" value="custom_post_type">
	<input type="hidden" name="query-post_status" value="publish">
	<input type="hidden" name="query-posts_per_page" value="6">
	<input type="hidden" name="query-paged" value="1">
	<input type="hidden" name="query-orderby" value="menu_order title">
	<input type="hidden" name="query-order" value="DESC">
</form>
```
***

## PHP
|Hooks					|								|
|-----------------------|-------------------------------|
|fillter_post_content	| Ajax Loop Post Content Action |
|fillter_post_no_content| Ajax Loop No Posts Content 	|

#### Examples

fillter_post_content
```
add_action('fillter_post_content', 'post_type_content');
function post_type_content() {
	get_template_part('content', 'post-type');
}
```

fillter_post_no_content
```
add_action('fillter_post_no_content', 'post_type_no_content');
function post_type_no_content() {
	echo '<p>No Posts To Display</p>';
}
```

|Filters			|						|
|-------------------|-----------------------|
|fillter_post_args  | Modify WP Query Args  |

#### Examples

fillter_post_args
```
add_filter( 'fillter_post_args', 'post_type_query_args', 10, 1);
function post_type_query_args($args){

	// Modify query args

	return $args;
}
```

***

## JavaScript

|Events				|				|
|-------------------|---------------|
|fillter-successful |On Ajax Appended|

#### Examples
```
$('div.fillter-ajax-container').on('fillter-successful', function(){

	// Manipulate Appended Items, or bind JS to items

});
```

***