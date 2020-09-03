---
title: Metin şablonu yardımcı program yöntemleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 52
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c38b15a3b819ce561c098c3b9810ee6884e526b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658531"
---
# <a name="text-template-utility-methods"></a>Metin Şablonu Yardımcı Program Yöntemleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir metin şablonunda kod yazdığınızda her zaman kullanabileceğiniz çeşitli yöntemler vardır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Bu yöntemler içinde tanımlanmıştır <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

> [!TIP]
> Ayrıca, ana bilgisayar ortamı tarafından sunulan diğer yöntemleri ve Hizmetleri normal (önceden işlenmiş) metin şablonunda de kullanabilirsiniz. Örneğin, dosya yollarını çözümleyebilir, hataları günlüğe kaydedebilir ve tarafından sunulan hizmetleri [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve yüklü paketleri alabilirsiniz.  Daha fazla bilgi için bkz. [bir metin şablonundan Visual Studio 'Ya erişme](https://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).

## <a name="write-methods"></a>Yazma yöntemleri
 `Write()` `WriteLine()` Bir ifade kodu bloğu kullanmak yerine standart bir kod bloğunun içine metin eklemek için ve yöntemlerini kullanabilirsiniz. Aşağıdaki iki kod bloğu işlevsel olarak eşdeğerdir.

##### <a name="code-block-with-an-expression-block"></a>İfade bloğuna sahip kod bloğu

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

##### <a name="code-block-using-writeline"></a>WriteLine () kullanarak kod bloğu

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
 Hata Listesi ileti eklemek için hata ve uyarı yardımcı programı yöntemlerini kullanabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Örneğin, aşağıdaki kod Hata Listesi bir hata mesajı ekler.

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

 Türü, `this.Host` şablonun yürütüldüğü konak türüne bağlıdır. İçinde çalışan bir şablonda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , `this.Host` `IServiceProvider` IDE gibi hizmetlere erişim kazanmak için ' a atayabilirsiniz. Örneğin:

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
