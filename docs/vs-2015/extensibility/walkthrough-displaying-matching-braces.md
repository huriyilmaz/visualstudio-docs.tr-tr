---
title: 'İzlenecek yol: eşleşen ayraçları görüntüleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caaafd0143d3b09a51518ee5f54a02b06dbf10aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165786"
---
# <a name="walkthrough-displaying-matching-braces"></a>İzlenecek Yol: Eşleşen Küme Ayraçlarını Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eşleştirmek istediğiniz küme ayraçlarını tanımlayarak, parantez eşleştirme gibi dil tabanlı özellikleri uygulayabilir ve sonra şapka işareti ayraçlarından birinde olduğunda, eşleşen ayraçların içine bir metin işaretçisi etiketi ekleyebilirsiniz. Bir dilin bağlamında küme ayraçları tanımlayabilir veya kendi dosya adı uzantınızı ve içerik türünü tanımlayabilir ve etiketleri yalnızca o türe uygulayabilir ya da etiketleri varolan bir içerik türüne (örneğin "metin") uygulayabilirsiniz. Aşağıdaki izlenecek yol, "metin" içerik türüne parantez ile eşleşen etiketlerin nasıl uygulanacağını gösterir.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) projesi oluşturma  
  
#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1. Bir düzenleyici sınıflandırıcı projesi oluşturun. Çözümü adlandırın `BraceMatchingTest` .  
  
2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Varolan sınıf dosyalarını silin.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Tagger ile eşleşen bir küme ayracı uygulama  
 Visual Studio 'da kullanılan bir küme ayracı vurgulama efektini almak için, türünde bir Tagger uygulayabilirsiniz <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . Aşağıdaki kod, herhangi bir iç içe geçme düzeyinde küme ayracı çiftleri için etiketi nasıl tanımlayacağınızı gösterir. Bu örnekte, ayraç çiftleri []. [], ve {} Tagger oluşturucusunda tanımlanmıştır, ancak tam dil uygulamasında ilgili küme çiftleri dil belirtiminde tanımlanacaktır.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Tagger ile eşleşen bir küme ayracı uygulamak için  
  
1. Bir sınıf dosyası ekleyin ve Braceeþleþen olarak adlandırın.  
  
2. Aşağıdaki ad alanlarını içeri aktarın.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3. Türünden devralan bir sınıf tanımlayın `BraceMatchingTagger` <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4. Metin görünümü, kaynak arabelleği ve geçerli anlık görüntü noktası ve ayrıca küme ayracı çiftleri için özellikler ekleyin.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5. Tagger kurucusunda özellikleri ayarlayın ve görünüm değiştirme olayları ' na abone olun <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . Bu örnekte, tanım amaçları için, eşleşen çiftler oluşturucuda da tanımlanmıştır.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6. Uygulamanın bir parçası olarak <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> , TagsChanged olayını bildirin.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7. Olay işleyicileri, özelliğin geçerli giriş işareti konumunu güncelleştirir `CurrentChar` ve TagsChanged olayını yükseltir.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>Geçerli karakter açık bir küme ayracı olduğunda ya da önceki karakter, Visual Studio 'da olduğu gibi bir kapanış ayracı olduğunda, ayraçları eşleştirmek için yöntemini uygulayın. Eşleşme bulunduğunda bu yöntem, biri açık küme ayracı ve diğeri de kapatma ayracı için olmak üzere iki etiket oluşturur.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. Aşağıdaki özel yöntemler, eşleşen küme ayracını herhangi bir iç içe geçme düzeyinde bulur. İlk yöntem, açma karakteriyle eşleşen kapatma karakterini bulur:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. Aşağıdaki yardımcı yöntemi bir kapatma karakteriyle eşleşen açma karakterini bulur:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Bir küme ayracı ile eşleşen Tagger sağlayıcısı uygulama  
 Bir Tagger uygulamaya ek olarak, bir Tagger sağlayıcısı da uygulamanız ve dışarı aktarmanız gerekir. Bu durumda, sağlayıcının içerik türü "metin" olur. Bu, tüm metin dosyalarında yer alan eşleştirme eşleşmesinin görüneceği anlamına gelir, ancak Fuller uygulaması yalnızca belirli bir içerik türü için küme ayracı uygular.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Bir küme ayracı ile eşleşen Tagger sağlayıcısı uygulamak için  
  
1. Öğesinden devralan bir Tagger sağlayıcısı bildirin <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , bu dosyayı BraceMatchingTaggerProvider olarak adlandırın ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" ve a ile dışarı aktarın <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2. <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>Bir BraceMatchingTagger örneği oluşturmak için yöntemini uygulayın.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>Kodu derleme ve test etme  
 Bu kodu test etmek için, BraceMatchingTest çözümünü derleyin ve deneysel örnekte çalıştırın.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>BraceMatchingTest çözümünü derlemek ve test etmek için  
  
1. Çözümü derleyin.  
  
2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği oluşturulur.  
  
3. Bir metin dosyası oluşturun ve eşleşen küme ayraçları içeren bir metin yazın.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4. Giriş işaretini bir açık küme ayracından önce konumlandırdığınızda, hem bu küme ayracı hem de eşleşen kapatma ayracı vurgulanmalıdır. İmleci kapalı küme ayracından hemen sonra konumlandırdığınızda, bu küme ayracı ve eşleşen açma ayracı her ikisi de vurgulanmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
