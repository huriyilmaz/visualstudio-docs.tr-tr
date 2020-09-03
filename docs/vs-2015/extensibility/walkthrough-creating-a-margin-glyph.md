---
title: 'İzlenecek yol: kenar boşluğu karakteri oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa18b900ca44fbb52c646bfdf021beed6e77f504
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148853"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>İzlenecek Yol: Dış Boşluk Karakteri Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel Düzenleyici uzantıları kullanarak Düzenleyici kenar boşluklarının görünümünü özelleştirebilirsiniz. Bu izlenecek yol, bir kod açıklamasında "Todo" sözcüğünün göründüğü her zaman gösterge marjına özel bir karakter koyar.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>MEF projesi oluşturma  
  
1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `TodoGlyphTest` .  
  
2. Bir düzenleyici sınıflandırıcı proje öğesi ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Varolan sınıf dosyalarını silin.  
  
## <a name="defining-the-glyph"></a>Glifi tanımlama  
 Arabirimi uygulayarak bir karakter tanımlayın <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .  
  
#### <a name="to-define-the-glyph"></a>Glifi tanımlamak için  
  
1. Bir sınıf dosyası ekleyin ve adlandırın `TodoGlyphFactory` .  
  
2. Aşağıdakileri using bildirimleri ekleyin.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3. Uygulayan adlı bir sınıf ekleyin `TodoGlyphFactory` <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4. Glifin boyutlarını tanımlayan bir özel alan ekleyin.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5. `GenerateGlyph`Glif Kullanıcı arabirimi (UI) öğesini tanımlayarak uygulayın. `TodoTag` Bu izlenecek yolda daha sonra tanımlanmıştır.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6. Uygulayan adlı bir sınıf ekleyin `TodoGlyphFactoryProvider` <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Bu sınıfı bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Vstextmarkafter öğesinden sonra, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" ve a TodoTag a 'dan dışarı aktarın <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> .  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7. Öğesini <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> örnekleyerek yöntemini uygulayın `TodoGlyphFactory` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Todo etiketi ve Tagger tanımlama  
 Bir etiket türü ve Tagger oluşturup bir Tagger sağlayıcısı kullanarak dışarı aktararak önceki adımlarda tanımladığınız UI öğesi ile gösterge kenar boşluğu arasındaki ilişkiyi tanımlayın.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Todo etiketi ve Tagger tanımlamak için  
  
1. Projeye yeni bir sınıf dosyası ekleyin ve bunu adlandırın `TodoTagger` .  
  
2. Aşağıdaki içeri aktarmaları ekleyin.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3. Adlı bir sınıf ekleyin `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4. Türünü uygulayan adlı sınıfı değiştirin `TodoTagger` <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5. `TodoTagger`Sınıfına, için <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> ve sınıflandırma yayılmasında bulunacak metin için özel alanlar ekleyin.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6. Sınıflandırıcının ayarlayan bir Oluşturucu ekleyin.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>Adları "Açıklama" sözcüğünü içeren ve metin arama metnini içeren tüm sınıflandırma yayılmalarını bularak yöntemini uygulayın. Arama metni bulunduğunda, yeni bir türü geri dönün <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8. Bir `TagsChanged` olay bildirin.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. Öğesini uygulayan adlı bir sınıf ekleyin `TodoTaggerProvider` <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> ve bunu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" ve a TodoTag ile dışarı aktarın <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> .  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. Öğesini içe aktarın <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. Öğesini <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> örnekleyerek yöntemini uygulayın `TodoTagger` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>Kodu derleme ve test etme  
 Bu kodu test etmek için TodoGlyphTest çözümünü derleyin ve deneysel örnekte çalıştırın.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>TodoGlyphTest çözümünü derlemek ve test etmek için  
  
1. Çözümü derleyin.  
  
2. F5 tuşuna basarak projeyi çalıştırın. Visual Studio 'nun ikinci bir örneği örneği oluşturulur.  
  
3. Gösterge kenar boşluğunun göründüğünden emin olun. ( **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Metin Düzenleyicisi** sayfasında **Gösterge kenar boşluğunun** seçildiğinden emin olun.)  
  
4. Açıklamalar içeren bir kod dosyası açın. "Todo" sözcüğünü açıklama bölümlerinden birine ekleyin.  
  
5. Koyu mavi bir ana hattı olan açık mavi bir daire, kod penceresinin solundaki gösterge kenar boşluğunda görünmelidir.
