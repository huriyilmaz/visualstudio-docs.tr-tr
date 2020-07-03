---
title: 'İzlenecek yol: deyimin tamamlanmasını görüntüleme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 472ff8c10e1346f25e7bc72ed5fd4ee9f31bbafa
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904787"
---
# <a name="walkthrough-display-statement-completion"></a>İzlenecek yol: görüntüleme ifadesinin tamamlanması
Tamamlanmasını sağlamak istediğiniz tanımlayıcıları tanımlayarak ve ardından bir tamamlanma oturumu tetikleyerek, dil tabanlı ifade tamamlamayı uygulayabilirsiniz. Bir dil hizmeti bağlamında deyimin tamamlanmasını tanımlayabilir, kendi dosya adı uzantınızı ve içerik türünü tanımlayabilir ve ardından yalnızca bu tür için tamamlamayı görüntüleyebilirsiniz. Ya da, var olan bir içerik türü için tamamlamayı (örneğin, "düz metin") tetikleyebilirsiniz. Bu izlenecek yol, metin dosyalarının içerik türü olan "düz metin" içerik türü için deyimin tamamlanmasının nasıl tetikleneceğini gösterir. "Metin" içerik türü, kod ve XML dosyaları da dahil olmak üzere diğer tüm içerik türlerinin üst öğesi.

 Deyimin tamamlanması genellikle belirli karakterler yazılarak tetiklenir — Örneğin, "Using" gibi bir tanımlayıcının başlangıcını yazarak tetiklenir. Bir seçimi yürütmek için **boşluk çubuğu**, **sekme**veya **ENTER** tuşuna basılarak genellikle kapatılır. Tuş vuruşları ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirim) ve arabirimi uygulayan bir işleyici sağlayıcısı için bir komut işleyicisi kullanarak, bir karakter yazarken tetiklenecek IntelliSense özelliklerini uygulayabilirsiniz <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Tamamlanma aşamasında yer alan tanımlayıcıların listesi olan tamamlama kaynağını oluşturmak için, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> arabirimi ve tamamlanma kaynak sağlayıcısını ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> arabirim) uygulayın. Sağlayıcılar Managed Extensibility Framework (MEF) bileşen bölümleridir. Bunlar, kaynak ve denetleyici sınıflarını dışa ve hizmet ve aracıları içeri aktarmaktan sorumludur — Örneğin, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> metin arabelleğinde gezinmeyi sağlayan ve <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> tamamlanma oturumunu tetikleyen olan.

 Bu izlenecek yol, sabit kodlanmış bir tanımlayıcı kümesi için nasıl ifade tamamlanmasının uygulanacağını gösterir. Tam uygulamalarda, dil hizmeti ve dil belgeleri bu içeriği sağlamaktan sorumludur.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için

1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `CompletionTest` .

2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Varolan sınıf dosyalarını silin.

4. Aşağıdaki başvuruları projeye ekleyin ve **CopyLocal** 'in şu şekilde ayarlandığından emin olun `false` :

     Microsoft. VisualStudio. Editor

     Microsoft. VisualStudio. Language. IntelliSense

     Microsoft. VisualStudio. OLE. Interop

     Microsoft. VisualStudio. Shell. 15.0

     Microsoft. VisualStudio. Shell. sabit. 10.0

     Microsoft. VisualStudio. TextManager. Interop

## <a name="implement-the-completion-source"></a>Tamamlanma kaynağını uygulama
 Tamamlanma kaynağı, tanımlayıcı kümesini toplamaktan ve bir Kullanıcı bir tanımlayıcının ilk harfleri gibi bir tamamlama tetikleyicisi yazdığında, içeriğin tamamlanma penceresine eklenmesine sorumludur. Bu örnekte, tanımlayıcılar ve açıklamaları yönteminde sabit olarak kodlanmıştır <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> . Çoğu gerçek dünyada kullanımlar için, tamamlama listesini doldurmak üzere belirteçleri almak üzere dilinizin ayrıştırıcısını kullanırsınız.

### <a name="to-implement-the-completion-source"></a>Tamamlanma kaynağını uygulamak için

1. Bir sınıf dosyası ekleyin ve adlandırın `TestCompletionSource` .

2. Bu içeri aktarmaları ekleyin:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Sınıf bildirimini, `TestCompletionSource` uygulayan şekilde değiştirin <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Kaynak sağlayıcı, metin arabelleği ve bir <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> nesne listesi (Tamamlanma oturumunda yer alacak tanımlayıcılara karşılık gelen) için özel alanlar ekleyin:

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Kaynak sağlayıcıyı ve arabelleği ayarlayan bir Oluşturucu ekleyin. `TestCompletionSourceProvider`Sınıfı sonraki adımlarda tanımlanmıştır:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>Bağlam içinde sağlamak istediğiniz tamamlamaların bulunduğu bir tamamlanma kümesi ekleyerek yöntemini uygulayın. Her tamamlama kümesi bir tamamlama kümesi içerir <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> ve tamamlanma penceresinin sekmesine karşılık gelir. (Visual Basic projelerinde, tamamlama pencere sekmeleri **ortak** ve **hepsi**olarak adlandırılır.) `FindTokenSpanAtPosition`Yöntemi bir sonraki adımda tanımlanmıştır.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. Aşağıdaki yöntem, imlecin konumundan geçerli sözcüğü bulmak için kullanılır:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Yöntemi uygulayın `Dispose()` :

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Tamamlama kaynak sağlayıcısını uygulama
 Tamamlanma kaynak sağlayıcısı, tamamlanma kaynağını örnekleyen MEF bileşeni bölümüdür.

### <a name="to-implement-the-completion-source-provider"></a>Tamamlama kaynak sağlayıcısını uygulamak için

1. Uygulayan adlı bir sınıf ekleyin `TestCompletionSourceProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Bu sınıfı <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "düz metin" ve <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "test tamamlama" ile dışarı aktarın.

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>Tamamlanma kaynağında geçerli sözcüğü bulan a içeri aktarma.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A>Tamamlama kaynağını başlatmak için yöntemini uygulayın.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Tamamlama komut işleyicisi sağlayıcısını uygulama
 Tamamlama komut işleyicisi sağlayıcısı <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , bir metin görünümü oluşturma olayını dinleyen ve görünümü bir ile dönüştürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> — Bu, komutun Visual Studio Kabuğu komut zinciri ' ne ' a eklenmesini sağlar <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Bu sınıf bir MEF dışarı aktarması olduğundan, komut işleyicisinin kendisi tarafından istenen Hizmetleri içeri aktarmak için de kullanabilirsiniz.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Tamamlama komut işleyicisi sağlayıcısını uygulamak için

1. Adlı bir dosya ekleyin `TestCompletionCommandHandler` .

2. Bu yönergeleri kullanarak bunları ekleyin:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Uygulayan adlı bir sınıf ekleyin `TestCompletionHandlerProvider` <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Bu sınıfı <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "belirteç tamamlama işleyicisi", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "düz metin" ve ' nin bir ile dışarı aktarın <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> Standart Visual Studio Hizmetleri 'ne erişim sağlayan bir, bir, ve a 'ya dönüştürmeyi sağlayan öğesini içe aktarın.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>Komut işleyicisini başlatmak için yöntemini uygulayın.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Tamamlama komut işleyicisini uygulama
 Deyimin tamamlanması tuş vuruşları tarafından tetiklendiğinden, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> tamamlama oturumunu tetikleyen, işleyecek ve kapatabelirten tuş vuruşlarını almak ve işlemek için arabirimi uygulamanız gerekir.

#### <a name="to-implement-the-completion-command-handler"></a>Tamamlama komut işleyicisini uygulamak için

1. Şunu uygulayan adlı bir sınıf ekleyin `TestCompletionCommandHandler` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Sonraki komut işleyicisine (komutunu geçirdiğiniz), metin görünümüne, komut işleyici sağlayıcısına (çeşitli hizmetlere erişim sağlayan) ve bir tamamlanma oturumuna yönelik özel alanlar ekleyin:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Metin görünümü ve sağlayıcı alanlarını ayarlayan bir Oluşturucu ekleyin ve komutu komut zincirine ekler:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Komutu şu şekilde <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> geçirerek yöntemi uygulayın:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Yöntemini uygulayın <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> . Bu yöntem bir tuş vuruşu aldığında, aşağıdakilerden birini yapması gerekir:

   - Karakterin arabelleğe yazılmasına izin verin ve ardından tetikleme veya filtre tamamlamayı izleyin. (Yazdırma karakterleri bunu yapın.)

   - Tamamlamayı işleyin, ancak karakterin arabelleğe yazılmasına izin vermeyin. (Boşluk, **sekme**ve **ENTER** , bir tamamlama oturumu görüntülenirken bunu yapın.)

   - Komutun bir sonraki işleyiciye geçirilmesine izin verin. (Diğer tüm komutlar.)

     Bu yöntem Kullanıcı arabirimini görüntüleyebilir, <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> bunun bir Otomasyon bağlamında çağrılmadığından emin olmak için çağırın:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Bu kod, tamamlanma oturumunu tetikleyen özel bir yöntemdir:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. Sonraki örnek, olayından abone olan özel bir yöntemdir <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> :

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin
 Bu kodu test etmek için, CompletionTest çözümünü derleyin ve deneysel örnekte çalıştırın.

#### <a name="to-build-and-test-the-completiontest-solution"></a>CompletionTest çözümünü derlemek ve test etmek için

1. Çözümü derleyin.

2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun ve "Ekle" sözcüğünü içeren bir metin yazın.

4. İlk "a" ve ardından "d" yazdığınızda, "ekleme" ve "uyarlama" içeren bir liste görünmelidir. Ek olarak seçili olduğuna dikkat edin. Başka bir "d" yazdığınızda, liste yalnızca seçili olan "ek" i içermelidir. **Ara çubuğu**, **sekme**veya **ENTER** tuşuna basarak veya ESC ya da başka bir anahtar yazarak listeyi kapatabilmeniz için "ekleme" gerçekleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: bir içerik türünü bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
