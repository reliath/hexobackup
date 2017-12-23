---
title: Orthodox C++
thumbnail: /images/cpp.jpg
comments: true
categories:
  - Programming
tags:
  - Etc
date: 2017-08-05 02:05:35
---

# Orthodox C++

이 글은 C++을 사용하는 스타일에 대한 글입니다.

이 글은 기본적으로 당신이 C++에 숙달되었으며, C언어를 알고 있으며, 상업적인 프로그래머인 것을 가정하고 쓰여진 글입니다. C언어를 제대로 배우지 않았고, C++을 상업적인 프로젝트에서 5년이상 사용하지 않았다면, 브라우져 백버튼을 누르는 것이 옳은 선택입니다.

C++은 자유로운 언어이며, 이 글은 단지 Modern C++을 폄하하는 글이 아닙니다. 당신이 게임 엔진을 만드는 사람이고, 아주 고성능의 코드가 필요한 경우, 선택할 수 있는 C++ 사용 스타일의 하나일 뿐입니다.

번역문이며, [원문](https://gist.github.com/bkaradzic/2e39896bc7d8c34e042b)은 이곳입니다.

## Orthodox C++ 이란?

Orthodox C++이란 (때로는 그냥 **C+** 이라고 지칭되는) C++의 아주 작은 집합체로서 C언어를 개선한 것을 의미합니다, 그러나 Modern C++이라 불리는 모든 것을 제외했습니다. 사실상 [Modern C++](https://stackoverflow.com/questions/3661237/what-is-modern-c)의 정반대 개념이라고 할 수 있습니다.

## Modern C++ 은 왜 아닌가?

1990년대 우리는 C++을 열렬히 사랑했고, 모든 최신 기능들을 사용했으며, 모든 사람이 그렇게 해야한다고 말하고 다녔습니다. 시간이 흐른 뒤에 우리는 몇몇 기능들 불필요하다는 것을 알게 되었으며, 심지어는 몇몇 좋지 않다고 판명난 기능들( RTTI, Exceptions, Streams같은)은 실제로 코드 복잡도를 쓸데없이 증가시켜 역효과를 일으킨다는 것 또한 알게 되었습니다. 이 생각이 말도 안된다고 생각한다면 그냥 그 상태로 몇 년을 더 개발하시면 됩니다, 그러면 아마 자연히 Modern C++이 싫어지게 되실 겁니다. [이 글을 읽어보셔도 좋습니다.](http://archive.is/2016.05.17-214038/https://www.linkedin.com/pulse/why-i-dont-spend-time-modern-c-anymore-henrique-bucher-phd)
 
## 왜 Orthodox C++를 선택하는가?

Orthodox C++의 제약을 가지고 짜여진 코드는 이해하기 쉽고 간단하며, 구버젼 컴파일러에서 잘 빌드됩니다. 프로젝트가 Orthodox C++의 문법으로 작성되었다면, 다른 C++ 프로젝트과 잘 어울립니다. Orthodox C++의 문법은 다른 C++의 프로젝트들의 문법을 위반하지 않습니다. 즉 문법적 충돌을 일으키지 않습니다.

## Hello World in Orthodox C++

``` cpp
	#include <stdio.h>

	int main()
	{
	    printf("hello, world\n");
	    return 0;
	}
```

## 그래서 정확히 뭘 하라는 건가?

 - C 처럼 C++을 짜면 된다. 굳이 C++의 추가 기능이 필요없다면 이 것으로 충분하다. 보통 C처럼 짜여진 코드는 읽기 편하다.
 - [이런 방식](http://archive.is/2014.04.28-125041/http://www.boost.org/doc/libs/1_55_0/libs/geometry/doc/html/geometry/design.html)의 코드를 짜지마라, Orthodox C++의 '디자인의 이론적 근거'는 "아주 간단하게,그리고 실용적으로 작성하자. EOF."이다.
 - exceptions 을 쓰지 않는다.
 - RTTI 을 쓰지 않는다.
 - C 런타임에 대한 C++ 런타임 wrapper (`<cstdio>`, `<cmath>`, etc.)를 쓰지 않는다, 그냥 C 런타임을 사용하자. (`<stdio.h>`, `<math.h>`, etc.)
 - stream 을 쓰지 않는다. (`<iostream>`, `<stringstream>`, etc.), printf style 함수들을 사용한다.
 - 메모리를 내부적으로 할당하는 STL은 사용하지 않는다, 메모리 관리를 아예 신경쓰지 않는 경우가 아니라면 말이다.
 - metaprogramming을 쓰지 않는다. 꼭 써야 한다면, 코드량이 정말 획기적으로 주는 경우에, 꼭 필요하다고 판단될 때, 아주 절제해서 사용한다.

## 현대적인 C++의 기능 및 문법은 언제쯔음 사용해도 괜찮을지?

C++ 컴파일러들이 새로운 문법에 적응하고, 운영체제에 배포되기 전까지는 시간이 걸린다, 따라서 바로 새로운 언어적 기능들을 사용할 수는 없다. 일반적인 가이드라인은, 현재 년수가 **C++언어스펙 년수 + 5** 가 되면 슬슬 사용해도 된다. 예를 들자면 C++11의 경우 2016년 이후 부터 사용해도 괜찮다라는 뜻이다. 즉 2016년에 C++17을 사용한다는 건, 그냥 말그대로 개념적 코딩을 하고 있을 뿐이며, 오픈 소스 에서 이런 짓을 하면 다른 사람들이 사용할 수 없는 것을 만들게 된다.

## 비슷한 생각들이 존재하는지?

 - [Embedded C++](https://en.wikipedia.org/wiki/Embedded_C%2B%2B)
 - [Nominal C++](http://archive.is/2016.08.07-162105/https://namandixit.github.io/blog/nominal-c++/)
 - [Sane C++](http://archive.is/2016.08.07-162220/http://flohofwoe.blogspot.nl/2013/06/sane-c.html)
 - [Why Your C++ Should Be Simple](http://archive.fo/2017.03.19-055108/https://hacksoflife.blogspot.nl/2017/03/why-your-c-should-be-simple.html)
 
## 코드 예제들
-------------

 - 모든 C++ 컴파일러에서 동작하는 C 소스들
 - [DOOM 3 BFG](https://github.com/id-Software/DOOM-3-BFG)
 - [Qt](https://github.com/qtproject) (no-rtti, no-exceptions으로 빌드한 경우)
 - [dear imgui](https://github.com/ocornut/imgui)
 - [bgfx](https://github.com/bkaradzic/bgfx)