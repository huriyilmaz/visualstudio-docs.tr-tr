---
title: 'İzlenecek yol: Ana hat | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c1dd3d28b9978b52c95b5ff905d57720ed10f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201964"
---
# <a name="walkthrough-outlining"></a>İzlenecek Yol: Ana Hat Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Genişletmek veya daraltmak istediğiniz metin bölgesi türlerini tanımlayarak, ana hat gibi dil tabanlı özellikleri uygulayabilirsiniz. Bir dil hizmeti bağlamında bölgeleri tanımlayabilir veya kendi dosya adı uzantınızı ve içerik türünü tanımlayabilir ve bölge tanımını yalnızca bu türe uygulayabilir ya da bölge tanımlarını varolan bir içerik türüne (örneğin, "metin") uygulayabilirsiniz. Bu izlenecek yol, ana hat bölgelerini tanımlama ve görüntüleme işlemlerinin nasıl yapılacağını gösterir.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) projesi oluşturma  
  
#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1. VSıX projesi oluşturun. Çözümü adlandırın `OutlineRegionTest` .  
  
2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Varolan sınıf dosyalarını silin.  
  
## <a name="implementing-an-outlining-tagger"></a>Ana hat etiketi uygulama  
 Ana hat bölgeleri bir tür etiketle ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ) işaretlenir. Bu etiket, Standart anahat oluşturma davranışını sağlar. Özetlenen bölge genişletilebilir veya daraltılabilirler. Ana hatlarıyla belirtilen bölge, daraltılmışsa bir artı IŞARETI veya genişletilmişse EKSI IŞARETI ile işaretlenir ve genişletilmiş bölge dikey bir çizgi ile parçalanmışsa.  
  
 Aşağıdaki adımlarda, "[" ve "]" ile ayrılmış tüm bölgeler için anahat bölgeleri oluşturan bir Tagger nasıl tanımlanacağı gösterilmektedir.  
  
#### <a name="to-implement-an-outlining-tagger"></a>Bir anahat etiketi uygulamak için  
  
1. Bir sınıf dosyası ekleyin ve adlandırın `OutliningTagger` .  
  
2. Aşağıdaki ad alanlarını içeri aktarın.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3. Adlı bir sınıf oluşturun `OutliningTagger` ve şunları uygular <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4. Metin arabelleğini ve anlık görüntüsünü izlemek ve ana hat bölgeleri olarak etiketlenmesi gereken satır kümelerini biriktirmek için bazı alanlar ekleyin. Bu kod, ana hat bölgelerini temsil eden bölge nesnelerinin bir listesini (daha sonra tanımlanması için) içerir.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5. Alanları Başlatan bir Tagger Oluşturucu ekleyin, arabelleği ayrıştırır ve olaya bir olay işleyicisi ekler <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>Etiketi yayılmaları Başlatan yöntemini uygulayın. Bu örnekte, yönteme geçilen yayılmalar, <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> her zaman bir durum olmasa da, her zaman bir şekilde olmayabilir. Bu yöntem, ana hat bölgelerinin her biri için yeni bir etiket aralığı oluşturur.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7. Bir `TagsChanged` olay işleyicisi bildirin.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8. `BufferChanged`Metin arabelleğini ayrıştırarak olaylara yanıt veren bir olay işleyicisi ekleyin <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Arabelleği ayrıştırtıran bir yöntem ekleyin. Burada verilen örnek yalnızca gösterim amaçlıdır. Bu, arabelleği iç içe ana hat bölgelerinde eşzamanlı olarak ayrıştırır.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. Aşağıdaki yardımcı yöntemi, ana hat düzeyini temsil eden bir tamsayı alır; örneğin, en sol ayraç çifti.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. Aşağıdaki yardımcı yöntemi bir bölgeyi (Bu konunun ilerleyen kısımlarında tanımlanır) bir SnapshotSpan olarak çevirir.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. Aşağıdaki kod yalnızca gösterim amaçlıdır. Bir anahat bölgesinin başlangıcının satır numarasını ve sapmasını ve ayrıca üst bölgeye (varsa) bir başvuru içeren bir PartialRegion sınıfını tanımlar. Bu, ayrıştırıcısının iç içe ana hat bölgelerini ayarlamaya olanak sağlar. Türetilmiş bölge sınıfı, bir ana hat bölgesinin sonundaki satır numarasına bir başvuru içerir.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Tagger sağlayıcısı uygulama  
 Tagger için bir Tagger sağlayıcısı dışarı aktarmanız gerekir. Tagger sağlayıcı, `OutliningTagger` "metin" içerik türü için bir arabellek oluşturur veya `OutliningTagger` arabellekte zaten bir tane varsa, bir döndürür.  
  
#### <a name="to-implement-a-tagger-provider"></a>Bir Tagger sağlayıcısı uygulamak için  
  
1. Uygulayan adlı bir sınıf oluşturun `OutliningTaggerProvider` <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> ve bunu ContentType ve TagType öznitelikleriyle dışarı aktarın.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2. <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>Arabellek özelliklerine bir ekleyerek yöntemini uygulayın `OutliningTagger` .  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Kodu derleme ve test etme  
 Bu kodu test etmek için, OutlineRegionTest çözümünü derleyin ve deneysel örnekte çalıştırın.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>OutlineRegionTest çözümünü derlemek ve test etmek için  
  
1. Çözümü derleyin.  
  
2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği oluşturulur.  
  
3. Bir metin dosyası oluşturun. Açma küme ayracını ve kapatma küme ayracını içeren bir metin yazın.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4. Her iki küme ayracı de içeren bir anahat bölgesi olmalıdır. Ana hat bölgesini daraltmak için açık küme ayracın solundaki eksı IŞARETINE tıklamanız gerekir. Bölge daraltıldığında, üç nokta simgesi (...) daraltılan bölgenin solunda görünmelidir ve işaretçiyi üç nokta üzerine getirdiğinizde metin **Vurgulu metin** içeren bir açılan pencere görünmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
