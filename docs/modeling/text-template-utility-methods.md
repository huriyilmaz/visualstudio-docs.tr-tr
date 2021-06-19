---
title: Metin Şablonu Yardımcı Program Yöntemleri
description: Uygulama içinde kod yazarak size uygun olan çeşitli metin şablonu yardımcı Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b45bf6418562da5315c986a64a1295c137e982d6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388691"
---
# <a name="text-template-utility-methods"></a>Metin Şablonu Yardımcı Program Yöntemleri

Bir metin şablonunda kod yazarak her zaman Visual Studio vardır. Bu yöntemler içinde <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> tanımlanır.

> [!TIP]
> Ayrıca, konak ortamı tarafından sağlanan diğer yöntemleri ve hizmetleri normal (önceden işlenmemiş) bir metin şablonunda da kullanabilirsiniz. Örneğin, dosya yollarını, günlük hatalarını çözümleyebilirsiniz ve bu yollar ve yüklü Visual Studio tarafından sağlanan hizmetleri edinebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio Şablondan Erişim.](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\))

## <a name="write-methods"></a>Yazma yöntemleri

İfade kod bloğu kullanmak yerine standart kod bloğuna metin eklemek için ve `Write()` `WriteLine()` yöntemlerini kullanabilirsiniz. Aşağıdaki iki kod bloğu işlevsel olarak eşdeğerdir.

### <a name="code-block-with-an-expression-block"></a>İfade bloğu ile kod bloğu

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>WriteLine() kullanan kod bloğu

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

İç içe denetim yapılarına sahip uzun bir kod bloğu içinde ifade bloğu yerine bu yardımcı yöntemlerden birini kullanmak yararlı olabilir.

ve yöntemleri, biri tek bir dize parametresi, biri bileşik biçim dizesi ve dizeye dahil etmek için bir nesne dizisi (yöntemi gibi) alan iki aşırı `Write()` `WriteLine()` `Console.WriteLine()` yüklemeye sahiptir. Aşağıdaki iki kullanımı işlevsel `WriteLine()` olarak eşdeğerdir:

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

Metin şablonlarının çıkışını biçimlendirmek için girintileme yöntemlerini kullanabilirsiniz. sınıfı, <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> metin şablonunda geçerli girintiyi gösteren bir dize özelliğine ve eklenen girintilerin listesi `CurrentIndent` olan bir alana `indentLengths` sahip. yöntemiyle bir girinti ekleyebilir `PushIndent()` ve yöntemiyle bir girinti `PopIndent()` çıkarebilirsiniz. Tüm girintileri kaldırmak için yöntemini `ClearIndent()` kullanın. Aşağıdaki kod bloğu, bu yöntemlerin kullanımını gösterir:

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

Bu kod bloğu aşağıdaki çıkışı üretir:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Hata ve uyarı yöntemleri

Hata Listesi'ne ileti eklemek için hata ve uyarı yardımcı Visual Studio kullanabilirsiniz. Örneğin, aşağıdaki kod Hata Listesine bir hata iletisi ekler.

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

## <a name="access-to-host-and-service-provider"></a>Konak ve Hizmet Sağlayıcısına Erişim

özelliği, `this.Host` şablonu yürüten konak tarafından ortaya çıkacak özelliklere erişim sağlar. kullanmak `this.Host` için yönergesinde `hostspecific` özniteliğini `<@template#>` ayarlay gerekir:

`<#@template ... hostspecific="true" #>`

türü, `this.Host` şablonun yürütültt olduğu konak türüne bağlıdır. IDE gibi hizmetlere erişim Visual Studio için, veritabanı içinde çalışan bir şablonda, 'a `this.Host` `IServiceProvider` atabilirsiniz. Örneğin:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Farklı bir yardımcı program yöntemleri kümesi kullanma

Metin oluşturma işleminin bir parçası olarak, şablon dosyanız her zaman adlı ve 'den devralınan `GeneratedTextTransformation` bir sınıfa dönüştürülmektedir. <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> Bunun yerine farklı bir yöntem kümesi kullanmak için kendi sınıfınızı yazabilir ve şablon yönergesinde belirtebilirsiniz. Sınıfınız sınıfından <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> devralmalı.

```
<#@ template inherits="MyUtilityClass" #>
```

Derlenmiş `assembly` sınıfın buluna olduğu derlemeye başvuru yapmak için yönergesi kullanın.
