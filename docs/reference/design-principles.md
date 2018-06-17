<!-- # Gutenberg Design Principles & Vision -->
# Gutenbergのデザイン原則とビジョン

<!-- This living document serves to describe some of the design principles and patterns that have served in designing the editor interface. The purpose is to explain the background for the design, to help inform future improvements. -->
この随時更新される文書は、エディター画面を設計する際に役立つデザイン原則とパターンのいくつかを記述するのに役立ちます。目的は、デザインの背景を説明し、今後の改善についての周知を助けることです。

![Block](https://cldup.com/7HCnN5cFc0.png)

<!-- This document will also go over how a _good block_ should be designed. -->
この文書では、どのように _適切なブロック_ をデザインするべきかということも検討していきます。

<!-- ## Goal of Gutenberg -->
## Gutenbergのゴール

<!-- The all-encompassing goal of Gutenberg is to create a post and page building experience that makes it easy to create _rich post layouts_. From the [kickoff post](https://make.wordpress.org/core/2017/01/04/focus-tech-and-design-leads/): -->
Gutenberg の包括的な目標は、 _リッチな投稿レイアウト_ を簡単に作成できる投稿とページを構築する経験を作り出すことです。[キックオフ投稿](https://make.wordpress.org/core/2017/01/04/focus-tech-and-design-leads/)より:

<!-- > The editor will endeavour to create a new page and post building experience that makes writing rich posts effortless, and has “blocks” to make it easy what today might take shortcodes, custom HTML, or “mystery meat” embed discovery. -->
> エディターは、新しいページやポストを簡単に作成し構築する経験を実現するために懸命に努力します。そのために、今日の時点では、ショートコード、カスタム HTML 、または「ミステリー・ミート」などの埋め込みの検出を容易にするためのブロックがあります。

<!-- We can extract from this the following: -->
これから以下の事が言えます :

<!--- Authoring rich posts is a key strength of WordPress.
- The block concept aims to unify multiple different interfaces under a single umbrella. You shouldn't have to write shortcodes, custom HTML or paste URLs to embed. You should only have to learn how the block works, and then know how to do everything.
- "Mystery meat" refers to hidden features in software, that you have to discover. WordPress already supports a large amount of blocks and 30+ embeds, so let's increase their visibility so people don't install plugins thinking it isn't already there. -->
- リッチな投稿を作成することは WordPress の強みのカギとなります。
- ブロックの概念は、一つの傘の下に複数の異なるインターフェースを統一することを目指しています。オブジェクトを埋め込むためにショートコードやカスタム HTML を書いたり、URL を貼り付ける必要はないのです。ブロックの仕組みを覚えるだけで、全てのやり方が分かるようになるべきです。
- 「ミステリー・ミート」とは、ソフトウェアの隠された機能を示します。それはあなたが発見しなくてはなりません。 WordPress は既に大量のブロックと30以上の埋め込みをサポートしているので、人々が既にある機能を見つけられずにプラグインをインストールしないで済むように、その視認性を高めましょう。

<!-- ## Why -->
## なぜか

<!-- One thing that sets WordPress apart from other systems is that it allows you to create as rich a post layout as you can imagine -- but only if you know HTML & CSS and build your own custom theme. By thinking of the editor as a tool to let you write rich posts, and in a few clicks create beautiful layouts, hopefully, we can make people start to love WordPress and what it can do for your content, as opposed to pick it because it installed with one click. -->
WordPress を他のシステムと区別できることの一つとして、自分で想像できるようにリッチな投稿レイアウトを作成できるということがあります -- しかしそれは HTML と CSS を理解し自分のカスタムテーマを構築出来る場合にのみ可能です。リッチな投稿を書けるツールとしてエディターを捉えることによって、数回クリックするだけで美しいレイアウトを作成できるなら、うまくいけば、人々はワンクリックでインストールできるから WordPress を選ぶのではなく、 WordPress がコンテンツのために何でも出来るから好きになってくれるようなるでしょう。

<!-- ## Vision -->
## ビジョン

<!-- **Everything is a block**. Text, images, galleries, widgets, shortcodes, and even chunks of custom HTML, no matter if it's added by plugins or otherwise. You should only have to learn to master a single interface: the block interface, and then you know how to do everything. -->
**全てをブロックにする**。 テキスト、画像、ギャラリー、ウィジェット、ショートコード、そしてカスタム HTML の塊さえも、たとえプラグインや他の方法によって追加されていたとしても、単一のインターフェイス（ブロックインターフェイス）を習得するだけで、すべての操作方法を知ることができます。

<!--**All blocks are created equal**. They all live in the same inserter interface. We use recency, search, tabs, and grouping, to ensure the blocks you use the most are easily within reach.-->
**全てのブロックを均等に作成する**。すべては同じ挿入インターフェースの中にあります。最近の投稿、検索、タブ、およびグループ化を使用して、最も多く使用するブロックを簡単に使えるようにします。

<!--**Drag and drop is additive**. Only when explicit actions (click or tab & space) exist, can we add drag and drop as an additive enhancement on top of it. -->
**ドラックアンドドロップが追加できる**。明示的なアクション（クリックまたはタブやスペース）が存在する場合にのみ、ドラッグアンドドロップを追加エンハンスメントとしてその上に追加できます。

<!-- **Placeholders are key**. If your block can have a neutral placeholder state, it should. An image placeholder block shows a button to open the media library, a text placeholder block shows a writing prompt. By embracing placeholders we can predefine editable layouts, so all you have to do is _fill in the blanks_. -->
**プレースホルダーはカギである**。ブロックが中立のプレースホルダー状態を持つことができるなら、そうすべきです。画像のプレースホルダーブロックにはメディアライブラリを開くボタンが表示され、テキストのプレースホルダーブロックには書き込みプロンプトが表示されます。プレースホルダーを使用することで編集可能なレイアウトを事前に定義することができるので、あとは _空白を埋める_ だけでよいのです。

<!-- **Direct manipulation**. The block technology we are building optimizes for the user experience of manipulating content directly on the page. Plugin and theme authors will have the ability of composing together the different tools core will provide to create their own tailored and specific blocks that give users a WYSIWYG environment for creating on the web. -->
**直接操作**。私たちが構築しているブロック技術は、ページ上で直接コンテンツを操作するユーザーエクスペリエンスを最適化します。プラグインとテーマ作成者は、ユーザーが Web 上で創作するための WYSIWYG （見たままが得られる）環境を提供する目的にぴったり合った具体的なブロックを作成するために、コアが提供するさまざまなツールを一緒に構成する能力を備えるでしょう。

<!-- **Customization**. What previously required using complicated markup and shielding users from breaking it—through shortcodes, meta-fields, etc. becomes easier and more intuitive. With blocks a developer would be able to provide a theme-specific block that directly renders a portion of a layout (a three columns grid of features, for instance) and clearly specifies what can be directly edited by the user. That means the user gets a WYSIWYG experience where they can't ruin the markup established but can easily update text, swap images, reduce the number of columns, etc, without having to ask the developer for it and without fearing that they will break things. -->
**カスタマイズ**。以前は複雑なマークアップを使用する必要があったため、ショートコードやメタフィールドなどを使用してユーザーがサイトを壊さないように保護していたことが、より簡単で直感的になります。ブロックを使用すると、開発者はレイアウトの一部（たとえば、オススメの3列グリッド）を直接レンダリングするテーマ固有のブロックを提供し、ユーザが直接編集できるものを明確に指定できます。つまり、ユーザーは WYSIWYG 経験を得ることができるのです。壊すかもしれないと恐れる必要もなく、開発者に頼まなくてもマークアップを崩さずに簡単に文書を更新したり、画像を入れ替えたり、コラムの数を減らしたりできます。

<!-- Ultimately, the vision for Gutenberg is to make it much easier to author rich content. Through ensuring good defaults, wrapping and bundling advanced layout options blocks, and making the most important actions immediately available, authoring content with WordPress should be accessible to anyone. -->
結局のところ、 Gutenberg のビジョンは、リッチなコンテンツを投稿者が簡単に作成できるようにすることです。適切なデフォルトを確保し、高度なレイアウトオプションのブロックをラップしてバンドルし、最も重要なアクションをすぐに利用できるようにすることで、誰でも WordPress でコンテンツを編集し使えるようにするべきなのです。

<!-- ## Interface Blueprints -->
## インターフェイスのブループリント

<!-- Basic editor interface: -->
基本的なエディターのインターフェイス:

![Basic Interface](https://cldup.com/NDhf6ofFmq.png)

<!-- Block interface: -->
ブロックのインターフェイス:

![Block Selected](https://cldup.com/GlUdQnu0TR.png)

<!-- Gutenberg has a basic separation between a bar at the top, and content below. -->
Gutenberg は上のバーと下のコンテンツの間に基本的な区切りがあります。

<!-- The **editor bar** holds _document level_ actions. Like editor mode, save status indicator, global actions for undo/redo/insert, the settings toggle, and finally publish options. -->
**editor bar(エディターバー)** は、 _文書レベル_ のアクションが配置されます。エディターモードと同様に、ステータスインジケーターの保存、取り消し/やり直し/挿入のためのグローバルアクション、設定の切り替え、最後にオプションの公開があります。

<!-- The **content area** holds the document itself. -->
**content area(コンテンツ領域)** は文書そのものが配置されます。

<!-- The **settings sidebar** holds document metadata. Both for the document itself (tags, categories, schedule etc.), but also for blocks in the "Block" tab. -->
**settings sidebar(設定サイドバー)** は文書のメタデータが配置されます。どちらも文書そのもの（タグ、カテゴリ、スケジュールなど）のデータだけでなく、「ブロック」タブのブロックも対象となります。

<!-- On mobile, the sidebar is hidden until you click the cog button to open it. On a desktop you can dismiss it for an immersive writing experience. -->
モバイルでは、歯車ボタンをクリックするまでサイドバーは非表示になります。デスクトップでは書くことに集中するためにそれを隠すことができます。

<!-- ## The Block Interface -->
## ブロックのインターフェイス

<!-- The block itself is the most basic unit of the editor. Everything is a block, and you build them together mimicking the vertical flow of the underlying HTML markup. By surfacing each section of the document as a block we can manipulate, we can attach features that are unique to each block, contextually. Inspired by desktop layout apps, it's a way to add a breadth of advanced features without weighing down the UI. -->
ブロック自体がエディターの最も基本的な単位です。全てはブロックであり、基礎である HTML マークアップの垂直なフローを模倣して構築されます。文書の各セクションを操作可能なブロックとして表示させることで、各ブロックに文脈上、固有の機能を付与できます。これはデスクトップのレイアウトアプリから着想を得たもので、UIに重荷を追わせることなく、高度な機能の拡張を追加するための方法です。

<!-- The block interface holds _basic actions_. Through ensuring good defaults, and only the most common actions, you should be able to get all your blogging done without ever having to use the Settings sidebar. -->
このブロックのインターフェイスは _基本的なアクション_ を持ちます。適切なデフォルトを保証し、最も一般的なアクションのみを使用することで、設定サイドバーを使用せずにブログを書くこと全てを完了できるようにするべきです。

<!-- The block itself has multiple states: -->
ブロック自体には複数の状態があります:

<!-- - An _unselected block_ is the closest thing to a live preview of the contents itself.
- A _selected block_ shows the "quick toolbar", direct actions that manipulate the block. Extra elements can also be surfaced in the block content itself. For example an image block surfaces a caption field, a quote surfaces a citation field, and dynamic blocks can surface buttons to let you add form fields. -->
- _選択されていないブロック_ は、コンテンツ自体のライブプレビューに最も近いものです。
- _選択されたブロック_ には、「クイックツールバー」が表示され、ブロックを操作する直接アクションが表示されます。特別な要素もブロックコンテンツ自体に表示されます。たとえば、画像ブロックにはキャプションフィールドが表示され、引用符には引用フィールドが表示され、ダイナミックブロックにはフォームフィールドを追加するためのボタンが表示されます。

<!-- Note that _selection_ and _focus_ can be different, i.e. an image block can be selected but the focus can be on the caption field, exposing extra (caption-specific) UI. -->
注釈 _選択_ と _フォーカス_ は異なります。つまり、イメージブロックは選択できますがそのフォーカスはキャプションフィールドにあり、特別な（キャプション固有の）UIが表示されます。

<!-- As you scroll down a page on long blocks, the quick toolbar unsticks from the block, and sticks to the top of the screen. -->
長いブロックのページを下にスクロールすると、クイックツールバーがブロックから外れ、画面の上部に張り付きます。

<!-- ## Editor Settings -->
## エディターの設定

<!-- If your block needs advanced configuration, those live in the Settings sidebar. Editor block settings can also be reached directly by clicking the cog icon next to a block. -->
ブロックに高度な設定が必要な場合は、設定サイドバーに表示されます。エディターのブロック設定は、そのブロックの隣にある歯車アイコンをクリックして直接行うこともできます。

<!-- The sidebar has two tabs, Document and Block: -->
サイドバーには文書とブロックの2つのタブがあります。

<!-- - The "Document" tab shows metadata and settings for the post or page being edited.
- The "Block" tab shows metadata and settings for the currently selected block. -->
- 「文書」タブには編集している投稿やページのメタデータと設定が表示されます。
- 「ブロック」タブには現在選択されているブロックのメタデータと設定が表示されます。

<!-- Don't put anything in the sidebar "Block" tab that is necessary for the basic operation of your block. Your user might dismiss the sidebar for an immersive writing experience. So pick good defaults, and make important actions available in the quick toolbar. -->
サイドバーの「ブロック」タブには、ブロックの基本操作に必要なものは置かないでください。ユーザーは書くことに集中するためにサイドバーを隠すかもしれません。 したがって、適切なデフォルトを選択し、クイックツールバーで重要なアクションを利用できるようにします。

<!-- Examples of actions that could go in the "Block" tab of the sidebar could be: -->
サイドバーの「ブロック」タブに表示されるアクションの例:

<!-- - drop cap for text
- number of columns for galleries
- number of posts, or category, in the "Latest Posts" block
- any configuration that you don't _need_ access to in order to perform basic tasks -->
- テキストのドロップキャップ
- ギャラリーの列の数
- 「最新の投稿」ブロック内での、投稿数やカテゴリー数
- 基本的なタスクを実行するためにアクセスする _必要_ のない設定

<!-- ## Block Design Checklist, Do's and Don'ts, and Examples -->
## ブロックデザインのチェックリスト、すべきこととすべきでないこと、事例

<!-- The following is a list of blocks and which options go where. If you're developing a new block, hopefully this can help suggest where to put an option. -->
以下は、ブロックと、どのオプションがどこにあるかのリストです。 新しいブロックを開発している場合は、これがオプションを配置する場所を示唆するのに役立つでしょう。

<!-- This is the basic recipe for a block: -->
これがブロックの基本的なレシピです:

<!-- - It should have a nice icon and label for the Inserter. Keep it simple.
- When you insert it, it should have a good placeholder state. If it's meant for text input, provide good placeholder text. If it's meant to hold media, have buttons for uploading or accessing media libraries, drop-zones for drag and drop, or anything else. The placeholder state will be used to make page and post templates in the future.
- Your block when unselected should preview its contents.
- Your block when selected can surface additional options, like input fields, or — if necessary for basic operation — buttons to configure the block directly.
- Every block should, at minimum, show a description in the "Block" tab of the Settings sidebar. You can access this for any block by clicking the cog next to the selected block.
- Additional block options and configuration can be added to the "Block" tab, but keep in mind a user might dismiss the sidebar and never use it, so you can't put configuration critical to the block here. -->
- ブロックの挿入ツールには素敵なアイコンとラベルを付けるべきです。出来るだけシンプルに。
- ブロックを挿入した時には、適切なプレースホルダーの状態を持たせるべきです。テキストの入力の場合は、適切なプレースホルダーのテキストを表示してください。メディアを表示する場合は、メディアライブラリへアップロードまたはアクセスするためのボタンや、ドラッグアンドドロップのドロップゾーンなどを持たせてください。プレースホルダーの状態は、将来、ページや投稿のテンプレートを作成するために使用されるでしょう。
- 未選択時のブロックにはそのコンテンツがプレビューされるべきです。
- 選択時のブロックには、入力フィールドなどの、追加のオプションが表示されます。または — 基本的操作にとって必要ならば — ブロックを直接設定するためのボタンが表示されます。
- 全てのブロックには、設定サイドバーの「ブロック」タブに最低限の説明を表示させるべきです。選択しているブロックの横の歯車をクリックすることで、どのブロックのものにもアクセスできます。
- 追加ブロックのオプションと設定を「ブロック」タブにも追加することが出来ますが、ユーザーはサイドバーを隠してしまうかもしれませんし一度も使わないかもしれないことを忘れないでください。そのため、ブロックにとって重要な設定はここに置けません。

<!-- Here are a couple of block examples, describing which options go where, and why. -->
以下にブロックの例を幾つかと、どのオプションがどこに行くか、其の理由を書き出します。

<!-- ### Text -->
### テキスト

<!-- The most basic unit of the editor. Text is a simple input field. -->
エディターの最も基本的な単位です。テキストはシンプルな入力フィールドです。

<!-- Placeholder: -->
プレースホルダー:

<!-- - Simple placeholder text that says "New Paragraph". -->
- 「新しい段落」というシンプルなプレースホルダーのテキスト

<!-- Selected state: -->
選択された状態:

<!-- - Quick Toolbar: Has a switcher to perform transformations to headings, etc.
- Quick Toolbar: Has basic text alignments
- Quick Toolbar: Has inline formatting options, bold, italic, strikethrough and link -->
- クイックツールバー: 見出しなどへの変換を実行するための切り替えツールを備えています
- クイックツールバー: 基本的なテキストの配置を備えています
- クイックツールバー: 太字、イタリック、取り消し線やリンクといったインラインの書式設定オプションを備えています

<!-- Editor block settings: -->
エディターブロックの設定:

<!-- - Has description: "This is a simple text only block for inserting a single paragraph of content."
- Has option to enable or disable a drop-cap. Note that the drop-cap is only visible in the blocks unselected (preview) state. -->
- 「コンテンツに段落を追加するためのシンプルなテキストのみのブロックです。」という説明があります。
- ドロップキャップを有効または無効にするオプションがあります。 ドロップキャップは、選択されていない（プレビュー）状態のブロックでのみ表示されます。

<!-- _Because the drop-cap feature is not critical to the basic operation of the block, it's in the advanced sidebar, thus keeping the Quick Toolbar light-weight._ -->
_ドロップキャップ機能はブロックの基本操作には重要ではないため、拡張されたサイドバーにあり、クイックツールバーを軽くしています。_

<!-- ### Image -->
### 画像

<!-- Basic image block. -->
基本的な画像のブロック。

<!-- Placeholder: -->
プレースホルダー:

<!-- - A generic gray placeholder block with options to upload an image, drop an image directly on it, or pick an image from the media library. The placeholder block can be laid out as if it was an actual image, and this layout persists when a user adds an actual image into it. -->
- 画像をアップロードしたり、画像を直接ドロップしたり、メディアライブラリから画像を選択したりするためのオプションを備えた包括的なグレーのプレースホルダーのブロックです。 このプレースホルダーのブロックは、実際の画像のようにレイアウトすることができ、ユーザーが実際の画像を追加してもこのレイアウトが維持されます。

<!-- Selected state: -->
選択された状態:

<!-- - Quick Toolbar: Alignments, including wide and full-wide (if the theme supports it).
- Quick Toolbar: Edit Gallery (opens media library)
- Quick Toolbar: Link button
- A caption input field appears with a "Write caption..." placeholder text below the image -->
- クイックツールバー： ワイドおよびフルワイド（テーマでサポートされている場合）などの配置。
- クイックツールバー： ギャラリーの編集（メディアライブラリを開く）
- クイックツールバー： リンクボタン
- キャプション入力フィールドが表示され、画像の下に「キャプションを入力...」というプレースホルダテキストが表示されます

<!-- Editor block settings: -->
エディターブロックの設定:

<!-- - Has description: "Worth a thousand words."
- Has options for changing or adding `alt` text, and adding additional custom CSS classes. -->
- 「千の言葉に値する。」という説明があります。
- `alt` テキストを変更または追加するオプションと、カスタムCSSクラスを追加するオプションがあります。

<!-- _Future improvements to the Image block could include getting rid of the media modal, in place of letting you select images directly from the placeholder itself. In general, try to avoid modals._ -->
_画像ブロックの今後の改善点としては、プレースホルダ自体から直接イメージを選択させる代わりに、メディアのモーダル画面を取り除くことなどがあります。 一般的に、モーダル画面を避けるようにしてください。_

<!-- ### Latest Posts -->
### 最新の投稿

<!-- Placeholder: -->
プレースホルダー:

<!-- - Has no placeholder, as it works fine upon insertion. The default inserted state shows the last 5 posts. -->
- プレースホルダーはなく、挿入時に正常に動作します。デフォルトの挿入された状態では最新5件の投稿を表示します。

<!-- Selected state: -->
選択された状態:

<!-- - Quick Toolbar: Alignments
- Quick Toolbar: Options for picking list view or grid view -->
- クイックツールバー: 配置
- クイックツールバー: リストビューかグリットビューかを選択するオプション

<!-- Editor block settings: -->
エディターブロックの設定:

<!-- - Has description: "Shows a list of your site's most recent posts."
- Has options for showing the post date, changing the default number of posts to show, and an option for adding an additional CSS class. -->
- 「あなたのサイトで最も最近の投稿のリストを表示します」という説明があります。
- 投稿日を表示したり、デフォルトの表示数を変更したり、追加 CSS のクラスを追加できるオプションがあります。

<!-- _Latest Posts is fully functional as soon as you insert it, because it comes with good defaults._ -->
_挿入するとすぐに、最新の投稿は完全に機能します。なぜなら、それは良いデフォルトが付いているからです。_

<!-- ### Contact Form -->
### お問合わせフォーム

<!-- Placeholder: -->
プレースホルダー:

<!-- - Has no placeholder, as the default inserted state shows a functional contact form. -->
- プレースホルダはなく、デフォルトの挿入状態には機能するお問合わせフォームが表示されます。

<!-- Selected state: -->
選択された状態:

<!-- - Quick Toolbar: Alignments
- Shows "Remove" buttons next to fields that can be removed.
- Shows an "Add field" button, which opens a popout where you can select additional contact field options. -->
- クイックツールバー: 配置
- 削除できるフィールドの横に「削除」ボタンが表示されます。
- 「フィールドを追加」ボタンが表示され、追加の連絡先フィールドのオプションを選択できるポップアップが開きます。

<!-- Editor block settings: -->
エディターブロックの設定:

<!-- - Has description: "A basic contact form."
- Has options for making email address mandatory, checked by default.
- Has options for changing the form ID/name, in case you have multiple forms on a page. -->
- 「基本的なお問合わせフォーム」という説明があります。
- 電子メールアドレスを必須にするためのオプションがあり、デフォルトでチェックされています。
- １ページに複数のフォームがある場合に備えて、フォームIDまたは名前を変更するオプションがあります。

<!-- _Note: this block doesn't exist in Gutenberg currently, but the above describes a "best practices" for designing such a block. Being one of the more complex blocks, it's still important that it is fully functional upon insertion, helped along by good defaults._ -->
_注釈: このブロックは現在 Gutenberg には存在しませんが、上記ではこのようなブロックをデザインするための「ベストプラクティス」について説明しています。より複雑なブロックの1つで、挿入時に完全に機能することが重要であり、適切なデフォルトによって助けられています。_

<!-- ## Future Opportunities -->
## 今後の改善

<!-- Gutenberg as part of the kickoff goal is primarily limited to the confines of the _content area_ (specifically `post_content`) of posts and pages. Within those confines, we are embracing the web as a vertical river of content, by appending blocks sequentially, then adding layout options to each block. -->
キックオフ目標の一環としての Gutenberg は、主に、投稿とページの _コンテンツ領域_ （特に `post_content` ）の範囲に限定されています。 これらの領域内では、ブロックを順次に追加することによって、コンテンツの垂直な流れとして Web を取り入れています。そして、各ブロックにレイアウトオプションを追加しています。

<!-- But just like how the verticality of the web itself doesn't prevent more advanced layouts from being possible, similarly there isn't any fixed limit to the kind of layout Gutenberg will be able to accomplish. As such, it's very possible for Gutenberg to grow beyond the confines of post and page _content_, to include the whole page, including everything that surrounds the content. -->
しかし、 Web 自体の垂直性がより高度なレイアウトを可能にしないように、 Gutenberg が達成できるレイアウトの種類には一定の制限はありません。 そのため、 Gutenberg は、投稿やページ _コンテンツ_ の範囲を超えて、コンテンツを囲むすべてを含め、ページ全体を含めて、発展することが限りなく可能なのです。

<!-- One way to think of it is a theme template being just a comma separated list of blocks, like this: -->
それを考える方法の1つは、次のような、カンマで区切られただけのブロックのリストであるテーマテンプレートです:

```{
{
  'themename/header',
  'themename/sidebar',
  'core/content' {
    'core/cover-image',
    'themename/author-card',
    'core/text',
  },
  'themename/footer',
}
```

<!-- Every block nested inside the _content_ block would be _rearrangable_. Every block would be _editable_. Every block would be built using the same API, and both the editor and the theme would load the same `style.css` file directly. In the end you'd see the same in the editor/page builder, as you would looking at the theme/front-end itself. -->
_コンテンツ_ ブロック内にネストされたすべてのブロックは _再配置可能_ です。すべてのブロックは _編集可能_ です。すべてのブロックは同じ API を使用して作成され、エディターとテーマの両方が同じ `style.css` ファイルを直接ロードします。最終的には、テーマもしくはフロントエンド自体を見ているように、エディターもしくはページビルダーでも同じように見えるようになるでしょう。

<!-- *Page Templates*. Since blocks have empty states, it becomes easy to imagine theme templates being a declaration of which blocks compose a given page. These blocks would naturally guide a user to fill the information necessary to achieve what the theme promises it can deliver — it's very common that users struggle to mimic the theme demo that caught their attention. These templates could function similarly to apps like Keynote, where you can choose a specific template when creating a new page and have content blocks already laid out to help you achieve specific looks. -->
*ページテンプレート* 。ブロックが空の状態から、テーマテンプレートはブロックが与えられたページを構成する宣言であると想像しやすくなります。これらのブロックは、自然に、提供できるテーマを達成するために必要な情報を入力するようにユーザーを誘導します — ユーザーが注目したテーマデモを模倣するのは非常に一般的です。これらのテンプレートは、Keynote のようなアプリケーションと同様に機能するでしょう、それは新しいページを作成するときに特定のテンプレートを選択し、特定の外観を実現するためにコンテンツのブロックが既にレイアウトされています。

<!-- This concept is speculative, but it's one direction Gutenberg could go in the future. -->
この概念は思索的なものですが、将来的に Gutenberg が到達できるひとつの方向です。

<!-- ## More resources -->
## その他のリソース

<!-- If you'd like to contribute, you can download a Sketch file of the Gutenberg mockups. Note that those are still mockups, and not 1:1 accurate. It is also possible that the Sketch files aren't up-to-date with the latest Gutenberg itself, as development sometimes moves faster than our updating of the Sketch files! -->
あなたが貢献したい場合は、 Gutenberg モックアップの Sketch ファイルをダウンロードすることができます。それらはまだモックアップであり、正確な1：1ではないことに注意してください。 Sketch ファイルの更新よりも速く開発が進むことがあるため、 Sketch ファイルは最新の Gutenberg 自体にとって最新ではない可能性もあります!

<!-- **<a href="https://cloudup.com/c8Rbgsgg3nq">Download Sketch mockups & patterns files</a>**. -->
**<a href="https://cloudup.com/c8Rbgsgg3nq">Sketch のモックアップとパターンファイルをダウンロードする</a>**。

<!-- Be sure to also read <a href="https://wordpress.org/gutenberg/handbook/reference/faq/">the FAQ</a>, and <a href="https://wordpress.org/gutenberg/handbook/">how to build blocks</a>. -->
<a href="https://wordpress.org/gutenberg/handbook/reference/faq/">FAQ</a> や <a href="https://wordpress.org/gutenberg/handbook/">ブロックの作成方法</a> も合わせてお読みください。
