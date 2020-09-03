---
title: 'İzlenecek yol: kod parçacıklarını uygulama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb720589bc9bc31b7cf2a04b05559cb9c9d46961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201990"
---
# <a name="walkthrough-implementing-code-snippets"></a>İzlenecek Yol: Kod Parçacıkları Uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod parçacıkları oluşturabilir ve bunları bir düzenleyici uzantısına ekleyerek uzantı kullanıcılarının bunları kendi koduna ekleyebilmesini sağlayabilirsiniz.  
  
 Kod parçacığı, bir kod parçası veya bir dosyaya dahil edilebilir başka bir metindir. Belirli programlama dilleri için kaydedilmiş tüm kod parçacıklarını görüntülemek için, **Araçlar** menüsünde **kod parçacığı Yöneticisi**' ne tıklayın. Bir dosyaya kod parçacığı eklemek için, kod parçacığını istediğiniz yere sağ tıklayın, **kod parçacığı** veya **çevreleme**Ekle ' ye tıklayın, istediğiniz kod parçacığını bulun ve ardından çift tıklayın. Kod parçacığının ilgili bölümlerini değiştirmek için sekme veya SHIFT + TAB tuşlarına basın ve ardından kabul etmek için ENTER veya ESC tuşuna basın. Daha fazla bilgi için bkz. [kod parçacıkları](../ide/code-snippets.md).  
  
 Kod parçacığı,. kod parçacığı dosya adı uzantısına sahip bir XML dosyasında bulunur. Bir kod parçacığı, kullanıcının onları bulabileceği ve değiştirebilmeleri için kod parçacığı eklendikten sonra vurgulanan alanları içerebilir. Kod parçacığı oluşturma dosyası aynı zamanda **kod parçacığı Yöneticisi** için bilgi sağlar, böylece kod parçacığı adı doğru kategoride de görüntülenebilir. Kod parçacığı şeması hakkında daha fazla bilgi için bkz. [kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md).  
  
 Bu izlenecek yol, şu görevleri nasıl gerçekleştireceğinizi öğretir:  
  
1. Belirli bir dil için kod parçacıkları oluşturun ve kaydedin.  
  
2. Bir kısayol menüsüne **kod parçacığı Ekle** komutunu ekleyin.  
  
3. Kod parçacığı genişletmeyi Uygula.  
  
   Bu izlenecek yol, [Izlenecek yol: Using Ifadesinin tamamlanmasını](../extensibility/walkthrough-displaying-statement-completion.md)temel alır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-and-registering-code-snippets"></a>Kod parçacıkları oluşturma ve kaydetme  
 Genellikle, kod parçacıkları kayıtlı bir dil hizmeti ile ilişkilendirilir. Ancak, <xref:Microsoft.VisualStudio.Package.LanguageService> kod parçacıklarını kaydetmek için bir uygulamanız gerekmez. Bunun yerine, kod parçacığı dizin dosyasında bir GUID belirtmeniz ve ardından projenize eklediğiniz GUID 'yi kullanmanız yeterlidir <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> .  
  
 Aşağıdaki adımlarda, kod parçacıklarının nasıl oluşturulacağı ve belirli bir GUID ile nasıl ilişkilendirileceğini gösterilmektedir.  
  
1. Aşağıdaki dizin yapısını oluşturun:  
  
    **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
    Burada *% InstallDir%* , Visual Studio yükleme klasörüdür. (Bu yol genellikle kod parçacıklarını yüklemek için kullanılsa da, herhangi bir yol belirtebilirsiniz.)  
  
2. \ 1033 \ klasöründe bir. xml dosyası oluşturun ve **TestSnippets.xml**adlandırın. (Bu ad genellikle bir kod parçacığı Dizin dosyası için kullanılsa da, bir. xml dosya adı uzantısına sahip olduğu sürece herhangi bir ad belirtebilirsiniz.) Aşağıdaki metni ekleyin ve ardından yer tutucu GUID 'INI silin ve kendinizinkini ekleyin.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8" ?>  
   <SnippetCollection>  
       <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">  
           <SnippetDir>  
               <OnOff>On</OnOff>  
               <Installed>true</Installed>  
               <Locale>1033</Locale>  
               <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>  
               <LocalizedName>Snippets</LocalizedName>  
           </SnippetDir>  
       </Language>  
   </SnippetCollection>  
   ```  
  
3. Kod parçacığı klasöründe bir dosya oluşturun, **Test** `.snippet` edin ve ardından aşağıdaki metni ekleyin:  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8" ?>  
   <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
       <CodeSnippet Format="1.0.0">  
           <Header>  
               <Title>Test replacement fields</Title>  
               <Shortcut>test</Shortcut>  
               <Description>Code snippet for testing replacement fields</Description>  
               <Author>MSIT</Author>  
               <SnippetTypes>  
                   <SnippetType>Expansion</SnippetType>  
               </SnippetTypes>  
           </Header>  
           <Snippet>  
               <Declarations>  
                   <Literal>  
                     <ID>param1</ID>  
                       <ToolTip>First field</ToolTip>  
                       <Default>first</Default>  
                   </Literal>  
                   <Literal>  
                       <ID>param2</ID>  
                       <ToolTip>Second field</ToolTip>  
                       <Default>second</Default>  
                   </Literal>  
               </Declarations>  
               <References>  
                  <Reference>  
                      <Assembly>System.Windows.Forms.dll</Assembly>  
                  </Reference>  
               </References>  
               <Code Language="TestSnippets">  
                   <![CDATA[MessageBox.Show("$param1$");  
        MessageBox.Show("$param2$");]]>  
               </Code>    
           </Snippet>  
       </CodeSnippet>  
   </CodeSnippets>  
   ```  
  
   Aşağıdaki adımlarda kod parçacıklarının nasıl kaydedileceği gösterilmektedir.  
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>Belirli bir GUID için kod parçacıklarını kaydetmek için  
  
1. **CompletionTest** projesini açın. Bu projenin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [Izlenecek yol: Using deyimin tamamlanmasını görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2. Projede, aşağıdaki derlemelere başvurular ekleyin:  
  
    - Microsoft. VisualStudio. TextManager. Interop  
  
    - Microsoft. VisualStudio. TextManager. Interop. 8.0  
  
    - Microsoft. MSXML  
  
3. Projesinde, kaynak. Extension. valtmanifest dosyasını açın.  
  
4. **Varlıklar** sekmesinin **VSPackage** içerik türünü içerdiğinden ve bu **projenin** projenin adına ayarlandığından emin olun.  
  
5. CompletionTest projesini seçin Özellikler penceresi set **Generate pkgdef dosyasını** **true**olarak ayarlayın. Projeyi kaydedin.  
  
6. Projeye statik bir `SnippetUtilities` sınıf ekleyin.  
  
     [!code-csharp[VSSDKCompletionTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#22)]
     [!code-vb[VSSDKCompletionTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#22)]  
  
7. SnippetUtilities sınıfında bir GUID tanımlayın ve SnippetsIndex.xml dosyasında kullandığınız değeri verin.  
  
     [!code-csharp[VSSDKCompletionTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#23)]
     [!code-vb[VSSDKCompletionTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#23)]  
  
8. <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> `TestCompletionHandler` Sınıfını sınıfına ekleyin. Bu öznitelik, projedeki herhangi bir genel veya iç (statik olmayan) sınıfa eklenebilir. ( `using` Microsoft. VisualStudio. Shell ad alanı için bir ifade eklemeniz gerekebilir.)  
  
     [!code-csharp[VSSDKCompletionTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#24)]
     [!code-vb[VSSDKCompletionTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#24)]  
  
9. Projeyi derleyin ve çalıştırın. Projeyi çalıştırdığınızda, Visual Studio 'nun deneysel örneğinde, yeni kaydettiğiniz kod parçacığı, **Test parçacıkları** dili altındaki **kod parçacıkları yöneticisinde** görüntülenmelidir.  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>Kısayol menüsüne kod parçacığı Ekle komutu ekleme  
 **Kod parçacığı Ekle** komutu, bir metin dosyasının kısayol menüsüne dahil değildir. Bu nedenle, komutunu etkinleştirmeniz gerekir.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Kısayol menüsüne kod parçacığı Ekle komutu eklemek için  
  
1. `TestCompletionCommandHandler`Sınıf dosyasını açın.  
  
     Bu sınıf uyguladığından <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , yönteminde **kod parçacığı Ekle** komutunu etkinleştirebilirsiniz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> . Komutu etkinleştirmeden önce, **kod parçacığı Ekle** komutuna tıklandığında bu yöntemin bir Otomasyon işlevi içinde çağrılmadığından emin olun, kod parçacığı seçici Kullanıcı ARABIRIMINI (UI) görüntüler.  
  
     [!code-csharp[VSSDKCompletionTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#25)]
     [!code-vb[VSSDKCompletionTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#25)]  
  
2. Projeyi derleyin ve çalıştırın. Deneysel örnekte,. zzz dosya adı uzantısına sahip bir dosya açın ve ardından içinde herhangi bir yere sağ tıklayın. **Kod parçacığı Ekle** komutu, kısayol menüsünde görünmelidir.  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>Kod parçacığı seçici Kullanıcı arabiriminde kod parçacığı genişletmeyi uygulama  
 Bu bölümde, kısayol menüsünde kod **parçacığı Ekle** tıklandığında Parçacık Seçici Kullanıcı arabiriminin görüntülenmesi için kod parçacığı genişletmesinin nasıl uygulanacağı gösterilmektedir. Bir Kullanıcı kod parçacığı kısayolunu yazdığında ve sonra SEKME tuşuna bastığında bir kod parçacığı de genişletilir.  
  
 Kod parçacığı seçici Kullanıcı arabirimini göstermek ve gezinti ve ekleme sonrası kod parçacığı kabulünü etkinleştirmek için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemini kullanın. Ekleme yöntemi tarafından işlenir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> .  
  
 Kod parçacığı genişletmesinin uygulanması eski arabirimleri kullanır <xref:Microsoft.VisualStudio.TextManager.Interop> . Geçerli düzenleyici sınıflarından eski koda çevirinizde, eski arabirimlerin bir metin arabelleğindeki konumları belirtmek için satır numaralarının ve sütun sayılarının bir bileşimini kullanmasını unutmayın, ancak geçerli sınıflar bir dizin kullanır. Bu nedenle, bir arabellekte her biri on karakter (artı 1 karakter olarak sayan bir yeni satır) varsa, üçüncü satırdaki dördüncü karakter geçerli uygulamada 27 konumunda, ancak 2. satır, eski uygulamada 3. konumda yer alır.  
  
#### <a name="to-implement-snippet-expansion"></a>Kod parçacığı genişletmeyi uygulamak için  
  
1. Sınıfını içeren dosyaya `TestCompletionCommandHandler` aşağıdaki `using` deyimleri ekleyin.  
  
     [!code-csharp[VSSDKCompletionTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#26)]
     [!code-vb[VSSDKCompletionTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#26)]  
  
2. `TestCompletionCommandHandler`Sınıfın arabirimini uygulamasını sağlayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> .  
  
     [!code-csharp[VSSDKCompletionTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#27)]
     [!code-vb[VSSDKCompletionTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#27)]  
  
3. Sınıfında, `TestCompletionCommandHandlerProvider` öğesini içe aktarın <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .  
  
     [!code-csharp[VSSDKCompletionTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#28)]
     [!code-vb[VSSDKCompletionTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#28)]  
  
4. Kod genişletme arabirimleri ve için bazı özel alanlar ekleyin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
     [!code-csharp[VSSDKCompletionTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#29)]
     [!code-vb[VSSDKCompletionTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#29)]  
  
5. `TestCompletionCommandHandler`Sınıfının oluşturucusunda aşağıdaki alanları ayarlayın.  
  
     [!code-csharp[VSSDKCompletionTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#30)]
     [!code-vb[VSSDKCompletionTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#30)]  
  
6. Kullanıcı **kod parçacığı Ekle** komutuna tıkladığında kod parçacığı seçicisini göstermek için aşağıdaki kodu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemine ekleyin. (Bu açıklamayı daha okunabilir hale getirmek için, deyimin tamamlanması için kullanılan exec () kodu gösterilmez; bunun yerine, kod blokları var olan yönteme eklenir.) Bir karakteri denetleyen koddan sonra aşağıdaki kod bloğunu ekleyin.  
  
     [!code-csharp[VSSDKCompletionTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#31)]
     [!code-vb[VSSDKCompletionTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#31)]  
  
7. Bir kod parçacığında gezinilebilirler alanları varsa, genişletme açık olarak kabul edilene kadar genişletme oturumu açık tutulur; kod parçacığında alan yoksa, oturum kapatılır ve `null` yöntemi tarafından olarak döndürülür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> . <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>Yönteminde, önceki adımda eklediğiniz kod parçacığı seçicisinin Kullanıcı arabirimi kodundan sonra, kod parçacığı gezintisini işlemek için aşağıdaki kodu ekleyin (Kullanıcı sekme veya kod parçacığı eklendikten sonra SHIFT + TAB tuşlarına bastığında).  
  
     [!code-csharp[VSSDKCompletionTest#32](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#32)]
     [!code-vb[VSSDKCompletionTest#32](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#32)]  
  
8. Kullanıcı ilgili kısayolu yazdığında ve sonra SEKME tuşuna bastığında kod parçacığını eklemek için yöntemine kod ekleyin <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> . Parçacığı ekleyen özel yöntem sonraki bir adımda gösterilir. Önceki adımda eklediğiniz gezinti kodundan sonra aşağıdaki kodu ekleyin.  
  
     [!code-csharp[VSSDKCompletionTest#33](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#33)]
     [!code-vb[VSSDKCompletionTest#33](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#33)]  
  
9. Arabirimin yöntemlerini uygulayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> . Bu uygulamada, ilgilendiğiniz tek Yöntemler ve ' dir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . Diğer yöntemler yalnızca döndürmelidir <xref:Microsoft.VisualStudio.VSConstants.S_OK> .  
  
     [!code-csharp[VSSDKCompletionTest#34](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#34)]
     [!code-vb[VSSDKCompletionTest#34](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#34)]  
  
10. Yöntemini uygulayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . Aslında genişletmeleri ekleyen yardımcı yöntem sonraki bir adımda ele alınacaktır. , <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> ' Den alabileceğiniz satır ve sütun bilgilerini sağlar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
     [!code-csharp[VSSDKCompletionTest#35](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#35)]
     [!code-vb[VSSDKCompletionTest#35](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#35)]  
  
11. Aşağıdaki özel yöntem, kısayolu ya da başlık ve yol üzerine bağlı olarak bir kod parçacığı ekler. Ardından, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> kod parçacığı ile yöntemini çağırır.  
  
     [!code-csharp[VSSDKCompletionTest#36](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#36)]
     [!code-vb[VSSDKCompletionTest#36](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#36)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>Kod parçacığı genişletmeyi derleme ve test etme  
 Kod parçacığının genişletmesinin projenizde çalışıp çalışmadığını test edebilirsiniz.  
  
1. Çözümü derleyin. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği oluşturulur.  
  
2. Bir metin dosyası açın ve metin yazın.  
  
3. Metinde bir yere sağ tıklayın ve **kod parçacığı Ekle**' ye tıklayın.  
  
4. Kod parçacığı seçici Kullanıcı arabirimi, **Test değiştirme alanlarını**belirten bir açılır pencere ile görüntülenmelidir. Açılır pencerede çift tıklayın.  
  
     Aşağıdaki kod parçacığı eklenmelidir.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     ENTER veya ESC tuşuna basmayın.  
  
5. "First" ve "Second" arasında geçiş yapmak için sekme ve SHIFT + TAB tuşlarına basın.  
  
6. ENTER veya ESC tuşuna basarak ekleme işlemini kabul edin.  
  
7. Metnin farklı bir bölümünde "test" yazın ve ardından SEKME tuşuna basın. "Test" kod parçacığı kısayolu olduğundan, kod parçacığı yeniden eklenmelidir.  
  
## <a name="next-steps"></a>Sonraki Adımlar
