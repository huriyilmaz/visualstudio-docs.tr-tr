---
title: Sınıf Tasarımcısı C++ 'de görsel sınıflar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4fc312736508a11d43cadf789b08aae77c528d35
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608674"
---
# <a name="visual-c-classes-in-class-designer"></a>Sınıf Tasarımcısında Visual C++ Sınıfları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Tasarımcısı sınıfları C++ destekler ve Visual Basic ve görsel C++ C# sınıf şekilleriyle aynı şekilde yerel sınıfları görselleştirir, ancak C++ sınıfların birden fazla devralma ilişkisi olabilir. Sınıfında daha fazla alan ve yöntem göstermek için sınıf şeklini genişletebilir veya alanı korumak için daraltabilirsiniz.

> [!NOTE]
> Sınıf Tasarımcısı birleşimleri desteklemez (ayrılan belleğin yalnızca birleşimin en büyük veri üyesi için gereken miktar olduğu özel bir sınıf türü).

## <a name="simple-inheritance"></a>Basit devralma
 Bir sınıf diyagramına birden fazla sınıf sürüklediğinizde ve sınıfların bir sınıf devralma ilişkisi varsa, bir ok bunları bağlar. Ok, taban sınıfının yönünde işaret eder. Örneğin, aşağıdaki sınıflar bir sınıf diyagramında görüntülendiğinde, bir ok, B 'den A 'ya işaret eden bir okla bağlantı kurar:

```
class A {};
class B : A {};
```

 Sınıf diyagramına yalnızca B sınıfını da sürükleyebilirsiniz, B için sınıf şekline sağ tıklayıp **temel sınıfları göster**' e tıklayabilirsiniz. Bu, kendi temel sınıfını görüntüler: A.

## <a name="multiple-inheritance"></a>Birden Çok Devralma
 Sınıf Tasarımcısı birden çok sınıf devralma ilişkilerinin görselleştirmesini destekler. Türetilmiş bir sınıfın birden fazla temel sınıf özniteliği olduğunda *birden çok devralma* kullanılır. Birden çok devralım örneği aşağıda verilmiştir:

```
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

 Sınıf diyagramına birden fazla sınıf sürüklediğinizde ve sınıfların birden çok sınıf devralma ilişkisi varsa, bir ok bunları bağlar. Ok, temel sınıfların yönlerine işaret eder.

 Bir sınıf şekline sağ tıklayıp, **temel sınıfları göster** ' e tıkladığınızda seçili sınıf için temel sınıflar görüntülenir.

> [!NOTE]
> **Türetilmiş sınıfları göster** komutu kod için C++ desteklenmiyor. Türetilmiş sınıfları Sınıf Görünümü giderek, tür düğümünü genişleterek, **türetilmiş türler** alt klasörünü genişleterek ve ardından bu türleri sınıf diyagramına sürükleyerek görüntüleyebilirsiniz.

 Birden çok sınıf devralma hakkında daha fazla bilgi için bkz. [(NOTINBUILD) birden fazla devralma](https://msdn.microsoft.com/3b74185e-2beb-4e29-8684-441e51d2a2ca) ve [birden çok temel sınıf](https://msdn.microsoft.com/library/a30c69fe-401c-4a87-96a0-e0da70c7c740).

## <a name="abstract-classes"></a>Soyut sınıflar
 Sınıf Tasarımcısı soyut sınıfları ("soyut temel sınıflar" olarak da adlandırılır) destekler. Bunlar hiçbir şekilde hiçbir şekilde örnekleyemezsiniz, ancak başka sınıflar türetilebilir. Bu belgede daha önce "çoklu devralma" işleminden bir örnek kullanarak, `Bird` sınıfını ayrı nesneler olarak aşağıdaki gibi oluşturabilirsiniz:

```
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

 Ancak, `Swimmer` sınıfını ayrı nesneler olarak örneğini oluşturmak istemeyebilirsiniz. Örneğin, `Penguin`, `Whale` ve `Fish` gibi diğer tür bir sınıf sınıfını türetebilirsiniz. Bu durumda, `Swimmer` sınıfını soyut temel sınıf olarak bildirirsiniz.

 Bir sınıfı Özet olarak bildirmek için `abstract` anahtar sözcüğünü kullanabilirsiniz. Soyut olarak işaretlenen veya soyut bir sınıfa eklenen Üyeler sanal ve soyut sınıftan türetilmiş sınıflar tarafından uygulanmalıdır.

```
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

 Ayrıca, en az bir saf sanal işlevi ekleyerek bir sınıfı soyut olarak bildirebilirsiniz:

```
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

 Bu bildirimleri bir sınıf diyagramında görüntülediğinizde, sınıf adı `Swimmer` ve saf sanal işlevi `swim`, gösterim **soyut sınıfıyla**birlikte bir soyut sınıf şeklinde italik olarak görüntülenir. Soyut sınıf türü şeklinin, kenarlığının noktalı bir çizgi olması dışında normal bir sınıftan aynı olduğuna dikkat edin.

 Soyut taban sınıftan türetilmiş bir sınıf, temel sınıftaki her bir saf sanal işlevi geçersiz kılmalıdır, aksi durumda türetilmiş sınıf başlatılamaz. Bu nedenle, örneğin, `Swimmer` sınıfından bir `Fish` sınıfı türetirsiniz `Fish` `swim` yöntemi geçersiz kılmalıdır:

```
class Fish : public Swimmer
{
   void swim(int speed);
};

int main()
{
   Fish guppy;
}
```

 Bu kodu bir sınıf diyagramında görüntülediğinizde Sınıf Tasarımcısı, `Fish` bir devralım çizgisi çizer `Swimmer`.

## <a name="anonymous-classes"></a>Anonim sınıflar
 Sınıf Tasarımcısı anonim sınıfları destekler. *Anonim sınıf türleri* tanımlayıcı olmadan tanımlanmış sınıflardır. Bir Oluşturucu veya yıkıcı olamaz, işlevlere bağımsız değişken olarak geçirilemez ve işlevlerden dönüş değeri olarak döndürülemez. Bir sınıf adını aşağıdaki örnekte olduğu gibi bir typedef adı ile değiştirmek için anonim bir sınıf kullanabilirsiniz:

```
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

 Yapılar da anonim olabilir. Sınıf Tasarımcısı, anonim sınıfları ve yapıları ilgili türü görüntülediği gibi görüntüler. Anonim sınıfları ve yapıları bildirebilmenize ve görüntüleyseniz de Sınıf Tasarımcısı belirttiğiniz etiket adını kullanmaz. Sınıf Görünümü oluşturduğu adı kullanacaktır. Sınıf veya yapı, Sınıf Görünümü ve Sınıf Tasarımcısı **__adlandırılmamış**adlı bir öğe olarak görünür.

 Anonim sınıflar hakkında daha fazla bilgi için bkz. [anonim sınıf türleri](https://msdn.microsoft.com/library/9ba667b2-8c2a-4c29-82a6-fa120b9233c8).

## <a name="template-classes"></a>Şablon sınıfları
 Sınıf Tasarımcısı, şablon sınıflarının görselleştirmesini destekler. İç içe geçmiş bildirimler desteklenir. Aşağıdaki tabloda bazı tipik bildirimler gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------|-------------------------|
|`template <class T>`<br /><br /> `class A {};`|`A<T>`<br /><br /> Şablon sınıfı|
|`template <class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Şablon sınıfı|
|`template <class T, int i>`<br /><br /> `class A {};`|`A<T, i>`<br /><br /> Şablon sınıfı|
|`template <class T, template <class K> class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Şablon sınıfı|

 Aşağıdaki tabloda kısmi özelleşmenin bazı örnekleri gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------|-------------------------|
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Şablon sınıfı|
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Şablon sınıfı|
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Şablon sınıfı|
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Şablon sınıfı|

 Aşağıdaki tabloda kısmi özelleşmenin bazı devralma örnekleri gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------|-------------------------|
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Şablon sınıfı<br /><br /> `B`<br /><br /> örneği<br /><br /> (sınıf A 'ya işaret eder)<br /><br /> `C`<br /><br /> örneği<br /><br /> (sınıf A 'ya işaret eder)|

 Aşağıdaki tabloda kısmi özelleşme şablonu işlevlerinin bazı örnekleri gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------|-------------------------|
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> Func \<T, U > (+ 1 aşırı yükleme)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Şablon sınıfı<br /><br /> `B<T2>`<br /><br /> Şablon sınıfı<br /><br /> (B sınıf içinde **Iç Içe geçmiş türler**altında bulunur)|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> örneği<br /><br /> -> C \<int ><br /><br /> `C<T>`<br /><br /> Şablon sınıfı|

 Aşağıdaki tabloda şablon devralmanın bazı örnekleri gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------|-------------------------|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> örneği<br /><br /> -> B<br /><br /> `C<int>`<br /><br /> örneği<br /><br /> (B, **Iç Içe türler**altında C sınıfı içinde bulunur)<br /><br /> `C<T>`<br /><br /> Şablon sınıfı|

 Aşağıdaki tabloda, kurallı özelleştirilmiş sınıf bağlantısının bazı örnekleri gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------|-------------------------|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> örneği<br /><br /> -> C \<int ><br /><br /> `C<int>`<br /><br /> örneği<br /><br /> `C<T>`<br /><br /> Şablon sınıfı<br /><br /> `D`<br /><br /> örneği<br /><br /> -> C \<float >|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> Min \<T >|

## <a name="see-also"></a>Ayrıca Bkz.
 [C++ Visual Code (sınıf Tasarımcısı)](../ide/working-with-visual-cpp-code-class-designer.md) [sınıfları ve yapıları için](https://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873) [anonim sınıf türleri](https://msdn.microsoft.com/library/9ba667b2-8c2a-4c29-82a6-fa120b9233c8) [(NOTINBUILD) birden fazla devralma](https://msdn.microsoft.com/3b74185e-2beb-4e29-8684-441e51d2a2ca) [birden çok temel sınıf](https://msdn.microsoft.com/library/a30c69fe-401c-4a87-96a0-e0da70c7c740) [şablonu](https://msdn.microsoft.com/library/90fcc14a-2092-47af-9d2e-dba26d25b872)
