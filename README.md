# Genel CSS notları, tavsiyeleri ve prensipler

---

## Çeviriler

* [English](https://github.com/csswizardry/CSS-Guidelines/blob/master/README.md)
* [русский](https://github.com/matmuchrapna/CSS-Guidelines/blob/master/README%20Russian.md)
* [中国的](https://github.com/chadluo/CSS-Guidelines/blob/master/README.md)
* [Français](https://github.com/flexbox/CSS-Guidelines/blob/master/README.md)
* [日本の](https://github.com/kiwanami/CSS-Guidelines/blob/master/README.ja.md)
* [Türkçe](https://github.com/rssems/CSS-Rehberi/blob/master/README.md)


---


Birçok geliştirici ile birlikte büyük ve uzun vadeli projeler üzerinde çalışırken, hepimizin farklı alanlar üzerinde de olsa belirli bir düzen halinde çalışmamız oldukça önemlidir, bunun için de:

* Stil dosyalarını sürdürülebilir ve ölçeklenebilir tutmak
* Kodun okunabilir ve anlaşılır olması 

gerekmektedir. Bu ideali gerçekleştirmek için uygulanması gereken çeşitli teknikler bulunmaktadır. 

Bu dökümanın ilk bölümünde sözdizimi (syntax), biçim (formatting) ve CSS yapısı ile ilgileneceğiz, ikinci bölümde ise yaklaşım, akılcı bakış ve CSS yazma ve mimarisine yönelik fikirler ile ilgileneceğiz. Heyecan verici, di mi?


## İçerik

* [CSS döküman yapısı](#$todo)
  * [Genel](#genel)
  * [Tek ve çok dosya karşılaştırması](#$todo)
  * [İçindekiler](#$todo)
  * [Bölüm başlıkları](#$todo)
* [Kaynağa göre sıralama](#$todo)
* [Kural Setleri](#$todo)
* [İsimlendirme Düzeni](#$todo)
  * [JS hooks](#$todo)
  * [Internationalisation](#$todo)
* [Comments](#$todo)
  * [Comments on steroids](#$todo)
    * [Quasi-qualified selectors](#$todo)
    * [Tagging code](#$todo)
    * [Object/extension pointers](#$todo)
* [Writing CSS](#$todo)
* [Building new components](#$todo)
* [OOCSS](#$todo)
* [Layout](#$todo)
* [Sizing UIs](#$todo)
  * [Font sizing](#$todo)
* [Shorthand](#$todo)
* [IDs](#$todo)
* [Selectors](#$todo)
  * [Over qualified selectors](#$todo)
  * [Selector performance](#$todo)
* [CSS selector intent](#$todo)
* [`!important`](#important)
* [Magic numbers and absolutes](#$todo)
* [Conditional stylesheets](#$todo)
* [Debugging](#$todo)
* [Preprocessors](#$todo)

---

## CSS Döküman Yapısı

Döküman farketmezsizin, biz her zaman ortak biçimlendirme kullanmaya çalışmalıyız. Bunun anlamı tutarlı yorumlama, tutarlı sözdizimi ve tutarlı isimlendirmedir.

### Genel

Stil dosyalarınızı en fazla 80 karakter genişlikte limitlemeye çalışın.
Degrade (gradient) ve yorum olarak eklenmiş linkler istisna olarak kabul edilebilir, ki bu konuda yapabileceğimiz bir şey yok.

Ben elementlerde birden çok özellik tanımlarken veya tab kullanımında dört (4) boşluk girinti (indent) kullanmayı tercih ediyorum.

### Tek ve çok dosya karşılaştırması

Bazı insanlar tek ve büyük bir dosya ile çalışmayı tercih ederler ve bunda herangi problem olmamakla birlikte aşağıdaki rehberi takip ettiğiniz taktirde hiçbir problemle karşılaşmamaya devam edeceksiniz. 

Sass'a geçtiğimden beri ben stil dosyalarımı olabildiğince küçük parçaların birleşimi halinde tutmaya başladım ve bunda da herangi bir problem yok. 

Hangi yöntemi kullanırsanız kullanın, aşağıdaki kurallar ve prensipler geçerli olacaktır. Tek farkın içindekiler bölümü ve bölüm başlıkları olacağını birazdan göreceksiniz.


### İçindekiler

Stil dosyasının en başında, bölümlerin başlıklarının ve açıklamalarının yer aldığı içindekiler bölümünü sürekli güncel tutuyorum, örneğin:

    /*------------------------------------*\
        $ICINDEKILER
    \*------------------------------------*/
    /**
     * ICINDEKILER...........Okumakta oldugun sey!
     * NORMALIZE.............Tarayicilari tutarli ve cagdas olmaya zorlamaca
     * FONT-FACE.............Kullanilan ozel font dosyalarini tanimlamaca
     */

Bu geliştiricilere dosyada tam olarak neyi bulabileceklerini belirtmekte. İçindekiler bölümündeki her bir öge, ilgili bölüm başlılığı ile bire-bir eşleşmektedir.

Eğer tek ve büyük bir stil dosyası üzerinde çalışıyorsanız, benzer bir yapı kullanıyor olacaksınız. Eğer farklı dosyalar bütünü ile çalışıyorsanız içindekiler bölümünde ilgili çağırdığı dosyaları da belirtmelisiniz.

> Çevirmenin Notu: Orijinal metinde reset.css kullanılarak anlatım yapılmasına rağmen normalize.css 'i desteklediğimden ötürü ilgili yerler tarafımca düzenlenerek çevrilmiştir ve çevrilmekte olacaktır.

### Bölüm başlıkları

İçindekiler bölümündeki başlıklar ile bölüm başlıkları eşleşmezse tamamen anlamsız olacaktır. Bir bölümü bu şekilde gösterebilirsiniz:

    /*------------------------------------*\
        $NORMALIZE
    \*------------------------------------*/

Önüne eklediğimiz `$` ile aramalarımızda ([Cmd|Ctrl]+F), `$[BOLUM-ISMI]` sorgusu ile **kapsamımızı bölüm başlıkları ile limitleyebiliyor** olacağız.

Eğer tek ve büyük bir stil dosyası üzerinde çalışıyorsanız, her bölüm arasına beş (5) satır boşluk bırakınız, örneğin:

    /*------------------------------------*\
        $NORMALIZE
    \*------------------------------------*/
    [Normallesmesi
    gereken
    stiller]





    /*------------------------------------*\
        $FONT-FACE
    \*------------------------------------*/

Bu boşluk hızlıca scroll ettiğimizde bölüm sonlarının farkedilebilirlir olmasını sağlayacaktır.

Eğer çoklu ve içe çağrılan stil dosyaları ile çalışıyorsunuz, her bir dosya için bölüm başlığı oluşturarak başlayın fakat bu durumda bölümler arası boşluk kullanmanıza gerek yoktur.


## Kaynağa göre sıralama

Stil kodlarınızı kullanım sıranıza göre yazmaya çalışın. 

Try and write stylesheets in specificity order. Bu sadece kalıtım (inheritance) ve CSS'in <i>C</i>i olan basamaklı dizilimden (cascade) kelimenin tam anlamıyla faydalanmanızı sağlar.

Sıralaması iyi yapılmış bir stil dosyası örneği:

1. **Normalize** – tarayıcıları normalleştirme.
2. **Elementler** – genel `h1`, `ul` özellikleri gibi
3. **Objeler ve ortak sınıflar** — genel ve temel tasarım örüntüleri (design patterns)
4. **Bileşenler** – bileşenler ve bileşenleri meydana getiren objeler ve uzantıları
5. **Diğer stiller** – hata durumları gibi.

Bunun anlamı, dökümanda aşağı indikçe her bölüm mantıklı bir şekilde kalıtım sırasına göre oluşmuş olacaktır. Böylece daha az felaketle, seçici sorunlarıyla veya olası problemleri çevresinden dolaşarak çözmeye gerek kalmadan daha iyi bir CSS yapısı kurmuş olacaksınız.

Daha fazla bilgi için Jonathan Snook’un [SMACSS](http://smacss.com) isimli kitabını inceleyebilirsiniz.

## Kural Setleri

    [secici]{
        [ozellik]:[deger];
        [<- ifade ->]
    }

Kural setlerini oluştururken kullandığım standartlar:

* Tire ile ayrılmış class isimleri kullanın (BEM isimlendirme metolojisi hariç,
  [aşağıya bakınız](#$todo)).
* 4 boşluk girinti (indent) bırakın.
* Her satırda bir özellik tanımlayın.
* Alakaya göre sıralama (ALFABEYE GÖRE DEĞİL) yapın.
* Vendor ön eklerinde girintiler kullanarak ana ozelligi ve degerleri hizalı hale getirin.
* DOM görüntüsüne ayna tutarcasına çocuk (child) seçicileri girinti ile kullanın.
* Always include the final semi-colon in a ruleset $todo

Kısa bir örnek:

    .bilesen{
        padding:10px;
        border:1px solid #BADA55;
        background-color:#C0FFEE;
        -webkit-border-radius:4px;
           -moz-border-radius:4px;
                border-radius:4px;
    }
        .bilesen-baslik{
            font-size:1.5rem;
            line-height:1;
            font-weight:bold;
            color:#BADA55;
            margin-right:-10px;
            margin-left: -10px;
            padding:0.25em;
        }

Örnekte gördüğünüz gibi `.bilesen-baslik`,  `.bilesen` elementinin çocuğu olmalı, bu nedenden ötürü de `.bilesen-baslik`ı, `.bilesen`e göre bir level daha derin girintide kullandık. Bu sayede bir başka geliştirici tek bakışta girintiler sayesinde DOMu gözünde canlandırabilir.


Ayrıca `.bilesen-baslik`'in bildirimlerinin alakalarına göre sıralandığını görebiliriz, `.bilesen-baslik` isminden de belli olduüu gibi metne dair bir element olmalı, dolayısıyla metin kurallarını tanımlayarak başladık, ardından diğer tanımlamaları yaptık.

Izgara (grid) yapı tanımlamaları, daha önce belirttiğim 'Her satırda bir özellik tanımlama' kuralının istisnası sayılabilir. Örneğin:

    .t10    { width:10% }
    .t20    { width:20% }
    .t25    { width:25% }       /* 1/4 */
    .t30    { width:30% }
    .t33    { width:33.333% }   /* 1/3 */
    .t40    { width:40% }
    .t50    { width:50% }       /* 1/2 */
    .t60    { width:60% }
    .t66    { width:66.666% }   /* 2/3 */
    .t70    { width:70% }
    .t75    { width:75% }       /* 3/4*/
    .t80    { width:80% }
    .t90    { width:90% }


[inuit.css’s tablo ızgara sistemi](https://github.com/csswizardry/inuit.css/blob/master/inuit.css/partials/base/_tables.scss#L88)nden alınan bu örnekte tek satırda tanımlamaları yapmak daha mantıklı olacaktır.

## İsimlendirme Düzeni

Ben çoğunlukla tire ile ayrılmış classlar kullanıyorum (örn. '.foo-bar' fakat '.foo_bar' veya '.fooBar' değil), ancak belirli koşullarda BEM (Block, Element, Modifier) metodunu da kullanmaktayım.

> Çevirmenin Notu: Metni mouse ile üzerinde çift tıklayarak seçmek istediğinizde `_` (alttan tire) ile `.foo_bar` şeklinde kullandıysanız hepsini, `-` (normal tire) ile `.foo-bar` şeklinde ayırdaysanız tıkladığınız alana göre `foo` veya `bar` metnini seçecektir. Temel anlamda `_` ile `-` arasındaki fark budur ve kullanıcı uzun vadede kullanma şekline göre seçimini kendi yapmalıdır.

<abbr title="Block, Element, Modifier">BEM</abbr>, CSS seçicilerini isimlendirme ve sınıflandırma için kullanılan çok daha kesin, şeffaf ve bilgilendirici bir yöntemdir.  

Adlandırma kuralı şu şekildedir:

    .block{}
    .block__element{}
    .block--modifier{}

* `.block` represents the higher level of an abstraction or component.
* `.block__element` represents a descendent of `.block` that helps form `.block`
  as a whole.
* `.block--modifier` represents a different state or version of `.block`.

An **analogy** of how BEM classes work might be:

    .person{}
    .person--woman{}
        .person__hand{}
        .person__hand--left{}
        .person__hand--right{}

Here we can see that the basic object we’re describing is a person, and that a
different type of person might be a woman. We can also see that people have
hands; these are sub-parts of people, and there are different variations,
like left and right.

We can now namespace our selectors based on their base objects and we can also
communicate what job the selector does; is it a sub-component (`__`) or a
variation (`--`)?

So, `.page-wrapper` is a standalone selector; it doesn’t form part of an
abstraction or a component and as such it named correctly. `.widget-heading`,
however, _is_ related to a component; it is a child of the `.widget` construct
so we would rename this class `.widget__heading`.

BEM looks a little uglier, and is a lot more verbose, but it grants us a lot of
power in that we can glean the functions and relationships of elements from
their classes alone. Also, BEM syntax will typically compress (gzip) very well
as compression favours/works well with repetition.

Regardless of whether you need to use BEM or not, always ensure classes are
sensibly named; keep them as short as possible but as long as necessary. Ensure
any objects or abstractions are very vaguely named (e.g. `.ui-list`, `.media`)
to allow for greater reuse. Extensions of objects should be much more explicitly
named (e.g. `.user-avatar-link`). Don’t worry about the amount or length of
classes; gzip will compress well written code _incredibly_ well.

### Classes in HTML

In a bid to make things easier to read, separate classes in your HTML with two
(2) spaces, thus:

    <div class="foo--bar  bar__baz">

This increased whitespace should hopefully allow for easier spotting and reading
of multiple classes.

### JS hooks

**Never use a CSS _styling_ class as a JavaScript hook.** Attaching JS behaviour
to a styling class means that we can never have one without the other.

If you need to bind to some markup use a JS specific CSS class. This is simply a
class namespaced with `.js-`, e.g. `.js-toggle`, `.js-drag-and-drop`. This means
that we can attach both JS and CSS to classes in our markup but there will never
be any troublesome overlap.

    <th class="is-sortable  js-is-sortable">
    </th>

The above markup holds two classes; one to which you can attach some styling for
sortable table columns and another which allows you to add the sorting
functionality.

### Internationalisation

Despite being a British developer—and spending all my life writing <i>colour</i>
instead of <i>color</i>—I feel that, for the sake of consistency, it is better
to always use US-English in CSS. CSS, as with most (if not all) other languages,
is written in US-English, so to mix syntax like `color:red;` with classes like
`.colour-picker{}` lacks consistency. I have previously suggested and advocated
writing bilingual classes, for example:

    .color-picker,
    .colour-picker{
    }

However, having recently worked on a very large Sass project where there were
dozens of colour variables (e.g. `$brand-color`, `$highlight-color` etc.),
maintaining two versions of each variable soon became tiresome. It also means
twice as much work with things like find and replace.

In the interests of consistency, always name classes and variables in the locale
of the language you are working with.

## Comments

I use a docBlock-esque commenting style which I limit to 80 characters in length:

    /**
     * This is a docBlock style comment
     *
     * This is a longer description of the comment, describing the code in more
     * detail. We limit these lines to a maximum of 80 characters in length.
     *
     * We can have markup in the comments, and are encouraged to do so:
     *
       <div class=foo>
           <p>Lorem</p>
       </div>
     *
     * We do not prefix lines of code with an asterisk as to do so would inhibit
     * copy and paste.
     */

You should document and comment our code as much as you possibly can, what may
seem or feel transparent and self explanatory to you may not be to another dev.
Write a chunk of code then write about it.

### Comments on steroids

There are a number of more advanced techniques you can employ with regards
comments, namely:

* Quasi-qualified selectors
* Tagging code
* Object/extension pointers

#### Quasi-qualified selectors

You should never qualify your selectors; that is to say, we should never write
`ul.nav{}` if you can just have `.nav`. Qualifying selectors decreases selector
performance, inhibits the potential for reusing a class on a different type of
element and it increases the selector’s specificity. These are all things that
should be avoided at all costs.

However, sometimes it is useful to communicate to the next developer(s) where
you intend a class to be used. Let’s take `.product-page` for example; this
class sounds as though it would be used on a high-level container, perhaps the
`html` or `body` element, but with `.product-page` alone it is impossible to
tell.

By quasi-qualifying this selector (i.e. commenting out the leading type
selector) we can communicate where we wish to have this class applied, thus:

    /*html*/.product-page{}

We can now see exactly where to apply this class but with none of the
specificity or non-reusability drawbacks.

Other examples might be:

    /*ol*/.breadcrumb{}
    /*p*/.intro{}
    /*ul*/.image-thumbs{}

Here we can see where we intend each of these classes to be applied without
actually ever impacting the specificity of the selectors.

#### Tagging code

If you write a new component then leave some tags pertaining to its function in
a comment above it, for example:

    /**
     * ^navigation ^lists
     */
    .nav{}

    /**
     * ^grids ^lists ^tables
     */
    .matrix{}

These tags allow other developers to find snippets of code by searching for
function; if a developer needs to work with lists they can run a find for
`^lists` and find the `.nav` and `.matrix` objects (and possibly more).

#### Object/extension pointers

When working in an object oriented manner you will often have two chunks of CSS
(one being the skeleton (the object) and the other being the skin (the
extension)) that are very closely related, but that live in very different
places. In order to establish a concrete link between the object and its
extension with use <i>object/extension pointers</i>. These are simply comments
which work thus:

In your base stylesheet:

    /**
     * Extend `.foo` in theme.css
     */
     .foo{}

In your theme stylesheet:

    /**
     * Extends `.foo` in base.css
     */
     .bar{}

Here we have established a concrete relationship between two very separate
pieces of code.

---

## Writing CSS

The previous section dealt with how we structure and form our CSS; they were
very quantifiable rules. The next section is a little more theoretical and deals
with our attitude and approach.

## Building new components

When building a new component write markup **before** CSS. This means you can
visually see which CSS properties are naturally inherited and thus avoid
reapplying redundant styles.

By writing markup first you can focus on data, content and semantics and then
apply only the relevant classes and CSS _afterwards_.

## OOCSS

I work in an OOCSS manner; I split components into structure (objects) and
skin (extensions). As an **analogy** (note, not example) take the following:

    .room{}

    .room--kitchen{}
    .room--bedroom{}
    .room--bathroom{}

We have several types of room in a house, but they all share similar traits;
they all have floors, ceilings, walls and doors. We can share this information
in an abstracted `.room{}` class. However we have specific types of room that
are different from the others; a kitchen might have a tiled floor and a bedroom
might have carpets, a bathroom might not have a window but a bedroom most likely
will, each room likely has different coloured walls. OOCSS teaches us to
abstract the shared styles out into a base object and then _extend_ this
information with more specific classes to add the unique treatment(s).

So, instead of building dozens of unique components, try and spot repeated
design patterns across them all and abstract them out into reusable classes;
build these skeletons as base ‘objects’ and then peg classes onto these to
extend their styling for more unique circumstances.

If you have to build a new component split it into structure and skin; build the
structure of the component using very generic classes so that we can reuse that
construct and then use more specific classes to skin it up and add design
treatments.

## Layout

All components you build should be left totally free of widths; they should
always remain fluid and their widths should be governed by a parent/grid system.

Heights should **never** be be applied to elements. Heights should only be
applied to things which had dimensions _before_ they entered the site (i.e.
images and sprites). Never ever set heights on `p`s, `ul`s, `div`s, anything.
You can often achieve the desired effect with `line-height` which is far more
flexible.

Grid systems should be thought of as shelves. They contain content but are not
content in themselves. You put up your shelves then fill them with your stuff.
By setting up our grids separately to our components you can move components
around a lot more easily than if they had dimensions applied to them; this makes
our front-ends a lot more adaptable and quick to work with.

You should never apply any styles to a grid item, they are for layout purposes
only. Apply styling to content _inside_ a grid item. Never, under _any_
circumstances, apply box-model properties to a grid item.

## Sizing UIs

I use a combination of methods for sizing UIs. Percentages, pixels, ems, rems
and nothing at all.

Grid systems should, ideally, be set in percentages. Because I use grid systems
to govern widths of columns and pages, I can leave components totally free of
any dimensions (as discussed above).

Font sizes I set in rems with a pixel fallback. This gives the accessibility
benefits of ems with the confidence of pixels. Here is a handy Sass mixin to
work out a rem and pixel fallback for you (assuming you set your base font
size in a variable somewhere):

    @mixin font-size($font-size){
        font-size:$font-size +px;
        font-size:$font-size / $base-font-size +rem;
    }

I only use pixels for items whose dimensions were defined before the came into
the site. This includes things like images and sprites whose dimensions are
inherently set absolutely in pixels.

### Font sizing

I define a series of classes akin to a grid system for sizing fonts. These
classes can be used to style type in a double stranded heading hierarchy. For a
full explanation of how this works please refer to my article
[Pragmatic, practical font-sizing in CSS](http://csswizardry.com/2012/02/pragmatic-practical-font-sizing-in-css)

## Shorthand

**Shorthand CSS needs to be used with caution.**

It might be tempting to use declarations like `background:red;` but in doing so
what you are actually saying is ‘I want no image to scroll, aligned top-left,
repeating X and Y, and a background colour of red’. Nine times out of ten this
won’t cause any issues but that one time it does is annoying enough to warrant
not using such shorthand. Instead use `background-color:red;`.

Similarly, declarations like `margin:0;` are nice and short, but
**be explicit**. If you actually only really want to affect the margin on
the bottom of an element then it is more appropriate to use `margin-bottom:0;`.

Be explicit in which properties you set and take care to not inadvertently unset
others with shorthand. E.g. if you only want to remove the bottom margin on an
element then there is no sense in setting all margins to zero with `margin:0;`.

Shorthand is good, but easily misused.

## IDs

A quick note on IDs in CSS before we dive into selectors in general.

**NEVER use IDs in CSS.**

They can be used in your markup for JS and fragment identifiers but use only
classes for styling. You don’t want to see a single ID in any stylesheets!

Classes come with the benefit of being reusable (even if we don’t want to, we
can) and they have a nice, low specificity. Specificity is one of the quickest
ways to run into difficulties in projects and keeping it low at all times is
imperative. An ID is **255** times more specific than a class, so never ever use
them in CSS _ever_.

## Selectors

Keep selectors short, efficient and portable.

Heavily location-based selectors are bad for a number of reasons. For example,
take `.sidebar h3 span{}`. This selector is too location-based and thus we
cannot move that `span` outside of a `h3` outside of `.sidebar` and maintain
styling.

Selectors which are too long also introduce performance issues; the more checks
in a selector (e.g. `.sidebar h3 span` has three checks, `.content ul p a` has
four), the more work the browser has to do.

Make sure styles aren’t dependent on location where possible, and make sure
selectors are nice and short.

Selectors as a whole should be kept short (e.g. one class deep) but the class
names themselves should be as long as they need to be. A class of `.user-avatar`
is far nicer than `.usr-avt`.

**Remember:** classes are neither semantic or insemantic; they are sensible or
insensible! Stop stressing about ‘semantic’ class names and pick something
sensible and futureproof.

### Over-qualified selectors

As discussed above, qualified selectors are bad news.

An over-qualified selector is one like `div.promo`. You could probably get the
same effect from just using `.promo`. Of course sometimes you will _want_ to
qualify a class with an element (e.g. if you have a generic `.error` class that
needs to look different when applied to different elements (e.g.
`.error{ color:red; }` `div.error{ padding:14px; }`)), but generally avoid it
where possible.

Another example of an over-qualified selector might be `ul.nav li a{}`. As
above, we can instantly drop the `ul` and because we know `.nav` is a list, we
therefore know that any `a` _must_ be in an `li`, so we can get `ul.nav li a{}`
down to just `.nav a{}`.

### Selector performance

Whilst it is true that browsers will only ever keep getting faster at rendering
CSS, efficiency is something you could do to keep an eye on. Short, unnested
selectors, not using the universal (`*{}`) selector as the key selector, and
avoiding more complex CSS3 selectors should help circumvent these problems.

## CSS selector intent

Instead of using selectors to drill down the DOM to an element, it is often best
to put a class on the element you explicitly want to style. Let’s take a
specific example with a selector like `.header ul{}`…

Let’s imagine that `ul` is indeed the main navigation for our website. It lives
in the header as you might expect and is currently the only `ul` in there;
`.header ul{}` will work, but it’s not ideal or advisable. It’s not very future
proof and certainly not explicit enough. As soon as we add another `ul` to that
header it will adopt the styling of our main nav and the the chances are it
won’t want to. This means we either have to refactor a lot of code _or_ undo a
lot of styling on subsequent `ul`s in that `.header` to remove the effects of
the far reaching selector.

Your selector’s intent must match that of your reason for styling something;
ask yourself **‘am I selecting this because it’s a `ul` inside of `.header` or
because it is my site’s main nav?’**. The answer to this will determine your
selector.

Make sure your key selector is never an element/type selector or
object/abstraction class. You never really want to see selectors like
`.sidebar ul{}` or `.footer .media{}` in our theme stylesheets.

Be explicit; target the element you want to affect, not its parent. Never assume
that markup won’t change. **Write selectors that target what you want, not what
happens to be there already.**

For a full write up please see my article
[Shoot to kill; CSS selector intent](http://csswizardry.com/2012/07/shoot-to-kill-css-selector-intent/)

## `!important`

It is okay to use `!important` on helper classes only. To add `!important`
preemptively is fine, e.g. `.error{ color:red!important }`, as you know you will
**always** want this rule to take precedence.

Using `!important` reactively, e.g. to get yourself out of nasty specificity
situations, is not advised. Rework your CSS and try to combat these issues by
refactoring your selectors. Keeping your selectors short and avoiding IDs will
help out here massively.

## Magic numbers and absolutes

A magic number is a number which is used because ‘it just works’. These are bad
because they rarely work for any real reason and are not usually very
futureproof or flexible/forgiving. They tend to fix symptoms and not problems.

For example, using `.dropdown-nav li:hover ul{ top:37px; }` to move a dropdown
to the bottom of the nav on hover is bad, as 37px is a magic number. 37px only
works here because in this particular scenario the `.dropdown-nav` happens to be
37px tall.

Instead you should use `.dropdown-nav li:hover ul{ top:100%; }` which means no
matter how tall the `.dropdown-nav` gets, the dropdown will always sit 100% from
the top.

Every time you hard code a number think twice; if you can avoid it by using
keywords or ‘aliases’ (i.e. `top:100%` to mean ‘all the way from the top’)
or&mdash;even better&mdash;no measurements at all then you probably should.

Every hard-coded measurement you set is a commitment you might not necessarily
want to keep.

## Conditional stylesheets

IE stylesheets can, by and large, be totally avoided. The only time an IE
stylesheet may be required is to circumvent blatant lack of support (e.g. PNG
fixes).

As a general rule, all layout and box-model rules can and _will_ work without an
IE stylesheet if you refactor and rework your CSS. This means you never want to
see `<!--[if IE 7]> element{ margin-left:-9px; } < ![endif]-->` or other such
CSS that is clearly using arbitrary styling to just ‘make stuff work’.

## Debugging

If you run into a CSS problem **take code away before you start adding more** in
a bid to fix it. The problem exists in CSS that is already written, more CSS
isn’t the right answer!

Delete chunks of markup and CSS until your problem goes away, then you can
determine which part of the code the problem lies in.

It can be tempting to put an `overflow:hidden;` on something to hide the effects
of a layout quirk, but overflow was probably never the problem; **fix the
problem, not its symptoms.**

## Preprocessors

Sass is my preprocessor of choice. **Use it wisely.** Use Sass to make your CSS
more powerful but avoid nesting like the plague! Nest only when it would
actually be necessary in vanilla CSS, e.g.

    .header{}
    .header .site-nav{}
    .header .site-nav li{}
    .header .site-nav li a{}

Would be wholly unnecessary in normal CSS, so the following would be **bad**
Sass:

    .header{
        .site-nav{
            li{
                a{}
            }
        }
    }

If you were to Sass this up you’d write it as:

    .header{}
    .site-nav{
        li{}
        a{}
    }
