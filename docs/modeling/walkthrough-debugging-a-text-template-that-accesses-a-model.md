---
title: 'İzlenecek yol: Modele Erişen Metin Şablonunda Hata Ayıklama'
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e33297bba899c1843b8601c031d7669531a1bd3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546906"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>İzlenecek yol: Modele Erişen Metin Şablonunda Hata Ayıklama
Etki alanına özgü dil çözümünde metin şablonlarını değiştirirken veya eklediğinizde, motor şablonu kaynak koda dönüştürdiğinde veya üretilen kodu derlediğinde hata alabilirsiniz. Aşağıdaki kılavuzda, bir metin şablonunda hata ayıklamak için yapabileceğiniz bazı şeyler gösterilmektedir.

> [!NOTE]
> Genel olarak metin şablonları hakkında daha fazla bilgi için bkz. [kod oluşturma ve T4 Metin şablonları](../modeling/code-generation-and-t4-text-templates.md). Metin şablonlarının hatalarını ayıklama hakkında daha fazla bilgi için bkz. [Izlenecek yol: metin şablonunda hata ayıklama](debugging-a-t4-text-template.md).

## <a name="creating-a-domain-specific-language-solution"></a>Etki alanına özgü dil çözümü oluşturma
 Bu yordamda, aşağıdaki özelliklere sahip olan, etki alanına özgü bir dil çözümü oluşturursunuz:

- Ad: DebuggingTestLanguage

- Çözüm şablonu: minimal dil

- Dosya Uzantısı:. ddd

- Şirket adı: fabrikam

  Etki alanına özgü dil çözümü oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: etki alanına özgü dil çözümü oluşturma](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="creating-a-text-template"></a>Metin şablonu oluşturma
 Çözümünüze bir metin şablonu ekleyin.

#### <a name="to-create-a-text-template"></a>Metin şablonu oluşturmak için

1. Çözümü derleyin ve hata ayıklayıcıda çalıştırmayı başlatın. ( **Derle** menüsünde **çözümü yeniden derle**' ye tıklayın ve ardından **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat**' a tıklayın.) Visual Studio 'nun yeni bir örneği hata ayıklama projesini açar.

2. Hata ayıklama projesine adlı bir metin dosyası ekleyin `DebugTest.tt` .

3. DebugTest.tt öğesinin **özel araç** özelliğinin olarak ayarlandığından emin olun `TextTemplatingFileGenerator` .

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Bir metin şablonundan bir modele erişen hata ayıklama yönergeleri
 Bir metin şablonundaki deyimlerden ve ifadelerden bir modele erişebilmek için önce oluşturulan bir yönerge işlemcisini çağırmanız gerekir. Oluşturulan yönerge işlemcisini çağırmak, modelinizdeki sınıfları metin şablonu kodu özelliği olarak kullanılabilir hale getirir. Daha fazla bilgi için bkz. [metin şablonlarından modellere erişme](../modeling/accessing-models-from-text-templates.md).

 Aşağıdaki yordamlarda yanlış yönerge adı ve yanlış özellik adı hatalarını ayıklayacaksınız.

#### <a name="to-debug-an-incorrect-directive-name"></a>Yanlış yönerge adında hata ayıklamak için

1. DebugTest.tt içindeki kodu aşağıdaki kodla değiştirin:

    > [!NOTE]
    > Kod bir hata içeriyor. Hata ayıklama için hatayı alırsınız.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2. **Çözüm Gezgini**' de, DebugTest.tt ' a sağ tıklayın ve ardından **özel araç Çalıştır**' a tıklayın.

     **Hata listesi** penceresinde şu hata görüntülenir:

     **' DebuggingTestLanguageDirectiveProcessor ' adlı işlemci ' modelRoot ' adlı yönergeyi desteklemez. Dönüşüm çalıştırılmayacak.**

     Bu durumda, yönerge çağrısı yanlış bir yönerge adı içeriyor. `modelRoot`Yönerge adı olarak belirttiniz, ancak doğru yönerge adı `DebuggingTestLanguage` .

3. Koda gitmek için **hata listesi** penceresindeki hataya çift tıklayın.

4. Kodu düzeltmek için yönerge adını olarak değiştirin `DebuggingTestLanguage` .

     Değişiklik vurgulanır.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. **Çözüm Gezgini**' de, DebugTest.tt ' a sağ tıklayın ve ardından **özel araç Çalıştır**' a tıklayın.

     Artık sistem metin şablonunu dönüştürür ve ilgili çıktı dosyasını oluşturur. **Hata listesi** penceresinde herhangi bir hata görmezsiniz.

#### <a name="to-debug-an-incorrect-property-name"></a>Yanlış özellik adında hata ayıklamak için

1. DebugTest.tt içindeki kodu aşağıdaki kodla değiştirin:

    > [!NOTE]
    > Kod bir hata içeriyor. Hata ayıklama için hatayı alırsınız.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2. **Çözüm Gezgini**' de, DebugTest.tt ' a sağ tıklayın ve ardından **özel araç Çalıştır**' a tıklayın.

     **Hata listesi** penceresi görünür ve şu hatalardan birini görüntüler:

     (C#)

     **Dönüştürme derleniyor: Microsoft. VisualStudio. Textşablon oluşturma \<GUID> . GeneratedTextTransformation ', ' ExampleModel ' için bir tanım içermiyor**

     (Visual Basic)

     **Dönüştürme derleniyor: ' ExampleModel ', ' Microsoft. VisualStudio. Textşablon oluşturma ' üyesi değil \<GUID> . GeneratedTextTransformation'.**

     Bu durumda, metin şablonu kodu yanlış bir özellik adı içerir. `ExampleModel`Özellik adı olarak belirttiniz, ancak doğru özellik adı `LibraryModel` . Doğru özellik adını aşağıdaki kodda gösterildiği gibi, sağlar parametresinde bulabilirsiniz:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. Koda gitmek için Hata Listesi penceresindeki hataya çift tıklayın.

4. Kodu düzeltmek için özellik adını `LibraryModel` metin şablonu kodunda olarak değiştirin.

     Değişiklikler vurgulanır.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.LibraryModel #>
    <#
    foreach (ExampleElement element in this.LibraryModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.LibraryModel #>
    <#
    For Each element as ExampleElement in Me.LibraryModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

5. **Çözüm Gezgini**' de, DebugTest.tt ' a sağ tıklayın ve ardından **özel araç Çalıştır**' a tıklayın.

     Artık sistem metin şablonunu dönüştürür ve ilgili çıktı dosyasını oluşturur. **Hata listesi** penceresinde herhangi bir hata görmezsiniz.
