---
title: 'Walkthrough: İfade Tamamlama Görüntüleme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 1d2f5499511c9dc0bbb6711d0da630315384f8e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697408"
---
# <a name="walkthrough-display-statement-completion"></a>Walkthrough: Görüntü deyimi tamamlama
Tamamlamasağlamak istediğiniz tanımlayıcıları tanımlayarak ve ardından bir tamamlama oturumunu tetikleyerek dil tabanlı ifade tamamlamayı uygulayabilirsiniz. Bir dil hizmeti bağlamında deyim tamamlama tanımlayabilir, kendi dosya adı uzantısınızı ve içerik türünü tanımlayabilir ve ardından yalnızca bu tür için tamamlamayı görüntüleyebilirsiniz. Veya, varolan bir içerik türü için tamamlanmasını tetikleyebilirsiniz(örneğin, "düz metin". Bu izlenme, metin dosyalarının içerik türü olan "düz metin" içerik türü için deyim tamamlamanın nasıl tetiklenir olduğunu gösterir. "Metin" içerik türü, kod ve XML dosyaları da dahil olmak üzere diğer tüm içerik türlerinin atasıdır.

 Deyim tamamlama genellikle belirli karakterler yazarak tetiklenir(örneğin, "kullanma" gibi bir tanımlayıcının başlangıcını yazarak. Genellikle **Spacebar,** **Tab**tuşuna basarak **veya** seçim yapmak için enter tuşuna basılarak kapatılır. Tuş vuruşları <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> (arabirim) için bir komut işleyicisi ve <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> arabirimi uygulayan bir işleyici sağlayıcısı kullanarak bir karakter yazarken tetikleyen IntelliSense özelliklerini uygulayabilirsiniz. Tamamlanmaya katılan tanımlayıcıların listesi olan tamamlanma kaynağını oluşturmak için <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> arabirimi ve bir tamamlama kaynak sağlayıcısını <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> (arabirimi) uygulayın. Sağlayıcılar Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşen parçalarıdır. Kaynak ve denetleyici sınıflarının dışa aktarılmasını ve hizmet ve aracıların <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>içe aktarılmasını (örneğin, metin arabelleğinde gezinmeyi sağlayan ve tamamlama oturumunu <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>tetikleyen) sorumludurlar.

 Bu gözden geçirme, sabit kodlanmış bir tanımlayıcı kümesi için deyim tamamlamanın nasıl uygulanacağını gösterir. Tam uygulamalarda, dil hizmeti ve dil dokümantasyonu bu içeriğisağlamakla yükümlüdür.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>MEF Projesi Oluşturma

#### <a name="to-create-a-mef-project"></a>Bir MEF projesi oluşturmak için

1. Bir C# VSIX projesi oluşturun. (Yeni **Proje** iletişim kutusunda Visual **C# / Genişletilebilirlik,** ardından **VSIX Project'i**seçin.) Çözümü `CompletionTest`adlandırın.

2. Projeye Bir Düzenleyici Sınıflandırıcı öğesi şablonu ekleyin. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Varolan sınıf dosyalarını silin.

4. Projeye aşağıdaki başvuruları ekleyin ve **CopyLocal'ın** aşağıdaki `false`şekilde ayarlandıklarından emin olun:

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.visualstudio.ole

     Microsoft.VisualStudio.Shell.15.0

     Microsoft.VisualStudio.Shell.Immutable.10.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-the-completion-source"></a>Tamamlama kaynağını uygulayın
 Tamamlama kaynağı tanımlayıcı kümesini toplamaktan ve kullanıcı tanımlayıcının ilk harfleri gibi bir tamamlama tetikleyicisi yazdığında içeriği tamamlama penceresine eklemekten sorumludur. Bu örnekte, tanımlayıcılar ve açıklamaları <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> yöntemde sabit kodlanır. Gerçek dünyanın çoğu kullanımalanında, belirteçlerin tamamlanma listesini doldurmasını sağlamak için dilinizin ayrıştırıcısını kullanırsınız.

### <a name="to-implement-the-completion-source"></a>Tamamlama kaynağını uygulamak için

1. Bir sınıf dosyası ekleyin `TestCompletionSource`ve adlandırın.

2. Bu içeri almaları ekleyin:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Sınıf bildirimini `TestCompletionSource` uygulayacağı şekilde <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>değiştirin:

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Kaynak sağlayıcı, metin arabelleği ve <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> nesnelerin listesi (tamamlama oturumuna katılacak tanımlayıcılara karşılık gelen):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Kaynak sağlayıcı ve arabellek ayarlayan bir oluşturucu ekleyin. Sınıf `TestCompletionSourceProvider` sonraki adımlarda tanımlanır:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Bağlamında <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> sağlamak istediğiniz tamamlanma kümesini içeren bir tamamlama kümesi ekleyerek yöntemi uygulayın. Her tamamlama kümesi bir <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> tamamlanma kümesi içerir ve tamamlama penceresinin bir sekmesine karşılık gelir. (Visual Basic projelerinde, tamamlama penceresi sekmeleri **Ortak** ve **Tümü**olarak adlandırılır.) Yöntem `FindTokenSpanAtPosition` bir sonraki adımda tanımlanır.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. İmlecin konumundan geçerli sözcüğü bulmak için aşağıdaki yöntem kullanılır:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Yöntemi `Dispose()` uygulayın:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Tamamlama kaynak sağlayıcısını uygulama
 Tamamlama kaynak sağlayıcısı, tamamlanma kaynağını anında alan MEF bileşeni parçasıdır.

### <a name="to-implement-the-completion-source-provider"></a>Tamamlama kaynak sağlayıcısını uygulamak için

1. 'yi uygulayan `TestCompletionSourceProvider` bir <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>sınıf ekleyin. Bu sınıfı "düz metin" ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "test tamamlama" ile dışa aktarın.

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Tamamlanma <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>kaynağında geçerli sözcüğü bulan a, içe aktarın.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Tamamlama <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> kaynağını anında bulmak için yöntemi uygulayın.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Tamamlama komut işleyicisağlayıcısını uygulama
 Tamamlama komut işleyicisi sağlayıcısı, metin görünümü oluşturma olayını dinleyen ve görünümü <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>Visual Studio kabuğunun komut zincirine eklenmesini sağlayan bir 'den <xref:Microsoft.VisualStudio.Text.Editor.ITextView>bir ' e dönüştüren bir <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>' den türetilmiştir. Bu sınıf bir MEF dışa aktarma olduğundan, komut işleyicisinin kendisi tarafından gerekli olan hizmetleri almak için de kullanabilirsiniz.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Tamamlama komut işleyicisağlayıcısını uygulamak için

1. Adlı `TestCompletionCommandHandler`dosya ekle

2. Yönergeleri kullanarak bunları ekleyin:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. 'yi uygulayan `TestCompletionHandlerProvider` bir <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>sınıf ekleyin. Bu sınıfı "belirteç <xref:Microsoft.VisualStudio.Utilities.NameAttribute> tamamlama işleyicisi", "düz <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> metin" <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>ve bir .

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Standart <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>Visual Studio hizmetlerine erişim <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sağlayan <xref:Microsoft.VisualStudio.Text.Editor.ITextView>a <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> a ve a'ya dönüştürmeyi sağlayan ,

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Komut <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> işleyicisini anında anileştirmek için yöntemi uygulayın.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Tamamlama komut işleyicisini uygulama
 İfade tamamlama tuş vuruşlarından tetiklendirildi, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> tamamlanma oturumunu tetikleyen, işleyen ve reddeden tuş vuruşlarını almak ve işlemek için arabirimi uygulamanız gerekir.

#### <a name="to-implement-the-completion-command-handler"></a>Tamamlama komut işleyicisini uygulamak için

1. Uygulayan adlandırılmış `TestCompletionCommandHandler` bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>sınıf ekleyin:

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Bir sonraki komut işleyicisi (komutu geçtiğiniz), metin görünümü, komut işleyicisağlayıcısı (çeşitli hizmetlere erişim sağlayan) ve tamamlama oturumu için özel alanlar ekleyin:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Metin görünümünü ve sağlayıcı alanlarını ayarlayan ve komutu komut zincirine ekleyen bir oluşturucu ekleyin:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Komutu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> birlikte geçirerek yöntemi uygulayın:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Yöntemi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> uygulayın. Bu yöntem bir tuş vuruşu aldığında, şu şeylerden birini yapmalıdır:

   - Karakterin arabelleğe yazılmasına izin verin ve ardından tamamlamayı tetikleyin veya filtreleyin. (Yazdırma karakterleri bunu yapar.)

   - Tamamlamayı taahhüt edin, ancak karakterin arabelleğe yazılmasına izin vermez. (Bir tamamlama oturumu görüntülendiğinde Whitespace, **Sekme**ve **Enter** bunu yapın.)

   - Komutun bir sonraki işleyiciye geçmesine izin verin. (Diğer tüm komutlar.)

     Bu yöntem UI görüntülediğinden, otomasyon bağlamında çağrılmadığından emin olmak için arayın: <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A>

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Bu kod, tamamlama oturumunu tetikleyen özel bir yöntemdir:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. Sonraki örnek, <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> olaydan aboneliğini kaldıran özel bir yöntemdir:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Kodu oluşturma ve test edin
 Bu kodu sınamak için CompletionTest çözümlerini oluşturun ve deneme örneğinde çalıştırın.

#### <a name="to-build-and-test-the-completiontest-solution"></a>CompletionTest çözümlerini oluşturmak ve test etmek için

1. Çözümü derleyin.

2. Bu projeyi hata ayıklamada çalıştırdığınızda, Visual Studio'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun ve "ekle" sözcüğü içeren bazı metinler yazın.

4. Önce "a" ve sonra "d" yazdıkça, "ekleme" ve "uyarlama" içeren bir liste görünmelidir. Eklemenin seçildiğine dikkat edin. Başka bir "d" yazdığınızda, liste yalnızca şimdi seçili olan "ek" içermelidir. **Spacebar,** **Tab**veya **Enter** tuşuna basarak "ekleme" işleyebilir veya Esc veya başka bir tuş yazarak listeyi kapatabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Walkthrough: İçerik türünü dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
