---
title: 'adım adım kılavuz: Eşleşen Küme Ayraçlarını | Microsoft Docs'
description: Bu kılavuzda, bir dil bağlamında küme ayraçları tanımlamayı ve metin içerik türüne ayraç eşleştirme etiketleri uygulama hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 685e00f32343edc64f1ff72deffd38ea15d7aa7502fe7d57b793439d3128f8b3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121374967"
---
# <a name="walkthrough-display-matching-braces"></a>Adım adım kılavuz: Eşleşen ayraçları görüntüleme
Eşleştirmek istediğiniz küme ayraçlarını tanımlayarak ve küme ayraçlarından biri üzerindeyken eşleşen küme ayraçlarına bir metin işaretçisi etiketi ekleyerek küme ayracı eşleştirme gibi dil tabanlı özellikleri uygulama. Ayraçları bir dil bağlamında tanımlayabilir, kendi dosya adı uzantınızı ve içerik türünü tanımlayabilir ve etiketleri yalnızca bu türe uygulayabilir veya mevcut içerik türüne ("metin" gibi) uygulayabilirsiniz. Aşağıdaki izlenecek yol, "metin" içerik türüne ayraç eşleştirme etiketlerinin nasıl uygulanarak uygulanabileceklerini gösterir.

## <a name="prerequisites"></a>Önkoşullar
 2015 Visual Studio den başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Kurulumda isteğe bağlı bir özellik olarak Visual Studio dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) projesi oluşturma

#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için

1. Düzenleyici Sınıflandırıcı projesi oluşturun. Çözüme adını `BraceMatchingTest` girin.

2. Projeye bir Düzenleyici Sınıflandırıcı öğesi şablonu ekleyin. Daha fazla bilgi için [bkz. Düzenleyici öğesi şablonuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Mevcut sınıf dosyalarını silin.

## <a name="implement-a-brace-matching-tagger"></a>Küme ayracı eşleştirme etiketger'ı uygulama
 Küme ayracı vurgulama etkisi elde etmek için Visual Studio türünde bir etiketger <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> gerçekleştirebilirsiniz. Aşağıdaki kod, küme ayracı çiftleri için herhangi bir iç içe yerleştirme düzeyinde etiketger tanımlamayı gösterir. Bu örnekte, [] ve küme ayracı çiftleri etiket oluşturucuda tanımlanır, ancak tam dil uygulamasında, ilgili küme ayracı çiftleri dil {} belirtiminde tanımlanır.

### <a name="to-implement-a-brace-matching-tagger"></a>Küme ayracı eşleşen bir etiketger uygulamak için

1. Bir sınıf dosyası ekleyin ve BraceMatching olarak ad girin.

2. Aşağıdaki ad alanlarını içeri aktarın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet1":::

3. türünden `BraceMatchingTagger` devralan bir <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> sınıf <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> tanımlayın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet2":::

4. Metin görünümü, kaynak arabelleği, geçerli anlık görüntü noktası ve ayraç çiftleri kümesi için özellikler ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet3":::

5. Tagger oluşturucussinde, özellikleri ayarlayın ve değişiklik olaylarını ve görüntülemeye abone <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> olun. Bu örnekte, açıklayıcı amaçlarla, eşleşen çiftler oluşturucuda da tanımlanır.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet4":::

6. Uygulamanın bir <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> parçası olarak bir TagsChanged olayı bildirin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet5":::

7. Olay işleyicileri özelliğin geçerli caret konumunu `CurrentChar` güncelleştirin ve TagsChanged olayına neden olur.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet6":::

8. Geçerli karakter bir açık küme ayracı olduğunda veya önceki karakter, küme ayracı olduğunda küme ayraçlarını <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Visual Studio. Eşleşme bulunursa, bu yöntem biri açık küme ayracı, biri de kapatma ayracı için olmak için olmak için iki etiket örneği açar.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet7":::

9. Aşağıdaki özel yöntemler eşleşen küme ayracı herhangi bir iç içe yerleştirme düzeyinde bulur. İlk yöntem, açık karakterle eşleşen kapatma karakterini bulur:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet8":::

10. Aşağıdaki yardımcı yöntem, bir kapatma karakteriyle eşleşen açık karakteri bulur:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet9":::

## <a name="implement-a-brace-matching-tagger-provider"></a>Küme ayracı eşleştirme etiket sağlayıcısı uygulama
 Bir etiketger uygulamaya ek olarak, bir etiketger sağlayıcısını da uygulamalı ve dışarı aktarabilirsiniz. Bu durumda sağlayıcının içerik türü "text" olur. Bu nedenle, küme ayracı eşleştirme tüm metin dosyası türlerinde görünür, ancak daha dolu bir uygulama yalnızca belirli bir içerik türüne küme ayracı eşleştirme uygular.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Küme ayracı eşleştirme etiket sağlayıcısı uygulamak için

1. 'den devralan bir tagger sağlayıcısını bildirerek <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> BraceMatchingTaggerProvider olarak ad girin ve "text" ve a ile <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> birlikte dışarı <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> aktarın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet10":::

2. <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>BraceMatchingTagger örneği için yöntemini uygulama.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet11":::

## <a name="build-and-test-the-code"></a>Kodu derleme ve test
 Bu kodu test etmek için BraceMatchingTest çözümünü derleme ve deneysel örnekte çalıştırma.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>BraceMatchingTest çözümünü derlemek ve test etmek için

1. Çözümü derleyin.

2. Bu projeyi hata ayıklayıcısında çalıştırarak, hata ayıklayıcısının Visual Studio örneği başlatıldı.

3. Bir metin dosyası oluşturun ve eşleşen ayraçlar içeren bazı metinler yazın.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Küme ayracı, açık bir küme ayracı öncesinde konumlandırmak için hem bu küme ayracı hem de eşleşen kapatma ayracı vurgulanmış olur. İmleci, kapatma ayracı'nın hemen ardından yerleştirdikten sonra hem bu küme ayracı hem de eşleşen açık ayracın vurgulanmış olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Adım adım kılavuz: İçerik türünü bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
