---
title: 'Kılavuz: Modele Erişen Metin Şablonlarında Hata Ayıklama'
description: Modele erişen bir metin şablonunda hata ayıklama hakkında bilgi sağlar.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: d39b1ac72210145cc1efa1c513b7f3b76d8c2e36
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388236"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>İzlenecek yol: Modele Erişen Metin Şablonunda Hata Ayıklama
Etki alanına özgü bir dil çözümünde metin şablonlarını değiştirerek veya eklerken, altyapı şablonu kaynak koduna dönüştürerek veya oluşturulan kodu derleyene zaman hatayla karşınıza çıkabilirsiniz. Aşağıdaki kılavuzda, metin şablonunda hata ayıklamak için gerçekleştirebilirsiniz.

> [!NOTE]
> Genel olarak metin şablonları hakkında daha fazla bilgi için bkz. [Kod Oluşturma ve T4 Metin Şablonları.](../modeling/code-generation-and-t4-text-templates.md) Metin şablonlarında hata ayıklama hakkında daha fazla bilgi için [bkz. Adım adım kılavuz: Metin Şablonunda Hata Ayıklama.](debugging-a-t4-text-template.md)

## <a name="creating-a-domain-specific-language-solution"></a>Domain-Specific Dili Çözümü Oluşturma
 Bu yordamda, aşağıdaki özelliklere sahip etki alanına özgü bir dil çözümü oluşturabilirsiniz:

- Ad: DebuggingTestLanguage

- Çözüm şablonu: Minimum Dil

- Dosya uzantısı: .ddd

- Şirket adı: Fabrikam

  Etki alanına özgü bir dil çözümü oluşturma hakkında daha fazla bilgi için [bkz. Nasıl: Domain-Specific Dil Çözümü Oluşturma.](../modeling/how-to-create-a-domain-specific-language-solution.md)

## <a name="creating-a-text-template"></a>Metin şablonu oluşturma
 Çözümünüz için bir metin şablonu ekleyin.

#### <a name="to-create-a-text-template"></a>Metin şablonu oluşturmak için

1. Çözümü derleme ve hata ayıklayıcıda çalıştırmaya başlama. (Derleme menüsünde **Çözümü Yeniden** Oluştur'a **tıklayın** ve ardından Hata Ayıklama menüsünde Hata **Ayıklamayı** **Başlat'a tıklayın.)** Hata ayıklama Visual Studio yeni bir örnek açılır.

2. Hata Ayıklama projesine `DebugTest.tt` adlı bir metin dosyası ekleyin.

3. Uygulamanın Özel **Araç özelliğinin** olarak DebugTest.tt emin `TextTemplatingFileGenerator` olun.

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Metin şablonundan modele erişen hata ayıklama yönergeleri
 Bir metin şablonunda deyimlerinden ve ifadelerinden bir modele erişmek için önce oluşturulan yönerge işlemcisini çağırmalısınız. Oluşturulan yönerge işlemcisinin çağrılarak modeliniz sınıflarını metin şablonu koduna özellik olarak kullanılabilir. Daha fazla bilgi için [bkz. Metin Şablonlarından Modellere Erişme.](../modeling/accessing-models-from-text-templates.md)

 Aşağıdaki yordamlarda, yanlış yönerge adı ve yanlış bir özellik adı için hata ayıklarsiniz.

#### <a name="to-debug-an-incorrect-directive-name"></a>Yanlış yönerge adının hata ayıklaması için

1. aşağıdaki kodla DebugTest.tt kodu değiştirin:

    > [!NOTE]
    > Kod bir hata içeriyor. Hata ayıklamak için hataya neden olur.

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

2. Bu **Çözüm Gezgini,** Özel Araç'DebugTest.tt sağ tıklayın ve ardından Özel **Aracı Çalıştır'a tıklayın.**

     Hata **Listesi penceresinde** şu hata görüntülenir:

     **'DebuggingTestLanguageDirectiveProcessor' adlı işlemci, 'modelRoot' adlı yönergeyi desteklemez. Dönüştürme çalıştırmayacak.**

     Bu durumda, yönerge çağrısı yanlış bir yönerge adı içerir. Yönerge adı `modelRoot` olarak belirttiniz ancak doğru yönerge adı şu şekildedir: `DebuggingTestLanguage` .

3. Hata Listesi penceresinde hataya **çift tıklayıp** koda atlayın.

4. Kodu düzeltmek için yönerge adını olarak `DebuggingTestLanguage` değiştirebilirsiniz.

     Değişiklik vurgulanır.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. Bu **Çözüm Gezgini,** Özel Araç'DebugTest.tt sağ tıklayın ve ardından Özel **Aracı Çalıştır'a tıklayın.**

     Şimdi sistem metin şablonunu dönüştüren ve karşılık gelen çıkış dosyasını oluşturur. Hata Listesi penceresinde herhangi bir **hata görmüyorsanız.**

#### <a name="to-debug-an-incorrect-property-name"></a>Yanlış özellik adının hata ayıklaması için

1. aşağıdaki kodla DebugTest.tt kodu değiştirin:

    > [!NOTE]
    > Kod bir hata içeriyor. Hata ayıklamak için hataya neden olur.

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

2. Bu **Çözüm Gezgini,** Özel Araç'DebugTest.tt sağ tıklayın ve ardından Özel **Aracı Çalıştır'a tıklayın.**

     Hata **Listesi penceresi** görüntülenir ve şu hatalardan birini görüntüler:

     (C#)

     **Dönüştürmeyi derleme: Microsoft.VisualStudio.TextTemplating \<GUID> . GeneratedTextTransformation', 'ExampleModel' için bir tanım içermez**

     (Visual Basic)

     **Dönüştürmeyi derleme: 'ExampleModel', 'Microsoft.VisualStudio.TextTemplating' üyesi \<GUID> değil. GeneratedTextTransformation'.**

     Bu durumda, metin şablonu kodu yanlış bir özellik adı içeriyor. Özellik adı `ExampleModel` olarak belirttiniz, ancak doğru özellik adı : `LibraryModel` . Aşağıdaki kodda gösterildiği gibi, provides parametresinde doğru özellik adını bulabilirsiniz:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. Hata Listesi penceresinde hataya çift tıklayıp koda atlayın.

4. Kodu düzeltmek için metin şablonu kodunda `LibraryModel` özellik adını olarak değiştirebilirsiniz.

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

5. Bu **Çözüm Gezgini,** Özel Araç'DebugTest.tt sağ tıklayın ve ardından Özel **Aracı Çalıştır'a tıklayın.**

     Şimdi sistem metin şablonunu dönüştüren ve karşılık gelen çıkış dosyasını oluşturur. Hata Listesi penceresinde herhangi bir **hata görmüyorsanız.**
