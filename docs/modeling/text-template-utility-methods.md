---
title: Metin Şablonu Yardımcı Program Yöntemleri
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c55da4d58b717bc4d42b6fafdd084067b7e21a31
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591768"
---
# <a name="text-template-utility-methods"></a>Metin Şablonu Yardımcı Program Yöntemleri

Visual Studio metin şablonunda kod yazdığınızda her zaman kullanabileceğiniz çeşitli yöntemler vardır. Bu yöntemler <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>tanımlanmıştır.

> [!TIP]
> Ayrıca, ana bilgisayar ortamı tarafından sunulan diğer yöntemleri ve Hizmetleri normal (önceden işlenmiş) metin şablonunda de kullanabilirsiniz. Örneğin, dosya yollarını çözümleyebilir, hataları günlüğe kaydedebilir ve Visual Studio tarafından sunulan hizmetleri ve yüklenmiş tüm paketleri alabilirsiniz. Daha fazla bilgi için bkz. [bir metin şablonundan Visual Studio 'Ya erişme](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

## <a name="write-methods"></a>Yazma yöntemleri

`Write()` ve `WriteLine()` yöntemlerini, bir ifade kod bloğu kullanmak yerine standart bir kod bloğunun içine metin eklemek için kullanabilirsiniz. Aşağıdaki iki kod bloğu işlevsel olarak eşdeğerdir.

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

`Write()` ve `WriteLine()` yöntemlerinin iki aşırı yüklemesi vardır, biri tek bir dize parametresi ve bir bileşik biçim dizesi ve bir dizi nesnenin içermesi için bir nesne dizisi (`Console.WriteLine()` yöntemi gibi) alır. Aşağıdaki iki kullanım `WriteLine()` işlevsel olarak eşdeğerdir:

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

Metin şablonunuzun çıkışını biçimlendirmek için girintileme yöntemlerini kullanabilirsiniz. <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> sınıfı, metin şablonundaki geçerli girintiyi ve eklenen girintilendirme listesi olan bir `indentLengths` alanını gösteren bir `CurrentIndent` String özelliğine sahiptir. `PushIndent()` yöntemiyle bir girintileme ekleyebilir ve `PopIndent()` yöntemiyle bir girintileme çıkarabilirsiniz. Tüm girintileri kaldırmak istiyorsanız, `ClearIndent()` yöntemini kullanın. Aşağıdaki kod bloğu bu yöntemlerin kullanımını gösterir:

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

Özellik `this.Host`, şablonu yürüten ana bilgisayar tarafından kullanıma sunulan özelliklere erişim sağlayabilir. `this.Host`kullanmak için `<@template#>` yönergesinde `hostspecific` özniteliğini ayarlamanız gerekir:

`<#@template ... hostspecific="true" #>`

`this.Host` türü, şablonun yürütüldüğü konak türüne bağlıdır. Visual Studio 'da çalışan bir şablonda, IDE gibi hizmetlere erişim kazanmak için `this.Host` `IServiceProvider` çevirebilirsiniz. Örneğin:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Farklı bir yardımcı program yöntemi kümesi kullanma

Metin oluşturma sürecinin bir parçası olarak, şablon dosyanız her zaman `GeneratedTextTransformation`olarak adlandırılan ve <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>devralan bir sınıfa dönüştürülür. Bunun yerine farklı bir yöntem kümesi kullanmak istiyorsanız kendi sınıfınızı yazabilir ve onu şablon yönergesinde belirtebilirsiniz. Sınıfınızın <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>devralması gerekir.

```
<#@ template inherits="MyUtilityClass" #>
```

Derlenmiş sınıfın bulunabileceği derlemeye başvurmak için `assembly` yönergesini kullanın.
