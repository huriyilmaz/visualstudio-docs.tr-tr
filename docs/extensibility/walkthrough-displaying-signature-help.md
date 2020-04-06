---
title: 'Walkthrough: İmza Yardımı Görüntüleme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f85d7eb3959064468e7583ec0c8a927f3e139daf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697429"
---
# <a name="walkthrough-display-signature-help"></a>Walkthrough: İmza Yardım Görüntüle
İmza Yardımı *(Parametre Bilgisi*olarak da bilinir), bir kullanıcı parametre listesi başlangıç karakterini (genellikle açılış parantezi) yazdığında bir yöntemin imzasını araç ucunda görüntüler. Parametre ve parametre ayırıcı (genellikle virgül) yazılırken, araç ucu bir sonraki parametreyi kalın olarak göstermek üzere güncelleştirilir. İmza Yardımı'nı aşağıdaki yollarla tanımlayabilirsiniz: bir dil hizmeti bağlamında, kendi dosya adı uzantınızı ve içerik türünüzü tanımlayın ve yalnızca bu tür için İmza Yardımı görüntüleyebilir veya varolan bir içerik türü için İmza Yardımı (örneğin, "metin") görüntüleyebilirsiniz. Bu izlenecek yol, "metin" içerik türü için İmza Yardımı'nın nasıl görüntülenebildiğini gösterir.

 İmza Yardımı genellikle belirli bir karakter yazarak tetiklenir, örneğin, "(" (parantez açma) ve başka bir karakter yazarak görevden alınır, örneğin,")" (parantezi kapatma). Bir karakter yazarak tetiklenen IntelliSense özellikleri tuş vuruşları <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> (arabirim) için bir komut işleyicisi ve <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> arabirimi uygulayan bir işleyici sağlayıcısı kullanılarak uygulanabilir. İmza Yardımı'na katılan imzaların listesi olan İmza Yardım kaynağını oluşturmak <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> için <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> arabirimi ve arabirimi çalıştıran bir kaynak sağlayıcısı uygulayın. Sağlayıcılar Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşen parçalarıdır ve kaynak ve denetleyici sınıflarının dışa aktarılmalarından <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>ve örneğin metin arabelleğinde <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>gezinmenizi sağlayan , ve İmza Yardımı oturumunu tetikleyen , hizmet ve aracıları içe aktarmaktan sorumludur.

 Bu izlenecek yol, sabit kodlanmış bir tanımlayıcı kümesi için İmza Yardımı'nın nasıl ayarlanır olduğunu gösterir. Tam uygulamalarda, dil bu içeriği sağlamakla yükümlüdür.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="creating-a-mef-project"></a>MEF projesi oluşturma

#### <a name="to-create-a-mef-project"></a>Bir MEF projesi oluşturmak için

1. Bir C# VSIX projesi oluşturun. (Yeni **Proje** iletişim kutusunda Visual **C# / Genişletilebilirlik,** ardından **VSIX Project'i**seçin.) Çözümü `SignatureHelpTest`adlandırın.

2. Projeye Bir Düzenleyici Sınıflandırıcı öğesi şablonu ekleyin. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Varolan sınıf dosyalarını silin.

4. Projeye aşağıdaki başvuruları ekleyin ve **CopyLocal'ın** aşağıdaki `false`şekilde ayarlandıklarından emin olun:

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.visualstudio.ole

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>İmza Yardım imzalarını ve parametrelerini uygulayın
 İmza Yardım <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>kaynağı, her biri uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>parametreleri içeren imzaları temel adamıştır. Tam bir uygulamada, bu bilgiler dil belgelerinden elde edilir, ancak bu örnekte, imzalar sabit kodlanır.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>İmza Yardımı imzalarını ve parametrelerini uygulamak için

1. Bir sınıf dosyası ekleyin `SignatureHelpSource`ve adlandırın.

2. Aşağıdaki içeri almaları ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. 'yi uygulayan `TestParameter` bir <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>sınıf ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Tüm özellikleri ayarlayan bir oluşturucu ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>' nin özelliklerini ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. 'yi uygulayan `TestSignature` bir <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>sınıf ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Bazı özel alanlar ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Alanları ayarlayan ve <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> etkinliğe abone olan bir oluşturucu ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Bir `CurrentParameterChanged` olay bildirin. Bu olay, kullanıcı imzadaki parametrelerden birini doldurduğunda yükseltilir.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> Özellik değeri değiştirildiğinde `CurrentParameterChanged` olayı yükselten özelliği uygulayın.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. `CurrentParameterChanged` Olayı yükselten bir yöntem ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. İmzadaki virgül sayısıyla virgül <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> sayısını karşılaştırarak geçerli parametreyi hesaplayan bir yöntem ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Yöntemi çağıran <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> olay için bir olay `ComputeCurrentParameter()` işleyicisi ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Özelliği <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> uygulayın. Bu özellik, <xref:Microsoft.VisualStudio.Text.ITrackingSpan> imzanın uygulandığı arabellekteki metnin aralığına karşılık gelen bir özellik tutar.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Diğer parametreleri uygulayın.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>İmza Yardım kaynağını uygulama
 İmza Yardımı kaynağı, bilgi verdiğiniz imzalar kümesidir.

#### <a name="to-implement-the-signature-help-source"></a>İmza Yardım kaynağını uygulamak için

1. 'yi uygulayan `TestSignatureHelpSource` bir <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>sınıf ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Metin arabelleği için bir başvuru ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Metin arabelleği ve İmza Yardım kaynak sağlayıcısını ayarlayan bir oluşturucu ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Yöntemi <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> uygulayın. Bu örnekte, imzalar sabit kodlanmış, ancak tam bir uygulamada bu bilgileri dil belgelerinden alırsınız.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. Yardımcı yöntem `CreateSignature()` sadece illüstrasyon için sağlanır.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Yöntemi <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> uygulayın. Bu örnekte, her biri iki parametreiçeren sadece iki imza vardır. Bu nedenle, bu yöntem gerekli değildir. Birden fazla İmza Yardımı kaynağının bulunduğu daha kapsamlı bir uygulamada, bu yöntem en yüksek öncelikli İmza Yardım kaynağının eşleşen bir imza yı karşılayıp sağlayamayacağına karar vermek için kullanılır. Bu durumda, yöntem null döndürür ve bir sonraki en yüksek öncelikli kaynağın eşleşme sağlaması istenir.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Yöntemi `Dispose()` uygulayın:

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>İmza Yardımı kaynak sağlayıcısını uygulama
 İmza Yardım kaynağı sağlayıcısı, Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşen bölümünün dışa aktarımından ve İmza Yardım kaynağının anlık olarak ayrılmasından sorumludur.

#### <a name="to-implement-the-signature-help-source-provider"></a>İmza Yardım kaynak sağlayıcısını uygulamak için

1. "Metin" `TestSignatureHelpSourceProvider` ve "varsayılan" bir , <xref:Microsoft.VisualStudio.Utilities.NameAttribute>a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , a ve <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> bir ile dışa aktarın adlandırılmış <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>bir sınıf ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Anında <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> `TestSignatureHelpSource`uygulayın.

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Komut işleyicisini uygulama
 İmza Yardımı genellikle açılış parantezi "(" karakteri tarafından tetiklenir ve kapanış parantezi ")" karakteri tarafından kapatılır. Bu tuş vuruşlarını, bilinen <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> bir yöntem adından önce bir açılış parantezi karakteri aldığında bir İmza Yardımı oturumunu tetikleyerek ve kapanış parantezi karakteri aldığında oturumu kapatacak şekilde çalıştırabilirsiniz.

#### <a name="to-implement-the-command-handler"></a>Komut işleyicisini uygulamak için

1. 'yi uygulayan `TestSignatureHelpCommand` bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>sınıf ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Bağdaştırıcı için özel alanlar (komut işleyicisi komut işleyicileri zincirine eklemenize olanak sağlar), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>metin görünümü, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>İmza Yardım aracısı ve oturumu, bir , ve sonraki . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Bu alanları başlatmave komut filtresini komut filtreleri zincirine eklemek için bir oluşturucu ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Komut <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> filtresi bilinen yöntem adlarından birinden sonra bir açılış parantezi "(" karakteri aldığında İmza Yardımı oturumunu tetiklemek ve oturum hala etkinken kapanış parantezi ")" karakterini aldığında oturumu kapatmak için yöntemi uygulayın. Her durumda, komut iletilir.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Yöntemi, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> komutu her zaman iletin.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>İmza Yardımı komut sağlayıcısını uygulama
 Metin görünümü oluşturulduğunda komut işleyicisini anında uygulayarak <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> İmza Yardımı komutunu sağlayabilirsiniz.

### <a name="to-implement-the-signature-help-command-provider"></a>İmza Yardımı komut sağlayıcısını uygulamak için

1. Uygulayan `TestSignatureHelpController` <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> ve dışa aktaran bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute>sınıf <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>ekleyin, , ve <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (Nesne verilen, almak için kullanılan), (geçerli sözcüğü bulmak için <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> kullanılan) ve (İmza Yardımı oturumunu tetiklemek için) içe aktarın. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Yöntemi <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> anında uygulayarak uygulayın. `TestSignatureCommandHandler`

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Kodu Oluştur ve Test Et
 Bu kodu sınamak için SignatureHelpTest çözümlerini oluşturun ve deneme örneğinde çalıştırın.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>SignatureHelpTest çözümlerini oluşturmak ve test etmek için

1. Çözümü derleyin.

2. Bu projeyi hata ayıklamada çalıştırdığınızda, Visual Studio'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun ve "ekle" sözcüğünün yanı sıra açılış parantezini içeren bazı metinler yazın.

4. Açılış parantezini yazdıktan sonra, `add()` yöntem için iki imzanın listesini görüntüleyen bir araç ipucu görmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Walkthrough: İçerik türünü dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
