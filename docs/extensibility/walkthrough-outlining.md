---
title: 'İzlenecek yol: Ana hat | Microsoft Docs'
description: Bir dil hizmeti bağlamında veya kendi dosya adı uzantınız ve içerik türü için anahat bölgelerini tanımlama ve görüntüleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7bf4c0cc8757ea4f034da2ac17d6c76971f86305
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217235"
---
# <a name="walkthrough-outlining"></a>İzlenecek Yol: Ana Hat Oluşturma
Genişletmek veya daraltmak istediğiniz metin bölgesi türlerini tanımlayarak anahat oluşturma gibi dil tabanlı özellikleri ayarlayın. Bir dil hizmeti bağlamında bölgeleri tanımlayabilir veya kendi dosya adı uzantınızı ve içerik türünü tanımlayabilir ve bölge tanımını yalnızca bu türe uygulayabilir ya da bölge tanımlarını varolan bir içerik türüne (örneğin, "metin") uygulayabilirsiniz. Bu izlenecek yol, ana hat bölgelerini tanımlama ve görüntüleme işlemlerinin nasıl yapılacağını gösterir.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) projesi oluşturma

### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için

1. VSıX projesi oluşturun. Çözümü adlandırın `OutlineRegionTest` .

2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Varolan sınıf dosyalarını silin.

## <a name="implement-an-outlining-tagger"></a>Ana hat etiketi uygulama
 Ana hat bölgeleri bir tür etiketle ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ) işaretlenir. Bu etiket, Standart anahat oluşturma davranışını sağlar. Özetlenen bölge genişletilebilir veya daraltılabilirler. Ana hatlarıyla belirtilen bölge, genişletilmişse bir artı işareti ( **+** ) veya genişletilmişse bir eksi işareti () ile işaretlenir **-** ve genişletilmiş bölge dikey bir çizgi tarafından parçalanmıştır.

 Aşağıdaki adımlarda, köşeli ayraçlar (**[**,**]**) ile ayrılmış tüm bölgeler için anahat bölgeleri oluşturan bir Tagger nasıl tanımlanacağı gösterilmektedir.

### <a name="to-implement-an-outlining-tagger"></a>Bir anahat etiketi uygulamak için

1. Bir sınıf dosyası ekleyin ve adlandırın `OutliningTagger` .

2. Aşağıdaki ad alanlarını içeri aktarın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet1":::

3. Adlı bir sınıf oluşturun `OutliningTagger` ve şunları uygular <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet2":::

4. Metin arabelleğini ve anlık görüntüsünü izlemek ve ana hat bölgeleri olarak etiketlenmesi gereken satır kümelerini biriktirmek için bazı alanlar ekleyin. Bu kod, ana hat bölgelerini temsil eden bölge nesnelerinin bir listesini (daha sonra tanımlanması için) içerir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet3":::

5. Alanları Başlatan bir Tagger Oluşturucu ekleyin, arabelleği ayrıştırır ve olaya bir olay işleyicisi ekler <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet4":::

6. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>Etiketi yayılmaları Başlatan yöntemini uygulayın. Bu örnekte, yönteme geçilen yayılmalar, <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> her zaman durum olmasa da her zaman bitişik olduğu varsayılır. Bu yöntem, ana hat bölgelerinin her biri için yeni bir etiket aralığı oluşturur.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet5":::

7. Bir `TagsChanged` olay işleyicisi bildirin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet6":::

8. `BufferChanged`Metin arabelleğini ayrıştırarak olaylara yanıt veren bir olay işleyicisi ekleyin <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet7":::

9. Arabelleği ayrıştırtıran bir yöntem ekleyin. Burada verilen örnek yalnızca gösterim amaçlıdır. Bu, arabelleği iç içe ana hat bölgelerinde eşzamanlı olarak ayrıştırır.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet8":::

10. Aşağıdaki yardımcı yöntemi, ana hat düzeyini temsil eden bir tamsayı alır; örneğin, en sol ayraç çifti.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet9":::

11. Aşağıdaki yardımcı yöntemi bir bölgeyi (Bu makalede daha sonra tanımlanan) bir SnapshotSpan olarak çevirir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet10":::

12. Aşağıdaki kod yalnızca gösterim amaçlıdır. Bir anahat bölgesinin başlangıcının satır numarasını ve sapmasını ve üst bölgeye (varsa) bir başvuru içeren bir PartialRegion sınıfını tanımlar. Bu kod, ayrıştırıcısının iç içe ana hat bölgelerini ayarlamaya olanak sağlar. Türetilmiş bölge sınıfı, bir ana hat bölgesinin sonundaki satır numarasına bir başvuru içerir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet11":::

## <a name="implement-a-tagger-provider"></a>Tagger sağlayıcısı uygulama
 Tagger için bir Tagger sağlayıcısını dışarı aktarın. Tagger sağlayıcı, `OutliningTagger` "metin" içerik türü için bir arabellek oluşturur veya `OutliningTagger` arabellekte zaten bir tane varsa, bir döndürür.

### <a name="to-implement-a-tagger-provider"></a>Bir Tagger sağlayıcısı uygulamak için

1. Uygulayan adlı bir sınıf oluşturun `OutliningTaggerProvider` <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> ve bunu ContentType ve TagType öznitelikleriyle dışarı aktarın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet12":::

2. <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>Arabellek özelliklerine bir ekleyerek yöntemini uygulayın `OutliningTagger` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet13":::

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin
 Bu kodu test etmek için, OutlineRegionTest çözümünü derleyin ve deneysel örnekte çalıştırın.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>OutlineRegionTest çözümünü derlemek ve test etmek için

1. Çözümü derleyin.

2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun. Açma köşeli ayracını ve sağ ayraçları içeren bir metin yazın.

    ```
    [
       Hello
    ]
    ```

4. Her iki ayraçları da içeren bir anahat bölgesi olmalıdır. Ana hat bölgesini daraltmak için açık köşeli ayracın solundaki eksi Işaretine tıklamanız gerekir. Bölge daraltıldığında, üç nokta simgesi (*...*) daraltılan bölgenin solunda görünmelidir ve işaretçiyi üç nokta üzerine getirdiğinizde metin **Vurgulu metin** içeren bir açılan pencere görünmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: bir içerik türünü bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
