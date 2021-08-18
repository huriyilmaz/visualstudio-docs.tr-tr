---
title: Metin Şablonu Denetim Blokları
description: Metin şablonu denetim blokları ve denetim bloklarının çıkışı değiştirme amacıyla metin şablonunuz içinde kod yazmanıza nasıl izin ver olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, template code
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 286bc3b1eba71f3c875e3cdf519a01464b19c6aa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116623"
---
# <a name="text-template-control-blocks"></a>Metin Şablonu Denetim Blokları
Denetim blokları, çıkışı değiştirme amacıyla metin şablonunuz içinde kod yazmanıza izin verir. Açma köşeli ayraçlarıyla ayırt edilen üç tür denetim bloğu vardır:

- `<# Standard control blocks #>` deyimlerini içerebilir.

- `<#= Expression control blocks #>` ifadeleri içerebilir.

- `<#+ Class feature control blocks #>` yöntemler, alanlar ve özellikler içerebilir.

## <a name="standard-control-block"></a>Standart denetim bloğu
 Standart denetim blokları deyimleri içerir. Örneğin, aşağıdaki standart blok XML belgesinde tüm özniteliklerin adlarını alır:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>

<#
    List<string> allAttributes = new List<string>();
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes.Count > 0)
    {
       foreach (XmlAttribute attr in attributes)
       {
           allAtributes.Add(attr.Name);
       }
     }
#>
```

 veya gibi bir bileşik deyimin içine düz metin `if` `for` ebilirsiniz. Örneğin, bu parça her döngü yinelemesinde bir çıkış satırı oluşturur:

```
<#
       foreach (XmlAttribute attr in attributes)
       {
#>
Found another one!
<#
           allAtributes.Add(attr.Name);
       }
#>
```

> [!WARNING]
> Her zaman {...} kullanın eklenmiş düz metin içeren iç içe geçmiş deyimleri sınırlandırma. Aşağıdaki örnek düzgün çalışmayabilir:
>
> `<# if (ShouldPrint) #> Some text. -- WRONG`
>
> Bunun yerine, {braces} öğesini aşağıdaki gibi dahil edersiniz:

```

<#
 if (ShouldPrint)
 {   //  "{" REQUIRED
#>
Some text.
<#
 }
#>
```

## <a name="expression-control-block"></a>İfade denetim bloğu
 İfade denetim blokları, çıkış dosyasına yazacak dizeler sağlayan kodlar için kullanılır. Örneğin, yukarıdaki örnekte kod bloğunda aşağıdaki gibi değiştirerek özniteliklerin adlarını çıktı dosyasına yazdırabilirsiniz:

```
<#
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {
#><#= attr.Name #><#
       }
    }
#>
```

## <a name="class-feature-control-block"></a>Sınıf özelliği denetim bloğu
 Metin şablonunuz için yöntemler, özellikler, alanlar ve hatta iç içe geçmiş sınıflar eklemek için sınıf özelliği denetim bloklarını kullanabilirsiniz. Sınıf özellik bloklarının en yaygın kullanımı, metin şablonunun diğer kısımlarında kod için yardımcı işlevler sağlamaktır. Örneğin, aşağıdaki sınıf özellik bloğu öznitelik adının ilk harfini büyük harfle (veya ad boşluk içeriyorsa, her sözcüğün ilk harfini büyük harfle) büyük harfle ifade ediyor olabilir:

```
<#@ import namespace="System.Globalization" #>
```

```
<#+
    private string FixAttributeName(string name)
    {
        return CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name);
    }
#>
```

> [!NOTE]
> Bir sınıf özellik denetim bloğu, aynı şablon dosyasındaki standart denetim blokları tarafından izlensin. Ancak, bu kısıtlama kullanım yönergelerinin sonucu `<#@include#>` için geçerli değildir. Dahil edilen her dosyada standart bloklar ve ardından sınıf özellik blokları olabilir.

 Metin ve ifade bloklarını bir sınıf özellik denetim bloğu içine katıştırarak çıkış oluşturan bir işlev oluşturabilirsiniz. Örnek:

```
<#+
    private void OutputFixedAttributeName(string name)
    {
#>
 Attribute:  <#= CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name) #>
<#+  // <<< Notice that this is also a class feature block.
    }
#>
```

 Bu işlevi standart bir bloktan veya başka bir sınıf özellik bloğundan çağırabilirsiniz:

```
<# foreach (Attribute attribute in item.Attributes)
{
  OutputFixedAttributeName(attribute.Name);
}
#>
```

## <a name="how-to-use-control-blocks"></a>Denetim bloklarını kullanma
 Tek bir şablonda yer alan tüm standart ve ifade denetim bloklarında yer alan tüm kodlar (dahil edilen şablonlara dahil edilen tüm kodlar dahil) bir araya getir getiri ve `TransformText()` oluşturulan kodun yöntemini oluşturur. (yönergesine diğer metin şablonlarını dahil etme hakkında daha fazla `include` bilgi için bkz. [T4 Metin Şablonu Yönergeleri.)](../modeling/t4-text-template-directives.md)

 Denetim bloklarını kullanırken aşağıdaki konuları göz önünde bulundurmalıdır:

- **Dil.** Bir metin şablonunda C# Visual Basic kodu kullanabilirsiniz. Varsayılan dil C# dilidir, ancak yönergenin Visual Basic ile bu `language` dili `template` belirtesiniz. (yönergesi hakkında daha fazla `template` bilgi için bkz. [T4 Metin Şablonu Yönergeleri.)](../modeling/t4-text-template-directives.md)

     Denetim bloklarında kullanmak istediğiniz dilin, metin şablonunda oluşturulan metnin diliyle veya biçimiyle hiçbir ilgisi yoktur. C# oluşturmak için kod Visual Basic veya tam tersi de yapabilirsiniz.

     Yönergesine dahil etmek istediğiniz tüm metin şablonları dahil olmak üzere, verilen metin şablonunda yalnızca bir dil `include` kullanabilirsiniz.

- **Yerel değişkenler.** Bir metin şablonundaki standart ve ifade denetim bloklarında yer alan tüm kodlar tek bir yöntem olarak oluşturulandan, yerel değişkenlerin adlarında çakışma olmadığını kesin olarak doğrulamalısınız. Diğer metin şablonlarını dahil ediyorsanız, değişken adlarının dahil edilen tüm şablonlar arasında benzersiz olduğundan emin olun. Bunun sağlanmasının bir yolu, içinde bildirilen metin şablonunu tanımlayan her yerel değişken adına bir dize eklemektir.

     Ayrıca, özellikle birden çok metin şablonu dahil ediyorsanız, yerel değişkenlerinizi, bunları bildirilen mantıklı değerlere başlatmak iyi bir fikirdir.

- **Denetim bloklarının iç içe yerleştirmesi.** Denetim blokları iç içe geçmiş olabilir. Başka bir denetim bloğu açmadan önce her zaman bir denetim bloğu sonlandırılmalı. Örneğin, aşağıda standart denetim bloğu kapsamında bir ifade bloğunda bazı metinlerin nasıl yazdırılır?

    ```
    <#
    int x = 10;
    while (x-- > 0)
    {
    #>
    <#= x #>
    <# } #>
    ```

- **Refactoring.** Metin şablonlarınızı kısa ve kolay anlaşılır bir şekilde tutmak için, yeniden kullanılabilir kodu sınıf özellik bloklarında yardımcı işlevler olarak çarpanlara dönüştürerek veya Microsoft.VisualStudio.TextTemplating.TextTransformation sınıfından devralınan kendi metin şablonu sınıfınızı oluşturarak tekrarlanan kodlardan kaçınmanız kesinlikle önerilir.
