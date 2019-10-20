---
title: T4 parametre yönergesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c1849cbccc1a903716ba94d02f47a339d6ce426
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658566"
---
# <a name="t4-parameter-directive"></a>T4 Parametre Yönergesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 metin şablonunda `parameter` yönergesi, şablon kodunuzda dış bağlamdan geçirilen değerlerden başlatılan özellikleri bildirir. Metin dönüşümünü çağıran kodu yazarsanız, bu değerleri ayarlayabilirsiniz.

## <a name="using-the-parameter-directive"></a>Parameter yönergesini kullanma

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 @No__t_0 yönergesi, şablon kodunuzda dış bağlamdan geçirilen değerlerden başlatılan özellikleri bildirir. Metin dönüşümünü çağıran kodu yazarsanız, bu değerleri ayarlayabilirsiniz. Değerler `Session` sözlüğünde ya da <xref:System.Runtime.Remoting.Messaging.CallContext> geçirilebilir.

 Herhangi bir uzaktan erişilebilir türün parametrelerini bildirebilirsiniz. Diğer bir deyişle, tür <xref:System.SerializableAttribute> ile bildirilmelidir veya <xref:System.MarshalByRefObject> türetmelidir. Bu, parametre değerlerinin, şablonun işlendiği AppDomain 'e geçirilmesini sağlar.

 Örneğin, aşağıdaki içeriğe sahip bir metin şablonu yazabilirsiniz:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>

```

## <a name="passing-parameter-values-to-a-template"></a>Parametre değerlerini bir şablona geçirme
 Bir menü komutu veya olay işleyicisi gibi bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı yazıyorsanız, metin şablonu oluşturma hizmetini kullanarak bir şablonu işleyebilirsiniz:

```csharp
// Get a service provider – how you do this depends on the context:
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example
// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
// Create a Session in which to pass parameters:
host.Session = host.CreateSession();
// Add parameter values to the Session:
session["TimesToRepeat"] = 5;
// Process a text template:
string result = t4.ProcessTemplate("MyTemplateFile.t4",
  System.IO.File.ReadAllText("MyTemplateFile.t4"));

```

## <a name="passing-values-in-the-call-context"></a>Çağrı bağlamındaki değerleri geçirme
 Alternatif olarak, <xref:System.Runtime.Remoting.Messaging.CallContext> değerleri mantıksal veri olarak geçirebilirsiniz.

 Aşağıdaki örnek, her iki yöntemi kullanarak değerleri geçirir:

```csharp
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
host.Session = host.CreateSession();
// Pass a value in Session:
host.Session["p1"] = 32;
// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");

// Process a small template inline:
string result = t4.ProcessTemplate("",
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"
 + "Test <#=p1#> <#=p2#>");

// Result value is:
//     Test 32 test

```

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Çalışma zamanı (önceden Işlenmiş) metin şablonuna değer geçirme
 Çalışma zamanı (önceden işlenmiş) metin şablonlarıyla `<#@parameter#>` yönergesini kullanmak genellikle gerekli değildir. Bunun yerine, ek bir Oluşturucu veya oluşturulmuş kod için parametre değerlerini geçirdiğiniz ayarlanabilir bir özellik tanımlayabilirsiniz. Daha fazla bilgi için bkz. [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Ancak, bir çalışma zamanı şablonunda `<#@parameter>` kullanmak istiyorsanız, oturum sözlüğünü kullanarak değerleri geçirebilirsiniz. Örnek olarak, dosyayı `PreTextTemplate1` adlı önceden işlenmiş bir şablon olarak oluşturduğunuzu varsayalım. Aşağıdaki kodu kullanarak programınızdaki şablonu çağırabilirsiniz.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();

```

## <a name="obtaining-arguments-from-texttemplateexe"></a>TextTemplate. exe ' den bağımsız değişkenler alma

> [!IMPORTANT]
> @No__t_0 yönergesi `TextTransform.exe` yardımcı programının `–a` parametresinde ayarlanan değerleri almaz. Bu değerleri almak için `template` yönergesinde `hostSpecific="true"` ayarlayın ve `this.Host.ResolveParameterValue("","","argName")` kullanın.
