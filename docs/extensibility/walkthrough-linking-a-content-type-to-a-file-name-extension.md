---
title: 'Walkthrough: İçerik Türünü Dosya Adı Uzantısına Bağlama | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 328be013b5d522938cd7450fc53d4866c632abb3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697076"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Walkthrough: İçerik türünü dosya adı uzantısına bağlama
Düzenleyici Yönetilen Genişletilebilirlik Çerçevesi (MEF) uzantılarını kullanarak kendi içerik türünüzü tanımlayabilir ve bir dosya adı uzantısını ona bağlayabilirsiniz. Bazı durumlarda, dosya adı uzantısı zaten bir dil hizmeti tarafından tanımlanır. Ancak, MEF ile kullanmak için, yine de bir içerik türüne bağlamak gerekir.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

1. Bir C# VSIX projesi oluşturun. (Yeni **Proje** iletişim kutusunda Visual **C# / Genişletilebilirlik,** ardından **VSIX Project'i**seçin.) Çözümü `ContentTypeTest`adlandırın.

2. **source.extension.vsixmanifest** dosyasında, **Varlıklar** sekmesine gidin ve **Type** alanını **Microsoft.VisualStudio.MefComponent,** **Kaynak** alanını **geçerli çözümdeki bir projeye**ve **Proje** alanını projenin adına ayarlayın.

## <a name="define-the-content-type"></a>İçerik türünü tanımlama

1. Bir sınıf dosyası ekleyin `FileAndContentTypes`ve adlandırın.

2. Aşağıdaki derlemelere başvurular ekleyin:

    1. System.ComponentModel.Composition

    2. Microsoft.VisualStudio.Text.Logic

    3. Microsoft.VisualStudio.CoreUtility

3. Aşağıdaki `using` yönergeleri ekleyin.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. Tanımları içeren statik bir sınıf bildirin.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. Bu sınıfta, "gizli" adlı bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> dışa aktarma ve temel tanımını "metin" olarak bildirin.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>Dosya adı uzantısını içerik türüne bağlama

- Bu içerik türünü bir dosya adı uzantısı <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> ile eşlemek için,.hid uzantısı ve içerik türü *"gıdıklanmış"* olan bir dışa aktarın.

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

## <a name="add-the-content-type-to-an-editor-export"></a>İçerik türünü düzenleyici dışa aktarmaya ekleme

1. Bir düzenleyici uzantısı oluşturun. Örneğin, Walkthrough'da açıklanan kenar boşluğu [glyph uzantısını kullanabilirsiniz: Kenar boşluğu gph'u oluşturun.](../extensibility/walkthrough-creating-a-margin-glyph.md)

2. Bu yordamda tanımladığınız sınıfı ekleyin.

3. Uzantı sınıfını dışa <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> aktarırken, buna "gizli" türüekleyin.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve editör uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
