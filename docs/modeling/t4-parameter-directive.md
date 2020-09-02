---
title: T4 Parametre Yönergesi
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f833eb651efda0edb837515e1bf2b3567e1a759
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591807"
---
# <a name="t4-parameter-directive"></a>T4 Parametre Yönergesi

Visual Studio metin şablonunda, `parameter` yönerge, şablon kodunuzda dış bağlamdan geçirilen değerlerden başlatılan özellikleri bildirir. Metin dönüşümünü çağıran kodu yazarsanız, bu değerleri ayarlayabilirsiniz.

## <a name="using-the-parameter-directive"></a>Parameter yönergesini kullanma

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 `parameter`Yönergesi, şablon kodunuzda dış bağlamdan geçirilen değerlerden başlatılan özellikleri bildirir. Metin dönüşümünü çağıran kodu yazarsanız, bu değerleri ayarlayabilirsiniz. Değerler sözlükte ya da `Session` içinde geçirilebilir <xref:System.Runtime.Remoting.Messaging.CallContext> .

 Herhangi bir uzaktan erişilebilir türün parametrelerini bildirebilirsiniz. Diğer bir deyişle, türü ile bildirilmelidir <xref:System.SerializableAttribute> veya türevi olmalıdır <xref:System.MarshalByRefObject> . Bu, parametre değerlerinin, şablonun işlendiği AppDomain 'e geçirilmesini sağlar.

 Örneğin, aşağıdaki içeriğe sahip bir metin şablonu yazabilirsiniz:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>Parametre değerlerini bir şablona geçirme
 Bir menü komutu veya olay işleyicisi gibi bir Visual Studio uzantısı yazıyorsanız, metin şablonu oluşturma hizmetini kullanarak bir şablonu işleyebilirsiniz:

```csharp
// Get a service provider - how you do this depends on the context:
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
 Alternatif olarak, ' de değerleri mantıksal veri olarak geçirebilirsiniz <xref:System.Runtime.Remoting.Messaging.CallContext> .

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
 `<#@parameter#>`Çalışma zamanı (önceden işlenmiş) metin şablonlarıyla yönergesini kullanmak genellikle gerekli değildir. Bunun yerine, ek bir Oluşturucu veya oluşturulmuş kod için parametre değerlerini geçirdiğiniz ayarlanabilir bir özellik tanımlayabilirsiniz. Daha fazla bilgi için bkz. [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Ancak, `<#@parameter>` bir çalışma zamanı şablonunda kullanmak istiyorsanız, oturum sözlüğünü kullanarak değerleri geçirebilirsiniz. Örnek olarak, dosyayı önceden işlenmiş bir şablon olarak oluşturduğunuzu varsayalım `PreTextTemplate1` . Aşağıdaki kodu kullanarak programınızdaki şablonu çağırabilirsiniz.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();
```

## <a name="obtaining-arguments-from-texttemplateexe"></a>TextTemplate.exe bağımsız değişkenleri alma

> [!IMPORTANT]
> `parameter`Yönerge, `-a` yardımcı programın parametresinde ayarlanan değerleri almaz `TextTransform.exe` . Bu değerleri almak için, `hostSpecific="true"` `template` yönergesinde ayarlayın ve kullanın `this.Host.ResolveParameterValue("","","argName")` .
