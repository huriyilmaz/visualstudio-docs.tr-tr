---
title: Bir VS Uzantısında Metin Dönüştürmeyi Çağırma
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8729a96d236fd565f31c827ebff6911dbc0b81d6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667762"
---
# <a name="invoke-text-transformation-in-a-visual-studio-extension"></a>Visual Studio uzantısında metin dönüştürmeyi çağırma

Bir menü komutu veya [etki alanına özgü dil](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)gibi bir Visual Studio uzantısı yazıyorsanız metin şablonlarını dönüştürmek için metin şablonu oluşturma hizmetini kullanabilirsiniz. [Stextşablon](/previous-versions/visualstudio/visual-studio-2012/bb932394(v=vs.110)) oluşturma hizmetini alın ve bunu [ıtextşablon](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110))oluşturma 'ya dönüştürün.

## <a name="get-the-text-templating-service"></a>Metin şablonu oluşturma hizmetini al

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;

// Process a text template:
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));
```

## <a name="pass-parameters-to-the-template"></a>Parametreleri şablona geçir

 Parametreleri şablona geçirebilirsiniz. Şablon içinde, `<#@parameter#>` yönergesini kullanarak parametre değerlerini alabilirsiniz.

 Parametre türü için, seri hale getirilebilen veya sıralanabilen bir tür kullanmalısınız. Diğer bir deyişle, tür <xref:System.SerializableAttribute> ile bildirilmelidir veya <xref:System.MarshalByRefObject> türetilmesi gerekir. Bu kısıtlama gereklidir çünkü metin şablonu ayrı bir AppDomain içinde yürütülür. **System. String** ve **System. Int32** gibi tüm yerleşik türler seri hale getirilebilir.

 Parametre değerlerini geçirmek için, çağıran kod `Session` sözlüğünde ya da <xref:System.Runtime.Remoting.Messaging.CallContext> bir değer yerleştirebilir.

 Aşağıdaki örnek bir kısa test şablonunu dönüştürmek için her iki yöntemi kullanmaktadır:

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte;

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;

// Create a Session in which to pass parameters:
sessionHost.Session = sessionHost.CreateSession();
sessionHost.Session["parameter1"] = "Hello";
sessionHost.Session["parameter2"] = DateTime.Now;

// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);

// Process a text template:
string result = t4.ProcessTemplate("",
   // This is the test template:
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");

// This test code yields a result similar to the following line:
//     Test: Hello    07/06/2010 12:37:45    42
```

## <a name="error-reporting-and-the-output-directive"></a>Hata raporlama ve çıkış yönergesi

İşlem sırasında ortaya çıkan hatalar Visual Studio hata penceresinde görüntülenir. Ayrıca, [ITextTemplatingCallback](/previous-versions/visualstudio/visual-studio-2012/bb932397(v=vs.110))uygulayan bir geri çağırma belirterek hatalarla ilgili bildirim alabilirsiniz.

Sonuç dizesini bir dosyaya yazmak istiyorsanız, şablondaki `<#@output#>` yönergesinde hangi dosya uzantısının ve kodlamasının belirtildiklerini bilmeniz gerekebilir. Bu bilgiler, geri çağırmanıza da geçirilir. Daha fazla bilgi için bkz. [T4 çıkış yönergesi](../modeling/t4-output-directive.md).

```csharp
void ProcessMyTemplate(string MyTemplateFile)
{
  string templateContent = File.ReadAllText(MyTemplateFile);
  T4Callback cb = new T4Callback();
  // Process a text template:
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);
  // If there was an output directive in the MyTemplateFile,
  // then cb.SetFileExtension() will have been called.
  // Determine the output file name:
  string resultFileName =
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),
        Path.GetFileNameWithoutExtension(MyTemplateFile))
      + cb.fileExtension;
  // Write the processed output to file:
  File.WriteAllText(resultFileName, result, cb.outputEncoding);
  // Append any error messages:
  if (cb.errorMessages.Count > 0)
  {
    File.AppendAllLines(resultFileName, cb.errorMessages);
  }
}

class T4Callback : ITextTemplatingCallback
{
  public List<string> errorMessages = new List<string>();
  public string fileExtension = ".txt";
  public Encoding outputEncoding = Encoding.UTF8;

  public void ErrorCallback(bool warning, string message, int line, int column)
  { errorMessages.Add(message); }

  public void SetFileExtension(string extension)
  { fileExtension = extension; }

  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)
  { outputEncoding = encoding; }
}
```

Kod, şuna benzer bir şablon dosyasıyla test edilebilir:

```
<#@output extension=".htm" encoding="ASCII"#>
<# int unused;  // Compiler warning "unused variable"
#>
Sample text.
```

Derleyici Uyarısı, Visual Studio hata penceresinde görünür ve ayrıca `ErrorCallback` bir çağrı oluşturur.

## <a name="reference-parameters"></a>Başvuru parametreleri

@No__t_0 türetilmiş bir parametre sınıfını kullanarak değerleri bir metin şablonundan geçirebilirsiniz.

## <a name="related-articles"></a>İlgili makaleler

Önceden işlenmiş bir metin şablonundan metin oluşturmak için: oluşturulan sınıfın `TransformText()` yöntemini çağırın. Daha fazla bilgi için bkz. [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md).

Visual Studio uzantısı dışında metin oluşturmak için: özel bir konak tanımlayın. Daha fazla bilgi için bkz. [özel bir konak kullanarak metin şablonlarını işleme](../modeling/processing-text-templates-by-using-a-custom-host.md).

Daha sonra derlenebilecek ve yürütülebilecek kaynak kodu oluşturmak için: [ıtextşablon](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110))oluşturma 'Nın [PreprocessTemplate](/previous-versions/visualstudio/visual-studio-2012/ee844321(v=vs.110)) metodunu çağırın.
