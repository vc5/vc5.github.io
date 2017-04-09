---
title: Hexo-with-Travis&Qiniu
date: 2017-04-08 01:01:59
tags:
---
#  预期效果
因为经常在不同的电脑间切换，所以采用Hexo写博客有点不方便。
本文想要实现随时换电脑都可以方便的写博客，以及同时保证在主力机器上可以本地部署。
#  Hexo配置
```
## 七牛同步
qiniu:
  offline: false
  sync: true
  # bucket_name请替换为自己的
  bucket: bucket_name
  secret_file: secret/qn.json
  dirPrefix: vc5
  urlPrefix: http://7xn70q.com1.z0.glb.clouddn.com/vc5
  up_host: http://upload.qiniu.com
  local_dir: static
  update_exist: true
  image: 
    folder: images
    extend: 
  js:
    folder: js
  css:
    folder: css
  
# 部署
deploy:
- type: git
  repo: 
      github: git@vc5.github.com:vc5/vc5.github.io.git,master
      coding: git@git.coding.net:intelligentvincent/intelligentvincent.git,coding-pages
```

#  Travis配置
`.travis.yml`
```yaml
language: node_js
node_js: stable
install:
- npm install
script:
- hexo qiniu s
- hexo g
- hexo d
- rm -rf ~/.ssh secret
branches:
  only:
  - hexo
before_install:
- mkdir secret
- openssl aes-256-cbc -K $encrypted_60db10461485_key -iv $encrypted_60db10461485_iv
  -in .travis/qn.json.enc -out secret/qn.json -d
- openssl aes-256-cbc -K $encrypted_c2f92b25f22f_key -iv $encrypted_c2f92b25f22f_iv
  -in .travis/id_rsa.enc -out ~/.ssh/id_rsa -d
- chmod 600 ~/.ssh/id_rsa
- eval $(ssh-agent)
- ssh-add ~/.ssh/id_rsa
- cp .travis/ssh_config ~/.ssh/config
- git config --global user.name "Vincent"
- git config --global user.email "intelligentvincent@gmail.com"

```
##  密钥问题
在安装了gem的电脑上运行`travis`
#  七牛云同步
##  密钥问题


未完待续