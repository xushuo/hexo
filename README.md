# hexo
博客项目

NEXT 配置
# ---------------------------------------------------------------
# Site Information Settings
# ---------------------------------------------------------------

# Put your favicon.ico into `hexo-site/source/` directory.
favicon: /favicon.ico

# Set default keywords (Use a comma to separate)
keywords: "Hexo, NexT, xs"

# Set rss to false to disable feed link.
# Leave rss as empty to use site's feed link.
# Set rss to specific value if you have burned your feed already.
rss:

# Specify the date when the site was setup
since: 2017

# icon between year and author @Footer
authoricon: heart

# Footer `powered-by` and `theme-info` copyright
copyright: true

# Canonical, set a canonical link tag in your hexo, you could use it for your SEO of blog.
# See: https://support.google.com/webmasters/answer/139066
# Tips: Before you open this tag, remember set up your URL in hexo _config.yml ( ex. url: http://yourdomain.com )
canonical: true

# Change headers hierarchy on site-subtitle (will be main site description) and on all post/pages titles for better SEO-optimization.
seo: false

# ---------------------------------------------------------------
# Menu Settings
# ---------------------------------------------------------------

# When running the site in a subdirectory (e.g. domain.tld/blog), remove the leading slash (/archives -> archives)
menu:
  home: /
  categories: /categories
  #about: /about
  archives: /archives
  tags: /tags
  #sitemap: /sitemap.xml
  #commonweal: /404.html


# Enable/Disable menu icons.
# Icon Mapping:
#   Map a menu item to a specific FontAwesome icon name.
#   Key is the name of menu item and value is the name of FontAwesome icon. Key is case-senstive.
#   When an question mask icon presenting up means that the item has no mapping icon.
menu_icons:
  enable: true
  #KeyMapsToMenuItemKey: NameOfTheIconFromFontAwesome
  home: home
  about: user
  categories: th
  schedule: calendar
  tags: tags
  archives: archive
  sitemap: sitemap
  commonweal: heartbeat




# ---------------------------------------------------------------
# Scheme Settings
# ---------------------------------------------------------------

# Schemes
scheme: Muse
#scheme: Mist
#scheme: Pisces


# ---------------------------------------------------------------
# Font Settings
# - Find fonts on Google Fonts (https://www.google.com/fonts)
# - All fonts set here will have the following styles:
#     light, light italic, normal, normal italic, bold, bold italic
# - Be aware that setting too much fonts will cause site running slowly
# - Introduce in 5.0.1
# ---------------------------------------------------------------
font:
  enable: true

  # Uri of fonts host. E.g. //fonts.googleapis.com (Default)
  host:

  # Global font settings used on <body> element.
  global:
    # external: true will load this font family from host.
    external: true
    family: Lato

  # Font settings for Headlines (h1, h2, h3, h4, h5, h6)
  # Fallback to `global` font settings.
  headings:
    external: true
    family:

  # Font settings for posts
  # Fallback to `global` font settings.
  posts:
    external: true
    family:

  # Font settings for Logo
  # Fallback to `global` font settings.
  # The `size` option use `px` as unit
  logo:
    external: true
    family:
    size:

  # Font settings for <code> and code blocks.
  codes:
    external: true
    family:
    size:




# ---------------------------------------------------------------
# Sidebar Settings
# ---------------------------------------------------------------


# Social Links
# Key is the link label showing to end users.
# Value is the target link (E.g. GitHub: https://github.com/iissnan)
social:
  #LinkLabel: Link
  GitHub: https://github.com/xushuo

# Social Links Icons
# Icon Mapping:
#   Map a menu item to a specific FontAwesome icon name.
#   Key is the name of the item and value is the name of FontAwesome icon. Key is case-senstive.
#   When an globe mask icon presenting up means that the item has no mapping icon.
social_icons:
  enable: true
  # Icon Mappings.
  # KeyMapsToSocialItemKey: NameOfTheIconFromFontAwesome
  GitHub: github
  Twitter: twitter
  Weibo: weibo


# Sidebar Avatar
# in theme directory(source/images): /images/avatar.jpg
# in site  directory(source/uploads): /uploads/avatar.jpg
avatar: /images/avatar.jpg


# Table Of Contents in the Sidebar
toc:
  enable: true

  # Automatically add list number to toc.
  number: true


# Creative Commons 4.0 International License.
# http://creativecommons.org/
# Available: by | by-nc | by-nc-nd | by-nc-sa | by-nd | by-sa | zero
#creative_commons: by-nc-sa
#creative_commons:


sidebar:
  # Sidebar Position, available value: left | right
  position: left
  #position: right

  # Sidebar Display, available value:
  #  - post    expand on posts automatically. Default.
  #  - always  expand for all pages automatically
  #  - hide    expand only when click on the sidebar toggle icon.
  #  - remove  Totally remove sidebar including sidebar toggle.
  display: post
  #display: always
  #display: hide
  #display: remove

  # Sidebar offset from top menubar in pixels.
  offset: 12
  offset_float: 0

  # Back to top in sidebar
  b2t: false

  # Scroll percent label in b2t button
  scrollpercent: false


# Blog rolls
#links_title: Links
#links_layout: block
#links_layout: inline
#links:
  #Title: http://example.com/


# ---------------------------------------------------------------
# Post Settings
# ---------------------------------------------------------------

# Automatically scroll page to section which is under <!-- more --> mark.
scroll_to_more: true

# Automatically excerpt description in homepage as preamble text.
excerpt_description: true

# Automatically Excerpt. Not recommend.
# Please use <!-- more --> in the post to control excerpt accurately.
auto_excerpt:
  enable: true
  length: 150

# Post meta display settings
post_meta:
  item_text: true
  created_at: true
  updated_at: false
  categories: true

# Post wordcount display settings
# Dependencies: https://github.com/willin/hexo-wordcount
post_wordcount:
  item_text: true
  wordcount: false
  min2read: false

# Wechat Subscriber
#wechat_subscriber:
  #enabled: true
  #qcode: /path/to/your/wechatqcode ex. /uploads/wechat-qcode.jpg
  #description: ex. subscribe to my blog by scanning my public wechat account



# ---------------------------------------------------------------
# Misc Theme Settings
# ---------------------------------------------------------------

# Custom Logo.
# !!Only available for Default Scheme currently.
# Options:
#   enabled: [true/false] - Replace with specific image
#   image: url-of-image   - Images's url
custom_logo:
  enabled: false
  image:


# Code Highlight theme
# Available value:
#    normal | night | night eighties | night blue | night bright
# https://github.com/chriskempson/tomorrow-theme
highlight_theme: normal


# ---------------------------------------------------------------
# Third Party Services Settings
# ---------------------------------------------------------------

# MathJax Support
mathjax:
  enable: false
  per_page: false
  cdn: //cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML


# Swiftype Search API Key
#swiftype_key:

# Baidu Analytics ID
baidu_analytics: 7e8851498eec67be493f9887c5c72501

# Duoshuo ShortName
duoshuo_shortname: xushuo

# Disqus
#disqus_shortname:

# Hypercomments
#hypercomments_id:

# Gentie productKey
#gentie_productKey:

# Support for youyan comments system.
# You can get your uid from http://www.uyan.cc
#youyan_uid: your uid

# Support for LiveRe comments system.
# You can get your uid from https://livere.com/insight/myCode (General web site)
#livere_uid: your uid

# Baidu Share
# Available value:
#    button | slide
# Warning: Baidu Share does not support https.
#baidushare:
##  type: button

# Share
#jiathis:
# Warning: JiaThis does not support https.
#add_this_id:

# Share
duoshuo_share: true

# Google Webmaster tools verification setting
# See: https://www.google.com/webmasters/
#google_site_verification:

# Google Analytics
#google_analytics:

# Yandex Webmaster tools verification setting
# See: https://webmaster.yandex.ru/
#yandex_site_verification:

# CNZZ count
#cnzz_siteid:

# Application Insights
# See https://azure.microsoft.com/en-us/services/application-insights/
# application_insights:

# Make duoshuo show UA
# user_id must NOT be null when admin_enable is true!
# you can visit http://dev.duoshuo.com get duoshuo user id.
duoshuo_info:
  ua_enable: true
  admin_enable: true
  user_id: 91bf4c3a712203aac2c250cea3b0b98c
  admin_nickname: 表闹蛋蛋酱


# Facebook SDK Support.
# https://github.com/iissnan/hexo-theme-next/pull/410
facebook_sdk:
  enable: false
  app_id:       #<app_id>
  fb_admin:     #<user_id>
  like_button:  #true
  webmaster:    #true

# Facebook comments plugin
# This plugin depends on Facebook SDK.
# If facebook_sdk.enable is false, Facebook comments plugin is unavailable.
facebook_comments_plugin:
  enable: false
  num_of_posts: 10  # min posts num is 1
  width: 100%       # default width is 550px
  scheme: light     # default scheme is light (light or dark)

# VKontakte API Support.
# To get your AppID visit https://vk.com/editapp?act=create
vkontakte_api:
  enable: false
  app_id:       #<app_id>
  like:         true
  comments:     true
  num_of_posts: 10


# Show number of visitors to each article.
# You can visit https://leancloud.cn get AppID and AppKey.
leancloud_visitors:
  enable: true
  app_id: fgplu58hnb8VHcpyhwGRImYX-gzGzoHsz
  app_key: GQ7t1KolkJ50r7tPqibJxpq5

# Show PV/UV of the website/page with busuanzi.
# Get more information on http://ibruce.info/2015/04/04/busuanzi/
busuanzi_count:
  # count values only if the other configs are false
  enable: true
  # custom uv span for the whole site
  site_uv: true
  site_uv_header: 本站访客数
  site_uv_footer: 人次
  # custom pv span for the whole site
  site_pv: true
  site_pv_header: 本站总访问量
  site_pv_footer: 次
  # custom pv span for one page only
  page_pv: true
  page_pv_header: <i class="fa fa-file-o"></i>
  page_pv_footer:


# Tencent analytics ID
# tencent_analytics: 61072188

# Tencent MTA ID
# tencent_mta:


# Enable baidu push so that the blog will push the url to baidu automatically which is very helpful for SEO
baidu_push: true

# Google Calendar
# Share your recent schedule to others via calendar page
#
# API Documentation:
# https://developers.google.com/google-apps/calendar/v3/reference/events/list
calendar:
  enable: false
  calendar_id: <required>
  api_key: <required>
  orderBy: startTime
  offsetMax: 24
  offsetMin: 4
  timeZone:
  showDeleted: false
  singleEvents: true
  maxResults: 250

# Algolia Search
algolia_search:
  enable: false
  hits:
    per_page: 10
  labels:
    input_placeholder: 查询
    hits_empty: "查询无相关结果: ${query}"
    hits_stats: "${hits} 条结果,用时 ${time} ms"
  applicationID: RG0G2PXALM
  apiKey: 9c2d424667dcce6827b37cd811607fd6
  adminApiKey: fef8fc43f069eb8549221cc425d1c560
  indexName: hexo
  chunkSize: 5000
  fields:
      - title
      - slug
      - content:strip

# Local search
local_search:
  enable: true
  path: search.xml
  field: post
  format: html
  limit: 10000


# External URL with BASE64 encrypt & decrypt
# Usage: {% exturl text url "title" %}
# Alias: {% extlink text url "title" %}
exturl: false


#! ---------------------------------------------------------------
#! DO NOT EDIT THE FOLLOWING SETTINGS
#! UNLESS YOU KNOW WHAT YOU ARE DOING
#! ---------------------------------------------------------------

# Motion
use_motion: true

# Fancybox
fancybox: true

# Canvas-nest
canvas_nest: false

# Script Vendors.
# Set a CDN address for the vendor you want to customize.
# For example
#    jquery: https://ajax.googleapis.com/ajax/libs/jquery/2.2.0/jquery.min.js
# Be aware that you should use the same version as internal ones to avoid potential problems.
# Please use the https protocol of CDN files when you enable https on your site.
vendors:
  # Internal path prefix. Please do not edit it.
  _internal: lib

  # Internal version: 2.1.3
  jquery:

  # Internal version: 2.1.5
  # See: http://fancyapps.com/fancybox/
  fancybox:
  fancybox_css:

  # Internal version: 1.0.6
  # See: https://github.com/ftlabs/fastclick
  fastclick:

  # Internal version: 1.9.7
  # See: https://github.com/tuupola/jquery_lazyload
  lazyload:

  # Internal version: 1.2.1
  # See: http://VelocityJS.org
  velocity:

  # Internal version: 1.2.1
  # See: http://VelocityJS.org
  velocity_ui:

  # Internal version: 0.7.9
  # See: https://faisalman.github.io/ua-parser-js/
  ua_parser:

  # Internal version: 4.6.2
  # See: http://fontawesome.io/
  fontawesome:

  # Internal version: 1
  # https://www.algolia.com
  algolia_instant_js:
  algolia_instant_css:

  # Internal version: 1.0.0
  # https://github.com/hustcc/canvas-nest.js
  canvas_nest:



# Assets
css: css
js: js
images: images

# Theme version
version: 5.1.0
