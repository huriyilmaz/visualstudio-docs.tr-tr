---
title: 'İzlenecek yol: Imza yardımını görüntüleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 280b5b517089ad9e5b38cb00dc9b14c68253d1e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202042"
---
# <a name="walkthrough-displaying-signature-help"></a>İzlenecek Yol: İmza Yardımını Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İmza yardımı ( *parametre bilgisi*olarak da bilinir), bir Kullanıcı parametre listesi başlangıç karakterini (genellikle bir açılış ayracı) yazdığında bir araç ipucunda bir yöntemin imzasını görüntüler. Bir parametre ve parametre ayırıcısı (genellikle virgül) yazıldığında araç ipucu, sonraki parametreyi kalın olarak göstermek için güncelleştirilir. Bir dil hizmeti bağlamında Imza yardımını tanımlayabilir veya yalnızca bu tür için kendi dosya adı uzantınızı ve içerik türünü tanımlayabilir ve Imza yardımını görüntüleyebilirsiniz veya var olan bir içerik türü için Imza yardımını (örneğin, "metin") görüntüleyebilirsiniz. Bu izlenecek yol, "metin" içerik türü için Imza yardımını görüntülemeyi gösterir.  
  
 İmza yardımı genellikle belirli bir karakter yazılarak tetiklenir, örneğin "(" (parantez açma) ve başka bir karakter yazılarak, örneğin ")" (kapatma parantezi). Bir karakter yazılarak tetiklenen IntelliSense özellikleri, tuş vuruşları ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirim) ve arabirimi uygulayan bir işleyici sağlayıcısı için bir komut işleyicisi kullanılarak uygulanabilir <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Imza yardımına katılan imzaların listesi olan Imza yardım kaynağını oluşturmak için, arabirimi <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> ve arabirimi uygulayan bir kaynak sağlayıcıyı uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> . Sağlayıcılar Managed Extensibility Framework (MEF) bileşen bölümleridir ve kaynak ve denetleyici sınıflarını dışa aktarıp, hizmet ve aracıları içeri aktarmaktan sorumludur; Örneğin, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> metin arabelleğinde gezinmenizi sağlar ve <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> imza Yardım oturumunu tetikleyen ' dir.  
  
 Bu izlenecek yol, sabit kodlanmış tanımlayıcı kümesi için Imza yardımına nasıl uygulanacağını gösterir. Tam uygulamalarda, bu içeriği sağlamaktan dil sorumludur.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>MEF projesi oluşturma  
  
#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `SignatureHelpTest` .  
  
2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Varolan sınıf dosyalarını silin.  
  
4. Aşağıdaki başvuruları projeye ekleyin ve **CopyLocal** 'in şu şekilde ayarlandığından emin olun `false` :  
  
     Microsoft. VisualStudio. Editor  
  
     Microsoft. VisualStudio. Language. IntelliSense  
  
     Microsoft. VisualStudio. OLE. Interop  
  
     Microsoft. VisualStudio. Shell. 14.0  
  
     Microsoft. VisualStudio. TextManager. Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Imza, yardım Imzaları ve parametreleri uygulama  
 Imza yardım kaynağı, <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> her biri uygulayan parametreleri içeren, uygulayan imzaları temel alır <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . Tam bir uygulamada, bu bilgiler dil belgelerinden elde edilir, ancak bu örnekte imzalar sabit kodludur.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Imzayı uygulamak için yardım imzaları ve parametreleri  
  
1. Bir sınıf dosyası ekleyin ve adlandırın `SignatureHelpSource` .  
  
2. Aşağıdaki içeri aktarmaları ekleyin.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3. Uygulayan adlı bir sınıf ekleyin `TestParameter` <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4. Tüm özellikleri ayarlayan bir Oluşturucu ekleyin.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5. Özelliklerini ekleyin <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6. Uygulayan adlı bir sınıf ekleyin `TestSignature` <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7. Bazı özel alanlar ekleyin.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8. Alanları ayarlayan ve olaya abone olan bir Oluşturucu ekleyin <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. Bir `CurrentParameterChanged` olay bildirin. Bu olay, Kullanıcı İmzadaki parametrelerden birini doldurduğunda tetiklenir.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. Özelliği, <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> özellik değeri değiştirildiğinde olayı harekete geçirmeyecek şekilde uygulayın `CurrentParameterChanged` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. Olayı oluşturan bir yöntem ekleyin `CurrentParameterChanged` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. İçindeki virgüllerin sayısını İmzadaki virgül sayısıyla karşılaştırarak geçerli parametreyi hesaplayan bir yöntem ekleyin <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. Yöntemini çağıran olay için bir olay işleyicisi ekleyin <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> `ComputeCurrentParameter()` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. Özelliğini uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> . Bu özellik, <xref:Microsoft.VisualStudio.Text.ITrackingSpan> imzanın uygulandığı arabellekteki metnin aralığına karşılık gelen bir içerir.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. Diğer parametreleri uygulayın.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>Imza yardım kaynağını uygulama  
 Imza yardım kaynağı, bilgi sağladığınız imzalar kümesidir.  
  
#### <a name="to-implement-the-signature-help-source"></a>Imza yardım kaynağını uygulamak için  
  
1. Uygulayan adlı bir sınıf ekleyin `TestSignatureHelpSource` <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2. Metin arabelleğine bir başvuru ekleyin.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3. Metin arabelleğini ve Imza yardım kaynak sağlayıcısını ayarlayan bir Oluşturucu ekleyin.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4. Yöntemini uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> . Bu örnekte, imzalar sabit kodludur, ancak tam bir uygulamada, bu bilgileri dil belgelerinden alırsınız.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5. Yardımcı yöntemi `CreateSignature()` Yalnızca çizim için verilmiştir.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6. Yöntemini uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> . Bu örnekte, her birinin iki parametresi bulunan yalnızca iki imzası vardır. Bu nedenle, bu yöntem gerekli değildir. Birden fazla Imza yardım kaynağının kullanılabildiği Fuller uygulamasında bu yöntem, en yüksek öncelikli Imza yardım kaynağının eşleşen bir imza sağlayabileceğine karar vermek için kullanılır. Bu, yöntemi null değerini döndürür ve bir sonraki en yüksek öncelikli kaynağın bir eşleşme sağlaması istenir.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7. Dispose () yöntemini uygulayın:  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Imza yardım kaynak sağlayıcısını uygulama  
 Imza yardım kaynak sağlayıcısı, Managed Extensibility Framework (MEF) bileşeni parçasını dışarı aktarma ve Imza yardım kaynağının örneğini oluşturma konusunda sorumludur.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Imza yardım kaynak sağlayıcısını uygulamak için  
  
1. Uygulayan adlı bir sınıf ekleyin `TestSignatureHelpSourceProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> ve bunu bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" ve bir <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before = "default" ile dışarı aktarın.  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2. Öğesini <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> örnekleyerek uygulayın `TestSignatureHelpSource` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>Komut Işleyicisini uygulama  
 İmza yardımı genellikle bir (karakter ve bir) karakteri tarafından tetiklenir. Bu tuş vuruşlarını, bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Imza yardım oturumu (önce bilinen bir yöntem adından önce gelen karakter) ve bir karakter aldığında oturumu kapatır) tetiklemesini sağlayacak şekilde uygulayarak işleyebilirsiniz.  
  
#### <a name="to-implement-the-command-handler"></a>Komut işleyicisini uygulamak için  
  
1. Uygulayan adlı bir sınıf ekleyin `TestSignatureHelpCommand` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2. Bağdaştırıcı için özel alanlar ekleyin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> (komut işleyicisini Komut işleyicilerinin zincirine eklemenize olanak tanır), metin görünümü, Imza yardım Aracısı ve oturum, a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> ve sonraki <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3. Bu alanları başlatmak ve komut filtresi zincirine komut filtresi eklemek için bir Oluşturucu ekleyin.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>Komut filtresi bir (bilinen yöntem adlarından birinden sonra bir karakter) aldığında Imza Yardım oturumunu tetiklemek için yöntemini uygulayın ve oturum hala etkinken bir karakter aldığında oturumu yoksayın. Her durumda, komut iletilir.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>Yöntemi her zaman komutunu iletmeleri için uygulayın.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Imza yardım komut sağlayıcısını uygulama  
 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>Metin görünümü oluşturulduğunda komut işleyicisini oluşturmak için öğesini uygulayarak Imza yardım komutunu sağlayabilirsiniz.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Imza yardım komut sağlayıcısını uygulamak için  
  
1. Uygulayan adlı bir sınıf ekleyin `TestSignatureHelpController` <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> ve, ve ile dışarı aktarın <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2. <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>(Nesnesi için kullanılır <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (geçerli sözcüğü bulmak için kullanılır) ve <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (imza Yardım oturumunu tetiklemek için) öğesini içe aktarın.  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3. Öğesini <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> örnekleyerek yöntemini uygulayın `TestSignatureCommandHandler` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>Kodu derleme ve test etme  
 Bu kodu test etmek için, SignatureHelpTest çözümünü derleyin ve deneysel örnekte çalıştırın.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>SignatureHelpTest çözümünü derlemek ve test etmek için  
  
1. Çözümü derleyin.  
  
2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği oluşturulur.  
  
3. Bir metin dosyası oluşturun ve "Ekle" sözcüğünün yanı sıra bir açılış ayracı içeren bir metin yazın.  
  
4. Açma parantezini yazdıktan sonra, yöntemi için iki imzanın listesini görüntüleyen bir araç ipucu görmeniz gerekir `add()` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
