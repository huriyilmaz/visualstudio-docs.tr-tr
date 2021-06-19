---
title: T4 Parametre Yönergesi
description: Bu konuda Visual Studio yönergesi, şablon kodunda dış bağlamdan geçirilen değerlerden başlatılan özellikleri bildirmektedir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8ef80179d43996669b9d883fd2ca9163208d18d7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386104"
---
# <a name="t4-parameter-directive"></a>T4 Parametre Yönergesi

Bir Visual Studio şablonunda yönergesi, şablon kodunda dış bağlamdan geçirilen değerlerden `parameter` başlatılan özellikleri bildirmektedir. Metin dönüştürmeyi çağıran bir kod yazarsanız bu değerleri ayarlayın.

## <a name="using-the-parameter-directive"></a>Parametre Yönergesi Kullanma

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 `parameter`yönergesi, şablon kodunda dış bağlamdan geçirilen değerlerden başlatılan özellikleri bildirmektedir. Metin dönüştürmeyi çağıran bir kod yazarsanız bu değerleri ayarlayın. Değerler sözlüğünde veya içinde `Session` <xref:System.Runtime.Remoting.Messaging.CallContext> geçirebilirsiniz.

 Herhangi bir uzamotable türünde parametreler bildirebilir. Başka bir ifadeyle türün ile bildirmiş olması <xref:System.SerializableAttribute> veya türünden türetmiş olması <xref:System.MarshalByRefObject> gerekir. Bu, parametre değerlerinin şablonun işlendiğinde AppDomain'e geçirilene izin verir.

 Örneğin, aşağıdaki içeriğe sahip bir metin şablonu yazabilirsiniz:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>Parametre değerlerini şablona geçirme
 Menü komutu veya olay Visual Studio gibi bir Uzantı Uzantısı yazıyorsanız, metin şablon oluşturma hizmetini kullanarak bir şablonu işebilirsiniz:

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

## <a name="passing-values-in-the-call-context"></a>Çağrı Bağlamına değer geçirme
 Alternatif olarak, içinde değerleri mantıksal veri olarak da <xref:System.Runtime.Remoting.Messaging.CallContext> geçebilirsiniz.

 Aşağıdaki örnek, her iki yöntemi kullanarak değerleri iletir:

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

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Değerleri bir Run-Time (Önceden İşlenmemiş) Metin Şablonuna Geçirme
 Yönergenin çalışma zamanı `<#@parameter#>` (önceden işlenmiştir) metin şablonlarıyla birlikte kullanımı genellikle gerekli değildir. Bunun yerine, parametre değerlerini iletirsiniz, oluşturulan kod için ek bir oluşturucu veya ayarlandırabilir bir özellik tanımlayabilirsiniz. Daha fazla bilgi için [bkz. T4 Metin Şablonları ile Çalışma Zamanı Metin Oluşturma.](../modeling/run-time-text-generation-with-t4-text-templates.md)

 Ancak, bir çalışma zamanı şablonunda kullanmak için, Oturum sözlüğü `<#@parameter>` kullanarak buna değer geçebilirsiniz. Örneğin, dosyayı adlı önceden işlenmemiş bir şablon olarak oluşturduğunuz `PreTextTemplate1` varsayalım. Aşağıdaki kodu kullanarak programda şablonu çağırabilirsiniz.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();
```

## <a name="obtaining-arguments-from-texttemplateexe"></a>Bağımsız değişkenleri TextTemplate.exe

> [!IMPORTANT]
> `parameter`yönergesi yardımcı programın parametresinde `-a` ayarlanmış değerleri `TextTransform.exe` almaz. Bu değerleri almak için `hostSpecific="true"` yönergesinde `template` ayarlayın ve `this.Host.ResolveParameterValue("","","argName")` kullanın.
