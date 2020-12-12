---
title: Metin Şablonu Yardımcı Program Yöntemleri
description: Visual Studio 'da kod yazdığınızda kullanabileceğiniz çeşitli metin şablonu yardımcı program yöntemleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b0015e68f7d78c2b33eaeb9e0bfb404acaed834
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362021"
---
# <a name="text-template-utility-methods"></a>Metin Şablonu Yardımcı Program Yöntemleri

Visual Studio metin şablonunda kod yazdığınızda her zaman kullanabileceğiniz çeşitli yöntemler vardır. Bu yöntemler içinde tanımlanmıştır <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

> [!TIP]
> Ayrıca, ana bilgisayar ortamı tarafından sunulan diğer yöntemleri ve Hizmetleri normal (önceden işlenmiş) metin şablonunda de kullanabilirsiniz. Örneğin, dosya yollarını çözümleyebilir, hataları günlüğe kaydedebilir ve Visual Studio tarafından sunulan hizmetleri ve yüklenmiş tüm paketleri alabilirsiniz. Daha fazla bilgi için bkz. [bir metin şablonundan Visual Studio 'Ya erişme](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

## <a name="write-methods"></a>Yazma yöntemleri

`Write()` `WriteLine()` Bir ifade kodu bloğu kullanmak yerine standart bir kod bloğunun içine metin eklemek için ve yöntemlerini kullanabilirsiniz. Aşağıdaki iki kod bloğu işlevsel olarak eşdeğerdir.

### <a name="code-block-with-an-expression-block"></a>İfade bloğuna sahip kod bloğu

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>WriteLine () kullanarak kod bloğu

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

İç içe geçmiş denetim yapılarına uzun bir kod bloğu içindeki bir ifade bloğu yerine bu yardımcı program yöntemlerinden birini kullanmayı yararlı bulabilirsiniz.

`Write()`Ve `WriteLine()` yöntemlerinin, tek bir dize parametresi alan ve bir bileşik biçim dizesi ve bir dize içeren bir nesne dizisi ile (yöntemi gibi) iki aşırı yüklemesi vardır `Console.WriteLine()` . Aşağıdaki iki kullanımı `WriteLine()` işlevsel olarak eşdeğerdir:

```
<#
    string msg = "Say: {0}, {1}, {2}";
    string s1 = "hello";
    string s2 = "goodbye";
    string s3 = "farewell";

    WriteLine(msg, s1, s2, s3);
    WriteLine("Say: hello, goodbye, farewell");
#>
```

## <a name="indentation-methods"></a>Girintileme yöntemleri

Metin şablonunuzun çıkışını biçimlendirmek için girintileme yöntemlerini kullanabilirsiniz. <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>Sınıfı, `CurrentIndent` metin şablonundaki geçerli girintiyi ve `indentLengths` eklenen girintilendirme listesi olan bir alanı gösteren bir dize özelliğine sahiptir. Yöntemiyle bir girintileme ekleyebilir ve bu yöntemle `PushIndent()` bir girintileme çıkarabilirsiniz `PopIndent()` . Tüm girintileri kaldırmak istiyorsanız `ClearIndent()` yöntemini kullanın. Aşağıdaki kod bloğu bu yöntemlerin kullanımını gösterir:

```
<#
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    ClearIndent();
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
#>
```

Bu kod bloğu aşağıdaki çıktıyı üretir:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Hata ve uyarı yöntemleri

Visual Studio Hata Listesi ileti eklemek için Error ve Warning yardımcı program yöntemlerini kullanabilirsiniz. Örneğin, aşağıdaki kod Hata Listesi bir hata mesajı ekler.

```
<#
  try
  {
    string str = null;
    Write(str.Length.ToString());
  }
  catch (Exception e)
  {
    Error(e.Message);
  }
#>
```

## <a name="access-to-host-and-service-provider"></a>Konak ve hizmet sağlayıcısına erişim

Özelliği, `this.Host` şablonu yürüten ana bilgisayar tarafından kullanıma sunulan özelliklere erişim sağlayabilir. Kullanmak için `this.Host` , `hostspecific` yönergesinde özniteliği ayarlamanız gerekir `<@template#>` :

`<#@template ... hostspecific="true" #>`

Türü, `this.Host` şablonun yürütüldüğü konak türüne bağlıdır. Visual Studio 'da çalışan bir şablonda, `this.Host` `IServiceProvider` IDE gibi hizmetlere erişim kazanmak için ' a atayabilirsiniz. Örneğin:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Farklı bir yardımcı program yöntemi kümesi kullanma

Metin oluşturma sürecinin bir parçası olarak, şablon dosyanız her zaman adlandırılmış ve devralan bir sınıfa dönüştürülür `GeneratedTextTransformation` <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> . Bunun yerine farklı bir yöntem kümesi kullanmak istiyorsanız kendi sınıfınızı yazabilir ve onu şablon yönergesinde belirtebilirsiniz. Sınıfınızın öğesinden devralması gerekir <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

```
<#@ template inherits="MyUtilityClass" #>
```

`assembly`Derlenen sınıfın bulunabileceği derlemeye başvurmak için yönergesini kullanın.
