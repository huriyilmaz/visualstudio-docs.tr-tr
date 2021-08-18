---
title: Sınıf Tasarımcısı'de C++ Sınıfları
description: C++ sınıfları ve bunların nasıl destekleneleri ve bu sınıflarda birden çok devralma ilişkisine sahip Sınıf Tasarımcısı.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: bad6d017bfe58af9a514f632b4bf1fc3047cb054
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094496"
---
# <a name="c-classes-in-class-designer"></a>Sınıf Tasarımcısı'de C++ sınıfları

**Sınıf Tasarımcısı** C++ sınıflarını destekler ve yerel C++ sınıflarını Visual Basic ve C# sınıf şekilleriyle aynı şekilde görselleştirin, ancak C++ sınıflarında birden çok devralma ilişkisi olabilir. Sınıf şeklini, sınıfta daha fazla alan ve yöntem gösterecek şekilde genişletebilirsiniz veya alandan tasarruf etmek için daraltabilirsiniz.

> [!NOTE]
> **Sınıf Tasarımcısı** birliği desteklemez (bellek ayrılan özel bir sınıf türü, yalnızca birliğin en büyük veri üyesi için gereken miktardır).

## <a name="simple-inheritance"></a>Basit devralma

Bir sınıf diyagramına birden fazla sınıf sürükler ve sınıfların bir sınıf devralma ilişkisi olduğunda, bir ok bunları bağlar. Ok, temel sınıfın yönüne doğru ilerler. Örneğin, aşağıdaki sınıflar bir sınıf diyagramında görüntülendiğinde, bunları B'den A'ya işaret eden bir ok bağlar:

```cpp
class A {};
class B : A {};
```

Ayrıca yalnızca B sınıfını sınıf diyagramına sürükleyip B için sınıf şekline sağ tıklar ve ardından Temel Sınıfları **Göster'e tıklarsiniz.** Bu, temel sınıfını görüntüler: A.

## <a name="multiple-inheritance"></a>Çoklu devralma

**Sınıf Tasarımcısı** sınıf devralma ilişkilerinin görselleştirmesini destekler. *Türetilmiş bir* sınıfın birden fazla temel sınıf özniteliği olduğunda birden çok devralma kullanılır. Aşağıda, birden çok devralma örneği ve ardından ve bir örnek ve ardından yer alır:

```cpp
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

Sınıf diyagramına birden fazla sınıf sürükler ve sınıflar çok sınıflı devralma ilişkisine sahip olduğunda, bunları bir ok bağlar. Ok, temel sınıfların yönüne doğru ilerler.

Bir sınıf şekline sağ tık ardından Temel Sınıfları **Göster'e** tıklarsanız, seçilen sınıfın temel sınıfları görüntülenir.

> [!NOTE]
> Türetilmiş **Sınıfları Göster** komutu C++ kodu için desteklenmiyor. Türetilmiş sınıfları görüntülemek için **Sınıf Görünümü,** tür düğümünü genişleterek,  Türetilmiş Türler alt klasörünü genişleterek ve ardından bu türleri sınıf diyagramına sürükleyerek görüntüebilirsiniz.

Birden çok sınıf devralma hakkında daha fazla bilgi için bkz. [Birden Çok Devralma](/previous-versions/6td5yws2(v=vs.140)) ve Birden Çok Temel [Sınıf.](/cpp/cpp/multiple-base-classes)

## <a name="abstract-classes"></a>Soyut sınıflar

**Sınıf Tasarımcısı** sınıfları ("soyut temel sınıflar" olarak da adlandırılır) destekler. Bunlar hiçbir zaman örneklenenem olarak değil, başka sınıflar türeten sınıflardır. Bu belgenin başlarındaki "Birden Çok Devralma" örneğinden bir örnek kullanarak, sınıfı aşağıdaki gibi `Bird` tek tek nesneler olarak örneği oluşturabilirsiniz:

```cpp
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

Ancak, sınıfı tek tek nesneler olarak örneğini `Swimmer` oluşturma amacına sahip değildirsiniz. Yalnızca, ve gibi diğer hayvan sınıflarını türetmek için bu `Penguin` türemiş `Whale` `Fish` olabilir. Bu durumda, sınıfı soyut bir `Swimmer` temel sınıf olarak bildirersiniz.

Bir sınıfı soyut olarak bildirebilirsiniz, anahtar sözcüğünü `abstract` kullanabilirsiniz. Soyut olarak işaretlenen veya soyut bir sınıfa dahil edilen üyeler sanaldır ve soyut sınıftan türeten sınıflar tarafından uygulanmalıdır.

```cpp
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

Ayrıca, en az bir saf sanal işlev dahil olmak üzere bir sınıfı soyut olarak bildiresiniz:

```cpp
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

Bu bildirimleri Bir Sınıf Diyagramında görüntülendiğinde, sınıf adı ve saf sanal işlevi soyut sınıf şeklinde, Soyut Sınıf ile birlikte `Swimmer` `swim` italik **olarak görüntülenir.** Soyut sınıf türü şeklinin, kenarlığı noktalı çizgi olması dışında normal bir sınıfın şekliyle aynı olduğunu fark vardır.

Soyut bir temel sınıftan türetilen bir sınıfın temel sınıftaki her saf sanal işlevi geçersiz kılması gerekir, yoksa türetilmiş sınıf örneği olamaz. Bu nedenle, örneğin sınıfından bir sınıf `Fish` türetmiş `Swimmer` olursanız, `Fish` yöntemini geçersiz `swim` kılması gerekir:

```cpp
class Fish : public Swimmer
{
   void swim(int speed);
};

int main()
{
   Fish guppy;
}
```

Bu kodu Bir Sınıf Diyagramında görüntüleye **Sınıf Tasarımcısı** için bir devralma çizgisi `Fish` `Swimmer` çizin.

## <a name="anonymous-classes"></a>Anonim sınıflar

**Sınıf Tasarımcısı** anonim sınıfları destekler. *Anonim sınıf türleri,* tanımlayıcı olmadan bildirilen sınıflardır. Oluşturucu veya yıkıcısı olamaz, işlevlere bağımsız değişken olarak geçirilemesi ve işlevlerden dönüş değerleri olarak döndürülmesi mümkün olamaz. Aşağıdaki örnekte olduğu gibi, bir sınıf adını typedef adıyla değiştirmek için anonim bir sınıf kullanabilirsiniz:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

Yapılar anonim de olabilir. **Sınıf Tasarımcısı,** anonim sınıfları ve yapıları ilgili türü görüntüle aynı şekilde görüntüler. Anonim sınıfları ve yapıları bildirebilirsiniz ve **görüntüleye Sınıf Tasarımcısı,** belirttiğiniz etiket adını kullanmaz. Bu, oluşturulan Sınıf Görünümü kullanır. Sınıf veya yapı, Sınıf Görünümü ve **Sınıf Tasarımcısı** adlı bir öğe **olarak** __unnamed.

Anonim sınıflar hakkında daha fazla bilgi için bkz. [Anonim Sınıf Türleri.](/cpp/cpp/anonymous-class-types)

## <a name="template-classes"></a>Şablon sınıfları

**Sınıf Tasarımcısı,** şablon sınıflarının görselleştirmesini destekler. İç içe bildirim desteği vardır. Aşağıdaki tabloda bazı tipik bildirimler yer almaktadır.

| Kod öğesi | Sınıf Tasarımcısı görünümü |
| - | - |
| `template <class T>`<br /><br /> `class A {};` | `A<T>`<br /><br /> Şablon Sınıfı |
| `template <class T, class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Şablon Sınıfı |
| `template <class T, int i>`<br /><br /> `class A {};` | `A<T, i>`<br /><br /> Şablon Sınıfı |
| `template <class T, template <class K> class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Şablon Sınıfı |

Aşağıdaki tabloda kısmi özelleştirmeye bazı örnekler verilmiştir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Şablon Sınıfı|
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Şablon Sınıfı|
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Şablon Sınıfı|
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Şablon Sınıfı|

Aşağıdaki tabloda kısmi özelleştirmede devralmaya bazı örnekler verilmiştir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Şablon Sınıfı<br /><br /> `B`<br /><br /> Sınıf<br /><br /> (Sınıf A'ya göre)<br /><br /> `C`<br /><br /> Sınıf<br /><br /> (Sınıf A'ya göre)|

Aşağıdaki tabloda kısmi özelleştirme şablonu işlevlerine bazı örnekler verilmiştir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> func \<T, U> (+ 1 aşırı yüklemesi)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Şablon Sınıfı<br /><br /> `B<T2>`<br /><br /> Şablon Sınıfı<br /><br /> (B, A sınıfında İç İçe **Türler altında yer alan )**|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Sınıf<br /><br /> -> C\<int><br /><br /> `C<T>`<br /><br /> Şablon Sınıfı|

Aşağıdaki tabloda şablon devralmaya bazı örnekler verilmiştir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Sınıf<br /><br /> ->B<br /><br /> `C<int>`<br /><br /> Sınıf<br /><br /> (B, İç İçe Geçmiş Türler altında C **sınıfında yer alan )**<br /><br /> `C<T>`<br /><br /> Şablon Sınıfı|

Aşağıdaki tabloda kurallı özelleştirilmiş sınıf bağlantısına bazı örnekler verilmiştir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Sınıf<br /><br /> ->C\<int><br /><br /> `C<int>`<br /><br /> Sınıf<br /><br /> `C<T>`<br /><br /> Şablon Sınıfı<br /><br /> `D`<br /><br /> Sınıf<br /><br /> ->C\<float>|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> Dk \<T>|

## <a name="see-also"></a>Ayrıca bkz.

- [C++ Kodu ile Çalışma](working-with-visual-cpp-code.md)
- [Sınıflar ve Yapılar](/cpp/cpp/classes-and-structs-cpp)
- [Anonim Sınıf Türleri](/cpp/cpp/anonymous-class-types)
- [Birden Çok Devralma](/previous-versions/6td5yws2(v=vs.140))
- [Birden Çok Temel Sınıf](/cpp/cpp/multiple-base-classes)
- [Şablonlar](/cpp/cpp/templates-cpp)