---
title: 'İzlenecek yol: SmartTags görüntüleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - smart tags
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
manager: jillfra
ms.openlocfilehash: 116f76324a2150413c0ae6d08bc99e114efcc50e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805577"
---
# <a name="walkthrough-displaying-smarttags"></a>İzlenecek yol: SmartTags görüntüleme
Akıllı Etiketler, hafif bultlerin yararına kullanım dışı bırakılmıştır. Bkz. [Izlenecek yol: ampul önerilerini görüntüleme](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
 Akıllı Etiketler, bir dizi eylemin görüntülenmesini sağlayan metin üzerindeki etiketlerdir. Örneğin, bir Visual Basic veya Visual C# projesinde, değişken adı gibi bir tanımlayıcıyı yeniden adlandırdığınızda bir sözcüğün altında kırmızı bir çizgi görünür. İşaretçiyi alt çizginin üzerine getirdiğinizde, işaretçinin yakınında bir düğme görüntülenir. Düğmeye tıkladığınızda, önerilen bir eylem görüntülenir, örneğin, **ısread, ısread olarak yeniden adlandırın**. Eyleme tıklarsanız, projedeki **ısread** öğesine yapılan tüm başvurular **IsReady**olarak yeniden adlandırılır.  
  
 Akıllı Etiketler, düzenleyicideki IntelliSense uygulamasının bir parçası olsa da, altsınıflama tarafından Akıllı Etiketler uygulayabilir <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> ve sonra <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> arabirimi ve <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> arabirimi uygulayabilirsiniz.  
  
> [!NOTE]
> Diğer tür Etiketler benzer bir şekilde uygulanabilir.  
  
 Aşağıdaki izlenecek yol, geçerli kelimede görüntülenen ve önerilen iki eyleme sahip bir akıllı etiketin nasıl oluşturulacağını gösterir: **büyük harfe Dönüştür** ve **küçük harfe Dönüştür**.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) projesi oluşturma  
  
#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1. Bir düzenleyici sınıflandırıcı projesi oluşturun. Çözümü adlandırın `SmartTagTest` .  
  
2. VSıX bildirim düzenleyicisinde source. Extension. valtmanifest dosyasını açın.  
  
3. **Varlıklar** bölümünün bir `Microsoft.VisualStudio.MefComponent` tür içerdiğinden, **kaynağın** olarak ayarlandığından `A project in current solution` ve **projenin** SmartTagTest.dll olarak ayarlandığından emin olun.  
  
4. Source. Extension. valtmanifest öğesini kaydedin ve kapatın.  
  
5. Aşağıdaki başvuruyu projeye ekleyin ve **CopyLocal** öğesini şu şekilde ayarlayın `false` :  
  
     Microsoft. VisualStudio. Language. IntelliSense  
  
6. Varolan sınıf dosyalarını silin.  
  
## <a name="implementing-a-tagger-for-smart-tags"></a>Akıllı Etiketler için bir Tagger uygulama  
  
#### <a name="to-implement-a-tagger-for-smart-tags"></a>Akıllı Etiketler için bir Tagger uygulamak için  
  
1. Bir sınıf dosyası ekleyin ve adlandırın `TestSmartTag` .  
  
2. Aşağıdaki içeri aktarmaları ekleyin:  
  
     [!code-csharp[VSSDKSmartTagTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#1)]
     [!code-vb[VSSDKSmartTagTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#1)]  
  
3. Öğesinden devralan adlı bir sınıf ekleyin `TestSmartTag` <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> .  
  
     [!code-csharp[VSSDKSmartTagTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#2)]
     [!code-vb[VSSDKSmartTagTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#2)]  
  
4. Temel oluşturucuyu çağıran ve bir <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> sözcüğün ilk karakterinin altında görünmesine neden olacak olan bu sınıf için bir Oluşturucu ekleyin. (Kullanıyorsanız <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> , kelimenin son karakterinin altında kırmızı bir çizgi görünür.)  
  
     [!code-csharp[VSSDKSmartTagTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#3)]
     [!code-vb[VSSDKSmartTagTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#3)]  
  
5. Türünden devralan adlı bir sınıf ekleyin `TestSmartTagger` <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> `TestSmartTag` ve uygular <xref:System.IDisposable> .  
  
     [!code-csharp[VSSDKSmartTagTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#4)]
     [!code-vb[VSSDKSmartTagTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#4)]  
  
6. Aşağıdaki özel alanları Tagger sınıfına ekleyin.  
  
     [!code-csharp[VSSDKSmartTagTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#5)]
     [!code-vb[VSSDKSmartTagTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#5)]  
  
7. Özel alanları ayarlayan ve olaya abone olan bir Oluşturucu ekleyin <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> .  
  
     [!code-csharp[VSSDKSmartTagTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#6)]
     [!code-vb[VSSDKSmartTagTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#6)]  
  
8. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>Etiketi geçerli sözcük için oluşturulacak şekilde uygulayın. (Bu yöntem ayrıca daha sonra açıklanan özel bir yöntemi çağırır `GetSmartTagActions` .)  
  
     [!code-csharp[VSSDKSmartTagTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#7)]
     [!code-vb[VSSDKSmartTagTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#7)]  
  
9. `GetSmartTagActions`Akıllı etiket eylemlerini ayarlamak için bir yöntem ekleyin. Eylemler sonraki adımlarda uygulanır.  
  
     [!code-csharp[VSSDKSmartTagTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#8)]
     [!code-vb[VSSDKSmartTagTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#8)]  
  
10. Olayı bildirin `SmartTagsChanged` .  
  
     [!code-csharp[VSSDKSmartTagTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#9)]
     [!code-vb[VSSDKSmartTagTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#9)]  
  
11. Olayı `OnLayoutChanged` yükseltmek için olay işleyicisini uygulayın `TagsChanged` , bu da çağrılmasına neden olur <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> .  
  
     [!code-csharp[VSSDKSmartTagTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#10)]
     [!code-vb[VSSDKSmartTagTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#10)]  
  
12. <xref:System.IDisposable.Dispose%2A>Olayı, olaydan abone olmak için uygulama <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> .  
  
     [!code-csharp[VSSDKSmartTagTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#11)]
     [!code-vb[VSSDKSmartTagTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#11)]  
  
## <a name="implementing-the-smart-tag-tagger-provider"></a>Akıllı etiket Tagger sağlayıcısını uygulama  
  
#### <a name="to-implement-the-smart-tag-tagger-provider"></a>Akıllı etiket Tagger sağlayıcısını uygulamak için  
  
1. Öğesinden devralan adlı bir sınıf ekleyin `TestSmartTagTaggerProvider` <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> . Bunu bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> önüne = "varsayılan" ve bir ' den dışa aktarın <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> .  
  
     [!code-csharp[VSSDKSmartTagTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#12)]
     [!code-vb[VSSDKSmartTagTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#12)]  
  
2. <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>Özelliği olarak içeri aktarın.  
  
     [!code-csharp[VSSDKSmartTagTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#13)]
     [!code-vb[VSSDKSmartTagTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#13)]  
  
3. Yöntemini uygulayın <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> .  
  
     [!code-csharp[VSSDKSmartTagTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#14)]
     [!code-vb[VSSDKSmartTagTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#14)]  
  
## <a name="implementing-smart-tag-actions"></a>Akıllı etiket eylemlerini uygulama  
  
#### <a name="to-implement-smart-tag-actions"></a>Akıllı etiket eylemlerini uygulamak için  
  
1. İlk adlandırılmış `UpperCaseSmartTagAction` ve ikinci adlı iki sınıf oluşturun `LowerCaseSmartTagAction` . Her iki sınıf de uygular <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction> .  
  
    [!code-csharp[VSSDKSmartTagTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#15)]
    [!code-vb[VSSDKSmartTagTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#15)]  
  
    [!code-csharp[VSSDKSmartTagTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#16)]
    [!code-vb[VSSDKSmartTagTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#16)]  
  
   Her iki sınıf de tek bir çağrı <xref:System.String.ToUpper%2A> ve diğer çağrılar dışında benzer <xref:System.String.ToLower%2A> . Aşağıdaki adımlar yalnızca büyük harfli eylem sınıfını kapsar, ancak her iki sınıfı da uygulamanız gerekir. Büyük harfli eylemi, küçük harfli eylemi uygulamak için bir model olarak uygulama adımlarını kullanın.  
  
2. Özel alanlar kümesi bildirin.  
  
    [!code-csharp[VSSDKSmartTagTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#17)]
    [!code-vb[VSSDKSmartTagTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#17)]  
  
3. Alanları ayarlayan bir Oluşturucu ekleyin.  
  
    [!code-csharp[VSSDKSmartTagTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#18)]
    [!code-vb[VSSDKSmartTagTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#18)]  
  
4. Özellikleri aşağıdaki şekilde uygulayın.  
  
    [!code-csharp[VSSDKSmartTagTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#19)]
    [!code-vb[VSSDKSmartTagTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#19)]  
  
5. <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A>Yayılma alanındaki metni büyük harfli eşdeğerleriyle değiştirerek yöntemini uygulayın.  
  
    [!code-csharp[VSSDKSmartTagTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#20)]
    [!code-vb[VSSDKSmartTagTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#20)]  
  
## <a name="building-and-testing-the-code"></a>Kodu derleme ve test etme  
 Bu kodu test etmek için, SmartTagTest çözümünü derleyin ve deneysel örnekte çalıştırın.  
  
#### <a name="to-build-and-test-the-smarttagtest-solution"></a>SmartTagTest çözümünü derlemek ve test etmek için  
  
1. Çözümü derleyin.  
  
2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği oluşturulur.  
  
3. Bir metin dosyası oluşturun ve metin yazın.  
  
     Metnin ilk sözcüğünün ilk harfinin altında mavi bir çizgi görüntülenmelidir.  
  
4. İşaretçiyi mavi çizginin üzerine getirin.  
  
     İşaretçinin yakınında bir düğme görüntülenmelidir.  
  
5. Düğmeye tıkladığınızda, iki önerilen eylem görüntülenmelidir: **büyük harfe Dönüştür** ve **küçük harfe Dönüştür**. İlk eyleme tıklarsanız, geçerli sözcükteki tüm metinlerin büyük harfe dönüştürülmesi gerekir. İkinci eyleme tıklarsanız, tüm metinlerin küçük harfe dönüştürülmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)