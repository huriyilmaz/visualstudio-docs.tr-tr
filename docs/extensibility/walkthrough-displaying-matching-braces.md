---
title: 'Walkthrough: Eşleşen Ayraçları Görüntüleme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 107610733ab9b5c8085b3f987fa999250b453d63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697444"
---
# <a name="walkthrough-display-matching-braces"></a>Walkthrough: Eşleşen ayraçları görüntüleme
Eşleştirmek istediğiniz ayraçları tanımlayarak ve bakım diş lerinden birindeyken eşleşen ayraçlara bir metin işaretçisi etiketi ekleyerek ayraç eşleştirme gibi dil tabanlı özellikleri uygulayın. Ayraçları bir dil bağlamında tanımlayabilir, kendi dosya adı uzantınızı ve içerik türünüzü tanımlayabilir ve etiketleri yalnızca bu türe uygulayabilir veya etiketleri varolan bir içerik türüne ("metin" gibi) uygulayabilirsiniz. Aşağıdaki izlik, "metin" içerik türüne ayraç eşleştirme etiketlerinin nasıl uygulanacağı gösterilmektedir.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Yönetilen Genişletilebilirlik Çerçevesi (MEF) projesi oluşturma

#### <a name="to-create-a-mef-project"></a>Bir MEF projesi oluşturmak için

1. Bir Düzenleyici Sınıflandırıcı projesi oluşturun. Çözümü `BraceMatchingTest`adlandırın.

2. Projeye Bir Düzenleyici Sınıflandırıcı öğesi şablonu ekleyin. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Varolan sınıf dosyalarını silin.

## <a name="implement-a-brace-matching-tagger"></a>Ayraç eşleştirme etiketerini uygulama
 Visual Studio'da kullanılan alete benzeyen bir ayraç vurgulama efekti elde etmek <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>için, bir tür etiketçit uygulayabilirsiniz. Aşağıdaki kod, herhangi bir iç içe geçme düzeyinde ayraç çiftleri için etiketerin nasıl tanımlandığını gösterir. Bu örnekte, [] ayraç {} çiftleri ve tagger oluşturucu tanımlanır, ancak tam bir dil uygulamasında, ilgili ayraç çiftleri dil belirtimi nde tanımlanır.

### <a name="to-implement-a-brace-matching-tagger"></a>Ayraç eşleştirme etiketerini uygulamak için

1. Bir sınıf dosyası ekleyin ve bracematching adını.

2. Aşağıdaki ad alanlarını içeri aktarın.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Türden <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> `BraceMatchingTagger` devralan bir sınıf tanımlayın.

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Metin görünümü, kaynak arabellek, geçerli anlık görüntü noktası ve ayrıca ayraç çiftleri kümesi için özellikler ekleyin.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. Tagger oluşturucuolarak, özellikleri ayarlayın ve görünüm değişikliği <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>olayları abone ve . Bu örnekte, açıklayıcı amaçlar için eşleşen çiftler de oluşturucu olarak tanımlanır.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. Uygulamanın <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> bir parçası olarak, bir EtiketlerDeğiştir olayını bildirin.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Olay işleyicileri `CurrentChar` özelliğin geçerli bakım konumunu günceller ve EtiketlerDeğiştirildi olayını yükseltir.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Geçerli <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> karakter açık bir ayraç olduğunda veya önceki karakter Visual Studio'da olduğu gibi yakın bir ayraç olduğunda ayraçları eşleştirme yöntemini uygulayın. Eşleşme bulunduğunda, bu yöntem, biri açık ayraç, diğeri de yakın ayraç için olmak üzere iki etiketi anında açar.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Aşağıdaki özel yöntemler, eşleşen ayraç iç içe herhangi bir düzeyde bulabilirsiniz. İlk yöntem, açık karakterle eşleşen yakın karakteri bulur:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. Aşağıdaki yardımcı yöntemi, yakın bir karakterle eşleşen açık karakteri bulur:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Ayraç eşleştirme etiket sağlayıcısı uygulama
 Bir etiketer uygulamaya ek olarak, bir etiket sağlayıcı uygulamak ve dışa aktarmak gerekir. Bu durumda, sağlayıcının içerik türü "metin"dir. Bu nedenle, ayraç eşleştirme metin dosyalarının tüm türlerinde görünür, ancak daha dolgun bir uygulama yalnızca belirli bir içerik türüyle eşleşen ayraç uygular.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Ayraç eşleştirme etiket sağlayıcısı uygulamak için

1. Devralan bir tagger sağlayıcı <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>bildirin, onu BraceMatchingTaggerProvider adını <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> ve bir "metin" ve bir <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> . <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Bir <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> BraceMatchingTagger anlık uygulamak için yöntemi uygulayın.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Kodu oluşturma ve test edin
 Bu kodu sınamak için BraceMatchingTest çözümlerini oluşturun ve deneme örneğinde çalıştırın.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>BraceMatchingTest çözümlü oluşturmak ve test etmek için

1. Çözümü derleyin.

2. Bu projeyi hata ayıklamada çalıştırdığınızda, Visual Studio'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun ve eşleşen ayraçlar içeren bazı metin yazın.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Caret'i açık bir ayraç önce konumlandırdığınızda, hem bu ayraç hem de eşleşen yakın ayracı vurgulanmalıdır. İmleci yakın ayraçtan hemen sonra konumlandırdığınızda, hem bu ayraç hem de eşleşen açık ayraç vurgulanmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Walkthrough: İçerik türünü dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
