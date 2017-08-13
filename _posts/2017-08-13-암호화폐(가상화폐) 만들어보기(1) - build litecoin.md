---
layout: post
title:  "암호화폐(가상화폐) 만들어 보기(1) - litecoin build"
date:   2017-08-13 17:00:00
categories: [CryptoCurrency]
comments: true
---

암호화폐를 하나 만들어보고 싶었는데, 아래의 글을 찾았다. 
https://bitcointalk.org/index.php?topic=225690.0

대충 보아하니 LiteCoin 기반으로 구현하는 것이고 연습삼아 한번 해볼만 해보인다.
연습삼아 Step By Step 으로 따라하기에는 많은 부분이 생략된 글이긴 하다.

https://github.com/litecoin-project/litecoin

1. 소스 다운로드하거나 Clone
{% highlight shell %}
git clone https://github.com/litecoin-project/litecoin.git/Users/Sunki/jekyll/sunki-lee.github.io/_posts/2017-08-13-그는 당신에게 반하지 않았다.1.md
{% endhighlight &}


2. Build
포함된 문서를 환경에 맞게 참고하여 빌드
https://github.com/litecoin-project/litecoin/blob/master/doc/build-osx.md

xcode command line tool, homebrew 설치 후 dependencies
{% highlight shell %}
xcode-select --install
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

brew install automake berkeley-db4 libtool boost --c++11 miniupnpc openssl pkg-config protobuf --c++11 qt5 libevent
brew install librsvg

./autogen.sh
./configure
make
{% endhighlight %}

configure 실행시 error: No working boost sleep implementation found. 에러가 발생하면서 진행이 안되었는데
boost install도 다시해보고 아래 처럼 unlink/link도 하다보니 해결되었다.
{% highlight shell %}
brew unlink boost
brew link boost
{% endhighlight %}

