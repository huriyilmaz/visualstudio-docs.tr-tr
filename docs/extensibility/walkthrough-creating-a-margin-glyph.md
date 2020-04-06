---
title: 'Walkthrough: Margin Glyph oluşturma | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9588b150dd795fc2bc5e6c55d8f6e2359f609939
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697697"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Walkthrough: Bir kenar boşluğu gph oluşturma
Özel düzenleyici uzantıları nı kullanarak düzenleyici kenar boşluklarının görünümünü özelleştirebilirsiniz. Bu gözden geçirme, bir kod yorumunda "todo" sözcüğü göründüğünde gösterge kenar boşluğuna özel bir glyph koyar.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

1. Bir C# VSIX projesi oluşturun. (Yeni **Proje** iletişim kutusunda Visual **C# / Genişletilebilirlik,** ardından **VSIX Project'i**seçin.) Çözümü `TodoGlyphTest`adlandırın.

2. Bir Düzenleyici Sınıflandırıcı proje öğesi ekleyin. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Varolan sınıf dosyalarını silin.

## <a name="define-the-glyph"></a>Glifleri tanımlayın
 Arabirimi çalıştırarak bir <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> glifler tanımlayın.

### <a name="to-define-the-glyph"></a>Glifleri tanımlamak için

1. Bir sınıf dosyası ekleyin `TodoGlyphFactory`ve adlandırın.

2. Bildirimleri kullanarak aşağıdaki kodu ekleyin.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. 'yi uygulayan `TodoGlyphFactory` bir <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>sınıf ekleyin.

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Gliflerin boyutlarını tanımlayan özel bir alan ekleyin.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. Glyph kullanıcı arabirimi (UI) öğesini tanımlayarak uygulayın. `GenerateGlyph` `TodoTag`daha sonra bu izbin içinde tanımlanır.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. 'yi uygulayan `TodoGlyphFactoryProvider` bir <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>sınıf ekleyin. Bu <xref:Microsoft.VisualStudio.Utilities.NameAttribute> sınıfı "TodoGlyph", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> After VsTextMarker, "kod" <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> ve <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag'ın bir sınıfıyla dışa aktarın.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Yöntemi <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> anında uygulayarak uygulayın. `TodoGlyphFactory`

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Todo etiketi ve etiketleme
 Önceki adımlarda tanımladığınız UU öğesi ile gösterge kenar boşluğu arasındaki ilişkiyi tanımlayın. Etiket türü ve etiketçit oluşturun ve bir etiket sağlayıcı kullanarak dışa aktarın.

### <a name="to-define-a-todo-tag-and-tagger"></a>Todo etiketi ve etiketer tanımlamak için

1. Projeye yeni bir sınıf dosyası ekleyin `TodoTagger`ve adlandırın.

2. Aşağıdaki içeri almaları ekleyin.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Adlı sınıf `TodoTag`ekle.

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Türü `TodoTag`uygulayan `TodoTagger` sınıf adlı <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> değiştirin.

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. Sınıfa, `TodoTagger` bir <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> ve metnin sınıflandırma açıklıklarında bulması için özel alanlar ekleyin.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Sınıflandırıcıyı ayarlayan bir oluşturucu ekleyin.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. Yöntemi, <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> adları "yorum" sözcüğü nün bulunduğu ve metni arama metnini içeren tüm sınıflandırma açıklıklarını bularak uygulayın. Arama metni bulunduğunda, yeni <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> bir tür `TodoTag`geri verim.

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Bir `TagsChanged` olay bildirin.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Uygulayan `TodoTaggerProvider` <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>adlı bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> sınıf ekleyin ve "kod" ve <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag ile dışa aktarın.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. İthalat <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Yöntemi <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> anında uygulayarak uygulayın. `TodoTagger`

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Kodu oluşturma ve test edin
 Bu kodu test etmek için TodoGlyphTest çözümlerini oluşturun ve deneme örneğinde çalıştırın.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>TodoGlyphTest çözümlerini oluşturmak ve test etmek için

1. Çözümü derleyin.

2. **F5**tuşuna basarak projeyi çalıştırın. Visual Studio'nun ikinci bir örneği başlıyor.

3. Gösterge marjının gösterdiğinden emin olun. (Araçlar **Tools** menüsünde **Seçenekler'i**tıklatın. Metin **Düzenleyicisi** sayfasında, **Gösterge kenar boşluğunun** seçildiğinden emin olun.)

4. Açıklamaları olan bir kod dosyası açın. Açıklama bölümlerinden birine "todo" sözcüğü ekleyin.

5. Kod penceresinin solundaki gösterge kenar boşluğunda koyu mavi anahat içeren açık mavi bir daire görüntülenir.
