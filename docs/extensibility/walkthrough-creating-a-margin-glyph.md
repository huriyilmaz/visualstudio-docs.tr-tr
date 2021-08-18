---
title: 'adım adım kılavuz: Margin Glyph | Microsoft Docs'
description: Bu kılavuzda, özel düzenleyici uzantılarını kullanarak düzenleyici kenar boşluklarının görünümünü özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5e5bd2d49f1bc2af8f90a1fb92e42a08a6de5c11
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078576"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Adım adım kılavuz: Kenar boşluğu ifadesi oluşturma
Özel düzenleyici uzantılarını kullanarak düzenleyici kenar boşluklarının görünümünü özelleştirebilirsiniz. Bu kılavuzda, kod açıklamasında "todo" sözcüğü her göründüğünde gösterge kenar boşluğuna özel bir glyph yer atır.

## <a name="prerequisites"></a>Önkoşullar
 2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

1. C# VSIX projesi oluşturun. (Yeni **Project** iletişim kutusunda Visual **C# / Genişletilebilirlik'i** seçin, ardından **VSIX Project**.) Çözüme adını `TodoGlyphTest` girin.

2. Düzenleyici Sınıflandırıcı proje öğesi ekleyin. Daha fazla bilgi için [bkz. Düzenleyici öğesi şablonuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Mevcut sınıf dosyalarını silin.

## <a name="define-the-glyph"></a>Klyph'i tanımlama
 Arabirimini çalıştırarak bir glyph <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> tanımlayın.

### <a name="to-define-the-glyph"></a>Glyph'i tanımlamak için

1. Bir sınıf dosyası ekleyin ve olarak ad `TodoGlyphFactory` girin.

2. Bildirimleri kullanarak aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet1":::

3. uygulayan adlı `TodoGlyphFactory` bir sınıf <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet2":::

4. Karakter boyutlarını tanımlayan özel bir alan ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet3":::

5. `GenerateGlyph`Glyph kullanıcı arabirimi (UI) öğesini tanımlayarak uygulama. `TodoTag` bu kılavuzda daha sonra tanımlanır.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet4":::

6. uygulayan adlı `TodoGlyphFactoryProvider` bir sınıf <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> ekleyin. Bu sınıfı <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", After <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> VsTextMarker, "code" ve TodoTag ile dışarı <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> aktarın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet5":::

7. örneğini <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> başlatarak yöntemini `TodoGlyphFactory` uygulama.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet6":::

## <a name="define-a-todo-tag-and-tagger"></a>Todo etiketi ve etiketger tanımlama
 Önceki adımlarda tanımladığınız kullanıcı arabirimi öğesi ile gösterge kenar boşluğu arasındaki ilişkiyi tanımlayın. Bir etiket türü ve etiketger oluşturun ve bir etiketger sağlayıcısı kullanarak dışarı aktarın.

### <a name="to-define-a-todo-tag-and-tagger"></a>Bir todo etiketi ve etiketger tanımlamak için

1. Projeye yeni bir sınıf dosyası ekleyin ve olarak ad `TodoTagger` girin.

2. Aşağıdaki içeri aktarmaları ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet7":::

3. adlı bir sınıf `TodoTag` ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet8":::

4. türünde uygulayan `TodoTagger` adlı <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> sınıfı `TodoTag` değiştirme.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet9":::

5. sınıfına, sınıflandırma aralıklarında metin bulmak için ve `TodoTagger` için özel alanlar <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet10":::

6. Sınıflandırıcıyı ayaran bir oluşturucu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet11":::

7. Adı "comment" sözcüğü olan ve metni arama metnini içeren tüm sınıflandırma aralıklarını <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> bularak yöntemini uygulama. Arama metni her bulunsa türünde yeni bir <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> verim elde. `TodoTag`

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet12":::

8. Bir olay `TagsChanged` bildir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet13":::

9. uygulayan adlı bir sınıf ekleyin ve "kod" ve TodoTag ile dışarı `TodoTaggerProvider` <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> aktarın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet14":::

10. 'i içeri <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> aktarın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet15":::

11. örneğini <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> başlatarak yöntemini `TodoTagger` uygulama.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet16":::

## <a name="build-and-test-the-code"></a>Kodu derleme ve test
 Bu kodu test etmek için TodoGlyphTest çözümünü derleme ve deneysel örnekte çalıştırma.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>TodoGlyphTest çözümünü derlemek ve test etmek için

1. Çözümü derleyin.

2. F5 tuşuna basarak **projeyi çalıştırın.** İkinci bir örnek Visual Studio başlar.

3. Gösterge kenar boşluğunda gösterilenden emin olun. (Araçlar menüsünde **Seçenekler'e** **tıklayın.** Metin Düzenleyici **sayfasında Gösterge** kenar boşluğu'nın **seçili olduğundan** emin olun.)

4. Açıklamalara sahip bir kod dosyası açın. Açıklama bölümlerinden biri için "todo" sözcüğü ekleyin.

5. Kod penceresinin sol tarafından gösterge kenar boşluğunda koyu mavi ana hatlı açık mavi bir daire görünür.
