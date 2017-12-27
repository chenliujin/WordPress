## 关闭文章版本控制
```
define('WP_POST_REVISIONS', FALSE);
```

## 分页数
添加到 wp-includes/funcitons.php

```
// 分页指定显示文章数量
function custom_posts_per_page($query){
	if(is_home()){
		$query->set('posts_per_page',5);//首页每页显示5篇文章
	}
	if(is_search()){
		$query->set('posts_per_page',-1);//搜索页显示所有匹配的文章，不分页
	}
	if(is_archive()){
		$query->set('posts_per_page',5);//archive每页显示5篇文章
	}
}

add_action('pre_get_posts','custom_posts_per_page');
```
