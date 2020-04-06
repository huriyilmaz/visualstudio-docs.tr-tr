---
title: 'Walkthrough: QuickInfo Araç İpuçları görüntüleme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 47a14ca0692ad0338b56fd1d372307fb0e2ccc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697432"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Walkthrough: QuickInfo araç ipuçlarını görüntüleyin
QuickInfo, kullanıcı işaretçiyi bir yöntem adı üzerinde hareket ettirdiğinde yöntem imzalarını ve açıklamalarını görüntüleyen bir IntelliSense özelliğidir. QuickInfo açıklamalarını sağlamak istediğiniz tanımlayıcıları tanımlayarak ve ardından içeriği görüntülemek için bir araç ipucu oluşturarak QuickInfo gibi dil tabanlı özellikleri uygulayabilirsiniz. QuickInfo'yu bir dil hizmeti bağlamında tanımlayabilir veya kendi dosya adı uzantınızı ve içerik yazınızı tanımlayabilir ve QuickInfo'yu yalnızca bu tür için görüntüleyebilir veya varolan bir içerik türü için QuickInfo'yu görüntüleyebilirsiniz ("metin" gibi). Bu izlenecek yol, "metin" içerik türü için QuickInfo'nun nasıl görüntülenebildiğini gösterir.

 Bu izbeden QuickInfo örneği, kullanıcı işaretçiyi bir yöntem adı üzerinde hareket ettirdiğinde araç uçlarını görüntüler. Bu tasarım, bu dört arabirimi uygulamanızı gerektirir:

- kaynak arabirimi

- kaynak sağlayıcı arabirimi

- denetleyici arabirimi

- denetleyici sağlayıcı arabirimi

  Kaynak ve denetleyici sağlayıcıları Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşen parçalarıdır ve kaynak ve denetleyici sınıflarının dışa <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>aktarımı ve araç ipucu metin arabelleği oluşturan , ve QuickInfo oturumunu tetikleyen , araç ipucu metin arabelleği gibi hizmet ve <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>brokerların içe aktarIlmesinden sorumludur.

  Bu örnekte, QuickInfo kaynağı yöntem adları ve açıklamaların sabit kodlanmış bir listesini kullanır, ancak tam uygulamalarda, dil hizmeti ve dil belgeleri bu içeriği sağlamaktan sorumludur.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren, Visual Studio SDK'yı indirme merkezinden yüklemeniz gerekmez. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

### <a name="to-create-a-mef-project"></a>Bir MEF projesi oluşturmak için

1. Bir C# VSIX projesi oluşturun. (Yeni **Proje** iletişim kutusunda Visual **C# / Genişletilebilirlik,** ardından **VSIX Project'i**seçin.) Çözümü `QuickInfoTest`adlandırın.

2. Projeye Bir Düzenleyici Sınıflandırıcı öğesi şablonu ekleyin. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Varolan sınıf dosyalarını silin.

## <a name="implement-the-quickinfo-source"></a>QuickInfo kaynağını uygulayın
 QuickInfo kaynağı tanımlayıcılar kümesini ve açıklamalarını toplamaktan ve tanımlayıcılardan birine rastlandığında içeriği araç ipucu metin arabelleğine eklemekten sorumludur. Bu örnekte, tanımlayıcılar ve açıklamaları kaynak oluşturucuya eklenir.

#### <a name="to-implement-the-quickinfo-source"></a>QuickInfo kaynağını uygulamak için

1. Bir sınıf dosyası ekleyin `TestQuickInfoSource`ve adlandırın.

2. *Microsoft.VisualStudio.Language.IntelliSense*adresine başvuru ekleyin.

3. Aşağıdaki içeri almaları ekleyin.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>bir sınıf bildirin ve `TestQuickInfoSource`adını.

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. QuickInfo kaynak sağlayıcısı, metin arabelleği ve yöntem adları ve yöntem imzaları kümesi için alan ekleyin. Bu örnekte, yöntem adları ve imzalar `TestQuickInfoSource` oluşturucuda başharflere getirilir.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. QuickInfo kaynak sağlayıcısını ve metin arabelleği ayarlayan ve yöntem adları kümesini ve yöntem imzalarını ve açıklamalarını dolduran bir oluşturucu ekleyin.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Yöntemi <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> uygulayın. Bu örnekte, imleç bir satırın veya metin arabelleği sonunda ise yöntem geçerli sözcüğü veya önceki sözcüğü bulur. Sözcük yöntem adlarından biriyse, bu yöntem adının açıklaması QuickInfo içeriğine eklenir.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. Ayrıca bir Elden Çıkarma() yöntemini de uygulamanız gerekir, çünkü <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> <xref:System.IDisposable>uygular:

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>QuickInfo kaynak sağlayıcısı uygulama
 QuickInfo kaynağının sağlayıcısı öncelikle bir MEF bileşen parçası olarak kendini dışa aktarmak ve QuickInfo kaynağı anlık hizmet vermektedir. Mef bileşen parçası olduğundan, diğer MEF bileşen parçalarını içe aktarabilir.

#### <a name="to-implement-a-quickinfo-source-provider"></a>QuickInfo kaynak sağlayıcısı uygulamak için

1. "ToolTip QuickInfo `TestQuickInfoSourceProvider` Source", <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>"ToolTip QuickInfo Source", <xref:Microsoft.VisualStudio.Utilities.NameAttribute> before="default" <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> ve "text" ile <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> birlikte uygulayan ve dışa aktaran bir QuickInfo kaynak sağlayıcısı bildirin.

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. İki düzenleyici hizmeti <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>alma ve `TestQuickInfoSourceProvider`' ın özellikleri olarak .

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Yeni <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> `TestQuickInfoSource`bir döndürmek için uygulayın.

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>QuickInfo denetleyicisi uygulayın
 QuickInfo denetleyicileri QuickInfo'nun ne zaman görüntüleneceğini belirler. Bu örnekte, işaretçi yöntem adlarından birine karşılık gelen bir sözcük üzerinde olduğunda QuickInfo görüntülenir. QuickInfo denetleyicisi, QuickInfo oturumunu tetikleyen bir fare gezinme olayı işleyicisi uygular.

### <a name="to-implement-a-quickinfo-controller"></a>QuickInfo denetleyicisi uygulamak için

1. Uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>bir sınıf bildirin ve `TestQuickInfoController`adını.

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Metin görünümü için özel alanlar, metin görünümünde temsil edilen metin arabellekleri, QuickInfo oturumu ve QuickInfo denetleyici sağlayıcısı ekleyin.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Alanları ayarlayan ve fare gezinme olayı işleyicisini ekleyen bir oluşturucu ekleyin.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. QuickInfo oturumunu tetikleyen fare gezinme olayı işleyicisini ekleyin.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> Denetleyici metin görünümünden ayrıldığında fare gezinme olayı işleyicisini kaldıracak şekilde yöntemi uygulayın.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Bu <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> örnek için <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> yöntem ve yöntemi boş yöntem olarak uygulayın.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>QuickInfo denetleyici sağlayıcısını uygulama
 QuickInfo denetleyicisağlayıcısı öncelikle bir MEF bileşen parçası olarak kendini dışa aktarmak ve QuickInfo denetleyicisi anlık hizmet vermektedir. Mef bileşen parçası olduğundan, diğer MEF bileşen parçalarını içe aktarabilir.

### <a name="to-implement-the-quickinfo-controller-provider"></a>QuickInfo denetleyici sağlayıcısını uygulamak için

1. "ToolTip `TestQuickInfoControllerProvider` QuickInfo <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>Controller" ve bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin" ile uygulayan ve dışa aktaran bir sınıf bildirin:

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Bir <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> özellik olarak içe aktarın.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. QuickInfo <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> denetleyicisini anında uygulayarak yöntemi uygulayın.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Kodu oluşturma ve test edin
 Bu kodu test etmek için QuickInfoTest çözümlerini oluşturun ve deneme örneğinde çalıştırın.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>QuickInfoTest çözümlerini oluşturmak ve test etmek için

1. Çözümü derleyin.

2. Bu projeyi hata ayıklamada çalıştırdığınızda, Visual Studio'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun ve "ekle" ve "çıkar" sözcülerini içeren bazı metinler yazın.

4. İşaretçiyi "ekle" olaylarından birinin üzerine taşıyın. İmza ve `add` yöntemin açıklaması görüntülenmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Walkthrough: İçerik türünü dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
