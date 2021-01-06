---
title: 'İzlenecek yol: eşleşen ayraçları görüntüleme | Microsoft Docs'
description: Bu kılavuzu kullanarak, metin içeriği türüne parantez ile eşleşen Etiketler uygulayarak bir dilin bağlamında küme ayraçları tanımlama hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce40f5673a8aba4ab3f7714a3aafdc3de4697cc4
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877955"
---
# <a name="walkthrough-display-matching-braces"></a>İzlenecek yol: eşleşen ayraçları görüntüle
Eşleştirmek istediğiniz küme ayraçlarını tanımlayarak, parantez eşleştirme ile eşleşen dil tabanlı özellikleri uygulayın ve şapka işareti ayraçlarından birinde olduğunda, eşleşen ayraçların içine bir metin işaretçisi etiketi ekleyin. Bir dilin bağlamında küme ayraçları tanımlayabilir, kendi dosya adı uzantınızı ve içerik türünü tanımlayabilir ve etiketleri yalnızca o türe uygulayabilir ya da etiketleri varolan bir içerik türüne (örneğin "metin") uygulayabilirsiniz. Aşağıdaki izlenecek yol, "metin" içerik türüne parantez ile eşleşen etiketlerin nasıl uygulanacağını gösterir.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) projesi oluşturma

#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için

1. Bir düzenleyici sınıflandırıcı projesi oluşturun. Çözümü adlandırın `BraceMatchingTest` .

2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Varolan sınıf dosyalarını silin.

## <a name="implement-a-brace-matching-tagger"></a>Tagger ile eşleşen bir küme ayracı uygulama
 Visual Studio 'da kullanılan birine benzeyen bir küme ayracı vurgulaması sağlamak için, türünde bir Tagger uygulayabilirsiniz <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . Aşağıdaki kod, herhangi bir iç içe geçme düzeyinde küme ayracı çiftleri için etiketi nasıl tanımlayacağınızı gösterir. Bu örnekte, [] öğesinin küme ayracı çiftleri ve {} Tagger oluşturucusunda tanımlanmıştır, ancak tam dil uygulamasında, ilgili ayraç çiftleri dil belirtiminde tanımlanmıştır.

### <a name="to-implement-a-brace-matching-tagger"></a>Tagger ile eşleşen bir küme ayracı uygulamak için

1. Bir sınıf dosyası ekleyin ve Braceeþleþen olarak adlandırın.

2. Aşağıdaki ad alanlarını içeri aktarın.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Türünden devralan bir sınıf tanımlayın `BraceMatchingTagger` <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Metin görünümü, kaynak arabelleği, geçerli anlık görüntü noktası ve ayrıca küme ayracı çiftleri için özellikler ekleyin.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. Tagger kurucusunda özellikleri ayarlayın ve görünüm değiştirme olayları ' na abone olun <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . Bu örnekte, tanım amaçları için, eşleşen çiftler oluşturucuda da tanımlanmıştır.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. Uygulamanın bir parçası olarak <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> , TagsChanged olayını bildirin.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Olay işleyicileri, özelliğin geçerli giriş işareti konumunu güncelleştirir `CurrentChar` ve TagsChanged olayını yükseltir.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>Geçerli karakter açık bir küme ayracı olduğunda ya da önceki karakter, Visual Studio 'da olduğu gibi bir kapanış ayracı olduğunda, ayraçları eşleştirmek için yöntemini uygulayın. Eşleşme bulunduğunda bu yöntem, biri açık küme ayracı ve diğeri de kapatma ayracı için olmak üzere iki etiket oluşturur.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Aşağıdaki özel yöntemler, eşleşen küme ayracını herhangi bir iç içe geçme düzeyinde bulur. İlk yöntem, açma karakteriyle eşleşen kapatma karakterini bulur:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. Aşağıdaki yardımcı yöntemi bir kapatma karakteriyle eşleşen açma karakterini bulur:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Bir ayraç ile eşleşen Tagger sağlayıcısı uygulama
 Bir Tagger uygulamaya ek olarak, bir Tagger sağlayıcısı da uygulamanız ve dışarı aktarmanız gerekir. Bu durumda, sağlayıcının içerik türü "metin" olur. Bu nedenle, parantez eşleştirme tüm metin dosyası türlerinde görünür, ancak Fuller bir uygulama yalnızca belirli bir içerik türüne sahip küme ayracı uygular.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Bir küme ayracı ile eşleşen Tagger sağlayıcısı uygulamak için

1. Öğesinden devralan bir Tagger sağlayıcısı bildirin <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , bu dosyayı BraceMatchingTaggerProvider olarak adlandırın ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" ve a ile dışarı aktarın <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>Bir BraceMatchingTagger örneği oluşturmak için yöntemini uygulayın.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin
 Bu kodu test etmek için, BraceMatchingTest çözümünü derleyin ve deneysel örnekte çalıştırın.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>BraceMatchingTest çözümünü derlemek ve test etmek için

1. Çözümü derleyin.

2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun ve eşleşen küme ayraçları içeren bir metin yazın.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Giriş işaretini bir açık küme ayracından önce konumlandırdığınızda, hem bu küme ayracı hem de eşleşen kapatma ayracı vurgulanmalıdır. İmleci kapalı küme ayracından hemen sonra konumlandırdığınızda, bu küme ayracı ve eşleşen açma ayracı her ikisi de vurgulanmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: bir içerik türünü bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
