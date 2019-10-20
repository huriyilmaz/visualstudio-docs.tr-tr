---
title: 'İzlenecek yol: deyimin tamamlanmasını görüntüleme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: madskristensen
ms.author: madsk
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 82ce8a1b9cbc79925ff2f4a1c1df9d832bb96f7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632521"
---
# <a name="walkthrough-display-statement-completion"></a>İzlenecek yol: görüntüleme ifadesinin tamamlanması
Tamamlanmasını sağlamak istediğiniz tanımlayıcıları tanımlayarak ve ardından bir tamamlanma oturumu tetikleyerek, dil tabanlı ifade tamamlamayı uygulayabilirsiniz. Bir dil hizmeti bağlamında deyimin tamamlanmasını tanımlayabilir, kendi dosya adı uzantınızı ve içerik türünü tanımlayabilir ve ardından yalnızca bu tür için tamamlamayı görüntüleyebilirsiniz. Ya da, var olan bir içerik türü için tamamlamayı (örneğin, "düz metin") tetikleyebilirsiniz. Bu izlenecek yol, metin dosyalarının içerik türü olan "düz metin" içerik türü için deyimin tamamlanmasının nasıl tetikleneceğini gösterir. "Metin" içerik türü, kod ve XML dosyaları da dahil olmak üzere diğer tüm içerik türlerinin üst öğesi.

 Deyimin tamamlanması genellikle belirli karakterler yazılarak tetiklenir — Örneğin, "Using" gibi bir tanımlayıcının başlangıcını yazarak tetiklenir. Bir seçimi yürütmek için **boşluk çubuğu**, **sekme**veya **ENTER** tuşuna basılarak genellikle kapatılır. Tuş vuruşları (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi) ve <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> arabirimini uygulayan bir işleyici sağlayıcısı için bir komut işleyicisi kullanarak, bir karakter yazarken tetiklenecek IntelliSense özelliklerini uygulayabilirsiniz. Tamamlamaya katılan tanımlayıcıların listesi olan tamamlama kaynağını oluşturmak için <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> arabirimini ve bir tamamlama kaynak sağlayıcısını (<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> arabirimi) uygulayın. Sağlayıcılar Managed Extensibility Framework (MEF) bileşen bölümleridir. Bunlar, kaynak ve denetleyici sınıflarını dışa aktarma ve hizmetleri ve aracıları içeri aktarma işleminden sorumludur — Örneğin, metin arabelleğinde gezinmeyi sağlayan <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> ve tamamlanma oturumunu tetikleyen <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>.

 Bu izlenecek yol, sabit kodlanmış bir tanımlayıcı kümesi için nasıl ifade tamamlanmasının uygulanacağını gösterir. Tam uygulamalarda, dil hizmeti ve dil belgeleri bu içeriği sağlamaktan sorumludur.

## <a name="prerequisites"></a>Prerequisites
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için

1. C# VSIX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **görsel C# /genişletilebilirlik**, sonra **VSIX projesi**' ni seçin.) @No__t_4 çözümü adlandırın.

2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Varolan sınıf dosyalarını silin.

4. Aşağıdaki başvuruları projeye ekleyin ve **CopyLocal** 'in `false` olarak ayarlandığından emin olun:

     Microsoft. VisualStudio. Editor

     Microsoft. VisualStudio. Language. IntelliSense

     Microsoft. VisualStudio. OLE. Interop

     Microsoft. VisualStudio. Shell. 14.0

     Microsoft. VisualStudio. Shell. sabit. 10.0

     Microsoft. VisualStudio. TextManager. Interop

## <a name="implement-the-completion-source"></a>Tamamlanma kaynağını uygulama
 Tamamlanma kaynağı, tanımlayıcı kümesini toplamaktan ve bir Kullanıcı bir tanımlayıcının ilk harfleri gibi bir tamamlama tetikleyicisi yazdığında, içeriğin tamamlanma penceresine eklenmesine sorumludur. Bu örnekte, tanımlayıcılar ve açıklamaları <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> yönteminde sabit kodludur. Çoğu gerçek dünyada kullanımlar için, tamamlama listesini doldurmak üzere belirteçleri almak üzere dilinizin ayrıştırıcısını kullanırsınız.

### <a name="to-implement-the-completion-source"></a>Tamamlanma kaynağını uygulamak için

1. Bir sınıf dosyası ekleyin ve `TestCompletionSource` adlandırın.

2. Bu içeri aktarmaları ekleyin:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. @No__t_0 için sınıf bildirimini değiştirin, böylece <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> uygular:

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Kaynak sağlayıcı, metin arabelleği ve <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> nesnelerinin bir listesi (Tamamlanma oturumunda yer alacak tanımlayıcılara karşılık gelen) için özel alanlar ekleyin:

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Kaynak sağlayıcıyı ve arabelleği ayarlayan bir Oluşturucu ekleyin. @No__t_0 sınıfı sonraki adımlarda tanımlanmıştır:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Bağlamda sağlamak istediğiniz tamamlamaların bulunduğu bir tamamlanma kümesi ekleyerek <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> yöntemini uygulayın. Her tamamlama kümesi, tamamlanmış bir <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> kümesi içerir ve tamamlama penceresinin bir sekmesine karşılık gelir. (Visual Basic projelerinde, tamamlama pencere sekmeleri **ortak** ve **hepsi**olarak adlandırılır.) @No__t_2 yöntemi bir sonraki adımda tanımlanmıştır.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. Aşağıdaki yöntem, imlecin konumundan geçerli sözcüğü bulmak için kullanılır:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. @No__t_0 yöntemini uygulayın:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Tamamlama kaynak sağlayıcısını uygulama
 Tamamlanma kaynak sağlayıcısı, tamamlanma kaynağını örnekleyen MEF bileşeni bölümüdür.

### <a name="to-implement-the-completion-source-provider"></a>Tamamlama kaynak sağlayıcısını uygulamak için

1. @No__t_1 uygulayan `TestCompletionSourceProvider` adlı bir sınıf ekleyin. Bu sınıfı bir "düz metin" <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> ve "test tamamlama" <xref:Microsoft.VisualStudio.Utilities.NameAttribute> bir "ile dışarı aktarın.

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Tamamlanma kaynağında geçerli kelimeyi bulan <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> içeri aktarın.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Tamamlanma kaynağını başlatmak için <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> yöntemini uygulayın.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Tamamlama komut işleyicisi sağlayıcısını uygulama
 Tamamlama komut işleyicisi sağlayıcısı, bir metin görünümü oluşturma olayını dinleyen bir <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> türetilir ve görünümü bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> dönüştürür — bu, komutun Visual Studio Kabuğu komut zincirine bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> eklenmesine olanak sağlar). Bu sınıf bir MEF dışarı aktarması olduğundan, komut işleyicisinin kendisi tarafından istenen Hizmetleri içeri aktarmak için de kullanabilirsiniz.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Tamamlama komut işleyicisi sağlayıcısını uygulamak için

1. @No__t_0 adlı bir dosya ekleyin.

2. Bu yönergeleri kullanarak bunları ekleyin:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. @No__t_1 uygulayan `TestCompletionHandlerProvider` adlı bir sınıf ekleyin. Bu sınıfı bir "belirteç tamamlama işleyicisi" <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, "düz metin" <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> ve <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> ile dışarı aktarın.

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> ve standart Visual Studio Hizmetleri 'ne erişim sağlayan bir <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> dönüştürmeyi sağlayan <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> içeri aktarın.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Komut işleyicisini başlatmak için <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> yöntemini uygulayın.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Tamamlama komut işleyicisini uygulama
 Deyimin tamamlanması tuş vuruşları tarafından tetiklendiğinden, tamamlama oturumunu tetikleyen, işleyecek ve kapatabelirten tuş vuruşlarını almak ve işlemek için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimini uygulamalısınız.

#### <a name="to-implement-the-completion-command-handler"></a>Tamamlama komut işleyicisini uygulamak için

1. @No__t_1 uygulayan `TestCompletionCommandHandler` adlı bir sınıf ekleyin:

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Sonraki komut işleyicisine (komutunu geçirdiğiniz), metin görünümüne, komut işleyici sağlayıcısına (çeşitli hizmetlere erişim sağlayan) ve bir tamamlanma oturumuna yönelik özel alanlar ekleyin:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Metin görünümü ve sağlayıcı alanlarını ayarlayan bir Oluşturucu ekleyin ve komutu komut zincirine ekler:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Komutu şu şekilde geçirerek <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemini uygulayın:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. @No__t_0 yöntemini uygulayın. Bu yöntem bir tuş vuruşu aldığında, aşağıdakilerden birini yapması gerekir:

   - Karakterin arabelleğe yazılmasına izin verin ve ardından tetikleme veya filtre tamamlamayı izleyin. (Yazdırma karakterleri bunu yapın.)

   - Tamamlamayı işleyin, ancak karakterin arabelleğe yazılmasına izin vermeyin. (Boşluk, **sekme**ve **ENTER** , bir tamamlama oturumu görüntülenirken bunu yapın.)

   - Komutun bir sonraki işleyiciye geçirilmesine izin verin. (Diğer tüm komutlar.)

     Bu yöntem Kullanıcı arabirimini görüntüleyebilir, çünkü bir Otomasyon bağlamında çağrılmadığından emin olmak için <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> çağırın:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Bu kod, tamamlanma oturumunu tetikleyen özel bir yöntemdir:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. Sonraki örnek, <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> olayından abone olmayan bir özel yöntemdir:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin
 Bu kodu test etmek için, CompletionTest çözümünü derleyin ve deneysel örnekte çalıştırın.

#### <a name="to-build-and-test-the-completiontest-solution"></a>CompletionTest çözümünü derlemek ve test etmek için

1. Çözümü oluşturun.

2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun ve "Ekle" sözcüğünü içeren bir metin yazın.

4. İlk "a" ve ardından "d" yazdığınızda, "ekleme" ve "uyarlama" içeren bir liste görünmelidir. Ek olarak seçili olduğuna dikkat edin. Başka bir "d" yazdığınızda, liste yalnızca seçili olan "ek" i içermelidir. **Ara çubuğu**, **sekme**veya **ENTER** tuşuna basarak veya ESC ya da başka bir anahtar yazarak listeyi kapatabilmeniz için "ekleme" gerçekleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: bir içerik türünü bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
