---
title: DebuggerDisplay özniteliğini kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aba6feb17a4e7bd4cabfe40bd45480a0f7a9f552
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683933"
---
# <a name="using-the-debuggerdisplay-attribute"></a>DebuggerDisplay Özniteliğini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Diagnostics.DebuggerDisplayAttribute>Bir nesne, özellik veya alanın hata ayıklayıcı değişkeni penceresinde nasıl görüntülendiğini denetler. Bu öznitelik türler, temsilciler, özellikler, alanlar ve derlemelere uygulanabilir.  
  
 `DebuggerDisplay`Özniteliğin tek bir bağımsız değişkeni vardır ve bu, türü örneklerin değer sütununda görüntülenecek bir dizedir. Bu dize, küme ayraçları ( `{` ve `}` ) içerebilir. Bir küme ayraçları içindeki metin, alan, özellik veya yöntem olarak değerlendirilir.  
  
 Bir sınıfta geçersiz kılınan bir `ToString()` Yöntem varsa, hata ayıklayıcı varsayılan yerine geçersiz kılınan yöntemi kullanır `{<typeName>}` . Bu nedenle, yöntemi geçersiz kıldıysanız `ToString()` , hata ayıklayıcı varsayılan yerine geçersiz kılınan yöntemi kullanır `{<typeName>}` ve kullanmak zorunda değilsiniz `DebuggerDisplay` . Her ikisini de kullanırsanız, `DebuggerDisplay` öznitelik geçersiz kılınan yönteme göre önceliklidir `ToString()` .  
  
 Hata ayıklayıcının bu örtük çağrıyı değerlendirip, `ToString()` **Araçlar/Seçenekler/hata ayıklama** iletişim kutusunda bir Kullanıcı ayarına bağlıdır. Visual Basic bu örtük `ToString()` değerlendirmeyi uygulamaz.  
  
> [!IMPORTANT]
> **Araçlar/Seçenekler/hata ayıklama** iletişim kutusunda **değişkenlerin ham yapısını göster Windows** onay kutusu işaretliyse, `DebuggerDisplay` öznitelik yok sayılır.  
  
 Aşağıdaki tabloda, özniteliğin bazı olası kullanımları `DebuggerDisplay` ve örnek çıktıları gösterilmektedir.  
  
|Öznitelik|**Değer** sütununda görünen çıkış)|  
|---------------|------------------------------------------------|  
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Alanlar ve içeren bir tür üzerinde `x` kullanılır `y` .|`x = 5 y = 18`|  
|`[DebuggerDisplay("String value is {getString()}")]`Parametre sözdizimi diller arasında farklılık gösterebilir. Bu nedenle, dikkatli bir şekilde kullanın.|`String value is [5, 6, 6]`|  
  
 `DebuggerDisplay` adlandırılmış parametreleri de kabul edebilir.  
  
|Parametreler|Amaç|  
|----------------|-------------|  
|`Name`, `Type`|Bu parametreler, Windows değişkeninin **ad** ve **tür** sütunlarını etkiler. (Oluşturucu ile aynı söz dizimini kullanan dizeler için de ayarlanabilir.) Bu parametrelerin aşırı kullanılması veya yanlış kullanılması, kafa karıştırıcı çıktıya neden olabilir.|  
|`Target`, `TargetTypeName`|Öznitelik, derleme düzeyinde kullanıldığında hedef türünü belirtir.|  
  
 Autoexp.cs dosyası, derleme düzeyinde DebuggerDisplay özniteliğini kullanır. Autoexp.cs dosyası, Visual Studio 'Nun .NET nesneleri için kullandığı varsayılan genişleimleri belirler. DebuggerDisplay özniteliğini kullanma örnekleri için autoexp.cs dosyasını inceleyebilir veya varsayılan genişletmeleri değiştirmek için autoexp.cs dosyasını değiştirebilir ve derleyebilirsiniz. Autoexp.cs dosyasını değiştirmeden önce yedeklediğinizden emin olun.  
  
 Autoexp.cs oluşturmak için, VS2015 için bir Geliştirici Komut İstemi açın ve aşağıdaki komutları çalıştırın  
  
```  
cd <directory containing autoexp.cs>  
csc /t:library autoexp.cs  
```  
  
 autoexp.dll yapılan değişiklikler bir sonraki hata ayıklama oturumunda alınacaktır.  
  
## <a name="using-expressions-in-debuggerdisplay"></a>DebuggerDisplay içinde Ifadeleri kullanma  
 DebuggerDisplay özniteliğinde küme ayraçları arasında genel bir ifade kullanabilseniz de, bu uygulama önerilmez.  
  
 DebuggerDisplay içindeki genel bir ifade, `this` yalnızca hedef türün geçerli örneği için işaretçiye örtülü erişime sahiptir. İfadenin diğer adlar, Yereller veya işaretçiler erişimi yok. İfade özelliklere başvuruyorsa, bu özelliklerdeki öznitelikler işlenmez. Örneğin, `[DebuggerDisplay("Object {count - 2}"`  alan 8 Ise C# kodu görüntülenir `Object 6` `count` .  
  
 DebuggerDisplay içinde ifadelerin kullanılması aşağıdaki sorunlara yol açabilir:  
  
- İfadeleri değerlendirmek hata ayıklayıcıda en pahalı işlemdir ve ifade her görüntülendiğinde değerlendirilir. Bu, kodun üzerinden adımlarken performans sorunlarına neden olabilir. Örneğin, öğelerin sayısı büyükse, bir koleksiyondaki veya listedeki değerleri göstermek için kullanılan karmaşık bir ifade çok yavaş olabilir.  
  
- İfadeler, ifadenin yazıldığı dilin değerlendiricisi tarafından değil, geçerli yığın çerçevesinin dilinin ifade değerlendiricisi tarafından değerlendirilir. Bu, diller farklı olduğunda öngörülemeyen sonuçlara neden olabilir.  
  
- Bir ifadeyi değerlendirmek uygulamanın durumunu değiştirebilir. Örneğin, bir özelliğin değerini ayarlayan bir ifade, yürütülen koddaki özellik değerini indirger.  
  
  İfade değerlendirmesinin olası sorunlarını azaltmanın bir yolu, işlemi gerçekleştiren ve bir dize döndüren özel bir özellik oluşturmaktır. DebuggerDisplay özniteliği daha sonra bu özel özelliğin değerini gösterebilir. Aşağıdaki örnek bu kalıbı uygular:  
  
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
             return string.Format("("Object {0}", count - 2);  
        }      
    }  
}  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği `DebuggerDisplay` , ve ile birlikte nasıl kullanılacağını göstermektedir `DebuggerBrowseable` `DebuggerTypeProxy` . **İzleme** penceresi gibi bir hata ayıklayıcı değişkenleri penceresinde görüntülendiğinde şuna benzer bir genişletme oluşturur:  
  
|**Ad**|**Değer**|**Tür**|  
|--------------|---------------|--------------|  
|Anahtar|ünden|nesne {String}|  
|Değer|3|nesne {int}|  
  
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
    }    private string DebuggerDisplay    {        get { return "Count = " + hashtable.Count); }    }  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 Hata [ayıklayıcı görüntü öznitelikleriyle hata ayıklamayı geliştirmeyle](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410) [DebuggerTypeProxy özniteliği kullanma](../debugger/using-debuggertypeproxy-attribute.md)
