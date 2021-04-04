---
title: 'İzlenecek yol: kenar boşluğu karakteri oluşturma | Microsoft Docs'
description: Bu kılavuzu kullanarak, özel Düzenleyici uzantıları kullanarak Düzenleyici kenar boşluklarının görünümünü nasıl özelleştireceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec5eecef40220c2cf2d4e3f1ece8eb5eb763bdeb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217417"
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

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet1":::

3. Uygulayan adlı bir sınıf ekleyin `TodoGlyphFactory` <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet2":::

4. Glifin boyutlarını tanımlayan bir özel alan ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet3":::

5. `GenerateGlyph`Glif Kullanıcı arabirimi (UI) öğesini tanımlayarak uygulayın. `TodoTag` Bu izlenecek yolda daha sonra tanımlanmıştır.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet4":::

6. Uygulayan adlı bir sınıf ekleyin `TodoGlyphFactoryProvider` <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Bu sınıfı bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Vstextmarkafter öğesinden sonra, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" ve a TodoTag a 'dan dışarı aktarın <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet5":::

7. Öğesini <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> örnekleyerek yöntemini uygulayın `TodoGlyphFactory` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet6":::

## <a name="define-a-todo-tag-and-tagger"></a>Todo etiketi ve Tagger tanımlama
 Önceki adımlarda tanımladığınız UI öğesi ile gösterge kenar boşluğu arasındaki ilişkiyi tanımlayın. Bir etiket türü ve Tagger oluşturun ve bir Tagger sağlayıcısı kullanarak dışarı aktarın.

### <a name="to-define-a-todo-tag-and-tagger"></a>Todo etiketi ve Tagger tanımlamak için

1. Projeye yeni bir sınıf dosyası ekleyin ve bunu adlandırın `TodoTagger` .

2. Aşağıdaki içeri aktarmaları ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet7":::

3. Adlı bir sınıf ekleyin `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet8":::

4. Türünü uygulayan adlı sınıfı değiştirin `TodoTagger` <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet9":::

5. `TodoTagger`Sınıfına, için <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> ve sınıflandırma yayılmasında bulunacak metin için özel alanlar ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet10":::

6. Sınıflandırıcının ayarlayan bir Oluşturucu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet11":::

7. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>Adları "Açıklama" sözcüğünü içeren ve metin arama metnini içeren tüm sınıflandırma yayılmalarını bularak yöntemini uygulayın. Arama metni bulunduğunda, yeni bir türü geri dönün <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet12":::

8. Bir `TagsChanged` olay bildirin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet13":::

9. Öğesini uygulayan adlı bir sınıf ekleyin `TodoTaggerProvider` <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> ve bunu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" ve a TodoTag ile dışarı aktarın <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet14":::

10. Öğesini içe aktarın <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet15":::

11. Öğesini <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> örnekleyerek yöntemini uygulayın `TodoTagger` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet16":::

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin
 Bu kodu test etmek için TodoGlyphTest çözümünü derleyin ve deneysel örnekte çalıştırın.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>TodoGlyphTest çözümünü derlemek ve test etmek için

1. Çözümü derleyin.

2. **F5** tuşuna basarak projeyi çalıştırın. Visual Studio 'nun ikinci bir örneği başlar.

3. Gösterge kenar boşluğunun göründüğünden emin olun. ( **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Metin Düzenleyicisi** sayfasında **Gösterge kenar boşluğunun** seçildiğinden emin olun.)

4. Açıklamalar içeren bir kod dosyası açın. "Todo" sözcüğünü açıklama bölümlerinden birine ekleyin.

5. Kod penceresinin solundaki gösterge kenar boşluğunda, koyu mavi ana hat ile açık mavi bir daire görünür.
