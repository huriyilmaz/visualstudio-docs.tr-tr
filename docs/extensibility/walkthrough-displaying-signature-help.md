---
title: 'İzlenecek yol: Imza yardımını görüntüleme | Microsoft Docs'
description: Bu yönergeyi kullanarak metin içerik türü için Imza yardımını görüntülemeyi öğrenin. İmza yardımı bir araç ipucunda bir yöntemin imzasını görüntüler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8933822ee5bb63b341ff51296ba2884fef2aeb75
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935917"
---
# <a name="walkthrough-display-signature-help"></a>İzlenecek yol: Imza yardımını görüntüle
İmza yardımı ( *parametre bilgisi* olarak da bilinir), bir Kullanıcı parametre listesi başlangıç karakterini (genellikle bir açılış ayracı) yazdığında bir araç ipucunda bir yöntemin imzasını görüntüler. Bir parametre ve parametre ayırıcısı (genellikle virgül) yazıldığında araç ipucu, sonraki parametreyi kalın olarak göstermek için güncelleştirilir. Aşağıdaki yollarla Imza yardımını tanımlayabilirsiniz: bir dil hizmeti bağlamında kendi dosya adı uzantınızı ve içerik türünü tanımlayabilir ve yalnızca bu tür için Imza yardımını görüntüleyebilir ya da mevcut bir içerik türü için Imza yardımını (örneğin, "metin") görüntüleyin. Bu izlenecek yol, "metin" içerik türü için Imza yardımını görüntülemeyi gösterir.

 İmza yardımı genellikle belirli bir karakter yazılarak tetiklenir, örneğin "(" (parantez açma) ve başka bir karakter yazılarak, örneğin ")" (kapatma parantezi). Bir karakter yazılarak tetiklenen IntelliSense özellikleri, tuş vuruşları ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirim) ve arabirimi uygulayan bir işleyici sağlayıcısı için bir komut işleyicisi kullanılarak uygulanabilir <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Imza yardımına katılan imzaların listesi olan Imza yardım kaynağını oluşturmak için, arabirimi <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> ve arabirimi çalıştıran bir kaynak sağlayıcıyı uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> . Sağlayıcılar Managed Extensibility Framework (MEF) bileşen bölümleridir ve kaynak ve denetleyici sınıflarını dışa aktarıp, hizmet ve aracıları içeri aktarmaktan sorumludur; Örneğin, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> metin arabelleğinde gezinmenizi sağlar ve <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> imza Yardım oturumunu tetikleyen ' dir.

 Bu izlenecek yol, sabit kodlanmış tanımlayıcı kümesi için Imza yardımını ayarlamayı gösterir. Tam uygulamalarda, bu içeriği sağlamaktan dil sorumludur.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

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

## <a name="implement-signature-help-signatures-and-parameters"></a>Imza yardım imzaları ve parametreleri uygulama
 Imza yardım kaynağı, <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> her biri uygulayan parametreleri içeren, uygulayan imzaları temel alır <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . Tam bir uygulamada, bu bilgiler dil belgelerinden elde edilir, ancak bu örnekte imzalar sabit kodludur.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Imzayı uygulamak için yardım imzaları ve parametreleri

1. Bir sınıf dosyası ekleyin ve adlandırın `SignatureHelpSource` .

2. Aşağıdaki içeri aktarmaları ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Uygulayan adlı bir sınıf ekleyin `TestParameter` <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Tüm özellikleri ayarlayan bir Oluşturucu ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Özelliklerini ekleyin <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Uygulayan adlı bir sınıf ekleyin `TestSignature` <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Bazı özel alanlar ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Alanları ayarlayan ve olaya abone olan bir Oluşturucu ekleyin <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Bir `CurrentParameterChanged` olay bildirin. Bu olay, Kullanıcı İmzadaki parametrelerden birini doldurduğunda tetiklenir.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Özelliği, <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> özellik değeri değiştirildiğinde olayı harekete geçirmeyecek şekilde uygulayın `CurrentParameterChanged` .

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Olayı oluşturan bir yöntem ekleyin `CurrentParameterChanged` .

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. İçindeki virgüllerin sayısını İmzadaki virgül sayısıyla karşılaştırarak geçerli parametreyi hesaplayan bir yöntem ekleyin <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> .

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Yöntemini çağıran olay için bir olay işleyicisi ekleyin <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> `ComputeCurrentParameter()` .

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Özelliğini uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> . Bu özellik, <xref:Microsoft.VisualStudio.Text.ITrackingSpan> imzanın uygulandığı arabellekteki metnin aralığına karşılık gelen bir içerir.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Diğer parametreleri uygulayın.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Imza yardım kaynağını uygulama
 Imza yardım kaynağı, bilgi sağladığınız imzalar kümesidir.

#### <a name="to-implement-the-signature-help-source"></a>Imza yardım kaynağını uygulamak için

1. Uygulayan adlı bir sınıf ekleyin `TestSignatureHelpSource` <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Metin arabelleğine bir başvuru ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Metin arabelleğini ve Imza yardım kaynak sağlayıcısını ayarlayan bir Oluşturucu ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Yöntemini uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> . Bu örnekte, imzalar sabit kodludur, ancak tam bir uygulamada, bu bilgileri dil belgelerinden alırsınız.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. Yardımcı yöntemi `CreateSignature()` Yalnızca çizim için verilmiştir.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Yöntemini uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> . Bu örnekte, her birinin iki parametresi bulunan yalnızca iki imzası vardır. Bu nedenle, bu yöntem gerekli değildir. Birden fazla Imza yardım kaynağının kullanılabildiği Fuller uygulamasında bu yöntem, en yüksek öncelikli Imza yardım kaynağının eşleşen bir imza sağlayabileceğine karar vermek için kullanılır. Bu, yöntemi null döndürür ve bir sonraki en yüksek öncelikli kaynağın bir eşleşme sağlaması istenir.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Yöntemi uygulayın `Dispose()` :

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Imza yardım kaynak sağlayıcısını uygulama
 Imza yardım kaynak sağlayıcısı, Managed Extensibility Framework (MEF) bileşeni parçasını dışarı aktarma ve Imza yardım kaynağının örneğini oluşturma konusunda sorumludur.

#### <a name="to-implement-the-signature-help-source-provider"></a>Imza yardım kaynak sağlayıcısını uygulamak için

1. Uygulayan adlı bir sınıf ekleyin `TestSignatureHelpSourceProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> ve bunu bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" ve bir <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before = "default" ile dışarı aktarın.

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Öğesini <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> örnekleyerek uygulayın `TestSignatureHelpSource` .

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Komut işleyicisini uygulama
 İmza yardımı genellikle bir açma parantezi "(" karakteri ile kapatılır ve bir kapatma ayracı ")" karakteriyle tetiklenir. Bu tuş vuruşlarını, bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Imza Yardım oturumunu önce bilinen bir yöntem adından önce gelen bir açma parantezi karakteri aldığında ve bir kapanış ayracı karakteri aldığında oturumu açığa vurarak tetikleyerek işleyebilirsiniz.

#### <a name="to-implement-the-command-handler"></a>Komut işleyicisini uygulamak için

1. Uygulayan adlı bir sınıf ekleyin `TestSignatureHelpCommand` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Bağdaştırıcı için özel alanlar ekleyin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> (komut işleyicisini Komut işleyicilerinin zincirine eklemenize olanak tanır), metin görünümü, Imza yardım Aracısı ve oturum, a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> ve sonraki <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Bu alanları başlatmak ve komut filtresi zincirine komut filtresi eklemek için bir Oluşturucu ekleyin.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>Komut filtresi, bir açma ayracı (bilinen yöntem adlarından birinden sonra karakter) aldığında Imza Yardım oturumunu tetiklemek için yöntemini uygulayın ve oturum halen etkin olduğunda bir kapatma parantezi ")" karakteri aldığında oturumu yoksayın. Her durumda, komut iletilir.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>Yöntemi her zaman komutunu iletmeleri için uygulayın.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Imza yardım komut sağlayıcısını uygulama
 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>Metin görünümü oluşturulduğunda komut işleyicisini oluşturmak için öğesini uygulayarak Imza yardım komutunu sağlayabilirsiniz.

### <a name="to-implement-the-signature-help-command-provider"></a>Imza yardım komut sağlayıcısını uygulamak için

1. Uygulayan adlı bir sınıf ekleyin `TestSignatureHelpController` <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> ve, ve ile dışarı aktarın <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>(Nesnesi için kullanılır <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (geçerli sözcüğü bulmak için kullanılır) ve <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (imza Yardım oturumunu tetiklemek için) öğesini içe aktarın.

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Öğesini <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> örnekleyerek yöntemini uygulayın `TestSignatureCommandHandler` .

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin
 Bu kodu test etmek için, SignatureHelpTest çözümünü derleyin ve deneysel örnekte çalıştırın.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>SignatureHelpTest çözümünü derlemek ve test etmek için

1. Çözümü derleyin.

2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun ve "Ekle" sözcüğünün yanı sıra bir açılış ayracı içeren bir metin yazın.

4. Açma parantezini yazdıktan sonra, yöntemi için iki imzanın listesini görüntüleyen bir araç ipucu görmeniz gerekir `add()` .

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: bir içerik türünü bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
