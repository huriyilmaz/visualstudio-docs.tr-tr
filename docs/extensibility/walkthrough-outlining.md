---
title: 'Walkthrough: Anahat | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97b9dcbb2a24f1a3ed336a4a6bb7de4a15e907b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697220"
---
# <a name="walkthrough-outlining"></a>İzlenecek Yol: Ana Hat Oluşturma
Genişletmek veya daraltmak istediğiniz metin bölgelerinin türlerini tanımlayarak anahat oluşturma gibi dil tabanlı özellikler ayarlayın. Bölgeleri bir dil hizmeti bağlamında tanımlayabilir veya kendi dosya adı uzantınızı ve içerik yazınızı tanımlayabilir ve bölge tanımını yalnızca bu türe uygulayabilir veya bölge tanımlarını varolan bir içerik türüne ("metin" gibi) uygulayabilirsiniz. Bu gözden geçirme, anahat bölgelerinin nasıl tanımlandığını ve görüntülenebildiğini gösterir.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Yönetilen Genişletilebilirlik Çerçevesi (MEF) projesi oluşturma

### <a name="to-create-a-mef-project"></a>Bir MEF projesi oluşturmak için

1. Bir VSIX projesi oluşturun. Çözümü `OutlineRegionTest`adlandırın.

2. Projeye Bir Düzenleyici Sınıflandırıcı öğesi şablonu ekleyin. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Varolan sınıf dosyalarını silin.

## <a name="implement-an-outlining-tagger"></a>Anahat etiketi uygulama
 Anahat bölgeleri bir tür etiketle<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>işaretlenir ( ). Bu etiket standart anahat davranışı sağlar. Özetlenen bölge genişletilebilir veya daraltılabilir. Özetlenen bölge, daraltılmışsa veya Eksi işareti (**+****-**) genişletilirse ve genişletilmiş bölge dikey bir çizgiyle çizilmişse, Artı işaretiyle işaretlenir.

 Aşağıdaki adımlar, parantezlerle sınırlandırılmış tüm bölgeler için anahat bölgeleri oluşturan bir etiketcinin nasıl tanımlandığını gösterir (**[**,**]**).

### <a name="to-implement-an-outlining-tagger"></a>Anahat etiketi uygulamak için

1. Bir sınıf dosyası ekleyin `OutliningTagger`ve adlandırın.

2. Aşağıdaki ad alanlarını içeri aktarın.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Adlı `OutliningTagger`bir sınıf oluşturun ve <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>uygulanmasını var:

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Metin arabelleği ve anlık görüntü izlemek ve bölgeleri anahat olarak etiketlenmiş olması gereken satır kümelerini toplamak için bazı alanlar ekleyin. Bu kod, anahat bölgelerini temsil eden Bölge nesnelerinin (daha sonra tanımlanacak) bir listesini içerir.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Alanları başharfe alan, arabelleği ayrıştıran ve olaya bir olay işleyicisi <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> ekleyen bir etiketleyici oluşturucu ekleyin.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Etiket <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> açıklıklarını anında belirleyen yöntemi uygulayın. Bu örnek, yönteme <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> geçen yayılma açıklıklarının bitişik olduğunu varsayar, ancak her zaman böyle olmayabilir. Bu yöntem, anahat bölgelerinin her biri için yeni bir etiket aralığı nı anında alır.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Olay `TagsChanged` işleyicisi bildirin.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Metin `BufferChanged` arabelleği ayrıştırarak olaylara <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> yanıt veren bir olay işleyicisi ekleyin.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Arabelleği ayrıştıran bir yöntem ekleyin. Burada verilen örnek yalnızca illüstrasyon içindir. Arabelleği iç içe giden anahat bölgelerine eşitleyerek ayırır.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. Aşağıdaki yardımcı yöntem, anahat düzeyini temsil eden bir tamsayı alır, örneğin 1 sol en ayraç çifti.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. Aşağıdaki yardımcı yöntemi, bir Bölgeyi (bu makalede daha sonra tanımlanan) SnapshotSpan'a çevirir.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. Aşağıdaki kod yalnızca illüstrasyon içindir. Bir anahat bölgesinin başlangıcının satır numarasını ve mahsuplarını ve ana bölgeye (varsa) başvuruyu içeren bir PartialRegion sınıfını tanımlar. Bu kod, ayrıştırıcının iç içe geçen anahat bölgelerini ayarlamasını sağlar. Türetilmiş Bölge sınıfı, anahat lı bölgenin sonunun satır numarasına bir başvuru içerir.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Bir etiket sağlayıcı uygulama
 Etiketciniz için bir etiket sağlayıcı dışa aktarın. Tagger sağlayıcı "metin" içerik türü bir arabellek için bir `OutliningTagger` oluşturur `OutliningTagger` veya başka bir arabellek zaten varsa bir döndürür.

### <a name="to-implement-a-tagger-provider"></a>Tagger sağlayıcısı uygulamak için

1. ContentType ve `OutliningTaggerProvider` TagType <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>özniteliklerini uygulayan adlandırılmış bir sınıf oluşturun ve dışa aktarın.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Arabellek <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> özelliklerine bir `OutliningTagger` ekleyerek yöntemi uygulayın.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Kodu oluşturma ve test edin
 Bu kodu sınamak için, AnahatRegionTest çözümlerini oluşturun ve deneme örneğinde çalıştırın.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>OutlineRegionTest çözümlerini oluşturmak ve test etmek için

1. Çözümü derleyin.

2. Bu projeyi hata ayıklamada çalıştırdığınızda, Visual Studio'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun. Hem açılış parantezini hem de kapanış köşeli ayraçlarını içeren bazı metinler yazın.

    ```
    [
       Hello
    ]
    ```

4. Her iki parantezi de içeren bir anahat bölgesi olmalıdır. Anahat bölgesini daraltmak için açık köşenin solundaki Eksi İşareti'ni tıklatabilirsiniz. Bölge daraltıldığında, elips sembolü (*...*) daraltılmış bölgenin solunda görünmeli ve işaretçiyi elipslerin üzerine taşıdığınızda metin **gezinme metnini** içeren bir açılır pencere görünmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Walkthrough: İçerik türünü dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
