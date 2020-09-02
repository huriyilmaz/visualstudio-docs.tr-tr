---
title: 'İzlenecek yol: QuickInfo araç Ipuçlarını görüntüleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b349f0293071dfa30677b7558ca93985d16d55e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64808180"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>İzlenecek Yol: HızlıBilgi Araç İpuçlarını Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

QuickInfo, Kullanıcı işaretçiyi bir yöntem adı üzerine taşırken Yöntem imzalarını ve açıklamalarını görüntüleyen bir IntelliSense özelliğidir. QuickInfo gibi dil tabanlı özellikleri, hızlı bilgi açıklamaları sağlamak istediğiniz tanımlayıcıları tanımlayarak ve sonra içeriğin görüntüleneceği bir araç ipucu oluşturmak için uygulayabilirsiniz. Hızlı bilgileri bir dil hizmeti bağlamında tanımlayabilir veya kendi dosya adı uzantınızı ve içerik türünü tanımlayabilir ve yalnızca bu tür için hızlı bilgileri görüntüleyebilir veya var olan bir içerik türü için QuickInfo görüntüleyebilirsiniz (örneğin, "metin"). Bu izlenecek yol, "metin" içerik türü için hızlı bilgi görüntülemeyi gösterir.  
  
 Bu kılavuzda QuickInfo örneği, bir kullanıcı işaretçiyi bir yöntem adı üzerine taşırken araç ipuçlarını görüntüler. Bu tasarım için şu dört arabirimi uygulamanız gerekir:  
  
- kaynak arabirim  
  
- kaynak sağlayıcı arabirimi  
  
- Denetleyici Arabirimi  
  
- denetleyici sağlayıcı arabirimi  
  
  Kaynak ve denetleyici sağlayıcıları Managed Extensibility Framework (MEF) bileşen bölümleridir ve kaynak ve denetleyici sınıflarının dışarı aktarılmasından ve <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> araç ipucu metin arabelleğini oluşturan, ve gibi <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> hızlı bilgi oturumunu tetikleyen ' de hizmet ve aracıları içeri aktarmaktan sorumludur.  
  
  Bu örnekte, QuickInfo kaynağı yöntem adlarının ve açıklamalarının sabit kodlanmış bir listesini kullanır, ancak tam uygulamalarda, dil hizmeti ve dil belgeleri bu içeriği sağlamaktan sorumludur.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>MEF projesi oluşturma  
  
#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `QuickInfoTest` .  
  
2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Varolan sınıf dosyalarını silin.  
  
## <a name="implementing-the-quickinfo-source"></a>QuickInfo kaynağını uygulama  
 QuickInfo kaynağı tanımlayıcı kümesini ve açıklamalarını toplamaktan ve tanımlayıcılardan biri ile karşılaşıldığında araç ipucu metin arabelleğine içerik eklemeye sorumludur. Bu örnekte, tanımlayıcılar ve açıklamaları yalnızca kaynak oluşturucuya eklenir.  
  
#### <a name="to-implement-the-quickinfo-source"></a>QuickInfo kaynağını uygulamak için  
  
1. Bir sınıf dosyası ekleyin ve adlandırın `TestQuickInfoSource` .  
  
2. Microsoft. VisualStudio. Language. IntelliSense için bir başvuru ekleyin.  
  
3. Aşağıdaki içeri aktarmaları ekleyin.  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4. Uygulayan bir sınıf bildirin <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> ve bunu adlandırın `TestQuickInfoSource` .  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5. QuickInfo kaynak sağlayıcısı, metin arabelleği ve bir yöntem adları ve yöntem imzaları kümesi için alanlar ekleyin. Bu örnekte, yöntem adları ve imzalar `TestQuickInfoSource` oluşturucuda başlatılır.  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6. QuickInfo kaynak sağlayıcısını ve metin arabelleğini ayarlayan bir Oluşturucu ekleyin ve yöntem adları kümesini ve Yöntem imzalarını ve açıklamalarını doldurur.  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7. Yöntemini uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> . Bu örnekte, yöntemi geçerli sözcüğü ya da imleç bir satırın sonunda veya bir metin arabelleği ise, önceki sözcüğü bulur. Sözcük Yöntem adlarından biri ise, bu yöntem adının açıklaması QuickInfo içeriğine eklenir.  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8. Şunları gerçekleştirdiğinden Dispose () yöntemini de uygulamalısınız <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> <xref:System.IDisposable> :  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>QuickInfo kaynak sağlayıcısı uygulama  
 QuickInfo kaynağının sağlayıcısı öncelikle kendisini bir MEF bileşeni parçası olarak dışa aktarıp QuickInfo kaynağını oluşturur. Bir MEF bileşeni parçası olduğundan, diğer MEF bileşen parçalarını içeri aktarabilir.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Bir QuickInfo kaynak sağlayıcısı uygulamak için  
  
1. Uygulayan adlı bir QuickInfo kaynak sağlayıcısı bildirin `TestQuickInfoSourceProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> ve bunu bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo Source", bir <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before = "default" ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" ile dışarı aktarın.  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2. İki düzenleyici hizmetini <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> ve <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , özellikleri olarak içeri aktarın `TestQuickInfoSourceProvider` .  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3. <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>Yeni bir döndürecek şekilde uygulayın `TestQuickInfoSource` .  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>QuickInfo denetleyicisi uygulama  
 QuickInfo denetleyicileri hızlı bilgi görüntülenmesi gereken zaman belirlenir. Bu örnekte, işaretçi Yöntem adlarından birine karşılık gelen bir sözcüğün üzerindeyken QuickInfo görüntülenir. QuickInfo denetleyicisi, bir QuickInfo oturumunu tetikleyen bir fare üzerine gelme olay işleyicisi uygular.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>QuickInfo denetleyicisi uygulamak için  
  
1. Uygulayan bir sınıf bildirin <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> ve bunu adlandırın `TestQuickInfoController` .  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2. Metin görünümünde, hızlı bilgi oturumunda ve QuickInfo denetleyici sağlayıcısında temsil edilen metin arabellekleri için metin görünümü için özel alanlar ekleyin.  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3. Alanları ayarlayan ve fare üzerine gelme olay işleyicisini ekleyen bir Oluşturucu ekleyin.  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4. QuickInfo oturumunu tetikleyen fare üzerine gelme olay işleyicisini ekleyin.  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5. <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>Denetleyici metin görünümünden ayrıldığında fare üzerine gelme olay işleyicisini kaldırabilmesi için yöntemini uygulayın.  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6. <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>Yöntemini ve <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> yöntemini Bu örnek için boş yöntemler olarak uygulayın.  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>QuickInfo denetleyici sağlayıcısını uygulama  
 QuickInfo denetleyicisi sağlayıcısı öncelikle kendisini bir MEF bileşeni parçası olarak dışa aktarıp QuickInfo denetleyicisi örneğini oluşturur. Bir MEF bileşeni parçası olduğundan, diğer MEF bileşen parçalarını içeri aktarabilir.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>QuickInfo denetleyici sağlayıcısını uygulamak için  
  
1. Uygulayan adlı bir sınıf bildirin `TestQuickInfoControllerProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> ve bunu bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo Controller" ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" ile dışarı aktarın:  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2. <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>Özelliği olarak içeri aktarın.  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3. <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>QuickInfo denetleyicisini örnekleyerek yöntemi uygulayın.  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>Kodu derleme ve test etme  
 Bu kodu test etmek için QuickInfoTest çözümünü derleyin ve deneysel örnekte çalıştırın.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>QuickInfoTest çözümünü derlemek ve test etmek için  
  
1. Çözümü derleyin.  
  
2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği oluşturulur.  
  
3. Bir metin dosyası oluşturun ve "Ekle" ve "çıkart" sözcüklerini içeren bir metin yazın.  
  
4. İşaretçiyi "Ekle" oluşumlarından birinin üzerine taşıyın. İmza ve `add` yöntemin açıklaması görüntülenmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
