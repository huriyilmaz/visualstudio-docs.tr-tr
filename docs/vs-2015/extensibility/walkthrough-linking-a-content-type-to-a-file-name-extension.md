---
title: 'İzlenecek yol: bir Içerik türünü bir dosya adı uzantısına bağlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: beae9d0526cb9f2f294f2267a8da52d3ce3d8c08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202003"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kendi içerik türünü tanımlayabilir ve düzenleyici Managed Extensibility Framework (MEF) uzantılarını kullanarak bir dosya adı uzantısını buna bağlayabilirsiniz. Bazı durumlarda, dosya adı uzantısı zaten bir dil hizmeti tarafından tanımlandı; Bununla birlikte, MEF ile kullanmak için yine de onu bir içerik türüne bağlamanız gerekir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>MEF projesi oluşturma  
  
1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `ContentTypeTest` .  
  
2. **Source. Extension. valtmanifest** dosyasında, **varlıklar** sekmesine gidin ve **tür** alanını **Microsoft. VisualStudio. MefComponent**, **kaynak** alanını ise **geçerli çözümdeki bir projeye**ve **proje alanını projenin** adına ayarlayın.  
  
## <a name="defining-the-content-type"></a>Içerik türünü tanımlama  
  
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
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Bir dosya adı uzantısını Içerik türüne bağlama  
  
- Bu içerik türünü bir dosya adı uzantısıyla eşlemek için, <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> ". HID" uzantısına ve "HID" içerik türüne sahip bir dışarı aktarın.  
  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Içerik türünü bir düzenleyici dışarı aktarmaya ekleme  
  
1. Bir Düzenleyici uzantısı oluşturun. Örneğin, [Izlenecek yol: bir kenar boşluğu karakteri oluşturma](../extensibility/walkthrough-creating-a-margin-glyph.md)bölümünde açıklanan kenar boşluğu glif uzantısını kullanabilirsiniz.  
  
2. Bu yordamda tanımladığınız sınıfı ekleyin.  
  
3. Uzantı sınıfını dışarı aktardığınızda, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> buna "HID" türünde bir tür ekleyin.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil Hizmeti ve Düzenleyici Uzantı Noktaları](../extensibility/language-service-and-editor-extension-points.md)
