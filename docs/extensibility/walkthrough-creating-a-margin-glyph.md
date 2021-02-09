---
title: 'İzlenecek yol: kenar boşluğu karakteri oluşturma | Microsoft Docs'
description: Bu kılavuzu kullanarak, özel Düzenleyici uzantıları kullanarak Düzenleyici kenar boşluklarının görünümünü nasıl özelleştireceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a2a1857edb8032d12cd23da5e2686ad90f15b574
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892469"
---
# <a name="walkthrough-create-a-margin-glyph"></a>İzlenecek yol: kenar boşluğu karakteri oluşturma
Özel Düzenleyici uzantıları kullanarak Düzenleyici kenar boşluklarının görünümünü özelleştirebilirsiniz. Bu izlenecek yol, bir kod açıklamasında "Todo" sözcüğünün göründüğü her zaman gösterge marjına özel bir karakter koyar.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `TodoGlyphTest` .

2. Bir düzenleyici sınıflandırıcı proje öğesi ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Varolan sınıf dosyalarını silin.

## <a name="define-the-glyph"></a>Glifi tanımlama
 Arabirimini çalıştırarak bir karakter tanımlayın <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

### <a name="to-define-the-glyph"></a>Glifi tanımlamak için

1. Bir sınıf dosyası ekleyin ve adlandırın `TodoGlyphFactory` .

2. Bildirimleri kullanarak aşağıdaki kodu ekleyin.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. Uygulayan adlı bir sınıf ekleyin `TodoGlyphFactory` <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Glifin boyutlarını tanımlayan bir özel alan ekleyin.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. `GenerateGlyph`Glif Kullanıcı arabirimi (UI) öğesini tanımlayarak uygulayın. `TodoTag` Bu izlenecek yolda daha sonra tanımlanmıştır.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. Uygulayan adlı bir sınıf ekleyin `TodoGlyphFactoryProvider` <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Bu sınıfı bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Vstextmarkafter öğesinden sonra, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" ve a TodoTag a 'dan dışarı aktarın <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> .

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Öğesini <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> örnekleyerek yöntemini uygulayın `TodoGlyphFactory` .

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Todo etiketi ve Tagger tanımlama
 Önceki adımlarda tanımladığınız UI öğesi ile gösterge kenar boşluğu arasındaki ilişkiyi tanımlayın. Bir etiket türü ve Tagger oluşturun ve bir Tagger sağlayıcısı kullanarak dışarı aktarın.

### <a name="to-define-a-todo-tag-and-tagger"></a>Todo etiketi ve Tagger tanımlamak için

1. Projeye yeni bir sınıf dosyası ekleyin ve bunu adlandırın `TodoTagger` .

2. Aşağıdaki içeri aktarmaları ekleyin.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Adlı bir sınıf ekleyin `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Türünü uygulayan adlı sınıfı değiştirin `TodoTagger` <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. `TodoTagger`Sınıfına, için <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> ve sınıflandırma yayılmasında bulunacak metin için özel alanlar ekleyin.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Sınıflandırıcının ayarlayan bir Oluşturucu ekleyin.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>Adları "Açıklama" sözcüğünü içeren ve metin arama metnini içeren tüm sınıflandırma yayılmalarını bularak yöntemini uygulayın. Arama metni bulunduğunda, yeni bir türü geri dönün <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Bir `TagsChanged` olay bildirin.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Öğesini uygulayan adlı bir sınıf ekleyin `TodoTaggerProvider` <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> ve bunu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" ve a TodoTag ile dışarı aktarın <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> .

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. Öğesini içe aktarın <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Öğesini <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> örnekleyerek yöntemini uygulayın `TodoTagger` .

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin
 Bu kodu test etmek için TodoGlyphTest çözümünü derleyin ve deneysel örnekte çalıştırın.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>TodoGlyphTest çözümünü derlemek ve test etmek için

1. Çözümü derleyin.

2. **F5** tuşuna basarak projeyi çalıştırın. Visual Studio 'nun ikinci bir örneği başlar.

3. Gösterge kenar boşluğunun göründüğünden emin olun. ( **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Metin Düzenleyicisi** sayfasında **Gösterge kenar boşluğunun** seçildiğinden emin olun.)

4. Açıklamalar içeren bir kod dosyası açın. "Todo" sözcüğünü açıklama bölümlerinden birine ekleyin.

5. Kod penceresinin solundaki gösterge kenar boşluğunda, koyu mavi ana hat ile açık mavi bir daire görünür.
