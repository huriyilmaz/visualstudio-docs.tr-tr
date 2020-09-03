---
title: 'İzlenecek yol: deyimin tamamlanmasını görüntüleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db4e63beb1e3d4ff53e547492ae9eae7ee8001e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202006"
---
# <a name="walkthrough-displaying-statement-completion"></a>İzlenecek Yol: Deyim Tamamlamayı Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tamamlanmasını sağlamak istediğiniz tanımlayıcıları tanımlayarak ve ardından bir tamamlanma oturumu tetikleyerek, dil tabanlı ifade tamamlamayı uygulayabilirsiniz. Bir dil hizmeti bağlamında deyimin tamamlanmasını tanımlayabilir, kendi dosya adı uzantınızı ve içerik türünü tanımlayabilir ve ardından yalnızca bu tür için tamamlamayı görüntüleyebilirsiniz veya var olan bir içerik türü için tamamlamayı (örneğin, "düz metin") tetikleyebilirsiniz. Bu izlenecek yol, metin dosyalarının içerik türü olan "düz metin" içerik türü için deyimin tamamlanmasının nasıl tetikleneceğini gösterir. "Metin" içerik türü, kod ve XML dosyaları da dahil olmak üzere diğer tüm içerik türlerinin üst öğesi.  
  
 Deyimin tamamlanması genellikle belirli karakterler yazılarak tetiklenir — Örneğin, "Using" gibi bir tanımlayıcının başlangıcını yazarak tetiklenir. Genellikle bir seçimi yürütmek için boşluk çubuğu, sekme veya ENTER tuşuna basılarak kapatılır. Tuş vuruşları ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirim) ve arabirimi uygulayan bir işleyici sağlayıcısı için bir komut işleyicisi kullanarak tetiklenen IntelliSense özelliklerini uygulayabilirsiniz <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Tamamlanma aşamasında yer alan tanımlayıcıların listesi olan tamamlama kaynağını oluşturmak için, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> arabirimi ve tamamlanma kaynak sağlayıcısını ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> arabirim) uygulayın. Sağlayıcılar Managed Extensibility Framework (MEF) bileşen bölümleridir. Bunlar, kaynak ve denetleyici sınıflarını dışa aktarma ve hizmetleri ve aracıları içeri aktarma işleminden sorumludur — Örneğin, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> metin arabelleğinde gezinmeyi sağlayan ve <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> tamamlanma oturumunu tetikleyen olan.  
  
 Bu izlenecek yol, sabit kodlanmış bir tanımlayıcı kümesi için nasıl ifade tamamlanmasının uygulanacağını gösterir. Tam uygulamalarda, dil hizmeti ve dil belgeleri bu içeriği sağlamaktan sorumludur.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>MEF projesi oluşturma  
  
#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `CompletionTest` .  
  
2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Varolan sınıf dosyalarını silin.  
  
4. Aşağıdaki başvuruları projeye ekleyin ve **CopyLocal** 'in şu şekilde ayarlandığından emin olun `false` :  
  
     Microsoft. VisualStudio. Editor  
  
     Microsoft. VisualStudio. Language. IntelliSense  
  
     Microsoft. VisualStudio. OLE. Interop  
  
     Microsoft. VisualStudio. Shell. 14.0  
  
     Microsoft. VisualStudio. Shell. sabit. 10.0  
  
     Microsoft. VisualStudio. TextManager. Interop  
  
## <a name="implementing-the-completion-source"></a>Tamamlanma kaynağını uygulama  
 Tamamlanma kaynağı, tanımlayıcı kümesini toplamaktan ve bir Kullanıcı bir tanımlayıcının ilk harfleri gibi bir tamamlama tetikleyicisi yazdığında, içeriğin tamamlanma penceresine eklenmesine sorumludur. Bu örnekte, tanımlayıcılar ve açıklamaları yönteminde sabit olarak kodlanmıştır <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> . Çoğu gerçek dünyada kullanımlar için, tamamlama listesini doldurmak üzere belirteçleri almak üzere dilinizin ayrıştırıcısını kullanırsınız.  
  
#### <a name="to-implement-the-completion-source"></a>Tamamlanma kaynağını uygulamak için  
  
1. Bir sınıf dosyası ekleyin ve adlandırın `TestCompletionSource` .  
  
2. Bu içeri aktarmaları ekleyin:  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3. Sınıf bildirimini, `TestCompletionSource` uygulayan şekilde değiştirin <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4. Kaynak sağlayıcı, metin arabelleği ve bir <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> nesne listesi (Tamamlanma oturumunda yer alacak tanımlayıcılara karşılık gelen) için özel alanlar ekleyin:  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5. Kaynak sağlayıcıyı ve arabelleği ayarlayan bir Oluşturucu ekleyin. `TestCompletionSourceProvider`Sınıfı sonraki adımlarda tanımlanmıştır:  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>Bağlam içinde sağlamak istediğiniz tamamlamaların bulunduğu bir tamamlanma kümesi ekleyerek yöntemini uygulayın. Her tamamlama kümesi bir tamamlama kümesi içerir <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> ve tamamlanma penceresinin sekmesine karşılık gelir. (Visual Basic projelerinde, tamamlama pencere sekmeleri **ortak** ve **hepsi**olarak adlandırılır.) FindTokenSpanAtPosition yöntemi bir sonraki adımda tanımlanmıştır.  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7. Aşağıdaki yöntem, imlecin konumundan geçerli sözcüğü bulmak için kullanılır:  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8. Yöntemi uygulayın `Dispose()` :  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>Tamamlama kaynak sağlayıcısını uygulama  
 Tamamlanma kaynak sağlayıcısı, tamamlanma kaynağını örnekleyen MEF bileşeni bölümüdür.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Tamamlama kaynak sağlayıcısını uygulamak için  
  
1. Uygulayan adlı bir sınıf ekleyin `TestCompletionSourceProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Bu sınıfı <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "düz metin" ve <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "test tamamlama" ile dışarı aktarın.  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2. <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>Tamamlanma kaynağında geçerli sözcüğü bulmak için kullanılan a ' yı içeri aktarma.  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A>Tamamlama kaynağını başlatmak için yöntemini uygulayın.  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Tamamlama komut Işleyicisi sağlayıcısını uygulama  
 Tamamlama komut işleyicisi sağlayıcısı <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , bir metin görünümü oluşturma olayını dinleyen ve görünümü bir ile dönüştürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> — Bu, komutun Visual Studio Kabuğu komut zinciri ' ne ' a eklenmesini sağlar <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Bu sınıf bir MEF dışarı aktarması olduğundan, komut işleyicisinin kendisi tarafından istenen Hizmetleri içeri aktarmak için de kullanabilirsiniz.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Tamamlama komut işleyicisi sağlayıcısını uygulamak için  
  
1. Adlı bir dosya ekleyin `TestCompletionCommandHandler` .  
  
2. Şu using deyimlerini ekleyin:  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3. Uygulayan adlı bir sınıf ekleyin `TestCompletionHandlerProvider` <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Bu sınıfı <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "belirteç tamamlama işleyicisi", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "düz metin" ve ' nin bir ile dışarı aktarın <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4. <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> Standart Visual Studio Hizmetleri 'ne erişim sağlayan bir, bir, ve a 'ya dönüştürmeyi sağlayan öğesini içe aktarın.  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5. <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>Komut işleyicisini başlatmak için yöntemini uygulayın.  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>Tamamlama komut Işleyicisini uygulama  
 Deyimin tamamlanması tuş vuruşları tarafından tetiklendiğinden, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> tamamlama oturumunu tetikleyen, işleyecek ve kapatabelirten tuş vuruşlarını almak ve işlemek için arabirimi uygulamanız gerekir.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Tamamlama komut işleyicisini uygulamak için  
  
1. Şunu uygulayan adlı bir sınıf ekleyin `TestCompletionCommandHandler` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :  
  
    [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
    [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2. Sonraki komut işleyicisine (komutunu geçirdiğiniz), metin görünümüne, komut işleyici sağlayıcısına (çeşitli hizmetlere erişim sağlayan) ve bir tamamlanma oturumuna yönelik özel alanlar ekleyin:  
  
    [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
    [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3. Metin görünümü ve sağlayıcı alanlarını ayarlayan bir Oluşturucu ekleyin ve komutu komut zincirine ekler:  
  
    [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
    [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4. Komutu şu şekilde <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> geçirerek yöntemi uygulayın:  
  
    [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
    [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5. Yöntemini uygulayın <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> . Bu yöntem bir tuş vuruşu aldığında, aşağıdakilerden birini yapması gerekir:  
  
   - Karakterin arabelleğe yazılmasına izin verin ve ardından tetikleme veya filtre tamamlamayı izleyin. (Yazdırma karakterleri bunu yapın.)  
  
   - Tamamlamayı işleyin, ancak karakterin arabelleğe yazılmasına izin vermeyin. (Boşluk, sekme ve ENTER, bir tamamlama oturumu görüntülenirken bunu yapın.)  
  
   - Komutun bir sonraki işleyiciye geçirilmesine izin verin. (Diğer tüm komutlar.)  
  
     Bu yöntem Kullanıcı arabirimini görüntüleyebilir, <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> bunun bir Otomasyon bağlamında çağrılmadığından emin olmak için çağırın:  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6. Bu kod, tamamlanma oturumunu tetikleyen özel bir yöntemdir:  
  
    [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
    [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7. Sonraki örnek, olayından abone olan özel bir yöntemdir <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> :  
  
    [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
    [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>Kodu derleme ve test etme  
 Bu kodu test etmek için, CompletionTest çözümünü derleyin ve deneysel örnekte çalıştırın.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>CompletionTest çözümünü derlemek ve test etmek için  
  
1. Çözümü derleyin.  
  
2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği oluşturulur.  
  
3. Bir metin dosyası oluşturun ve "Ekle" sözcüğünü içeren bir metin yazın.  
  
4. İlk "a" ve ardından "d" yazdığınızda, "ekleme" ve "uyarlama" içeren bir liste görüntülenmelidir. Ek olarak seçili olduğuna dikkat edin. Başka bir "d" yazdığınızda, liste yalnızca seçili olan "ek" i içermelidir. Ara çubuğu, sekme veya ENTER tuşuna basarak veya ESC ya da başka bir anahtar yazarak listeyi kapatabilmeniz için "ekleme" gerçekleştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
