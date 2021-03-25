---
title: Bir içerik türünü dosya adı uzantısına bağlama
description: Bu izlenecek yolda düzenleyici Managed Extensibility Framework uzantılarını kullanarak kendi içerik türünü bir dosya adı uzantısına bağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 990f10fe82b9230c12ba13d736750f2f644c3ee5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078454"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>İzlenecek yol: bir içerik türünü bir dosya adı uzantısına bağlama
Kendi içerik türünü tanımlayabilir ve düzenleyici Managed Extensibility Framework (MEF) uzantılarını kullanarak bir dosya adı uzantısı ile bağlantı oluşturabilirsiniz. Bazı durumlarda, dosya adı uzantısı zaten bir dil hizmeti tarafından tanımlandı. Ancak, MEF ile kullanmak için yine de onu bir içerik türüne bağlamanız gerekir.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `ContentTypeTest` .

2. **Source. Extension. valtmanifest** dosyasında, **varlıklar** sekmesine gidin ve **tür** alanını **Microsoft. VisualStudio. MefComponent**, **kaynak** alanını ise **geçerli çözümdeki bir projeye** ve **proje alanını projenin** adına ayarlayın.

## <a name="define-the-content-type"></a>İçerik türünü tanımlama

1. Bir sınıf dosyası ekleyin ve adlandırın `FileAndContentTypes` .

2. Aşağıdaki derlemelere başvurular ekleyin:

    1. System. ComponentModel. Composition

    2. Microsoft. VisualStudio. Text. Logic

    3. Microsoft. VisualStudio. CoreUtility

3. Aşağıdaki yönergeleri ekleyin `using` .

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. Tanımları içeren bir statik sınıf bildirin.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. Bu sınıfta, <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> adlandırılmış bir "HID" dışa aktarın ve temel tanımını "metin" olarak bildirin.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>Bir dosya adı uzantısını içerik türüne bağlama

- Bu içerik türünü bir dosya adı uzantısıyla eşlemek için, <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> *. HID* uzantısına ve "HID" içerik türüne sahip bir dışarı aktarma.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
         [Export]
         [Name("hid")]
         [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;

         [Export]
         [FileExtension(".hid")]
         [ContentType("hid")]
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;
    }
    ```

## <a name="add-the-content-type-to-an-editor-export"></a>İçerik türünü bir düzenleyici dışarı aktarmaya ekleme

1. Bir Düzenleyici uzantısı oluşturun. Örneğin, [Izlenecek yol: bir kenar boşluğu karakteri oluşturma](../extensibility/walkthrough-creating-a-margin-glyph.md)bölümünde açıklanan kenar boşluğu glif uzantısını kullanabilirsiniz.

2. Bu yordamda tanımladığınız sınıfı ekleyin.

3. Uzantı sınıfını dışarı aktardığınızda, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> buna "HID" türünde bir tür ekleyin.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
