---
title: 'Walkthrough: Kod Parçacıkları Uygulama | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: ba1b6e0852c1ec1b306938b791eed78e79d211ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697095"
---
# <a name="walkthrough-implement-code-snippets"></a>Walkthrough: Kod parçacıkları uygulama
Uzantıkullanıcılarının bunları kendi kodlarına ekleyebileceği şekilde kod parçacıkları oluşturabilir ve bunları bir düzenleyici uzantısına ekleyebilirsiniz.

 Kod parçacığı, bir dosyaya dahil edilebilen kod veya başka bir metin parçasıdır. Belirli programlama dilleri için kaydedilmiş tüm parçacıkları Görüntülemek **için, Araçlar** menüsünde **Kod Snippet Yöneticisi'ni**tıklatın. Bir dosyaya bir parçacık eklemek için, snippet'i istediğiniz yere sağ tıklatın, Snippet Ekle'yi veya **Surround With'i**tıklatın, istediğiniz parçacığı bulun ve ardından çift tıklatın. Snippet'in ilgili bölümlerini değiştirmek için **Sekme** veya **Kaydırma**+**Sekmesi'ne** basın ve ardından kabul etmek için **Enter** veya **Esc** tuşuna basın. Daha fazla bilgi için [Kod parçacıklarına](../ide/code-snippets.md)bakın.

 Kod snippet .snippet* dosya adı uzantısı olan bir XML dosyasında bulunur. Bir parçacık, kullanıcının bunları bulup değiştirebilmeleri için parçacık takıldıktan sonra vurgulanan alanları içerebilir. Bir parçacık dosyası, **snippet** adını doğru kategoride görüntüleyebilmek için Kod Parçacık Yöneticisi için de bilgi sağlar. Snippet şeması hakkında daha fazla bilgi için [Kod parçacıkları şeması referansına](../ide/code-snippets-schema-reference.md)bakın.

 Bu gözden geçirme, bu görevleri nasıl yerine getirilen öğretir:

1. Belirli bir dil için kod parçacıkları oluşturun ve kaydedin.

2. Ekle **Snippet** komutunu kısayol menüsüne ekleyin.

3. Parçacık genişletme uygulayın.

   Bu gözden geçirme, [Walkthrough: Display deyimi tamamlamaya](../extensibility/walkthrough-displaying-statement-completion.md)dayanır.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-and-register-code-snippets"></a>Kod parçacıkları oluşturma ve kaydetme
 Genellikle, kod parçacıkları kayıtlı bir dil hizmetiyle ilişkilidir. Ancak, kod parçacıklarını kaydetmek <xref:Microsoft.VisualStudio.Package.LanguageService> için bir uygulamanız gerekmez. Bunun yerine, parçacık dizin dosyasında bir GUID belirtmeniz ve <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> ardından projenize eklediğiniz guid'i kullanmanız gereken bir durumdur.

 Aşağıdaki adımlar, kod parçacıklarının nasıl oluşturulup belirli bir GUID ile ilişkilendirilen leri gösterir.

1. Aşağıdaki dizin yapısını oluşturun:

    **%InstallDir%\TestSnippets\Snippets\1033\\**

    *%InstallDir%* Visual Studio yükleme klasörüdür. (Bu yol genellikle kod parçacıklarını yüklemek için kullanılsa da, herhangi bir yol belirtebilirsiniz.)

2. \1033\ klasöründe, bir *.xml* dosyası oluşturun ve **testsnippets.xml**adını. (Bu ad genellikle bir snippet dizin dosyası için kullanılsa da, *.xml* dosya adı uzantısı olduğu sürece herhangi bir ad belirtebilirsiniz.) Aşağıdaki metni ekleyin ve ardından yer tutucu GUID'i silin ve kendi metninizi ekleyin.

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

3. Parçacık klasöründe bir dosya oluşturun, **sınadı**`.snippet`ve ardından aşağıdaki metni ekleyin:

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

   Aşağıdaki adımlar, kod parçacıklarının nasıl kaydedilebildiğini gösterir.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Belirli bir GUID için kod parçacıklarını kaydetmek için

1. **CompletionTest** projesini açın. Bu projenin nasıl oluşturulacığı hakkında daha fazla bilgi için [Walkthrough: Görüntülüşdeyimi](../extensibility/walkthrough-displaying-statement-completion.md)tamamlanmasına bakın.

2. Projede, aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.TextManager.Interop.8.0

    - microsoft.msxml

3. Projede **source.extension.vsixmanifest** dosyasını açın.

4. **Varlıklar** sekmesinin Bir **VsPackage** içerik türü içerdiğinden ve **projenin** projenin adına ayarlı olduğundan emin olun.

5. CompletionTest projesini seçin ve Özellikler penceresinde **Pkgdef Dosyasını** **true'ya getirin.** Projeyi kaydet.

6. Projeye statik `SnippetUtilities` bir sınıf ekleyin.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. SnippetUtilities sınıfında, bir GUID tanımlayın ve *SnippetsIndex.xml* dosyasında kullandığınız değeri verin.

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Sınıfa <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> `TestCompletionHandler` ekleyin. Bu öznitelik, projedeki herhangi bir genel veya iç (statik olmayan) sınıfa eklenebilir. (Microsoft.VisualStudio.Shell `using` ad alanı için bir yönerge eklemeniz gerekebilir.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Projeyi oluşturun ve çalıştırın. Proje çalıştırıldığında başlayan Visual Studio'nun deneysel örneğinde, yeni kaydettiğiniz parçacık **TestSnippets** dili altında **Code Snippets Manager'da** görüntülenmelidir.

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Kısayol menüsüne Ekle Snippet komutunu ekleyin
 **Ekle Snippet** komutu bir metin dosyası için kısayol menüsüne dahil edilmez. Bu nedenle, komutu etkinleştirmeniz gerekir.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Kısayol menüsüne Ekle Snippet komutunu eklemek için

1. Sınıf `TestCompletionCommandHandler` dosyasını açın.

     Bu sınıf <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>uygulandığından, yöntemde Ekle **Snippet** komutunu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> etkinleştirebilirsiniz. Komutu etkinleştirmeden önce, **Insert Snippet** komutu tıklatıldığında parçacık seçici kullanıcı arabirimini (UI) görüntülediği için bu yöntemin bir otomasyon işlevi içinde çağrılmadığını denetleyin.

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Projeyi oluşturun ve çalıştırın. Deneme örneğinde, *.zzz* dosya adı uzantısı olan bir dosyayı açın ve sonra dosyanın herhangi bir yerine sağ tıklayın. Ekle **Snippet** komutu kısayol menüsünde görünmelidir.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Snippet Picker UI'de parçacık genişletme uygulayın
 Bu bölümde, Snippet **Ekle** menüsüne tıklandığında parçacık seçici UI'nin görüntülenmesi için kod snippet genişletmesinin nasıl uygulanacağı gösterilmektedir. Bir kullanıcı kod-snippet kısayolu yazdığında ve sonra **Sekme**tuşuna bastığında bir kod snippet de genişletilir.

 Parçacık seçici UI'yi görüntülemek ve navigasyon ve ekleme sonrası snippet kabuletmesini etkinleştirmek için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi kullanın. Ekleme kendisi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> yöntemi ile işlenir.

 Kod snippet genişletme uygulaması <xref:Microsoft.VisualStudio.TextManager.Interop> eski arabirimleri kullanır. Geçerli düzenleyici sınıflarından eski koda çevirdiğinizde, eski arabirimlerin metin arabelleğindekonumları belirtmek için satır numaraları ve sütun numaraları nın bir birleşimini kullandığını, ancak geçerli sınıfların bir dizin kullandığını unutmayın. Bu nedenle, bir arabellek her biri 10 karakter (artı bir karakter olarak sayar yeni bir satır) üç satır varsa, üçüncü satırda dördüncü karakter geçerli uygulamada 27 konumundadır, ancak satır 2, pozisyon 3 eski uygulamada.

#### <a name="to-implement-snippet-expansion"></a>Parçacık genişletmesini uygulamak için

1. Sınıfı içeren dosyaya `TestCompletionCommandHandler` aşağıdaki `using` yönergeleri ekleyin.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. `TestCompletionCommandHandler` Sınıfın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> arabirimi uygulamasını sağla.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. `TestCompletionCommandHandlerProvider` Sınıfta, 'yi. <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Kod genişletme arabirimleri ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. `TestCompletionCommandHandler` Sınıfın oluşturucusu olarak, aşağıdaki alanları ayarlayın.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Kullanıcı **Ekle Snippet** komutunu tıklattığında parçacık seçiciyi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> görüntülemek için yönteme aşağıdaki kodu ekleyin. (Bu açıklamayı daha okunabilir hale `Exec()`getirmek için, deyim tamamlama için kullanılan kod gösterilmez; bunun yerine varolan yönteme kod blokları eklenir.) Bir karakteri denetleyen koddan sonra aşağıdaki kod bloğunu ekleyin.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Bir snippet'te gezinilebilen alanlar varsa, genişletme oturumu açıkça kabul edilene kadar açık tutulur; parçacıkta alan yoksa, oturum kapatılır ve `null` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> yöntemle döndürülür. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Yöntemde, önceki adımda eklediğiniz snippet picker UI kodundan sonra, parçacık gezintisini işlemek için aşağıdaki kodu ekleyin (kullanıcı snippet eklemeden sonra **Sekme** veya **Shift**+**Tab'a** bastığında).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Kullanıcı ilgili kısayolu yazdığında ve tab tuşuna bastığında kod snippet <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> eklemek **için,** yönteme kod ekleyin. Snippet'i ekleyen özel yöntem daha sonraki bir adımda gösterilir. Önceki adımda eklediğiniz gezinti kodundan sonra aşağıdaki kodu ekleyin.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Arabirimin yöntemlerini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> uygulayın. Bu uygulamada, ilgi sadece yöntemler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>ve . Diğer yöntemler sadece <xref:Microsoft.VisualStudio.VSConstants.S_OK>dönmelidir.

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> uygulayın. Genişletmeleri gerçekten ekleyen yardımcı yöntem daha sonraki bir adımda ele alınmıştır. Satır <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> ve sütun bilgilerini sağlar, hangi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>alabilirsiniz.

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. Aşağıdaki özel yöntem, kısayola veya başlık ve yola dayalı bir kod parçacığı ekler. Daha sonra <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> parçacık ile yöntemi çağırır.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Oluşturma ve test kodu parçacık genişletme
 Snippet genişletmenin projenizde çalışıp çalışmadığını test edebilirsiniz.

1. Çözümü derleyin. Bu projeyi hata ayıklamada çalıştırdığınızda, Visual Studio'nun ikinci bir örneği başlatılır.

2. Bir metin dosyası açın ve bazı metin yazın.

3. Metinde bir yere sağ tıklayın ve ardından **Snippet Ekle'yi**tıklatın.

4. Parçacık toplayıcı UI test **değiştirme alanları**diyor bir pop-up ile görünmelidir. Açılır pencereyi çift tıklatın.

     Aşağıdaki parçacık eklenmelidir.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     **Enter** veya **Esc tuşuna**basmayın.

5. "Birinci" ve "ikinci" arasında geçiş yapmak için **Sekme** ve **Kaydırma**+**Sekmesine** basın.

6. **Enter** veya **Esc**tuşuna basarak eklemeyi kabul edin.

7. Metnin farklı bir bölümünde "test" yazın ve ardından **Sekme tuşuna**basın. "Test" kod-snippet kısayolu olduğundan, parçacık yeniden eklenmelidir.

## <a name="next-steps"></a>Sonraki adımlar
