<!-- # Creating dynamic blocks -->
# 動的ブロックを作成する

<!-- It is possible to create dynamic blocks. These are blocks that can change their content even if the post is not saved. One example from WordPress itself is the latest posts block. This block will update everywhere it is used when a new post is published. -->
動的ブロックを作成することは可能です。 投稿が保存されていなくてもコンテンツを変更できるブロックです。 WordPress 自体の一例は、最新の投稿ブロックです。このブロックは、新しい投稿が公開されたときに、どこ使われていても更新されます。

<!-- The following code example shows how to create the latest post block dynamic block. -->
次のコード例は、最新の投稿ブロック動的ブロックを作成する方法を示します。

{% codetabs %}
{% ES5 %}
```js
// myblock.js

var el = wp.element.createElement,
	registerBlockType = wp.blocks.registerBlockType,
	withAPIData = wp.components.withAPIData;

registerBlockType( 'my-plugin/latest-post', {
	title: 'Latest Post',
	icon: 'megaphone',
	category: 'widgets',

	edit: withAPIData( function() {
		return {
			posts: '/wp/v2/posts?per_page=1'
		};
	} )( function( props ) {
		if ( ! props.posts.data ) {
			return "loading !";
		}
		if ( props.posts.data.length === 0 ) {
			return "No posts";
		}
		var className = props.className;
		var post = props.posts.data[ 0 ];
		
		return el(
			'a', 
			{ className: className, href: post.link },
			post.title.rendered
		);
	} ),

	save: function() {
		// Rendering in PHP
		return null;
	},
} );
```
{% ESNext %}
```js
// myblock.js

const { registerBlockType } = wp.blocks;
const { withAPIData } = wp.components;

registerBlockType( 'my-plugin/latest-post', {
	title: 'Latest Post',
	icon: 'megaphone',
	category: 'widgets',

	edit: withAPIData( () => {
		return {
			posts: '/wp/v2/posts?per_page=1'
		};
	} )( ( { posts, className } ) => {
		if ( ! posts.data ) {
			return "loading !";
		}
		if ( posts.data.length === 0 ) {
			return "No posts";
		}
		var post = posts.data[ 0 ];
		
		return <a className={ className } href={ post.link }>
			{ post.title.rendered }
		</a>;
	} ),

	save() {
		// Rendering in PHP
		return null;
	},
} );
```
{% end %}

<!-- Because it is a dynamic block it also needs a server component. The rendering can be added using the `render_callback` property when using the `register_block_type` function. -->
これは動的ブロックであるため、サーバーコンポーネントも必要です。 そのレンダリングは `register_block_type`関数の仕様時に` render_callback`プロパティを使って追加することができます。

```php
<?php
// block.php

function my_plugin_render_block_latest_post( $attributes ) {
	$recent_posts = wp_get_recent_posts( array(
		'numberposts' => 1,
		'post_status' => 'publish',
	) );
	if ( count( $recent_posts ) === 0 ) {
		return 'No posts';
	}
	$post = $recent_posts[ 0 ];
	$post_id = $post['ID'];
	return sprintf(
		'<a class="wp-block-my-plugin-latest-post" href="%1$s">%2$s</a>',
		esc_url( get_permalink( $post_id ) ),
		esc_html( get_the_title( $post_id ) )
	);
}

register_block_type( 'my-plugin/latest-post', array(
	'render_callback' => 'my_plugin_render_block_latest_post',
) );
```

<!-- There are a few things to notice: -->
気づくべきことがいくつかあります:

<!-- * The edit function still shows a representation of the block in the editor's context (this could be very different from the rendered version, it's up to the block's author)
* The save function just returns null because the rendering is performed server-side.
* The server-side rendering is a function taking the block attributes as an argument and returning the markup (quite similar to shortcodes) -->
* The edit function still shows a representation of the block in the editor's context (this could be very different from the rendered version, it's up to the block's author)
* 保存機能は null を返すだけです、なぜならそのレンダリングはサーバーサイドで行われているからです。
* サーバーサイドのレンダリングはブロックの属性を引数とし、（ショートコードと良く似た）マークアップを返す機能です。

<!-- ## Live rendering in Gutenberg editor -->
## Gutenberg エディタにおけるライブレンダリング

<!-- Gutenberg 2.8 added the [`<ServerSideRender>`](https://github.com/WordPress/gutenberg/tree/master/components/server-side-render) block which enables all the rendering to take place on the server using PHP rather than in JavaScript. Server-side render is meant as a fallback; client-side rendering in JavaScript is the preferred implementation. -->
Gutenberg 2.8 で[`<ServerSideRender>`](https://github.com/WordPress/gutenberg/tree/master/components/server-side-render)ブロックが追加されました、 JavaScript ではなく PHP を使用してすべてのレンダリングがサーバー上で行われるようになっています。 サーバーサイドレンダリングはフォールバックを意味します。JavaScript でのクライアント側のレンダリングが望ましい実装です。

{% codetabs %}
{% ES5 %}
```js
// myblock.js

var el = wp.element.createElement,
	registerBlockType = wp.blocks.registerBlockType,
	ServerSideRender = wp.components.ServerSideRender;

registerBlockType( 'my-plugin/latest-post', {
	title: 'Latest Post',
	icon: 'megaphone',
	category: 'widgets',

	edit: function( props ) {
		// ensure the block attributes matches this plugin's name
		return (
			el(ServerSideRender, {
				block: "my-plugin/latest-post",
				attributes:  props.attributes
			})
		);
	},

	save: function() {
		// Rendering in PHP
		return null;
	},
} );
```
{% ESNext %}
```js
// myblock.js

const { registerBlockType } = wp.blocks;
const { ServerSideRender } = wp.components;

registerBlockType( 'my-plugin/latest-post', {
	title: 'Latest Post',
	icon: 'megaphone',
	category: 'widgets',

	edit: function( props ) {
		// ensure the block attributes matches this plugin's name
		return (
			<ServerSideRender
				block="my-plugin/latest-post"
				attributes={ props.attributes }
			/>
		);
	},

	save() {
		// Rendering in PHP
		return null;
	},
} );
```
{% end %}

<!-- The PHP code is the same as above and is automatically handled through the WP REST API. -->
PHP コードは上記と同じで、WP REST API によって自動的に処理されます。
