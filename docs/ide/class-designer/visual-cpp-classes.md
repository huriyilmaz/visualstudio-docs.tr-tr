---
title: Sınıf Tasarımcısı C++ sınıfları
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75590741"
---
# <a name="c-classes-in-class-designer"></a>Sınıf Tasarımcısı C++ sınıfları

**Sınıf Tasarımcısı** c++ sınıflarını destekler ve c++ sınıflarının birden fazla devralma ilişkisine sahip olması dışında, yerel c++ sınıflarını Visual Basic ve C# sınıf şekilleriyle aynı şekilde görselleştirir. Sınıfında daha fazla alan ve yöntem göstermek için sınıf şeklini genişletebilir veya alanı korumak için daraltabilirsiniz.

> [!NOTE]
> **Sınıf Tasarımcısı** birleşimleri desteklemez (ayrılan belleğin yalnızca birleşimin en büyük veri üyesi için gereken miktar olduğu özel bir sınıf türü).

## <a name="simple-inheritance"></a>Basit devralma

Bir sınıf diyagramına birden fazla sınıf sürüklediğinizde ve sınıfların bir sınıf devralma ilişkisi varsa, bir ok bunları bağlar. Ok, taban sınıfının yönünde işaret eder. Örneğin, aşağıdaki sınıflar bir sınıf diyagramında görüntülendiğinde, bir ok, B 'den A 'ya işaret eden bir okla bağlantı kurar:

```cpp
class A {};
class B : A {};
```

Sınıf diyagramına yalnızca B sınıfını da sürükleyebilirsiniz, B için sınıf şekline sağ tıklayıp **temel sınıfları göster**' e tıklayabilirsiniz. Bu, kendi temel sınıfını görüntüler: A.

## <a name="multiple-inheritance"></a>Çoklu devralma

**Sınıf Tasarımcısı** birden çok sınıf devralma ilişkilerinin görselleştirmesini destekler. Türetilmiş bir sınıfın birden fazla temel sınıf özniteliği olduğunda *birden çok devralma* kullanılır. Birden çok devralım örneği aşağıda verilmiştir:

```cpp
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

Sınıf diyagramına birden fazla sınıf sürüklediğinizde ve sınıfların birden çok sınıf devralma ilişkisi varsa, bir ok bunları bağlar. Ok, temel sınıfların yönlerine işaret eder.

Bir sınıf şekline sağ tıklayıp, **temel sınıfları göster** ' e tıkladığınızda seçili sınıf için temel sınıflar görüntülenir.

> [!NOTE]
> **Türetilmiş sınıfları göster** komutu C++ kodu için desteklenmez. Türetilmiş sınıfları **sınıf görünümü**giderek, tür düğümünü genişleterek, **türetilmiş türler** alt klasörünü genişleterek ve ardından bu türleri sınıf diyagramına sürükleyerek görüntüleyebilirsiniz.

Birden çok sınıf devralma hakkında daha fazla bilgi için bkz. [birden fazla devralma](https://msdn.microsoft.com/library/6td5yws2.aspx) ve [birden çok temel sınıf](/cpp/cpp/multiple-base-classes).

## <a name="abstract-classes"></a>Soyut sınıflar

**Sınıf Tasarımcısı** soyut sınıfları ("soyut temel sınıflar" olarak da adlandırılır) destekler. Bunlar hiçbir şekilde hiçbir şekilde örnekleyemezsiniz, ancak başka sınıflar türetilebilir. Bu belgede daha önce "çoklu devralma" işleminden bir örnek kullanıldığında, `Bird` sınıfı ayrı nesneler olarak aşağıdaki gibi oluşturabilirsiniz:

```cpp
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

Ancak, `Swimmer` sınıfı ayrı nesneler olarak örneğini oluşturmak istemeyebilirsiniz. Örneğin,, ve gibi diğer sınıf türleri türetebilirsiniz `Penguin` `Whale` `Fish` . Bu durumda, `Swimmer` sınıfı bir soyut temel sınıf olarak bildirirsiniz.

Bir sınıfı Özet olarak bildirmek için `abstract` anahtar sözcüğünü kullanabilirsiniz. Soyut olarak işaretlenen veya soyut bir sınıfa eklenen Üyeler sanal ve soyut sınıftan türetilmiş sınıflar tarafından uygulanmalıdır.

```cpp
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

Ayrıca, en az bir saf sanal işlevi ekleyerek bir sınıfı soyut olarak bildirebilirsiniz:

```cpp
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

Bu bildirimleri bir sınıf diyagramında görüntülediğinizde, sınıf adı `Swimmer` ve saf sanal işlevi, `swim` gösterim **soyut sınıfıyla**birlikte bir soyut sınıf şeklinde italik olarak görüntülenir. Soyut sınıf türü şeklinin, kenarlığının noktalı bir çizgi olması dışında normal bir sınıftan aynı olduğuna dikkat edin.

Soyut taban sınıftan türetilmiş bir sınıf, temel sınıftaki her bir saf sanal işlevi geçersiz kılmalıdır, aksi durumda türetilmiş sınıf başlatılamaz. Bu nedenle, örneğin sınıfından bir sınıf türetirsiniz `Fish` `Swimmer` , `Fish` yöntemi geçersiz kılmalıdır `swim` :

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

Bu kodu bir sınıf diyagramında görüntülediğinizde **Sınıf Tasarımcısı** , öğesinden devralım çizgisi çizer `Fish` `Swimmer` .

## <a name="anonymous-classes"></a>Anonim sınıflar

**Sınıf Tasarımcısı** anonim sınıfları destekler. *Anonim sınıf türleri* tanımlayıcı olmadan tanımlanmış sınıflardır. Bir Oluşturucu veya yıkıcı olamaz, işlevlere bağımsız değişken olarak geçirilemez ve işlevlerden dönüş değeri olarak döndürülemez. Bir sınıf adını aşağıdaki örnekte olduğu gibi bir typedef adı ile değiştirmek için anonim bir sınıf kullanabilirsiniz:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

Yapılar da anonim olabilir. **Sınıf Tasarımcısı** , anonim sınıfları ve yapıları ilgili türü görüntülediği gibi görüntüler. Anonim sınıfları ve yapıları bildirebilmenize ve görüntüleyseniz de **Sınıf Tasarımcısı** belirttiğiniz etiket adını kullanmaz. Sınıf Görünümü oluşturduğu adı kullanacaktır. Sınıf veya yapı, Sınıf Görünümü ve **Sınıf Tasarımcısı** **__unnamed**adlı bir öğe olarak görünür.

Anonim sınıflar hakkında daha fazla bilgi için bkz. [anonim sınıf türleri](/cpp/cpp/anonymous-class-types).

## <a name="template-classes"></a>Şablon sınıfları

**Sınıf Tasarımcısı** , şablon sınıflarının görselleştirmesini destekler. İç içe geçmiş bildirimler desteklenir. Aşağıdaki tabloda bazı tipik bildirimler gösterilmektedir.

| Kod öğesi | Sınıf Tasarımcısı görünümü |
| - | - |
| `template <class T>`<br /><br /> `class A {};` | `A<T>`<br /><br /> Şablon sınıfı |
| `template <class T, class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Şablon sınıfı |
| `template <class T, int i>`<br /><br /> `class A {};` | `A<T, i>`<br /><br /> Şablon sınıfı |
| `template <class T, template <class K> class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Şablon sınıfı |

Aşağıdaki tabloda kısmi özelleşmenin bazı örnekleri gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Şablon sınıfı|
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Şablon sınıfı|
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Şablon sınıfı|
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Şablon sınıfı|

Aşağıdaki tabloda kısmi özelleşmenin bazı devralma örnekleri gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Şablon sınıfı<br /><br /> `B`<br /><br /> Sınıf<br /><br /> (sınıf A 'ya işaret eder)<br /><br /> `C`<br /><br /> Sınıf<br /><br /> (sınıf A 'ya işaret eder)|

Aşağıdaki tabloda kısmi özelleşme şablonu işlevlerinin bazı örnekleri gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> Func \<T, U> (+ 1 aşırı yükleme)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Şablon sınıfı<br /><br /> `B<T2>`<br /><br /> Şablon sınıfı<br /><br /> (B sınıf içinde **Iç Içe geçmiş türler**altında bulunur)|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Sınıf<br /><br /> -> C\<int><br /><br /> `C<T>`<br /><br /> Şablon sınıfı|

Aşağıdaki tabloda şablon devralmanın bazı örnekleri gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Sınıf<br /><br /> ->B<br /><br /> `C<int>`<br /><br /> Sınıf<br /><br /> (B, **Iç Içe türler**altında C sınıfı içinde bulunur)<br /><br /> `C<T>`<br /><br /> Şablon sınıfı|

Aşağıdaki tabloda, kurallı özelleştirilmiş sınıf bağlantısının bazı örnekleri gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Sınıf<br /><br /> ->C\<int><br /><br /> `C<int>`<br /><br /> Sınıf<br /><br /> `C<T>`<br /><br /> Şablon sınıfı<br /><br /> `D`<br /><br /> Sınıf<br /><br /> ->C\<float>|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> Min \<T>|

## <a name="see-also"></a>Ayrıca bkz.

- [C++ kodu ile çalışma](working-with-visual-cpp-code.md)
- [Sınıflar ve Yapılar](/cpp/cpp/classes-and-structs-cpp)
- [Anonim sınıf türleri](/cpp/cpp/anonymous-class-types)
- [Birden çok devralma](https://msdn.microsoft.com/library/6td5yws2.aspx)
- [Birden çok temel sınıf](/cpp/cpp/multiple-base-classes)
- [Şablonlar](/cpp/cpp/templates-cpp)
