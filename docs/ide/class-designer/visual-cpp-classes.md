---
title: Sınıf Tasarımcıc++ Sınıfları
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d68391bbd4c6c873940bbc2714ee41db8309b629
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590741"
---
# <a name="c-classes-in-class-designer"></a>Sınıf Tasarımcısı'nda C++ dersleri

**Sınıf Tasarımcısı** C++ sınıflarını destekler ve C++ sınıflarının birden çok devralma ilişkisi olması dışında, Visual Basic ve C# sınıf şekilleri ile aynı şekilde yerel C++ sınıflarını görselleştirir. Sınıfta daha fazla alan ve yöntem göstermek için sınıf şeklini genişletebilir veya alanı korumak için daraltabilirsiniz.

> [!NOTE]
> **Sınıf Tasarımcısı** birleşimleri desteklemez (ayrılan belleğin yalnızca birliğin en büyük veri üyesi için gerekli olan miktar olduğu özel bir sınıf türü).

## <a name="simple-inheritance"></a>Basit devralma

Birden fazla sınıfı sınıf diyagramına sürüklediğinizde ve sınıfların bir sınıf devralma ilişkisi varsa, bir ok onları bağlar. Ok, taban sınıfın yönünü işaret ediyor. Örneğin, aşağıdaki sınıflar sınıf diyagramında görüntülendiğinde, bir ok onları bağlar ve B'den A'ya işaret eder:

```cpp
class A {};
class B : A {};
```

Ayrıca sınıf diyagramına yalnızca B sınıfı sürükleyebilir, B için sınıf şeklini sağ tıklatabilir ve ardından **Temel Sınıfları Göster'i**tıklatabilirsiniz. Bu taban sınıfını görüntüler: A.

## <a name="multiple-inheritance"></a>Çoklu devralma

**Sınıf Tasarımcısı,** çok sınıflı kalıtım ilişkilerinin görselleştirilmesini destekler. *Türetilen* bir sınıfın birden fazla taban sınıfın öznitelikleri varsa, birden çok devralma kullanılır. Aşağıdaki birden çok devralma örneği:

```cpp
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

Birden fazla sınıfı sınıf diyagramına sürüklediğinizde ve sınıflar da çok sınıflı bir devralma ilişkisine sahipse, bir ok onları bağlar. Ok, temel sınıfların yönünü işaret ediyor.

Sınıf şeklini sağ tıklattıktan sonra **Temel Sınıfları Göster'i** tıklattığınızda, seçilen sınıfın temel sınıfları görüntülenir.

> [!NOTE]
> **Türemiş Sınıfları Göster** komutu C++ kodu için desteklenmez. Türemiş sınıfları **Sınıf Görünümü'ne**giderek, tür düğümünü genişleterek, **Türemiş Türler** alt klasörünü genişleterek ve bu türleri sınıf diyagramına sürükleyerek görüntüleyebilirsiniz.

Çok sınıflı devralma hakkında daha fazla bilgi için, [Çoklu Devralma](https://msdn.microsoft.com/library/6td5yws2.aspx) ve Çoklu [Temel Sınıflar'a](/cpp/cpp/multiple-base-classes)bakın.

## <a name="abstract-classes"></a>Soyut sınıflar

**Sınıf Tasarımcısı** soyut sınıfları destekler ("soyut temel sınıflar" olarak da adlandırılır). Bunlar asla anlık olarak elde edilemeyeceğiniz, ancak diğer sınıfları türetebileceğiniz sınıflardır. Bu belgenin daha önceki "Çoklu Devralma" örneğini kullanarak, `Bird` sınıfı aşağıdaki gibi tek tek nesneler olarak anında atabilirsiniz:

```cpp
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

Ancak, `Swimmer` sınıfı tek tek nesneler olarak anında yapmak niyetinde olmayabilir. Sadece ondan hayvan sınıfları diğer türleri türetmek niyetinde `Penguin`olabilir, örneğin, `Whale`, ve `Fish`. Bu durumda, `Swimmer` sınıfı soyut bir taban sınıf olarak bildirirsiniz.

Bir sınıfı soyut olarak bildirmek için `abstract` anahtar sözcüğü kullanabilirsiniz. Soyut olarak işaretlenmiş veya soyut bir sınıfa dahil edilen üyeler sanaldır ve soyut sınıftan türeyen sınıflar tarafından uygulanmalıdır.

```cpp
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

Ayrıca, en az bir saf sanal işlev ekleyerek bir sınıfı soyut olarak bildirebilirsiniz:

```cpp
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

Bu bildirimleri Sınıf Diyagramı'nda görüntülediğinizde, sınıf `Swimmer` `swim` adı ve saf sanal işlevi, notasyon **Abstract Class**ile birlikte soyut bir sınıf şeklinde görüntülenir. Soyut sınıf türü şeklinin, kenarlığı noktalı bir çizgi olması dışında, normal bir sınıfınşekliyle aynı olduğuna dikkat edin.

Soyut bir taban sınıftan türetilen bir sınıf, taban sınıftaki her saf sanal işlevi geçersiz kılmalı veya türetilmiş sınıf anında kullanılamaz. Bu nedenle, `Fish` örneğin, `Swimmer` sınıftan bir sınıf `Fish` türederseniz, `swim` yöntemi geçersiz kılmanız gerekir:

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

Bu kodu Sınıf Diyagramında görüntülediğinizde, **Sınıf** `Fish` Tasarımcısı `Swimmer`'ndan ''a bir devralma satırı çizer.

## <a name="anonymous-classes"></a>Anonim sınıflar

**Sınıf Tasarımcısı** anonim sınıfları destekler. *Anonim sınıf türleri* tanımlayıcıolmadan bildirilen sınıflardır. Bir oluşturucu veya yıkıcı olamazlar, işlevlere bağımsız değişken olarak geçirilemezler ve işlevlerden dönüş değerleri olarak döndürülemezler. Aşağıdaki örnekte olduğu gibi, bir sınıf adını typedef adı ile değiştirmek için anonim bir sınıf kullanabilirsiniz:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

Yapılar anonim de olabilir. **Sınıf Tasarımcısı,** ilgili türü gösterdiği gibi anonim sınıfları ve yapıları görüntüler. Anonim sınıfları ve yapıları bildirebilir ve görüntüleyebilirsiniz, ancak **Sınıf Tasarımcısı** belirttiğiniz etiket adını kullanmaz. Sınıf Görünümü'nün oluşturduğu adı kullanır. Sınıf veya yapı, Sınıf Görünümü ve **Sınıf Tasarımcısı'nda** **__unnamed**olarak adlandırılan bir öğe olarak görünür.

Anonim sınıflar hakkında daha fazla bilgi için [Bkz. Anonim Sınıf Türleri.](/cpp/cpp/anonymous-class-types)

## <a name="template-classes"></a>Şablon sınıfları

**Sınıf Tasarımcısı** şablon sınıflarının görselleştirilmesini destekler. İç içe verilen bildirimler desteklenir. Aşağıdaki tabloda bazı tipik bildirimler ilerler.

| Kod öğesi | Sınıf Tasarımcısı görünümü |
| - | - |
| `template <class T>`<br /><br /> `class A {};` | `A<T>`<br /><br /> Şablon Sınıfı |
| `template <class T, class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Şablon Sınıfı |
| `template <class T, int i>`<br /><br /> `class A {};` | `A<T, i>`<br /><br /> Şablon Sınıfı |
| `template <class T, template <class K> class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Şablon Sınıfı |

Aşağıdaki tablokısmi uzmanlık bazı örnekler gösterir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Şablon Sınıfı|
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Şablon Sınıfı|
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Şablon Sınıfı|
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Şablon Sınıfı|

Aşağıdaki tablokısmi uzmanlık içinde kalıtım bazı örnekler gösterir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Şablon Sınıfı<br /><br /> `B`<br /><br /> Sınıf<br /><br /> (A sınıfına işaret)<br /><br /> `C`<br /><br /> Sınıf<br /><br /> (A sınıfına işaret)|

Aşağıdaki tablo, kısmi uzmanlık şablonu işlevlerinin bazı örneklerini gösterir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> func\<T, U> (+ 1 aşırı yük)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Şablon Sınıfı<br /><br /> `B<T2>`<br /><br /> Şablon Sınıfı<br /><br /> (B İç **Içe Türleri**altında A sınıfı içinde yer almaktadır)|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Sınıf<br /><br /> ->\<C int><br /><br /> `C<T>`<br /><br /> Şablon Sınıfı|

Aşağıdaki tabloda şablon devralma bazı örnekler gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Sınıf<br /><br /> ->B<br /><br /> `C<int>`<br /><br /> Sınıf<br /><br /> (B İç **Içe Türleri**altında C sınıfı içinde yer almaktadır)<br /><br /> `C<T>`<br /><br /> Şablon Sınıfı|

Aşağıdaki tabloda kanonik özel sınıf bağlantısıbazı örnekler gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Sınıf<br /><br /> ->\<C int><br /><br /> `C<int>`<br /><br /> Sınıf<br /><br /> `C<T>`<br /><br /> Şablon Sınıfı<br /><br /> `D`<br /><br /> Sınıf<br /><br /> ->\<C float>|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T>|

## <a name="see-also"></a>Ayrıca bkz.

- [C++ Kodu ile Çalışma](working-with-visual-cpp-code.md)
- [Sınıflar ve Structs](/cpp/cpp/classes-and-structs-cpp)
- [Anonim Sınıf Türleri](/cpp/cpp/anonymous-class-types)
- [Çoklu Devralma](https://msdn.microsoft.com/library/6td5yws2.aspx)
- [Birden Çok Taban Sınıfı](/cpp/cpp/multiple-base-classes)
- [Şablon](/cpp/cpp/templates-cpp)
