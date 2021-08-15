---
title: 'İzlenecek yol: kod parçacıklarını uygulama | Microsoft Docs'
description: Kod parçacıkları oluşturabilir ve bunları bir düzenleyici uzantısına dahil edebilirsiniz. Bu yönergeyi kullanarak kod parçacıkları oluşturmayı/kaydetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 106339c932b0339542fd184675448b8ec8354bf0618fbddc7e351ab11763a289
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121234765"
---
# <a name="walkthrough-implement-code-snippets"></a>İzlenecek yol: kod parçacıklarını uygulama
Kod parçacıkları oluşturabilir ve bunları bir düzenleyici uzantısına ekleyerek uzantı kullanıcılarının bunları kendi koduna ekleyebilmesini sağlayabilirsiniz.

 Kod parçacığı, bir kod parçası veya bir dosyaya dahil edilebilir başka bir metindir. Belirli programlama dilleri için kaydedilmiş tüm kod parçacıklarını görüntülemek için, **Araçlar** menüsünde **kod parçacığı Yöneticisi**' ne tıklayın. Bir dosyaya kod parçacığı eklemek için, kod parçacığını istediğiniz yere sağ tıklayın, kod parçacığı Ekle ' ye tıklayın veya **Ile çevreleyin**, istediğiniz kod parçacığını bulun ve ardından çift tıklayın. Kod   + parçacığının ilgili bölümlerini değiştirmek için Tab veya SHIFT **Tab** tuşlarına basın ve ardından kabul etmek için **ENTER** veya **ESC** tuşuna basın. Daha fazla bilgi için bkz. [kod parçacıkları](../ide/code-snippets.md).

 Kod parçacığı,. parçacığının * dosya adı uzantısına sahip bir XML dosyasında bulunur. Bir kod parçacığı, kullanıcının onları bulabileceği ve değiştirebilmeleri için kod parçacığı eklendikten sonra vurgulanan alanları içerebilir. Kod parçacığı oluşturma dosyası aynı zamanda **kod parçacığı Yöneticisi** için bilgi sağlar, böylece kod parçacığı adı doğru kategoride de görüntülenebilir. Kod parçacığı şeması hakkında daha fazla bilgi için bkz. [kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md).

 Bu izlenecek yol, şu görevleri nasıl gerçekleştireceğinizi öğretir:

1. Belirli bir dil için kod parçacıkları oluşturun ve kaydedin.

2. Bir kısayol menüsüne **kod parçacığı Ekle** komutunu ekleyin.

3. Kod parçacığı genişletmeyi Uygula.

   Bu izlenecek yol, [Izlenecek yol: görüntüleme ifadesinin tamamlanmasını](../extensibility/walkthrough-displaying-statement-completion.md)temel alır.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulum 'da isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Kod parçacıkları oluşturma ve kaydetme
 Genellikle, kod parçacıkları kayıtlı bir dil hizmeti ile ilişkilendirilir. Ancak, <xref:Microsoft.VisualStudio.Package.LanguageService> kod parçacıklarını kaydetmek için bir uygulamanız gerekmez. Bunun yerine, kod parçacığı dizin dosyasında bir GUID belirtmeniz ve ardından projenize eklediğiniz GUID 'yi kullanmanız yeterlidir <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> .

 Aşağıdaki adımlarda, kod parçacıklarının nasıl oluşturulacağı ve belirli bir GUID ile nasıl ilişkilendirileceğini gösterilmektedir.

1. Aşağıdaki dizin yapısını oluşturun:

    **%InstallDir%\TestSnippets\Snippets\1033\\**

    burada *% ınstalldir%* Visual Studio yükleme klasörüdür. (Bu yol genellikle kod parçacıklarını yüklemek için kullanılsa da, herhangi bir yol belirtebilirsiniz.)

2. \ 1033 \ klasöründe bir *.xml* dosyası oluşturun ve **TestSnippets.xml** adlandırın. (Bu ad genellikle bir kod parçacığı Dizin dosyası için kullanılsa da, *.xml* dosya adı uzantısına sahip olduğu sürece herhangi bir ad belirtebilirsiniz.) Aşağıdaki metni ekleyin ve ardından yer tutucu GUID 'INI silin ve kendinizinkini ekleyin.

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

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Belirli bir GUID için kod parçacıklarını kaydetmek için

1. **CompletionTest** projesini açın. Bu projenin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [Izlenecek yol: görüntüleme ifadesinin tamamlanması](../extensibility/walkthrough-displaying-statement-completion.md).

2. Projede, aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft. VisualStudio. TextManager. Interop

    - Microsoft. VisualStudio. TextManager. Interop. 8.0

    - Microsoft. MSXML

3. Projesinde, **kaynak. Extension. valtmanifest** dosyasını açın.

4. **varlıklar** sekmesinin **vspackage** içerik türünü içerdiğinden ve **Project** projenin adına ayarlandığından emin olun.

5. CompletionTest projesini seçin Özellikler penceresi set **Generate pkgdef dosyasını** **true** olarak ayarlayın. Projeyi kaydedin.

6. Projeye statik bir `SnippetUtilities` sınıf ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet22":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet22":::

7. SnippetUtilities sınıfında bir GUID tanımlayın ve *SnippetsIndex.xml* dosyasında kullandığınız değeri verin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet23":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet23":::

8. <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> `TestCompletionHandler` Sınıfını sınıfına ekleyin. Bu öznitelik, projedeki herhangi bir genel veya iç (statik olmayan) sınıfa eklenebilir. ( `using` Microsoft. VisualStudio. Shell ad alanı için bir yönerge eklemeniz gerekebilir.)

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet24":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet24":::

9. Projeyi derleyin ve çalıştırın. proje çalıştırıldığında başlayan Visual Studio deneysel örneğinde, az önce kaydettiğiniz kod parçacığı, **test parçacıkları** dili altındaki **kod parçacıkları yöneticisinde** görüntülenmelidir.

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Kısayol menüsüne kod parçacığı Ekle komutunu ekleyin
 **Kod parçacığı Ekle** komutu, bir metin dosyasının kısayol menüsüne dahil değildir. Bu nedenle, komutunu etkinleştirmeniz gerekir.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Kısayol menüsüne kod parçacığı Ekle komutu eklemek için

1. `TestCompletionCommandHandler`Sınıf dosyasını açın.

     Bu sınıf uyguladığından <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , yönteminde **kod parçacığı Ekle** komutunu etkinleştirebilirsiniz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> . Komutu etkinleştirmeden önce, **kod parçacığı Ekle** komutuna tıklandığında bu yöntemin bir Otomasyon işlevi içinde çağrılmadığından emin olun, kod parçacığı seçici Kullanıcı ARABIRIMINI (UI) görüntüler.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet25":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet25":::

2. Projeyi derleyin ve çalıştırın. Deneysel örnekte, *. zzz* dosya adı uzantısına sahip bir dosya açın ve ardından içinde herhangi bir yere sağ tıklayın. **Kod parçacığı Ekle** komutu, kısayol menüsünde görünmelidir.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Kod parçacığı seçici Kullanıcı arabiriminde kod parçacığı genişletmeyi Uygula
 Bu bölümde, kısayol menüsünde kod **parçacığı Ekle** tıklandığında Parçacık Seçici Kullanıcı arabiriminin görüntülenmesi için kod parçacığı genişletmesinin nasıl uygulanacağı gösterilmektedir. Bir Kullanıcı kod parçacığı kısayolunu yazdığında ve sonra **sekme** tuşuna bastığında bir kod parçacığı de genişletilir.

 Kod parçacığı seçici Kullanıcı arabirimini göstermek ve gezinti ve ekleme sonrası kod parçacığı kabulünü etkinleştirmek için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemini kullanın. Ekleme yöntemi tarafından işlenir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> .

 Kod parçacığı genişletmesinin uygulanması eski arabirimleri kullanır <xref:Microsoft.VisualStudio.TextManager.Interop> . Geçerli düzenleyici sınıflarından eski koda çevirinizde, eski arabirimlerin bir metin arabelleğindeki konumları belirtmek için satır numaralarının ve sütun sayılarının bir bileşimini kullanmasını unutmayın, ancak geçerli sınıflar bir dizin kullanır. Bu nedenle, bir arabellekte her biri 10 karakter (artı bir karakter olarak sayan bir yeni satır) varsa, üçüncü satırdaki dördüncü karakter geçerli uygulamada 27 konumunda, ancak 2. satır, eski uygulamada 3. konumda yer alır.

#### <a name="to-implement-snippet-expansion"></a>Kod parçacığı genişletmeyi uygulamak için

1. Sınıfını içeren dosyaya `TestCompletionCommandHandler` aşağıdaki `using` yönergeleri ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet26":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet26":::

2. `TestCompletionCommandHandler`Sınıfın arabirimini uygulamasını sağlayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet27":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet27":::

3. Sınıfında, `TestCompletionCommandHandlerProvider` öğesini içe aktarın <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet28":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet28":::

4. Kod genişletme arabirimleri ve için bazı özel alanlar ekleyin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet29":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet29":::

5. `TestCompletionCommandHandler`Sınıfının oluşturucusunda aşağıdaki alanları ayarlayın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet30":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet30":::

6. Kullanıcı **kod parçacığı Ekle** komutuna tıkladığında kod parçacığı seçicisini göstermek için aşağıdaki kodu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemine ekleyin. (Bu açıklamayı daha okunabilir hale getirmek için, `Exec()` ifade tamamlama için kullanılan kod gösterilmez; bunun yerine, kod blokları var olan yönteme eklenir.) Bir karakteri denetleyen koddan sonra aşağıdaki kod bloğunu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet31":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet31":::

7. Bir kod parçacığında gezinilebilirler alanları varsa, genişletme açık olarak kabul edilene kadar genişletme oturumu açık tutulur; kod parçacığında alan yoksa, oturum kapatılır ve `null` yöntemi tarafından olarak döndürülür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> . <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>Yönteminde, önceki adımda eklediğiniz kod parçacığı Seçicisi Kullanıcı arabirimi kodundan sonra, kod parçacığı gezintisini işlemek için aşağıdaki kodu ekleyin (Kullanıcı, kod parçacığı eklendikten sonra **sekmeye** veya **SHIFT** + **sekmesine** bastığında).

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet32":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet32":::

8. Kullanıcı ilgili kısayolu yazdığında ve sonra **sekme** tuşuna bastığında kod parçacığını eklemek için yöntemine kod ekleyin <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> . Parçacığı ekleyen özel yöntem sonraki bir adımda gösterilir. Önceki adımda eklediğiniz gezinti kodundan sonra aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet33":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet33":::

9. Arabirimin yöntemlerini uygulayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> . Bu uygulamada, ilgilendiğiniz tek Yöntemler ve ' dir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . Diğer yöntemler yalnızca döndürmelidir <xref:Microsoft.VisualStudio.VSConstants.S_OK> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet34":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet34":::

10. Yöntemini uygulayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . Aslında genişletmeleri ekleyen yardımcı yöntemi sonraki bir adımda ele alınmıştır. , <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> ' Den alabileceğiniz satır ve sütun bilgilerini sağlar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet35":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet35":::

11. Aşağıdaki özel yöntem, kısayolu ya da başlık ve yol üzerine bağlı olarak bir kod parçacığı ekler. Ardından, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> kod parçacığı ile yöntemini çağırır.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet36":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet36":::

## <a name="build-and-test-code-snippet-expansion"></a>Kod parçacığı genişletmeyi derleme ve test etme
 Kod parçacığının genişletmesinin projenizde çalışıp çalışmadığını test edebilirsiniz.

1. Çözümü derleyin. bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio ikinci bir örneği başlatılır.

2. Bir metin dosyası açın ve metin yazın.

3. Metinde bir yere sağ tıklayın ve **kod parçacığı Ekle**' ye tıklayın.

4. Kod parçacığı seçici Kullanıcı arabirimi, **Test değiştirme alanlarını** belirten bir açılır pencere ile görüntülenmelidir. Açılır pencerede çift tıklayın.

     Aşağıdaki kod parçacığı eklenmelidir.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     **ENTER** veya **ESC** tuşuna basmayın.

5. "   + First" ve "Second" arasında geçiş yapmak için Tab ve Shift **Tab** tuşlarına basın.

6. **ENTER** veya **ESC** tuşuna basarak ekleme işlemini kabul edin.

7. Metnin farklı bir bölümünde "test" yazın ve ardından **sekme** tuşuna basın. "Test" kod parçacığı kısayolu olduğundan, kod parçacığı yeniden eklenmelidir.

## <a name="next-steps"></a>Sonraki adımlar
