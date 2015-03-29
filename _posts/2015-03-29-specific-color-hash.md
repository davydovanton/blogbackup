---
layout: post
title: "Создание color hash-а для любой строки"
tags:
  - ruby
---

Так случатся, что иногда нужно из строки сделать color hash. Как мне кажется, самый простой способ - использовать `Digest::MD5`. Ддя этого достаточно вызывать метод `hexdigest` и передать в него нужную строку:

``` ruby
Digest::MD5.hexdigest('My string')[0..5] # => 'a537d0'
```

Ну а если вы хотите сделать rgb, то достаточно каждые 2 симвора из color hash переобразовать в 10 ричную сисему с помощью `to_i(16)`:

``` ruby
Digest::MD5.hexdigest(worker)[0..5]
  .scan(/../)
  .map{ |color| color.to_i(16) }
```
