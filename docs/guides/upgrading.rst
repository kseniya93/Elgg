Upgrading Plugins
#################

Prepare your plugin for the next version of Elgg.

See the administrator guides for :doc:`how to upgrade a live site </admin/upgrading>`.

.. contents:: Contents
   :local:
   :depth: 2

From 2.x to 3.0
===============

Removed views
-------------

 * ``resources/file/download`` 
 * ``output/checkboxes``: use ``output/tags`` if you want the same behaviour
 * ``input/write_access``: mod/pages now uses the **access:collections:write** plugin hook.
 * ``invitefriends/form``
 * ``page/layouts/content``: use ``page/layouts/default``
 * ``page/layouts/one_column``: use ``page/layouts/default``
 * ``page/layouts/one_sidebar``: use ``page/layouts/default``
 * ``page/layouts/two_sidebar``: use ``page/layouts/default``
 * ``page/layouts/walled_garden``: use ``page/layouts/default``
 * ``page/layouts/walled_garden/cancel_button``
 * ``page/layouts/two_column_left_sidebar``
 * ``page/layouts/widgets/add_panel``
 * ``groups/group_sort_menu``: use ``register, filter:menu:groups/all`` plugin hook
 * ``subscriptions/form/additions``: extend ``notifications/settings/other`` instead
 * ``messageboard/css``
 * ``notifications/subscriptions/personal``
 * ``notifications/subscriptions/collections``
 * ``notifications/subscriptions/form``
 * ``notifications/subscriptions/jsfuncs``
 * ``notifications/subscriptions/forminternals``
 * ``notifications/css``
 * ``admin.js``
 * ``aalborg_theme/homepage.png``
 * ``aalborg_theme/css``
 * ``resources/avatar/view``: Use entity icon API
 * ``ajax_loader.gif``
 * ``button_background.gif``
 * ``button_graduation.png``
 * ``elgg_toolbar_logo.gif``
 * ``header_shadow.png``
 * ``powered_by_elgg_badge_drk_bckgnd.gif``
 * ``powered_by_elgg_badge_light_bckgnd.gif``
 * ``sidebar_background.gif``
 * ``spacer.gif``
 * ``toptoolbar_background.gif``
 * ``two_sidebar_background.gif``
 * ``ajax_loader_bw.gif``: use ``graphics/ajax_loader_bw.gif``
 * ``elgg_logo.png``: use ``graphics/elgg_logo.png``
 * ``favicon-128.png``: use ``graphics/favicon-128.png``
 * ``favicon-16.png``: use ``graphics/favicon-16.png``
 * ``favicon-32.png``: use ``graphics/favicon-32.png``
 * ``favicon-64.png``: use ``graphics/favicon-64.png``
 * ``favicon.ico``: use ``graphics/favicon.ico``
 * ``favicon.svg``: use ``graphics/favicon.svg``
 * ``friendspicker.png``: use ``graphics/friendspicker.png``
 * ``walled_garden.jpg``: use ``graphics/walled_garden.jpg``
 * ``core/friends/collection``
 * ``core/friends/collections``
 * ``core/friends/collectiontabs``
 * ``core/friends/tablelist``
 * ``core/friends/talbelistcountupdate``

Removed functions/methods
-------------------------

All the functions in ``engine/lib/deprecated-1.9.php`` were removed. See https://github.com/Elgg/Elgg/blob/2.0/engine/lib/deprecated-1.9.php for these functions. Each ``@deprecated`` declaration includes instructions on what to use instead.
All the functions in ``engine/lib/deprecated-1.10.php`` were removed. See https://github.com/Elgg/Elgg/blob/2.0/engine/lib/deprecated-1.10.php for these functions. Each ``@deprecated`` declaration includes instructions on what to use instead.

 * ``_elgg_manage_pagesetup``
 * ``datalist_get``
 * ``datalist_set``
 * ``developers_setup_menu``
 * ``elgg_get_metastring_id``
 * ``elgg_get_metastring_map``
 * ``get_default_filestore``
 * ``garbagecollector_orphaned_metastrings``
 * ``groups_setup_sidebar_menus``
 * ``set_default_filestore``
 * ``generate_user_password``: Use ``ElggUser::setPassword``
 * ``row_to_elggrelationship``
 * ``run_function_once``: Use ``Elgg\Upgrade\Batch`` interface
 * ``system_messages``
 * ``notifications_plugin_pagesetup``
 * ``elgg_format_url()``: Use elgg_format_element() or the "output/text" view for HTML escaping.
 * ``ElggEntity::addToSite``
 * ``ElggEntity::getSites``
 * ``ElggEntity::removeFromSite``
 * ``ElggFile::setFilestore``: ElggFile objects can no longer use custom filestores.
 * ``ElggFile::size``: Use ``getSize``
 * ``ElggDiskFilestore::makeFileMatrix``: Use ``Elgg\EntityDirLocator``
 * ``ElggData::get``: Usually can be replaced by property read
 * ``ElggData::getClassName``: Use ``get_class()``
 * ``ElggData::set``: Usually can be replaced by property write
 * ``ElggEntity::setURL``: See ``getURL`` for details on the plugin hook
 * ``ElggFileCache::sanitise_filename``: Use ``sanitizeFilename``
 * ``ElggMenuBuilder::compareByWeight``: Use ``compareByPriority``
 * ``ElggMenuItem::getWeight``: Use ``getPriority``
 * ``ElggMenuItem::getContent``: Use ``elgg_view_menu_item()``
 * ``ElggMenuItem::setWeight``: Use ``setPriority``
 * ``ElggRiverItem::getPostedTime``: Use ``getTimePosted``
 * ``ElggSession`` has removed all deprecated methods
 * ``ElggSite::addEntity``
 * ``ElggSite::addObject``
 * ``ElggSite::addUser``
 * ``ElggSite::getEntities``: Use ``elgg_get_entities_from_relationship()``
 * ``ElggSite::getExportableValues``: Use ``toObject``
 * ``ElggSite::getMembers``: Use ``elgg_get_entities_from_relationship()``
 * ``ElggSite::getObjects``: Use ``elgg_get_entities_from_relationship()``
 * ``ElggSite::listMembers``: Use ``elgg_list_entities_from_relationship()``
 * ``ElggSite::removeEntity``
 * ``ElggSite::removeObject``
 * ``ElggSite::removeUser``
 * ``ElggSite::isPublicPage``: Logic moved to the router and should not be accessed directly
 * ``ElggSite::checkWalledGarden``: Logic moved to the router and should not be accessed directly
 * ``ElggUser::countObjects``: Use ``elgg_get_entities()``
 * ``Logger::getClassName``: Use ``get_class()``
 * ``Elgg\Application\Database::getTablePrefix``: Read the ``prefix`` property
 * ``elgg_view_access_collections()``
 * ``ElggSession::get_ignore_access``: Use ``getIgnoreAccess``
 * ``ElggSession::set_ignore_access``: Use ``setIgnoreAccess``
 * ``profile_pagesetup``
 * ``groups_setup_sidebar_menus``
 * ``groups_set_icon_url``

Removed global vars
-------------------

 * ``$DEFAULT_FILE_STORE``
 * ``$ENTITY_CACHE``
 * ``$SESSION``: Use the API provided by ``elgg_get_session()``
 * ``$CONFIG->site_id``: Use ``elgg_get_config('site_guid')`` or ``elgg_get_site_entity()->guid``
 * ``$CONFIG->search_info``

Removed classes/interfaces
--------------------------

 * ``FilePluginFile``: replace with ``ElggFile`` (or load with ``get_entity()``)
 * ``Elgg_Notifications_Notification``
 * ``Elgg\Database\EntityTable\UserFetchResultException.php``
 * ``Elgg\Database\MetastringsTable``
 * ``Exportable`` and its methods ``export`` and ``getExportableValues``: Use ``toObject``
 * ``ExportException``
 * ``Importable`` and its method ``import``.
 * ``ImportException``
 * ``ODD`` and all classes beginning with ``ODD*``.
 * ``XmlElement``
 
Schema changes
--------------
 
The storage engine for the database tables has been changed from MyISAM to InnoDB. You maybe need to optimize your database settings for this change.
The ``datalists`` table has been removed. All settings from datalists table have been merged into the ``config`` table.

Metastrings in the database have been denormalized for performance purposes. We removed the metastrings table and put all the string values directly in the 
metadata and annotation tables. You need to update your custom queries to reflect these changes. Also the ``msv`` and ``msn`` table aliases are no longer available.
It is best practice not to rely on the table aliases used in core queries. If you need to use custom clauses you should do your own joins.

Multi Site Changes
------------------

Pre 3.0 Elgg has some (partial) support for having multiple sites in the same database. This Multi Site concept has been completely removed in 3.0.
Entities no longer have the site_guid attribute. This means there is no longer the ability to have entities on different sites.
If you currently have multiple sites in your database, upgrading Elgg to 3.0 will fail. 
You need to separate the different sites into separate databases/tables.

Related to the removal of the Multi Site concept in Elgg, there is no longer a need for entities having a 'member_of_site' relationship with the Site Entity.
All functions related to adding/removing this relationship has been removed. All existing relationships will be removed as part of this upgrade. 

Search changes
--------------

The FULLTEXT indices have been removed on various tables. The search plugin will now always use a like query when performing a search.

 * ``search_get_where_sql`` no longer supports the argument ``use_fulltext``
 * ``search_get_ft_min_max`` function is removed
 * ``$CONFIG->search_info`` is no longer provided

Form and field related changes
------------------------------

 * ``input/password``: by default this field will no longer show a value passed to it, this can be overridden by passing the view var ``always_empty`` and set it to false
 * ``input/submit``, ``input/reset`` and ``input/button`` are now rendered with a ``<button>`` instead of the ``<input>`` tag. These input view also accept ``text`` and ``icon`` parameters.
 * ``output/url`` now sets ``.elgg-anchor`` class on anchor elements and accepts ``icon`` parameter. If no ``text`` is set, the ``href`` parameter used as a label will be restricted to 100 characters.
 * ``output/url`` now supports a ``badge`` parameter, which can be used where a counter, a badge, or similar is required as a postfix (mainly in menu items that have counters).
 * ``output/tags`` no longer uses ``<ul>`` tags with floats and instead it relies on inherently inline elements such as ``<span>`` and ``<a>``

Removed libraries
-----------------

 * ``elgg:discussion``

Removed pagehandling
--------------------

 * ``file/download``
 * ``groupicon``
 * ``twitterservice``
 * ``collections/pickercallback``

Removed actions
---------------

 * ``file/download``: Use ``elgg_get_inline_url`` or ``elgg_get_download_url``
 * ``import/opendd``
 
Inheritance changes
-------------------

 * ``ElggData`` (and hence most Elgg domain objects) no longer implements ``Exportable``
 * ``ElggEntity`` no longer implements ``Importable``
 * ``ElggGroup`` no longer implements ``Friendable``
 * ``ElggRelationship`` no longer implements ``Importable``
 * ``ElggSession`` no longer implements ``ArrayAccess``
 * ``Elgg\Application\Database`` no longer extends ``Elgg\Database``

Removed JavaScript APIs
-----------------------

 * ``admin.js``
 * ``elgg.widgets``: Use the ``elgg/widgets`` module. The "widgets" layouts do this module automatically
 * ``lightbox.js``: Use the ``elgg/lightbox`` module as needed
 * ``lightbox/settings.js``: Use the ``getOptions, ui.lightbox`` JS hook or the ``data-colorbox-opts`` attribute
 * ``elgg.ui.popupClose``: Use the ``elgg/popup`` module
 * ``elgg.ui.popupOpen``: Use the ``elgg/popup`` module
 * ``elgg.ui.initAccessInputs``
 * ``elgg.ui.river``
 * ``elgg.ui.initDatePicker``: Use the ``input/date`` module
 * ``elgg.ui.likesPopupHandler``
 * ``elgg.embed``: Use the ``elgg/embed`` module
 * ``embed/custom_insert_js``: Use the ``embed, editor`` JS hook
 * ``elgg/ckeditor/insert.js``
 * ``likes.js``: The ``elgg/likes`` module is loaded automatically
 * ``messageboard.js``
 * ``elgg.autocomplete`` is no longer defined.
 * ``elgg.messageboard`` is no longer defined.
 * ``jQuery.fn.friendsPicker``

Removed hooks/events
--------------------

 * Event **login, user**: Use **login:before** or **login:after**. Note the user is not logged in during the **login:before** event.
 * Event **delete, annotations**: Use **delete, annotation**
 * Event **pagesetup, system**: Use the menu or page shell hooks instead.
 * Hook **index, system**: Override the ``resources/index`` view
 * Hook **object:notifications, <type>**: Use the hook **send:before, notifications**
 * Hook **output:before, layout**: Use **view_vars, page/layout/<layout_name>**
 * Hook **output:after, layout**: Use **view, page/layout/<layout_name>**

Removed forms/actions
---------------------

 * ``notificationsettings/save`` form and action
 * ``notificationsettings/groupsave`` form and action

APIs that now accept only an ``$options`` array
-----------------------------------------------

 * ``ElggEntity::getAnnotations``
 * ``ElggEntity::getEntitiesFromRelationship``
 * ``ElggGroup::getMembers``
 * ``ElggUser::getGroups``
 * ``ElggUser::getFriends`` (as part of ``Friendable``)
 * ``ElggUser::getFriendsOf`` (as part of ``Friendable``)
 * ``ElggUser::getFriendsObjects`` (as part of ``Friendable``)
 * ``ElggUser::getObjects`` (as part of ``Friendable``)
 * ``find_active_users``

Plugin functions that now require an explicit ``$plugin_id``
------------------------------------------------------------

 * ``elgg_get_all_plugin_user_settings``
 * ``elgg_set_plugin_user_setting``
 * ``elgg_unset_plugin_user_setting``
 * ``elgg_get_plugin_user_setting``
 * ``elgg_set_plugin_setting``
 * ``elgg_get_plugin_setting``
 * ``elgg_unset_plugin_setting``
 * ``elgg_unset_all_plugin_settings``

Class constructors that now accept only a ``stdClass`` object or ``null``
-------------------------------------------------------------------------

 * ``ElggAnnotation``: No longer accepts an annotation ID
 * ``ElggGroup``: No longer accepts a GUID
 * ``ElggMetadata``: No longer accepts a metadata ID
 * ``ElggObject``: No longer accepts a GUID
 * ``ElggRelationship``: No longer accepts a relationship ID or ``null``
 * ``ElggSite``: No longer accepts a GUID or URL
 * ``ElggUser``: No longer accepts a GUID or username

Miscellaneous API changes
-------------------------

 * ``ElggBatch``: You may only access public properties
 * ``ElggEntity``: The ``tables_split`` and ``tables_loaded`` properties were removed
 * ``ElggEntity``: Empty URLs will no longer be normalized. This means entities without URLs will no longer result in the site URL
 * ``ElggGroup::removeObjectFromGroup`` requires passing in an ``ElggObject`` (no longer accepts a GUID)
 * ``ElggUser::$salt`` no longer exists as an attribute, nor is it used for authentication
 * ``ElggUser::$password`` no longer exists as an attribute, nor is it used for authentication
 * ``elgg_get_widget_types`` no longer supports ``$exact`` as the 2nd argument
 * ``elgg_instanceof`` no longer supports the fourth ``class`` argument
 * ``elgg_view_icon`` no longer supports ``true`` as the 2nd argument
 * ``elgg_list_entities`` no longer supports the option ``view_type_toggle``
 * ``elgg_list_registered_entities`` no longer supports the option ``view_type_toggle``
 * ``elgg_log`` no longer accepts the level ``"DEBUG"``
 * ``elgg_gatekeeper`` and ``elgg_admin_gatekeeper`` no longer report ``login`` or ``admin`` as forward reason, but ``403``
 * ``Application::getDb()`` no longer returns an instance of ``Elgg\Database``, but rather a ``Elgg\Application\Database``
 * ``$CONFIG`` is no longer available as a local variable inside plugin ``start.php`` files.
 * ``elgg_get_config('siteemail')`` is no longer available. Use ``elgg_get_site_entity()->email``.
 * Group entities do no longer have the magic ``username`` attribute.
 * Pagehandling will no longer detect ``group:<guid>`` in the URL
 * The CRON interval ``reboot`` is removed.
 * The URL endpoints ``js/`` and ``css/`` are no longer supported. Use ``elgg_get_simplecache_url()``.
 * The generic comment save action no longer sends the notification directly, this has been offloaded to the notification system.
 * The script ``engine/start.php`` is removed.
 * The functions ``set_config``, ``unset_config`` and ``get_config`` have been deprecated and replaced by ``elgg_set_config``, ``elgg_remove_config`` and ``elgg_get_config``. 

JavaScript hook calling order may change
----------------------------------------

When registering for hooks, the ``all`` keyword for wildcard matching no longer has any effect
on the order that handlers are called. To ensure your handler is called last, you must give it the
highest priority of all matching handlers, or to ensure your handler is called first, you must give
it the lowest priority of all matching handlers.

If handlers were registered with the same priority, these are called in the order they were registered.

To emulate prior behavior, Elgg core handlers registered with the ``all`` keyword have been raised in
priority. Some of these handlers will most likely be called in a different order.

Widget layout related changes
-----------------------------

The widget layout usage has been changed. Content is no longer drawn as part of the layout. You need to wrap you content
in another layout and use the widgets layout as part of your content. If you want some special content to show if there
are no widgets in the layout, you can now pass a special ``no_widgets`` parameter (as String or as a Closure).

When registering widgets you can no longer omit passing a context as the ``all`` context is no longer supported. You need
to explicitely pass the contexts for which the widget is intended. 


HtmLawed is no longer a plugin
------------------------------

 * Do not call ``elgg_load_library('htmlawed')``.
 * In the hook params for ``'config', 'htmlawed'``, the ``hook_tag`` function name changed.

New approach to page layouts
----------------------------

``one_column``, ``one_sidebar``, ``two_sidebar`` and ``content`` layouts have been removed - instead layout rendering has been centralized in the ``default``. Updated ``default`` layout provides full control over the layout elements via ``$vars``.
For maximum backwards compatibility, calls to ``elgg_view_layout()`` with these layout names will still yield expected output, but the plugins should start using the ``default`` layout with an updated set of parameters.

Page layouts have been decomposed into smaller elements, which should make it easier for themes to target specific layout elements without having to override layouts at large.

As a result of these changes:

 * all layouts are consistent in how they handle title and filter menus, breadcrumbs and layout subviews
 * all layouts can now be easily extended to have multiple tabs. Plugins can pass ``filter_id`` parameter that will allow other plugins to hook into ``register, menu:filter:<filter_id>`` hook and add new tabs. If no ``filter_id`` is provided, default ``register, menu:filter`` hook can be used.
 * layout views and subviews now receive ``identifier`` and ``segments`` of the page being rendered
 * layout parameters are available to title and filter menu hooks, which allows resources to provide additional context information, for example, an ``$entity`` in case of a profile resource

Plugins and themes should:

 * Update calls to ``elgg_view_layout()`` to use ``default`` layout
 * Update replace ``nav`` parameter in layout views with ``breadcrumbs`` parameter
 * Update their use of ``filter`` parameter in layout views by either providing a default set of filter tabs, or setting a ``filter_id`` parameter and using hooks
 * Remove ``page/layouts/one_column`` view
 * Remove ``page/layouts/one_sidebar`` view
 * Remove ``page/layouts/two_sidebar`` view
 * Remove ``page/layouts/content`` view
 * Update their use of ``page/layouts/default``
 * Update their use of ``page/layouts/error``
 * Update their use of ``page/layouts/elements/filter``
 * Update their use of ``page/layouts/elements/header``
 * Update their use of ``page/layouts/elements/footer``
 * Update their use of ``page/elements/title``
 * Update their use of ``navigation/breadcrumbs`` to pass ``$vars['breadcrumbs']`` to ``elgg_get_breadcrumbs()``
 * Update hook registrations for ``output:before, layout`` to ``view_vars, page/layout/<layout_name>``
 * Update hook registrations for ``output:after, layout`` to ``view, page/layout/<layout_name>``
 * RSS extras menu is now registered with ``register, menu:extras`` hook

Notifications plugin
--------------------

Notifications plugin has been rewritten dropping many views and actions. The purpose of this rewrite was
to implement a more efficient, extendable and scalable interface for managing notifications preferences.
We have implemented a much simpler markup and removed excessive styling and javascript that was
required to make the old interface work.

If your plugin is extending any of the views or relies on any actions in the notifications plugin,
it has to be updated.

Theme and styling changes
-------------------------

Aalborg theme is no longer bundled with Elgg, instead all styles have been either moved to core views or to an appropriate core plugin.

This change may affect themes and plugins that were developed without Aalborg stylesheets loaded or were relying on a certain priority of views with Aalborg stylesheets loaded.

Notable changes in plugins:

 * search plugin no longer extends ``page/elements/header`` and instead extends ``page/elements/sidebar``
 * ``.elgg-icon`` no longer has a global ``font-size``, ``line-height`` or ``color``: these values will be inherited from parent items
 * Support for ``.elgg-icon-hover`` has been dropped
 * Admin theme now reuses icon classes from ``elements/icons.css``

Comment notifications
---------------------

 * The language keys related to comment notifications have changed. Check the ``generic_comment:notification:owner:`` language keys
 * The action for creating a comment (``action/comment/save``) was changed. If your plugin overruled this action you should have a look at it in order to prevent double notifications 

Object listing views
--------------------

 * ``object/elements/full/body`` now wraps the full listing body in a ``.elgg-listing-full-body`` wrapper
 * ``object/elements/full`` now supports ``attachments`` and ``responses`` which are rendered after listing body
 * In core plugins, resource views no longer render comments/replies - instead they pass a ``show_responses`` flag to the entity view, which renders the responses and passes them to the full listing view. Third party plugins will need to update their uses of ``object/<subtype>`` and ``resources/<handler>/view`` views.
 * Full discussion view is now rendered using ``object/elements/full`` view
 * ``object/file`` now passes image (specialcontent) view as an ``attachment`` to the full listing view

Menu changes
------------

Support for ``icon`` and ``badge`` parameters was added. Plugins should start using these parameters and prefer them to a single ``text`` parameter. CSS should be used to control visibility of the label, icon and badge, instead of conditionals in preparing menu items.

``topbar`` menu:

 * ``account`` menu item with priority ``800`` added to ``alt`` section
 * ``site_notifications`` menu item is now a child of ``account`` with priority ``100``
 * ``usersettings`` menu item is now a child of ``account`` with priority ``300``
 * ``administration`` menu item is now a child of ``account`` with priority ``800``
 * ``logout`` menu item is now a child of ``account`` with priority ``900``
 * ``dashboard`` menu item now has priority of ``100``
 * In ``default`` section (``profile``, ``friends``, ``messages``), core menu items now use ``icon`` parameter and use CSS to hide the label. Plugins that register items to this section and expect a visible label need to update their CSS.
 * ``profile`` menu item now uses ``icon`` parameter
 * ``friends`` menu item now uses ``icon`` parameter
 * ``messages`` menu item now uses ``icon`` and ``badge`` parameters

``extras`` menu:

 * ``bookmark``, ``report_this`` and ``rss`` menu items now use ``icon`` parameter

Entity icons
------------

Default icon image files have been moved and re-mapped as follows:

 * Default icons: ``views/default/icon/default/$size.png``
 * User icons: ``views/default/icon/user/default/$size.gif``
 * Group icons: ``views/default/icon/group/default/$size.gif`` in the groups plugin

Groups icon files have been moved from ``groups/<guid><size>.jpg`` relative to group owner's directory on filestore to a location prescribed by the entity icon service. Plugins should stop accessing files on the filestore directly and use the entity icon API. Upgrade script is available via admin interface.

Autocomplete (user and friends pickers)
---------------------------------------

Friends Picker input is now rendered using ``input/userpicker``.

Plugins should:

 * Update overriden ``input/userpicker`` to support new ``only_friends`` parameter
 * Remove friends picker CSS from their stylesheets

Friends collections
-------------------

Friends collections UI has been moved to its own plugins - ``friends_collections``.

From 2.2 to 2.3
===============

PHP Version
-----------

PHP 5.5 has reached end of life in July 2016. To ensure that Elgg sites are secure, we now require PHP 5.6 for new installations.

Existing installations can continue using PHP 5.5 until Elgg 3.0.

In order to upgrade Elgg to 2.3 using composer while using PHP 5.5, you may need to use ``--ignore-platform-reqs`` flag.

Deprecated APIs
---------------

 * Registering for ``to:object`` hook by the extender name: Use ``to:object, annotation`` and ``to:object, metadata`` hooks instead.
 * ``ajax_forward_hook()``: No longer used as handler for `'forward','all'` hook. Ajax response is now wrapped by the ``ResponseFactory``
 * ``ajax_action_hook()``: No longer used as handler for `'action','all'` hook. Output buffering now starts before the hook is triggered in ``ActionsService``
 * ``elgg_error_page_handler()``: No longer used as a handler for `'forward',<error_code>` hooks
 * ``get_uploaded_file()``: Use new file uploads API instead
 * ``get_user_notification_settings()``: Use ``ElggUser::getNotificationSettings()``
 * ``set_user_notification_setting()``: Use ``ElggUser::setNotificationSetting()``
 * ``pagesetup, system`` event: Use the menu or page shell hooks instead.
 * ``elgg.walled_garden`` JavaScript is deprecated: Use ``elgg/walled_garden`` AMD module instead.
 * ``elgg()->getDb()->getTableprefix()``: Use ``elgg_get_config('dbprefix')``.
 * Private ``update_entity_last_action()``: Refrain from manually updating last action timestamp.
 * Setting non-public ``access_id`` on metadata is deprecated. See below.
 * ``get_resized_image_from_existing_file()``: Use ``elgg_save_resized_image()``.
 * ``get_resized_image_from_uploaded_file()``: Use ``elgg_save_resized_image()`` in combination with upload API.
 * ``get_image_resize_parameters()`` will be removed.
 * ``elgg_view_input()``: Use ``elgg_view_field()``. Apologies for the API churn.

Deprecated Views
----------------

 * ``resources/file/world``: Use the ``resources/file/all`` view instead.
 * ``resources/pages/world``: Use the ``resources/pages/all`` view instead.
 * ``walled_garden.js``: Use the ``elgg/walled_garden`` module instead.

New API for page and action handling
------------------------------------

Page handlers and action script files should now return an instance of ``\Elgg\Http\ResponseBuilder``.
Plugins should use the following convenience functions to build responses:

 * ``elgg_ok_response()`` sends a 2xx response with HTML (page handler) or JSON data (actions)
 * ``elgg_error_response()`` sends a 4xx or 5xx response without content/data
 * ``elgg_redirect_response()`` silently redirects the request

New API for working with file uploads
-------------------------------------

 * ``elgg_get_uploaded_files()`` - returns an array of Symfony uploaded file objects
 * ``ElggFile::acceptUploadedFile()`` - moves an uploaded file to Elgg's filestore

New API for manipulating images
-------------------------------

New image manipulation service implements a more efficient approach to cropping and resizing images.

 * ``elgg_save_resized_image()`` - crops and resizes an image to preferred dimensions

New API for events
------------------

 * ``elgg_clear_event_handlers()`` - similar to ``elgg_clear_plugin_hook_handlers`` this functions removes all registered event handlers

New API for signing URLs
------------------------

URLs can now be signed with a SHA-256 HMAC key and validated at any time before URL expiry. This feature can be used to tokenize action URLs in email notifications, as well as other uses outside of the Elgg installation.

 * ``elgg_http_get_signed_url()`` - signs the URL with HMAC key
 * ``elgg_http_validate_signed_url()`` - validates the signed URL
 * ``elgg_signed_request_gatekeeper()`` - gatekeeper that validates the signature of the current request

Extendable form views
---------------------

Form footer rendering can now be deferred until the form view and its extensions have finished rendering. This allows plugins to collaborate on form views without breaking the markup logic.

 * ``elgg_set_form_footer()`` - sets form footer for deferred rendering
 * ``elgg_get_form_footer()`` - returns currently set form footer

Metadata ``access_id``
----------------------

It's now deprecated to create metadata with an explicit ``access_id`` value other than ``ACCESS_PUBLIC``.

In Elgg 3.0, metadata will not be access controlled, and will be available in all contexts. If your plugin relies on access control of metadata, it would be wise to migrate storage to annotations or entities instead.

New API for extracting class names from arrays
----------------------------------------------

Similar to ``elgg_extract()``, ``elgg_extract_class()`` extracts the "class" key (if present), merges into existing class names, and always returns an array.

Notifications
-------------

 * A high level ``'prepare','notification'`` hook is now triggered for instant and subscription notifications and can be used to alter notification objects irrespective of their type.
 * ``'format','notification:<method>'`` hook is now triggered for instant and subscription notifications and can be used to format the notification (e.g. strip HTML tags, wrap the notification body in a template etc).
 * Instant notifications are now handled by the notifications service, hence almost all hooks applicable to subscription notifications also apply to instant notifications.
 * ``elgg_get_notification_methods()`` can be used to obtain registered notification methods
 * Added ``ElggUser::getNotificationSettings()`` and ``ElggUser::setNotificationSetting()``

Entity list functions can output tables
---------------------------------------

In functions like ``elgg_list_entities($options)``, table output is possible by setting
``$options['list_type'] = 'table'`` and providing an array of table columns as ``$options['columns']``.
Each column is an ``Elgg\Views\TableColumn`` object, usually created via methods on the service
``elgg()->table_columns``.

Plugins can provide or alter these factory methods (see ``Elgg\Views\TableColumn\ColumnFactory``).
See the view ``admin/users/newest`` for a usage example.

Inline tabs components
----------------------

Inline tabs component can now be rendered with ``page/components/tabs`` view. The components allows to switch between pre-poluated and ajax-loaded.
See ``page/components/tabs`` in core views and ``theme_sandbox/components/tabs`` in developers plugin for usage instructions and examples.

API to alter registration and login URL
---------------------------------------

 * ``elgg_get_registration_url()`` should be used to obtain site's registration URL
 * ``elgg_get_login_url()`` should be used to obtain site's login URL
 * ``registration_url, site`` hook can be used to alter the default registration URL
 * ``login_url, site`` hook can be used to alter the default login URL

Support for fieldsets in forms
------------------------------

 * ``elgg_view_field()`` replaces ``elgg_view_input()``. It has a similar API, but accepts a single array.
 * ``elgg_view_field()`` supports ``#type``, ``#label``, ``#help`` and ``#class``, allowing unprefixed versions to be sent to the input view ``$vars``.
 * The new view ``input/fieldset`` can be used to render a set of fields, each rendered with ``elgg_view_field()``.

From 2.1 to 2.2
===============

Deprecated APIs
---------------

 * ``elgg.ui.river`` JavaScript library: Remove calls to ``elgg_load_js('elgg.ui.river')`` from plugin code. Update ``core/river/filter`` and ``forms/comment/save``, if overwritten, to require component AMD modules
 * ``elgg.ui.popupOpen()`` and ``elgg.ui.popupClose()`` methods in ``elgg.ui`` JS library: Use ``elgg/popup`` module instead.
 * ``lightbox.js`` library: Do not use ``elgg_load_js('lightbox.js');`` unless your code references deprecated ``elgg.ui.lightbox`` namespace. Use ``elgg/lightbox`` AMD module instead.
 * ``elgg.embed`` library and ``elgg.embed`` object: Do not use ``elgg_load_js('elgg.embed')``. Use ``elgg/embed`` AMD module instead
 * Accessing ``icons_sizes`` config value directly: Use ``elgg_get_icon_sizes()``
 * ``can_write_to_container()``: Use ``ElggEntity::canWriteToContainer()``

Deprecated Views
----------------

 * ``elgg/ui.river.js`` is deprecated: Do not rely on simplecache URLs to work.
 * ``groups/js`` is deprecated: Use ``groups/navigation`` AMD module as a menu item dependency for "feature" and "unfeature" menu items instead.
 * ``lightbox/settings.js`` is deprecated: Use ``getOptions, ui.lightbox`` JS plugin hook or ``data-colorbox-opts`` attribute.
 * ``elgg/ckeditor/insert.js`` is deprecated: You no longer need to include it, hook registration takes place in ``elgg/ckeditor`` module
 * ``embed/embed.js`` is deprecated: Use ``elgg/embed`` AMD module.

Added ``elgg/popup`` module
---------------------------

New :doc:`elgg/popup module <javascript>` can be used to build out more complex trigger-popup interactions, including binding custom anchor types and opening/closing popups programmatically.

Added ``elgg/lightbox`` module
------------------------------

New :doc:`elgg/lightbox module <javascript>` can be used to open and close the lightbox programmatically.

Added ``elgg/embed`` module
---------------------------

Even though rarely necessary, ``elgg/embed`` AMD module can be used to access the embed methods programmatically. The module bootstraps itself when necessary and is unlikely to require further decoration.

New API for handling entity icons
---------------------------------

 * ``ElggEntity`` now implements ``\Elgg\EntityIcon`` interface
 * ``elgg_get_icon_sizes()`` - return entity type/subtype specific icon sizes
 * ``ElggEntity::saveIconFromUploadedFile()`` - creates icons from an uploaded file
 * ``ElggEntity::saveIconFromLocalFile()`` - creates icons from a local file
 * ``ElggEntity::saveIconFromElggFile()`` - creates icons from an instance of ``ElggFile``
 * ``ElggEntity::getIcon()`` - returns an instanceof ``ElggIcon`` that points to entity icon location on filestore (this may be just a placeholder, use ``ElggEntity::hasIcon()`` to validate if file has been written)
 * ``ElggEntity::deleteIcon()`` - deletes entity icons
 * ``ElggEntity::getIconLastChange()`` - return modified time of the icon file
 * ``ElggEntity::hasIcon()`` - checks if an icon with given size has been created
 * ``elgg_get_embed_url()`` - can be used to return an embed URL for an entity's icon (served via `/serve-icon` handler)

Removed APIs
------------

Just a warning that the private entity cache functions (e.g. ``_elgg_retrieve_cached_entity``) have been removed. Some plugins may have been using them. Plugins should not use private APIs as they will more often be removed without notice.

Improved ``elgg/ckeditor`` module
---------------------------------

:doc:`elgg/ckeditor module <javascript>` can now be used to add WYSIWYG to a textarea programmatically with ``elgg/ckeditor#bind``.

From 2.0 to 2.1
===============

Deprecated APIs
---------------

 * ``ElggFile::setFilestore``
 * ``get_default_filestore``
 * ``set_default_filestore``
 * ``elgg_get_config('siteemail')``: Use ``elgg_get_site_entity()->email``
 * URLs starting with ``/css/`` and ``/js/``: ``Use elgg_get_simplecache_url()``
 * ``elgg.ui.widgets`` JavaScript object is deprecated by ``elgg/widgets`` AMD module

``Application::getDb()`` changes
--------------------------------

If you're using this low-level API, do not expect it to return an ``Elgg\Database`` instance in 3.0. It now
returns an ``Elgg\Application\Database`` with many deprecated. These methods were never meant to be made
public API, but we will do our best to support them in 2.x.

Added ``elgg/widgets`` module
-----------------------------

If your plugin code calls ``elgg.ui.widgets.init()``, instead use the :doc:`elgg/widgets module <javascript>`.

From 1.x to 2.0
===============

Elgg can be now installed as a composer dependency instead of at document root
------------------------------------------------------------------------------

That means an Elgg site can look something like this:

.. code::

    settings.php
    vendor/
      elgg/
        elgg/
          engine/
            start.php
          _graphics/
            elgg_sprites.png
    mod/
      blog
      bookmarks
      ...

``elgg_get_root_path`` and ``$CONFIG->path`` will return the path to the application
root directory, which is not necessarily the same as Elgg core's root directory (which
in this case is ``vendor/elgg/elgg/``).

Do not attempt to access the core Elgg from your plugin directly, since you cannot
rely on its location on the filesystem.

In particular, don't try load ``engine/start.php``.

.. code:: php

    // Don't do this!
    dirname(__DIR__) . "/engine/start.php";
    
To boot Elgg manually, you can use the class ``Elgg\Application``.

.. code:: php

    // boot Elgg in mod/myplugin/foo.php
    require_once dirname(dirname(__DIR__)) . '/vendor/autoload.php';
    \Elgg\Application::start();

However, use this approach sparingly. Prefer :doc:`routing` instead whenever possible
as that keeps your public URLs and your filesystem layout decoupled.

Also, don't try to access the ``_graphics`` files directly.

.. code:: php

    readfile(elgg_get_root_path() . "_graphics/elgg_sprites.png");
    
Use :doc:`views` instead:

.. code:: php

    echo elgg_view('elgg_sprites.png');
    

Cacheable views must have a file extension in their names
---------------------------------------------------------

This requirement makes it possibile for us to serve assets directly
from disk for performance, instead of serving them through PHP.

It also makes it much easier to explore the available cached resources
by navigating to dataroot/views_simplecache and browsing around.

 * Bad: ``my/cool/template``
 * Good: ``my/cool/template.html``

We now cache assets by ``"$viewtype/$view"``, not ``md5("$viewtype|$view")``,
which can result in conflicts between cacheable views that don't have file extensions
to disambiguate files from directories.


Dropped ``jquery-migrate`` and upgraded ``jquery`` to ^2.1.4
------------------------------------------------------------

jQuery 2.x is API-compatible with 1.x, but drops support for IE8-, which Elgg
hasn't supported for some time anyways.

See http://jquery.com/upgrade-guide/1.9/ for how to move off jquery-migrate.

If you'd prefer to just add it back, you can use this code in your plugin's init:

.. code:: php

    elgg_register_js('jquery-migrate', elgg_get_simplecache_url('jquery-migrate.js'), 'head');
    elgg_load_js('jquery-migrate');


Also, define a ``jquery-migrate.js`` view containing the contents of the script.

JS and CSS views have been moved out of the js/ and css/ directories
--------------------------------------------------------------------

They also have been given .js and .css extensions respectively if they didn't
already have them:

================= =============
Old view          New view
================= =============
``js/view``       ``view.js``
``js/other.js``   ``other.js``
``css/view``      ``view.css``
``css/other.css`` ``other.css``
``js/img.png``    ``img.png``
================= =============

The main benefit this brings is being able to co-locate related assets.
So a template (``view.php``) can have its CSS/JS dependencies right next to it
(``view.css``, ``view.js``).

Care has been taken to make this change as backwards-compatible as possible,
so you should not need to update any view references right away. However, you are
certainly encouraged to move your JS and CSS views to their new, canonical
locations.

Practically speaking, this carries a few gotchas:

The ``view_vars, $view_name`` and ``view, $view_name`` hooks will operate on the
*canonical* view name:

.. code:: php

    elgg_register_plugin_hook_handler('view', 'css/elgg', function($hook, $view_name) {
      assert($view_name == 'elgg.css') // not "css/elgg"
    });
    
Using the ``view, all`` hook and checking for individual views may not work as intended:

.. code:: php

    elgg_register_plugin_hook_handler('view', 'all', function($hook, $view_name) {
      // Won't work because "css/elgg" was aliased to "elgg.css"
      if ($view_name == 'css/elgg') {
        // Never executed...
      }
      
      // Won't work because no canonical views start with css/* anymore
      if (strpos($view_name, 'css/') === 0) {
        // Never executed...
      }
    });

Please let us know about any other BC issues this change causes.
We'd like to fix as many as possible to make the transition smooth.

``fxp/composer-asset-plugin`` is now required to install Elgg from source
-------------------------------------------------------------------------

We use ``fxp/composer-asset-plugin`` to manage our browser assets (js, css, html)
with Composer, but it must be installed globally *before installing Elgg* in order
for the ``bower-asset/*`` packages to be recognized. To install it, run:

.. code:: shell

    composer global require fxp/composer-asset-plugin

If you don't do this before running ``composer install`` or ``composer create-project``,
you will get an error message:

.. code:: shell

    [InvalidArgumentException]
    Package fxp/composer-asset-plugin not found


List of deprecated views and view arguments that have been removed
------------------------------------------------------------------

We dropped support for and/or removed the following views:

 * canvas/layouts/*
 * categories
 * categories/view
 * core/settings/tools
 * embed/addcontentjs
 * footer/analytics (Use page/elements/foot instead)
 * groups/left_column
 * groups/right_column
 * groups/search/finishblurb
 * groups/search/startblurb
 * input/calendar (Use input/date instead)
 * input/datepicker (Use input/date instead)
 * input/pulldown (Use input/select instead)
 * invitefriends/formitems
 * js/admin (Use AMD and ``elgg_require_js`` instead of extending JS views)
 * js/initialise_elgg (Use AMD and ``elgg_require_js`` instead of extending JS views)
 * members/nav
 * metatags (Use the 'head', 'page' plugin hook instead)
 * navigation/topbar_tools
 * navigation/viewtype
 * notifications/subscriptions/groupsform
 * object/groupforumtopic
 * output/calendar (Use output/date instead)
 * output/confirmlink (Use output/url instead)
 * page_elements/contentwrapper
 * page/elements/shortcut_icon (Use the 'head', 'page' plugin hook instead)
 * page/elements/wrapper
 * profile/icon (Use ``elgg_get_entity_icon``)
 * river/object/groupforumtopic/create
 * settings/{plugin}/edit (Use plugins/{plugin}/settings instead)
 * user/search/finishblurb
 * user/search/startblurb
 * usersettings/{plugin}/edit (Use plugins/{plugin}/usersettings instead)
 * widgets/{handler}/view (Use widgets/{handler}/content instead)

We also dropped the following arguments to views:

 * "value" in output/iframe (Use "src" instead)
 * "area2" and "area3" in page/elements/sidebar (Use "sidebar" or view extension instead)
 * "js" in icon views (e.g. icon/user/default)
 * "options" to input/radio and input/checkboxes which aren't key-value pairs
   will no longer be acceptable.


All scripts moved to bottom of page
-----------------------------------

You should test your plugin **with the JavaScript error console visible**. For performance reasons, Elgg no longer
supports ``script`` elements in the ``head`` element or in HTML views. ``elgg_register_js`` will now load *all*
scripts at the end of the ``body`` element.

You must convert inline scripts to :doc:`AMD </guides/javascript>` or to external scripts loaded with
``elgg_load_js``.

Early in the page, Elgg provides a shim of the RequireJS ``require()`` function that simply queues code until
the AMD ``elgg`` and ``jQuery`` modules are defined. This provides a straightforward way to convert many inline
scripts to use ``require()``.

Inline code which will fail because the stack is not yet loaded:

.. code:: html

    <script>
    $(function () {
        // code using $ and elgg
    });
    </script>

This should work in Elgg 2.0:

.. code:: html

    <script>
    require(['elgg', 'jquery'], function (elgg, $) {
        $(function () {
            // code using $ and elgg
        });
    });
    </script>

Attribute formatter removes keys with underscores
-------------------------------------------------

``elgg_format_attributes()`` (and all APIs that use it) now filter out attributes whose name contains an
underscore. If the attribute begins with ``data-``, however, it will not be removed.

Breadcrumbs
-----------

Breadcrumb display now removes the last item if it does not contain a link. To restore the previous behavior,
replace the plugin hook handler ``elgg_prepare_breadcrumbs`` with your own:

.. code:: php

    elgg_unregister_plugin_hook_handler('prepare', 'breadcrumbs', 'elgg_prepare_breadcrumbs');
    elgg_register_plugin_hook_handler('prepare', 'breadcrumbs', 'myplugin_prepare_breadcrumbs');

    function myplugin_prepare_breadcrumbs($hook, $type, $breadcrumbs, $params) {
        // just apply excerpt to titles
        foreach (array_keys($breadcrumbs) as $i) {
            $breadcrumbs[$i]['title'] = elgg_get_excerpt($breadcrumbs[$i]['title'], 100);
        }
        return $breadcrumbs;
    }

Callbacks in Queries
--------------------

Make sure to use only valid *callable* values for "callback" argument/options in the API.

Querying functions will now will throw a ``RuntimeException`` if ``is_callable()`` returns ``false`` for the given
callback value. This includes functions such as ``elgg_get_entities()``, ``get_data()``, and many more.

Comments plugin hook
--------------------

Plugins can now return an empty string from ``'comments',$entity_type`` hook in order to override the default comments component view. To force the default comments component, your plugin must return ``false``. If you were using empty strings to force the default comments view, you need to update your hook handlers to return ``false``.

Container permissions hook
--------------------------

The behavior of the ``container_permissions_check`` hook has changed when an entity is being created: Before 2.0, the hook would be called twice if the entity's container was not the owner. On the first call, the entity's owner would be passed in as ``$params['container']``, which could confuse handlers.

In 2.0, when an entity is created in a container like a group, if the owner is the same as the logged in user (almost always the case), this first check is bypassed. So the ``container_permissions_check`` hook will almost always be called once with ``$params['container']`` being the correct container of the entity.

Creating or deleting a relationship triggers only one event
-----------------------------------------------------------

The "create" and "delete" relationship events are now only fired once, with ``"relationship"`` as the object type.

E.g. Listening for the ``"create", "member"`` or ``"delete", "member"`` event(s) will no longer capture group membership additions/removals. Use the ``"create", "relationship"`` or ``"delete", "relationship"`` events.

Discussion feature has been pulled from groups into its own plugin
------------------------------------------------------------------

The ``object, groupforumtopic`` subtype has been replaced with the
``object, discussion`` subtype. If your plugin is using or altering
the old discussion feature, you should upgrade it to use the new
subtype.

Nothing changes from the group owners' point of view. The discussion
feature is still available as a group tool and all old discussions
are intact.

Dropped login-over-https feature
--------------------------------

For the best security and performance, serve all pages over HTTPS by switching
the scheme in your site's wwwroot to ``https`` at http://yoursite.tld/admin/settings/advanced

.. _migrated-to-pdo:

Elgg has migrated from ext/mysql to PDO MySQL
---------------------------------------------

Elgg now uses a ``PDO_MYSQL`` connection and no longer uses any ext/mysql functions. If you use
``mysql_*`` functions, implicitly relying on an open connection, these will fail.

If your code uses one of the following functions, read below.

- ``execute_delayed_write_query()``
- ``execute_delayed_read_query()``

If you provide a callable ``$handler`` to be called with the results, your handler will now receive a
``\Doctrine\DBAL\Driver\Statement`` object. Formerly this was an ext/mysql ``result`` resource.


Event/Hook calling order may change
-----------------------------------

When registering for events/hooks, the ``all`` keyword for wildcard matching no longer has any effect
on the order that handlers are called. To ensure your handler is called last, you must give it the
highest priority of all matching handlers, or to ensure your handler is called first, you must give
it the lowest priority of all matching handlers.

If handlers were registered with the same priority, these are called in the order they were registered.

To emulate prior behavior, Elgg core handlers registered with the ``all`` keyword have been raised in
priority. Some of these handlers will most likely be called in a different order.

``export/`` URLs are no longer available
----------------------------------------

Elgg no longer provides this endpoint for exposing resource data.

Icons migrated to Font Awesome
------------------------------

Elgg's sprites and most of the CSS classes beginning with ``elgg-icon-``
`have been removed <https://github.com/Elgg/Elgg/pull/8578/files#diff-b3912b37ca7bd6c53a2968ccb6c22a94L22>`_.

Usage of ``elgg_view_icon()`` is backward compatible, but static HTML using the ``elgg-icon``
classes will have to be updated to the new markup.

Increase of z-index value in elgg-menu-site class
-------------------------------------------------

The value of z-index in the elgg-menu-site class has been increased from 1 to 50 to allow for page elements
in the content area to use the z-index property without the "More" site menu's dropdown being displayed
behind these elements. If your plugin/theme overrides the elgg-menu-site class or views/default/elements/navigation.css
please adjust the z-index value in your modified CSS file accordingly.

input/autocomplete view
-----------------------

Plugins that override the ``input/autocomplete`` view will need to include the source URL in the ``data-source`` attribute of the input element, require the new ``elgg/autocomplete`` AMD module, and call its ``init`` method. The 1.x javascript library ``elgg.autocomplete`` is no longer used.

Introduced third-party library for sending email
------------------------------------------------

We are using the excellent ``Zend\Mail`` library to send emails in Elgg 2.0.
There are likely edge cases that the library handles differently than Elgg 1.x.
Take care to test your email notifications carefully when upgrading to 2.0.

Label elements
--------------

The following views received ``label`` elements around some of the input fields. If your plugin/theme overrides these views please check for the new content.

- views/default/core/river/filter.php
- views/default/forms/admin/plugins/filter.php
- views/default/forms/admin/plugins/sort.php
- views/default/forms/login.php

Plugin Aalborg Theme
--------------------

The view ``page/elements/navbar`` now uses a Font Awesome icon for the mobile menu selector instead of an image. The ``bars.png`` image and supporting CSS for the 1.12 rendering has been removed, so update your theme accordingly.

Plugin Likes
------------

Objects are no longer likable by default. To support liking, you can register a handler to permit the annotation,
or more simply register for the hook ``["likes:is_likable", "<type>:<subtype>"]`` and return true. E.g.

.. code:: php

    elgg_register_plugin_hook_handler('likes:is_likable', 'object:mysubtype', 'Elgg\Values::getTrue');

Just as before, the ``permissions_check:annotate`` hook is still called and may be used to override default behavior.

Plugin Messages
---------------

If you've removed or replaced the handler function ``messages_notifier`` to hide/alter the inbox icon, you'll instead need to do the
same for the topbar menu handler ``messages_register_topbar``. ``messages_notifier`` is no longer used to add the menu link.

Messages will no longer get the metadata 'msg' for newly created messages. This means you can not rely on that metadata to exist.

Plugin Blog
-----------

The blog pages showing 'Mine' or 'Friends' listings of blogs have been changed to list all the blogs owned by the users (including those created in groups).

Plugin Bookmarks
----------------

The bookmark pages showing 'Mine' or 'Friends' listings of bookmarks have been changed to list all the bookmarks owned by the users (including those created in groups).

Plugin File
-----------

The file pages showing 'Mine' or 'Friends' listings of files have been changed to list all the files owned by the users (including those created in groups).

Removed Classes
---------------

 - ``ElggInspector``
 - ``Notable``
 - ``FilePluginFile``: replace with ``ElggFile`` (or load with ``get_entity()``)

Removed keys available via ``elgg_get_config()``
------------------------------------------------

 - ``allowed_ajax_views``
 - ``dataroot_in_settings``
 - ``externals``
 - ``externals_map``
 - ``i18n_loaded_from_cache``
 - ``language_paths``
 - ``pagesetupdone``
 - ``registered_tag_metadata_names``
 - ``simplecache_enabled_in_settings``
 - ``translations``
 - ``viewpath``
 - ``views``
 - ``view_path``
 - ``viewtype``
 - ``wordblacklist``

Also note that plugins should not be accessing the global ``$CONFIG`` variable except for in ``settings.php``.

Removed Functions
-----------------

 - ``blog_get_page_content_friends`` 
 - ``blog_get_page_content_read`` 
 - ``count_unread_messages()``
 - ``delete_entities()``
 - ``delete_object_entity()``
 - ``delete_user_entity()``
 - ``elgg_get_view_location()``
 - ``elgg_validate_action_url()``
 - ``execute_delayed_query()``
 - ``extend_view()``
 - ``get_db_error()``
 - ``get_db_link()``
 - ``get_entities()``
 - ``get_entities_from_access_id()``
 - ``get_entities_from_access_collection()``
 - ``get_entities_from_annotations()``
 - ``get_entities_from_metadata()``
 - ``get_entities_from_metadata_multi()``
 - ``get_entities_from_relationship()``
 - ``get_filetype_cloud()``
 - ``get_library_files()``
 - ``get_views()``
 - ``is_ip_in_array()``
 - ``list_entities()``
 - ``list_entities_from_annotations()``
 - ``list_group_search()``
 - ``list_registered_entities()``
 - ``list_user_search()``
 - ``load_plugins()``
 - ``menu_item()``
 - ``make_register_object()``
 - ``mysql_*()``: Elgg :ref:`no longer uses ext/mysql<migrated-to-pdo>`
 - ``remove_blacklist()``
 - ``search_for_group()``
 - ``search_for_object()``
 - ``search_for_site()``
 - ``search_for_user()``
 - ``search_list_objects_by_name()``
 - ``search_list_groups_by_name()``
 - ``search_list_users_by_name()``
 - ``set_template_handler()``
 - ``test_ip()``

Removed methods
---------------

 - ``ElggCache::set_variable()``
 - ``ElggCache::get_variable()``
 - ``ElggData::initialise_attributes()``
 - ``ElggData::getObjectOwnerGUID()``
 - ``ElggDiskFilestore::make_directory_root()``
 - ``ElggDiskFilestore::make_file_matrix()``
 - ``ElggDiskFilestore::user_file_matrix()``
 - ``ElggDiskFilestore::mb_str_split()``
 - ``ElggEntity::clearMetadata()``
 - ``ElggEntity::clearRelationships()``
 - ``ElggEntity::clearAnnotations()``
 - ``ElggEntity::getOwner()``
 - ``ElggEntity::setContainer()``
 - ``ElggEntity::getContainer()``
 - ``ElggEntity::getIcon()``
 - ``ElggEntity::setIcon()``
 - ``ElggExtender::getOwner()``
 - ``ElggFileCache::create_file()``
 - ``ElggObject::addToSite()``: parent function in ElggEntity still available
 - ``ElggObject::getSites()``: parent function in ElggEntity still available
 - ``ElggSite::getCollections()``
 - ``ElggUser::addToSite()``: parent function in ElggEntity still available
 - ``ElggUser::getCollections()``
 - ``ElggUser::getOwner()``
 - ``ElggUser::getSites()``: parent function in ElggEntity still available
 - ``ElggUser::listFriends()``
 - ``ElggUser::listGroups()``
 - ``ElggUser::removeFromSite()``: parent function in ElggEntity still available

The following arguments have also been dropped:

 - ``ElggSite::getMembers()``
   - 2: ``$offset``
 - ``elgg_view_entity_list()``
   - 3: ``$offset``
   - 4: ``$limit``
   - 5: ``$full_view``
   - 6: ``$list_type_toggle``
   - 7: ``$pagination``

Removed Plugin Hooks
--------------------

 - ``[display, view]``: See the :ref:`new plugin hook<guides/views#altering-view-output>`.
 
Removed Actions
---------------

 - ``widgets/upgrade``

Removed Views
-------------

 - ``forms/admin/plugins/change_state``
 
Removed View Variables
----------------------

During rendering, the view system no longer injects these into the scope:

 - ``$vars['url']``: replace with ``elgg_get_site_url()``
 - ``$vars['user']``: replace with ``elgg_get_logged_in_user_entity()``
 - ``$vars['config']``: use ``elgg_get_config()`` and ``elgg_set_config()``
 - ``$CONFIG``: use ``elgg_get_config()`` and ``elgg_set_config()``

Also several workarounds for very old views are no longer performed. Make these changes:

 - Set ``$vars['full_view']`` instead of ``$vars['full']``.
 - Set ``$vars['name']`` instead of ``$vars['internalname']``.
 - Set ``$vars['id']`` instead of ``$vars['internalid']``.

Removed libraries
-----------------

 - ``elgg:markdown``: Elgg no longer provides a markdown implementation. You must provide your own.

Specifying View via Properties
------------------------------

The metadata ``$entity->view`` no longer specifies the view used to render in ``elgg_view_entity()``.

Similarly the property ``$annotation->view`` no longer has an effect within ``elgg_view_annotation()``.

Viewtype is static after the initial ``elgg_get_viewtype()`` call
-----------------------------------------------------------------

``elgg_set_viewtype()`` must be used to set the viewtype at runtime. Although Elgg still checks the
``view`` input and ``$CONFIG->view`` initially, this is only done once per request.


Deprecations
------------

It's deprecated to read or write to metadata keys starting with ``filestore::`` on ``ElggFile`` objects. In Elgg 3.0 this metadata will be deleted if it points to the current data root path, so few file objects will have it. Plugins should only use ``ElggFile::setFilestore`` if files need to be stored in a custom location.

.. note:: This is not the only deprecation in Elgg 2.0. Plugin developers should watch their site error logs.

From 1.10 to 1.11
=================

Comment highlighting
--------------------

If your theme is using the file ``views/default/css/elements/components.php``, you must add the following style definitions in it to enable highlighting for comments and discussion replies:

.. code:: css

	.elgg-comments .elgg-state-highlight {
		-webkit-animation: comment-highlight 5s;
		animation: comment-highlight 5s;
	}
	@-webkit-keyframes comment-highlight {
		from {background: #dff2ff;}
		to {background: white;}
	}
	@keyframes comment-highlight {
		from {background: #dff2ff;}
		to {background: white;}
	}

From 1.9 to 1.10
================

File uploads
------------

If your plugin is using a snippet copied from the ``file/upload`` action to fix detected mime types for Microsoft zipped formats, it can now be safely removed.

If your upload action performs other manipulations on detected mime and simple types, it is recommended to make use of available plugin hooks:

- ``'mime_type','file'`` for filtering detected mime types
- ``'simple_type','file'`` for filtering parsed simple types

From 1.8 to 1.9
===============

In the examples we are upgrading an imaginary "Photos" plugin.

Only the key changes are included. For example some of the deprecated functions are not mentioned here separately.

Each section will include information whether the change is backwards compatible with Elgg 1.8.

The manifest file
-----------------

No changes are needed if your plugin is compatible with 1.8.

It's however recommended to add the ``<id>`` tag. It's value should be the name of the directory where the plugin is located inside the ``mod/`` directory.

If you make changes that break BC, you must update the plugin version and the required Elgg release.

Example of (shortened) old version:

.. code:: xml

    <?xml version="1.0" encoding="UTF-8"?>
    <plugin_manifest xmlns="http://www.elgg.org/plugin_manifest/1.8">
        <name>Photos</name>
        <author>John Doe</author>
        <version>1.0</version>
        <description>Adds possibility to upload photos and arrange them into albums.</description>
        <requires>
            <type>elgg_release</type>
            <version>1.8</version>
        </requires>
    </plugin_manifest>

Example of (shortened) new version:

.. code:: xml

    <?xml version="1.0" encoding="UTF-8"?>
    <plugin_manifest xmlns="http://www.elgg.org/plugin_manifest/1.8">
        <name>Photos</name>
        <id>photos</id>
        <author>John Doe</author>
        <version>2.0</version>
        <description>Adds possibility to upload photos and arrange them into albums.</description>
        <requires>
            <type>elgg_release</type>
            <version>1.9</version>
        </requires>
    </plugin_manifest>

$CONFIG and $vars['config']
---------------------------

Both the global ``$CONFIG`` variable and the ``$vars['config']`` parameter have been deprecated. They should be replaced with the ``elgg_get_config()`` function.

Example of old code:

.. code:: php

    // Using the global $CONFIG variable:
    global $CONFIG;
    $plugins_path = $CONFIG->plugins_path

    // Using the $vars view parameter:
    $plugins_path = $vars['plugins_path'];

Example of new code:

.. code:: php

    $plugins_path = elgg_get_config('plugins_path');

.. note::

    Compatible with 1.8

.. note::

    See how the community_plugins plugin was updated: https://github.com/Elgg/community_plugins/commit/f233999bbd1478a200ee783679c2e2897c9a0483

Language files
--------------

In Elgg 1.8 the language files needed to use the ``add_translation()`` function. In 1.9 it is enough to just return the array that was
previously passed to the function as a parameter. Elgg core will use the file name (e.g. en.php) to tell which language the file contains.

Example of the old way in ``languages/en.php``:

.. code:: php

    $english = array(
        'photos:all' => 'All photos',
    );
    add_translation('en', $english);

Example of new way:

.. code:: php

    return array(
        'photos:all' => 'All photos',
    );

.. warning::

    Not compatible with 1.8

Notifications
-------------

One of the biggest changes in Elgg 1.9 is the notifications system. The new system allows more flexible and scalable way of sending notifications.

Example of the old way:

.. code:: php

    function photos_init() {
        // Tell core that we want to send notifications about new photos
        register_notification_object('object', 'photo', elgg_echo('photo:new'));

        // Register a handler that creates the notification message
        elgg_register_plugin_hook_handler('notify:entity:message', 'object', 'photos_notify_message');
    }

    /**
     * Set the notification message body
     *
     * @param string $hook    Hook name
     * @param string $type    Hook type
     * @param string $message The current message body
     * @param array  $params  Parameters about the photo
     * @return string
     */
    function photos_notify_message($hook, $type, $message, $params) {
        $entity = $params['entity'];
        $to_entity = $params['to_entity'];
        $method = $params['method'];
        if (elgg_instanceof($entity, 'object', 'photo')) {
            $descr = $entity->excerpt;
            $title = $entity->title;
            $owner = $entity->getOwnerEntity();
            return elgg_echo('photos:notification', array(
                $owner->name,
                $title,
                $descr,
                $entity->getURL()
            ));
        }
        return null;
    }

Example of the new way:

.. code:: php

    function photos_init() {
        elgg_register_notification_event('object', 'photo', array('create'));
        elgg_register_plugin_hook_handler('prepare', 'notification:publish:object:photo', 'photos_prepare_notification');
    }

    /**
     * Prepare a notification message about a new photo
     *
     * @param string                          $hook         Hook name
     * @param string                          $type         Hook type
     * @param Elgg_Notifications_Notification $notification The notification to prepare
     * @param array                           $params       Hook parameters
     * @return Elgg_Notifications_Notification
     */
    function photos_prepare_notification($hook, $type, $notification, $params) {
        $entity = $params['event']->getObject();
        $owner = $params['event']->getActor();
        $recipient = $params['recipient'];
        $language = $params['language'];
        $method = $params['method'];

        // Title for the notification
        $notification->subject = elgg_echo('photos:notify:subject', array($entity->title), $language);

        // Message body for the notification
        $notification->body = elgg_echo('photos:notify:body', array(
            $owner->name,
            $entity->title,
            $entity->getExcerpt(),
            $entity->getURL()
        ), $language);

        // The summary text is used e.g. by the site_notifications plugin
        $notification->summary = elgg_echo('photos:notify:summary', array($entity->title), $language);

        return $notification;
    }

.. warning::

    Not compatible with 1.8

.. note::

    See how the community_plugins plugin was updated to use the new system: https://github.com/Elgg/community_plugins/commit/bfa356cfe8fb99ebbca4109a1b8a1383b70ff123

Notifications can also be sent with the ``notify_user()`` function.

It has however been updated to support three new optional parameters passed inside an array as the fifth parameter.

The parameters give notification plugins more control over the notifications, so they should be included whenever possible. For example the bundled site_notifications plugin won't work properly if the parameters are missing.

Parameters:

-  **object** The object that we are notifying about (e.g. ElggEntity or ElggAnnotation). This is needed so that notification plugins can provide a link to the object.
-  **action** String that describes the action that triggered the notification (e.g. "create", "update", etc).
-  **summary** String that contains a summary of the notification. (It should be more informative than the notification subject but less informative than the notification body.)

Example of the old way:

.. code:: php

	// Notify $owner that $user has added a $rating to an $entity created by him

	$subject = elgg_echo('rating:notify:subject');
	$body = elgg_echo('rating:notify:body', array(
		$owner->name,
		$user->name,
		$entity->title,
		$entity->getURL(),
	));

	notify_user($owner->guid,
				$user->guid,
				$subject,
				$body
			);

Example of the new way:

.. code:: php

	// Notify $owner that $user has added a $rating to an $entity created by him

	$subject = elgg_echo('rating:notify:subject');
	$summary = elgg_echo('rating:notify:summary', array($entity->title));
	$body = elgg_echo('rating:notify:body', array(
		$owner->name,
		$user->name,
		$entity->title,
		$entity->getURL(),
	));

	$params = array(
		'object' => $rating,
		'action' => 'create',
		'summary' => $summary,
	);

	notify_user($owner->guid,
				$user->guid,
				$subject,
				$body,
				$params
			);

.. note::

    Compatible with 1.8

Adding items to the Activity listing
------------------------------------

.. code:: php

    add_to_river('river/object/photo/create', 'create', $user_guid, $photo_guid);

.. code:: php

    elgg_create_river_item(array(
        'view' => 'river/object/photo/create',
        'action_type' => 'create',
        'subject_guid' => $user_guid,
        'object_guid' => $photo_guid,
    ));

You can also add the optional ``target_guid`` parameter which tells the target of the create action.

If the photo would had been added for example into a photo album, we could add it by passing in also:

.. code:: php

    'target_guid' => $album_guid,

.. warning::

    Not compatible with 1.8

Entity URL handlers
-------------------

The ``elgg_register_entity_url_handler()`` function has been deprecated. In 1.9 you should use the ``'entity:url', 'object'`` plugin hook instead.

Example of the old way:

.. code:: php

    /**
     * Initialize the photo plugin
     */
    my_plugin_init() {
        elgg_register_entity_url_handler('object', 'photo', 'photo_url_handler');
    }

    /**
     * Returns the URL from a photo entity
     *
     * @param ElggEntity $entity
     * @return string
     */
    function photo_url_handler($entity) {
    	return "photo/view/{$entity->guid}";
    }

Example of the new way:

.. code:: php

    /**
     * Initialize the photo plugin
     */
    my_plugin_init() {
        elgg_register_plugin_hook_handler('entity:url', 'object', 'photo_url_handler');
    }

    /**
     * Returns the URL from a photo entity
     *
     * @param string $hook   'entity:url'
     * @param string $type   'object'
     * @param string $url    The current URL
     * @param array  $params Hook parameters
     * @return string
     */
    function photo_url_handler($hook, $type, $url, $params) {
        $entity = $params['entity'];

        // Check that the entity is a photo object
        if ($entity->getSubtype() !== 'photo') {
            // This is not a photo object, so there's no need to go further
            return;
        }

        return "photo/view/{$entity->guid}";
    }

.. warning::

    Not compatible with 1.8

Web services
------------

In Elgg 1.8 the web services API was included in core and methods were exposed
using ``expose_function()``. To enable the same functionality for Elgg 1.9,
enable the "Web services 1.9" plugin and replace all calls to
``expose_function()`` with  ``elgg_ws_expose_function()``.

From 1.7 to 1.8
===============
Elgg 1.8 is the biggest leap forward in the development of Elgg since version 1.0.
As such, there is more work to update core and plugins than with previous upgrades.
There were a small number of API changes and following our standard practice,
the methods we deprecated have been updated to work with the new API.
The biggest changes are in the standardization of plugins and in the views system.


Updating core
-------------
Delete the following core directories (same level as _graphics and engine):

* _css
* account
* admin
* dashboard
* entities
* friends
* search
* settings
* simplecache
* views

.. warning::

   If you do not delete these directories before an upgrade, you will have problems!


Updating plugins
----------------

Use standardized routing with page handlers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* All: /page_handler/all
* User’s content: /page_handler/owner/:username
* User’s friends' content: /page_handler/friends/:username
* Single entity: /page_handler/view/:guid/:title
* Added: /page_handler/add/:container_guid
* Editing: /page_handler/edit/:guid
* Group list: /page_handler/group/:guid/all


Include page handler scripts from the page handler
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Almost every page handler should have a page handler script.
(Example: ``bookmarks/all => mod/bookmarks/pages/bookmarks/all.php``)

* Call ``set_input()`` for entity guids in the page handler and use ``get_input()`` in the page handler scripts.
* Call ``gatekeeper()`` and ``admin_gatekeeper()`` in the page handler function if required.
* The group URL should use the ``pages/:handler/owner.php`` script.
* Page handlers should not contain HTML.
* Update the URLs throughout the plugin. (Don't forget to remove ``/pg/``!)


Use standardized page handlers and scripts
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* Store page handler scripts in ``mod/:plugin/pages/:page_handler/:page_name.php``
* Use the content page layout in page handler scripts:

  .. code:: php

     $content = elgg_view_layout('content', $options);

* Page handler scripts should not contain HTML.
* Call ``elgg_push_breadcrumb()`` in the page handler scripts.
* No need to set page owner if the URLs are in the standardized format.
* For group content, check the container_guid by using elgg_get_page_owner_entity().


The ``object/:subtype`` view
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* Make sure there are views for ``$vars['full_view'] == true`` and ``$vars['full_view'] == false``. ``$vars['full_view']`` replaced ``$vars['full]``.
* Check for the object in ``$vars['entity']``. Use ``elgg_instance_of()`` to make sure it's the type of entity you want.
* Return ``true`` to short circuit the view if the entity is missing or wrong.
* Use ``elgg_view(‘object/elements/summary’, array(‘entity’ => $entity));`` and ``elgg_view_menu(‘entity’, array(‘entity’ => $entity));`` to help format. You should use very little markup in these views.


Update action structure
~~~~~~~~~~~~~~~~~~~~~~~
* Namespace action files and action names (example: ``mod/blog/actions/blog/save.php`` => ``action/blog/save``)
* Use the following action URLs:

  * Add: ``action/:plugin/save``
  * Edit: ``action/:plugin/save``
  * Delete: ``action/:plugin/delete``

* Make the delete action accept ``action/:handler/delete?guid=:guid`` so the metadata entity menu has the correct URL by default.


Update deprecated functions
~~~~~~~~~~~~~~~~~~~~~~~~~~~
* Functions deprecated in 1.7 will produce visible errors in 1.8.
* You can also update functions deprecated in 1.8.

  * Many registration functions simply added an ``elgg_`` prefix for consistency, and should be easy to update.
  * See ``/engine/lib/deprecated-1.8.php`` for the full list.
  * You can set the debug level to “warning” to get visual reminders of deprecated functions.


Update the widget views
~~~~~~~~~~~~~~~~~~~~~~~
See the blog or file widgets for examples.


Update the group profile module
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Use the blog or file plugins for examples. This will help with making your plugin themeable by the new CSS framework.


Update forms
~~~~~~~~~~~~
* Move form bodies to the ``forms/:action`` view to use Evan's new ``elgg_view_form``.
* Use input views in form bodies rather than html. This helps with theming and future-proofing.
* Add a function that prepares the form (see ``mod/file/lib/file.php`` for an example)
* Make your forms sticky (see the file plugin's upload action and form prepare function).

The forms API is discussed in more detail in :doc:`/guides/actions`.


Clean up CSS/HTML
~~~~~~~~~~~~~~~~~
We have added many CSS patterns to the base CSS file (modules, image block, spacing primitives). We encourage you to use these patterns and classes wherever possible. Doing so should:

1. Reduce maintenance costs, since you can delete most custom CSS.
2. Make your plugin more compatible with community themes.

Look for patterns that can be moved into core if you need significant CSS.

We use hyphens rather than underscores in classes/ids and encourage you do the same for consistency.

If you do need your own CSS, you should use your own namespace, rather than ``elgg-``.


Update manifest.xml
~~~~~~~~~~~~~~~~~~~
* Use http://el.gg/manifest17to18 to automate this.
* Don't use the "bundled" category with your plugins. That is only for plugins distributed with Elgg.


Update settings and user settings views
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* The view for settings is now ``plugins/:plugin/settings`` (previously ``settings/:plugin/edit``).
* The view for user settings is now ``plugins/:plugin/usersettings`` (previously ``usersettings/:plugin/edit``).
