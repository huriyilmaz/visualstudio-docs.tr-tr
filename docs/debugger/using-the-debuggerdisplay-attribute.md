---
title: DebuggerDisplay komutlarını kullanarak özel bilgileri | Microsoft Docs
description: Hata ayıklayıcısı değişken pencerelerde bir nesnenin, özelliğin veya alanın nasıl görüntülendiğinden emin olmak için DebuggerDisplayAttribute örneğini kullanın.
ms.custom: SEO-VS-2020
ms.date: 01/09/2019
ms.topic: how-to
helpviewer_keywords:
- attributes, debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 339af0d541ff4493d6066cbd15b98bf4b6725dae158212530e6cf8334c536a81
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121308999"
---
# <a name="tell-the-debugger-what-to-show-using-the-debuggerdisplay-attribute-c-visual-basic-f-ccli"></a>Hata ayıklayıcısına DebuggerDisplay Özniteliğini (C#, Visual Basic, F#, C++/CLI) kullanarak ne göster göster

Bir <xref:System.Diagnostics.DebuggerDisplayAttribute> nesnenin, özelliğin veya alanın hata ayıklayıcısı değişken pencerelerde nasıl görüntülendiğinden emin olur. Bu öznitelik türlere, temsilcilere, özelliklere, alanlara ve derlemelere uygulanabilir. Temel türe uygulanırsa, öznitelik bir alt sınıf için de geçerlidir.

özniteliği, `DebuggerDisplay` tür örnekleri için değer sütununda görüntülenecek bir dize olan tek bir bağımsız değişkene sahip olur. Bu dize küme ayraçları ( ve ) `{` `}` içerebilir. Bir çift ayraç içindeki metin alan, özellik veya yöntem olarak değerlendirilir.

Bir sınıfın geçersiz kılınan bir `ToString()` yöntemi varsa, hata ayıklayıcı varsayılan yerine geçersiz kılma yöntemini `{<typeName>}` kullanır. Bu nedenle, yöntemini geçersiz kılmanız, hata ayıklayıcı varsayılan yerine geçersiz kılma yöntemini kullanır ve `ToString()` `{<typeName>}` kullanmak zorunda `DebuggerDisplay` değildir. Her ikisini de `DebuggerDisplay` kullanırsanız, özniteliği geçersiz kılınan yöntemden `ToString()` önceliklidir. Özniteliği `DebuggerDisplay` ayrıca bir alt sınıfta geçersiz kılınan `ToString()` yöntemden daha önceliklidir.

Hata ayıklayıcının bu örtülü çağrıyı değerlendirip değerlendirmeyip değerlendirmeyecekleri, Araçlar / Seçenekler / Hata Ayıklama iletişim kutusundaki `ToString()` **bir kullanıcı ayarına** bağlıdır.

> [!IMPORTANT]
> Araçlar / Seçenekler **/** **Hata Ayıklama iletişim** kutusunda Değişkenlerin ham yapısını göster onay kutusu seçiliyse, öznitelik `DebuggerDisplay` yoksayılır.

> [!NOTE]
> Yerel kod için bu öznitelik yalnızca C++/CLI kodunda de destekler.

Aşağıdaki tabloda özniteliğin bazı olası kullanımları `DebuggerDisplay` ve örnek çıkışlar yer almaktadır.

|Öznitelik|Değer sütununda görünen çıkış|
|---------------| - |
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> ve alanları ile bir tür üzerinde `x` `y` kullanılır.|`x = 5 y = 18`|
|`[DebuggerDisplay("String value is {getString()}")]`Parametre söz dizimi diller arasında değişiklik gösterebilir. Bu nedenle, bunu özenli bir şekilde kullanın.|`String value is [5, 6, 6]`|

`DebuggerDisplay` adlandırılmış parametreleri de kabul eder.

|Parametreler|Amaç|
|----------------|-------------|
|`Name`, `Type`|Bu parametreler değişken **pencerelerinin Ad** **ve** Tür sütunlarını etkiler. (Bunlar, oluşturucuyla aynı söz dizimi kullanılarak dizelere ayarlanır.) Bu parametreleri aşırı kullanmak veya yanlış kullanmak, kafa karıştırıcı çıkışlara neden olabilir.|
|`Target`, `TargetTypeName`|Öznitelik derleme düzeyinde kullanılırken hedef türü belirtir.|

autoexp.cs dosyası, derleme düzeyinde DebuggerDisplay özniteliğini kullanır. autoexp.cs dosyası, .NET nesneleri için Visual Studio varsayılan genişletmeleri belirler. DebuggerDisplay özniteliğini kullanma örnekleri için autoexp.cs dosyasını inceler veya varsayılan genişletmeleri değiştirmek için autoexp.cs dosyasını değiştirebilir ve derebilirsiniz. Değiştirmeden önce autoexp.cs dosyasını mutlaka arkanız.

autoexp.cs derlemek için VS2015 Geliştirici Komut İstemi bir dosya açın ve aşağıdaki komutları çalıştırın

```cmd
cd <directory containing autoexp.cs>
csc /t:library autoexp.cs
```

Hata autoexp.dll sonraki hata ayıklama oturumunda seçecek.

## <a name="using-expressions-in-debuggerdisplay"></a>DebuggerDisplay'de İfadeleri Kullanma
Bir DebuggerDisplay özniteliğinde küme ayraçları arasında genel bir ifade kullanabilirsiniz, ancak bu uygulama önerilmez.

DebuggerDisplay'de genel bir ifadenin yalnızca hedef türün geçerli örneğinin `this` işaretçisine örtülü erişimi vardır. İfadenin diğer adlara, yerellere veya işaretçilere erişimi yoktur. İfade özelliklere başvurursa, bu özelliklerdeki öznitelikler işlenmez. Örneğin, alan 8 ise C# `[DebuggerDisplay("Object {count - 2}")]` `Object 6` kodu `count` görüntülenir.

DebuggerDisplay içinde ifadelerin kullanımı aşağıdaki sorunlara yol açabilirsiniz:

- İfadeleri değerlendirme, hata ayıklayıcısında en pahalı işlemdir ve ifade her görüntülendiğinde değerlendirilir. Bu, kod adım adım adım performans sorunlarına neden olabilir. Örneğin, bir koleksiyon veya listede değerleri görüntülemek için kullanılan karmaşık bir ifade, öğe sayısı büyük olduğunda çok yavaş olabilir.

- İfadeler, ifadenin yazıldığı dilin değerlendiricisi tarafından değil, geçerli yığın çerçevesinin dilinin ifade değerlendiricisi tarafından değerlendirilir. Bu, diller farklı olduğunda öngörülemeyen sonuçlara neden olabilir.

- Bir ifadenin değerlendirilmesi uygulamanın durumunu değiştirebilir. Örneğin, bir özelliğin değerini ayar eden bir ifade, yürütülen kodda özellik değerinin değerinin yerine yer alar.

  İfade değerlendirmesinin olası sorunlarını azaltmanın bir yolu, işlemi gerçekleştiren ve bir dize döndüren özel bir özellik oluşturmaktır. DebuggerDisplay özniteliği daha sonra bu özel özelliğin değerini görüntüler. Aşağıdaki örnek bu düzeni uygulamaya almaktadır:

```csharp
[DebuggerDisplay("{DebuggerDisplay,nq}")]
public sealed class MyClass
{
    public int count { get; set; }
    public bool flag { get; set; }
    private string DebuggerDisplay
    {
        get
        {
            return string.Format("Object {0}", count - 2);
        }
    }
}
```

",nq" soneki, ifade değerlendiricisine son değeri (nq = tırnak yok) görüntülerken tırnaklarını kaldırmalarını söyler.

## <a name="example"></a>Örnek
Aşağıdaki kod örneği, ve ile birlikte `DebuggerDisplay` kullanmayı `DebuggerBrowsable` `DebuggerTypeProxy` gösterir. İzleme penceresi gibi bir hata ayıklayıcısı değişkenleri penceresinde **görüntü** olduğunda, aşağıdakine benzer bir genişletme üretir:

|**Ad**|**Değer**|**Tür**|
|--------------|---------------|--------------|
|Anahtar|"three"|object {string}|
|Değer|3|object {int}|

```csharp
[DebuggerDisplay("{value}", Name = "{key}")]
internal class KeyValuePairs
{
    private IDictionary dictionary;
    private object key;
    private object value;
    public KeyValuePairs(IDictionary dictionary, object key, object value)
    {
        this.value = value;
        this.key = key;
        this.dictionary = dictionary;
    }

    public object Key
    {
        get { return key; }
        set
        {
            object tempValue = dictionary[key];
            dictionary.Remove(key);
            key = value;
            dictionary.Add(key, tempValue);
        }
    }

    public object Value
    {
        get { return this.value; }
        set
        {
            this.value = value;
            dictionary[key] = this.value;
        }
    }
}

[DebuggerDisplay("{DebuggerDisplay,nq}")]
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable
{
    public Hashtable hashtable;

    public MyHashtable()
    {
        hashtable = new Hashtable();
    }

    private string DebuggerDisplay { get { return "Count = " + hashtable.Count; } }

    private class HashtableDebugView
    {
        private MyHashtable myhashtable;
        public HashtableDebugView(MyHashtable myhashtable)
        {
            this.myhashtable = myhashtable;
        }

        [DebuggerBrowsable(DebuggerBrowsableState.RootHidden)]
        public KeyValuePairs[] Keys
        {
            get
            {
                KeyValuePairs[] keys = new KeyValuePairs[myhashtable.hashtable.Count];

                int i = 0;
                foreach (object key in myhashtable.hashtable.Keys)
                {
                    keys[i] = new KeyValuePairs(myhashtable.hashtable, key, myhashtable.hashtable[key]);
                    i++;
                }
                return keys;
            }
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [DebuggerTypeProxy Özniteliğini Kullanma](../debugger/using-debuggertypeproxy-attribute.md)
- [Yönetilen nesnelerin özel görünümlerini oluşturma](../debugger/create-custom-views-of-managed-objects.md)
- [C# dilinde biçim belirticileri](../debugger/format-specifiers-in-csharp.md)
- [Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
