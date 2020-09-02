---
title: Bir VS Uzantısında Metin dönüştürmeyi çağırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 64674976-841f-43cb-8e61-0645c8a89eec
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a87f84a945d9d79f6d481f7bcc9e656f7ec7bcbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646144"
---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>Bir VS Uzantısında Metin Dönüştürmeyi Çağırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir menü komutu veya [etki alanına özgü dil](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)gibi bir [Visual Studio uzantısı](https://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14) yazıyorsanız metin şablonlarını dönüştürmek için metin şablonu oluşturma hizmetini kullanabilirsiniz. [Stextşablon](/previous-versions/visualstudio/visual-studio-2012/bb932394(v=vs.110)) oluşturma hizmetini alın ve bunu [ıtextşablon](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110))oluşturma 'ya dönüştürün.

## <a name="getting-the-text-templating-service"></a>Metin şablonu oluşturma hizmetini alma

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider – how you do this depends on the context:
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;

// Process a text template:
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));

```

## <a name="passing-parameters-to-the-template"></a>Parametreleri şablona geçirme
 Parametreleri şablona geçirebilirsiniz. Şablon içinde, yönergesini kullanarak parametre değerlerini alabilirsiniz `<#@parameter#>` .

 Parametre türü için, seri hale getirilebilen veya sıralanabilen bir tür kullanmalısınız. Diğer bir deyişle, türü ile bildirilmelidir <xref:System.SerializableAttribute> veya ' den türetilmiş olmalıdır <xref:System.MarshalByRefObject> . Bu kısıtlama gereklidir çünkü metin şablonu ayrı bir AppDomain içinde yürütülür. **System. String** ve **System. Int32** gibi tüm yerleşik türler seri hale getirilebilir.

 Parametre değerlerini geçirmek için, çağıran kod, sözlükte ya da içinde değer yerleştirebilir `Session` <xref:System.Runtime.Remoting.Messaging.CallContext> .

 Aşağıdaki örnek bir kısa test şablonunu dönüştürmek için her iki yöntemi kullanmaktadır:

```
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider – how you do this depends on the context:
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

## <a name="error-reporting-and-the-output-directive"></a>Hata Raporlama ve Çıkış Yönergesi
 İşlem sırasında ortaya çıkan hatalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata penceresinde görüntülenir. Ayrıca, [ITextTemplatingCallback](/previous-versions/visualstudio/visual-studio-2012/bb932397(v=vs.110))uygulayan bir geri çağırma belirterek hatalarla ilgili bildirim alabilirsiniz.

 Sonuç dizesini bir dosyaya yazmak istiyorsanız, şablondaki yönergede hangi dosya uzantısının ve kodlamasının belirtildiklerini bilmeniz gerekebilir `<#@output#>` . Bu bilgiler, geri çağırmanıza da geçirilir. Daha fazla bilgi için bkz. [T4 çıkış yönergesi](../modeling/t4-output-directive.md).

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

 Derleyici Uyarısı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata penceresinde görünür ve aynı zamanda öğesine bir çağrı oluşturacaktır `ErrorCallback` .

## <a name="reference-parameters"></a>Başvuru parametreleri
 Öğesinden türetilmiş bir parametre sınıfını kullanarak değerleri bir metin şablonundan geçirebilirsiniz <xref:System.MarshalByRefObject> .

## <a name="related-topics"></a>İlgili Konular
 Önceden işlenmiş bir metin şablonundan metin oluşturmak için: `TransformText()` oluşturulan sınıfın yöntemini çağırın. Daha fazla bilgi için bkz. [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Uzantı dışında metin oluşturmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] : özel bir konak tanımlayın. Daha fazla bilgi için bkz. [özel bir konak kullanarak metin şablonlarını işleme](../modeling/processing-text-templates-by-using-a-custom-host.md).

 Daha sonra derlenebilecek ve yürütülebilecek kaynak kodu oluşturmak için: [ıtextşablon](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110))oluşturma 'Nın [PreprocessTemplate](/previous-versions/visualstudio/visual-studio-2012/ee844321(v=vs.110)) metodunu çağırın.
