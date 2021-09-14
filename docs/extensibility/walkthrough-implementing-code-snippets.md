---
title: 'adım adım kılavuz: Kod Parçacıkları | Microsoft Docs'
description: Kod parçacıkları oluşturabilir ve bunları bir düzenleyici uzantısına ekleyebilirsiniz. Bu kılavuzda kod parçacıkları oluşturma/kaydetme hakkında bilgi edinebilirsiniz.
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
ms.openlocfilehash: b2a9bcd6a24edafc139cee4560fc36bfcc1b0a7f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725770"
---
# <a name="walkthrough-implement-code-snippets"></a>Adım adım kılavuz: Kod parçacıklarını uygulama
Kod parçacıkları oluşturabilir ve bunları bir düzenleyici uzantısına ekleyebilirsiniz; böylece uzantı kullanıcıları bunları kendi kodlarına ekleyebilir.

 Kod parçacığı, bir dosyaya dahil ekleyebilirsiniz kod parçası veya başka bir metindir. Belirli programlama dillerinde kayıtlı olan tüm kod parçacıklarını görüntülemek için Araçlar menüsünde **Kod** Parçacığı **Yöneticisi'ne tıklayın.** Bir dosyaya kod parçacığı eklemek için, kod parçacığını istediğiniz yere sağ tıklayın, Kod Parçacığı Ekle'ye tıklayın veya Ile Çevrele'ye **tıklayın,** istediğiniz kod parçacığını bulun ve çift tıklayın. Kod **parçacığının** **ilgili bölümlerini** değiştirmek için Sekme veya Shift Tuşuna basın ve ardından kabul etmek için +  **Enter** veya **Esc** tuşuna basın. Daha fazla bilgi için [bkz. Kod parçacıkları.](../ide/code-snippets.md)

 Kod parçacığı, .snippet* dosya adı uzantısına sahip bir XML dosyasında yer alan bir kod parçacığıdır. Bir kod parçacığı, kod parçacığı eklendikten sonra vurgulanan alanlar içerebilir, böylece kullanıcı bunları bulabilir ve değiştirebilir. Kod parçacığı dosyası, kod parçacığı adını **doğru kategoride** görüntüley için Kod Parçacığı Yöneticisi için de bilgi sağlar. Kod parçacığı şeması hakkında bilgi için [bkz. Kod parçacıkları şema başvurusu.](../ide/code-snippets-schema-reference.md)

 Bu kılavuzda, bu görevlerin nasıl yerine ulaşacağız öğretildi:

1. Belirli bir dil için kod parçacıkları oluşturma ve kaydetme.

2. Kod Parçacığı **Ekle komutunu** bir kısayol menüsüne ekleyin.

3. Kod parçacığı genişletmesi uygulama.

   Bu izlenecek yol, Adım [adım: Görüntüleme deyimi tamamlamayı temel alan bir adımdır.](../extensibility/walkthrough-displaying-statement-completion.md)

## <a name="prerequisites"></a>Önkoşullar
 2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Kurulumda isteğe bağlı bir özellik olarak Visual Studio dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-and-register-code-snippets"></a>Kod parçacıkları oluşturma ve kaydetme
 Kod parçacıkları genellikle kayıtlı bir dil hizmetiyle ilişkilendirilr. Ancak, kod parçacıklarını kaydetmek için <xref:Microsoft.VisualStudio.Package.LanguageService> bir uygulamanız gerekli değildir. Bunun yerine, yalnızca kod parçacığı dizin dosyasında bir GUID belirtin ve ardından projenize <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> eklemekte olduğu GUID'i kullanın.

 Aşağıdaki adımlarda, kod parçacıklarının nasıl oluşturularak belirli bir GUID ile ilişkilendirilerek nasıl ilişkilendiril olduğu açık bir şekilde açık bir şekilde ekleyebilirsiniz.

1. Aşağıdaki dizin yapısını oluşturun:

    **%InstallDir%\TestSnippets\Snippets\1033\\**

    Burada *%InstallDir%* Visual Studio klasörüdür. (Bu yol genellikle kod parçacıklarını yüklemek için kullanılıyor olsa da herhangi bir yol belirtebilirsiniz.)

2. \1033\ klasöründe bir.xmldosyası *oluşturun* ve bu dosyayı **TestSnippets.xml.** (Bu ad genellikle bir kod parçacığı dizin dosyası için kullanılıyor olsa da, dosya adı uzantısına sahip olduğu sürece *.xml* belirtebilirsiniz.) Aşağıdaki metni ekleyin ve ardından yer tutucu GUID'sini silin ve kendi guid'inizi ekleyin.

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

3. Kod parçacığı klasöründe bir dosya oluşturun, **test** olarak adını `.snippet` girin ve ardından aşağıdaki metni ekleyin:

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

   Aşağıdaki adımlarda kod parçacıklarını kaydetme adımları açık bir şekilde açık bir şekilde ekleyebilirsiniz.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Belirli bir GUID için kod parçacıklarını kaydetmek için

1. **CompletionTest projesini** açın. Bu projeyi oluşturma hakkında bilgi için bkz. [Walkthrough: Display statement completion](../extensibility/walkthrough-displaying-statement-completion.md).

2. Projede, aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.TextManager.Interop.8.0

    - microsoft.msxml

3. Projede **source.extension.vsixmanifest dosyasını** açın.

4. Varlıklar sekmesinde  bir **VsPackage** içerik türü olduğundan  ve Project projenin adına ayarlanmış olduğundan emin olun.

5. CompletionTest projesini seçin ve Özellikler penceresi **Pkgdef Dosyası Oluştur seçeneğini true olarak** **ayarlayın.** Projeyi kaydedin.

6. Projeye statik `SnippetUtilities` bir sınıf ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet22":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet22":::

7. SnippetUtilities sınıfında bir GUID tanımlayın ve bu değere bir guid dosyasında *SnippetsIndex.xml* verir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet23":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet23":::

8. sınıfına <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> `TestCompletionHandler` ekleyin. Bu öznitelik, projesinde herhangi bir genel veya iç (statik olmayan) sınıfa eklenebilir. `using`(Microsoft.VisualStudio.Shell ad alanı için bir yönerge eklemeniz gerekir.)

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet24":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet24":::

9. Projeyi derleme ve çalıştırma. Proje çalıştır çalıştır Visual Studio başlayan deneysel Visual Studio örneğinde, az önce kaydettiniz kod parçacığı **TestSnippets** dili altındaki Kod Parçacıkları **Yöneticisi'nde** görüntüleniyor.

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Kod Parçacığı Ekle komutunu kısayol menüsüne ekleyin
 Kod **Parçacığı Ekle** komutu, bir metin dosyasının kısayol menüsüne dahil değildir. Bu nedenle, komutunu etkinleştirmeniz gerekir.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Kod Parçacığı Ekle komutunu kısayol menüsüne eklemek için

1. Sınıf `TestCompletionCommandHandler` dosyasını açın.

     Bu sınıf uygulaması <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> olduğundan, yönteminde **Kod Parçacığı Ekle** komutunu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> etkinleştirebilirsiniz. Komutu etkinleştirmeden önce, Kod Parçacığı Ekle komutuna tıklanmışsa  kod parçacığı seçici kullanıcı arabirimini (UI) görüntüleyene kadar bu yöntemin otomasyon işlevinin içinde çağrılmay içerip çağrılmay olmadığını kontrol edin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet25":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet25":::

2. Projeyi derleme ve çalıştırma. Deneysel örnekte *.zzz* dosya adı uzantısına sahip bir dosya açın ve ardından içinde herhangi bir yere sağ tıklayın. Kod **Parçacığı Ekle** komutunun kısayol menüsünde görünmesi gerekir.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Kod Parçacığı Seçici kullanıcı arabiriminde kod parçacığı genişletmesi uygulama
 Bu bölümde kod parçacığı genişletmenin nasıl uygulanarak kod parçacığı  seçici kullanıcı arabiriminin kısayol menüsüne Kod Parçacığı Ekle'ye tıklanmış olarak görüntülenebilir. Kullanıcı kod parçacığı kısayolunu yazarak Sekme tuşuna basıyorsa bir kod parçacığı da **genişletilir.**

 Kod parçacığı seçici kullanıcı arabirimini görüntülemek ve gezintiyi ve ekleme sonrası kod parçacığı kabulünü etkinleştirmek için yöntemini <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> kullanın. Eklemenin kendisi yöntemi tarafından <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> işlemeye devam eder.

 Kod parçacığı genişletmesi uygulamasında eski <xref:Microsoft.VisualStudio.TextManager.Interop> arabirimler kullanılır. Geçerli düzenleyici sınıflarından eski koda çevirisini yapmak için eski arabirimlerin bir metin arabelleğinde konum belirtmek için satır numaraları ve sütun numaralarının bir bileşimini, ancak geçerli sınıfların tek bir dizin kullanır olduğunu unutmayın. Bu nedenle, bir arabellekte her biri 10 karakterden (artı bir karakter olarak sayan yeni satır) üç satır varsa, üçüncü satırda dördüncü karakter geçerli uygulamada 27 konumundadır, ancak eski uygulamada 3. konumdadır.

#### <a name="to-implement-snippet-expansion"></a>Kod parçacığı genişletmesi uygulamak için

1. sınıfını içeren dosyaya `TestCompletionCommandHandler` aşağıdaki yönergeleri `using` ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet26":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet26":::

2. sınıfının `TestCompletionCommandHandler` arabirimini uygulamasına neden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> olur.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet27":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet27":::

3. sınıfında, `TestCompletionCommandHandlerProvider` içeri <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> aktarın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet28":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet28":::

4. Kod genişletme arabirimleri ve için bazı özel alanlar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet29":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet29":::

5. sınıfının `TestCompletionCommandHandler` oluşturucusnda aşağıdaki alanları ayarlayın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet30":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet30":::

6. Kullanıcı Kod Parçacığı Ekle komutuna tıkladığında kod parçacığı **seçiciyi görüntülemek** için aşağıdaki kodu yöntemine <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> ekleyin. (Bu açıklamayı daha okunabilir hale yapmak için deyim tamamlama için kullanılan kod gösterilmez; bunun yerine mevcut yönteme kod `Exec()` blokları eklenir.) Bir karakteri kontrol eden koddan sonra aşağıdaki kod bloğuna ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet31":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet31":::

7. Bir kod parçacığında gezinilmesi mümkün olan alanlar varsa, genişletme açıkça kabul edilene kadar genişletme oturumu açık tutulur; Kod parçacığında alan yoksa oturum kapatılır ve yöntemi tarafından `null` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> döndürülür. yönteminde, önceki adımda ekley istediğiniz kod parçacığı seçici kullanıcı arabirimi kodunun ardından, kod parçacığı gezintisi işlemek için aşağıdaki kodu ekleyin (kullanıcı kod parçacığı ekledikten sonra Sekme veya <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> **Shift**  + **Sekmesi'ne** basıyorsa).

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet32":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet32":::

8. Kullanıcı karşılık gelen kısayolu yazarak Sekme tuşuna basıyorsa kod parçacığını **eklemek** için yöntemine kod <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> ekleyin. Kod parçacığını ekin özel yöntemi sonraki bir adımda gösterilir. Önceki adımda ekley istediğiniz gezinti kodunun ardından aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet33":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet33":::

9. Arabirimin yöntemlerini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> uygulama. Bu uygulamada, ilginiz olan tek yöntemler ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> yöntemleridir. Diğer yöntemler yalnızca şunun gibi bir dönüşle <xref:Microsoft.VisualStudio.VSConstants.S_OK> çalışmalı: .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet34":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet34":::

10. yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> uygulama. Aslında genişletmeleri ekser yardımcı yöntemi sonraki bir adımda ele almaktadır. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>, 'den edinebilirsiniz satır ve sütun bilgilerini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sağlar.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet35":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet35":::

11. Aşağıdaki özel yöntem, kısayolu veya başlığı ve yolu temel alan bir kod parçacığı ekler. Ardından kod <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> parçacığıyla yöntemini çağıran.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet36":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet36":::

## <a name="build-and-test-code-snippet-expansion"></a>Kod parçacığını derleme ve test genişletme
 Kod parçacığı genişletmesinin projeniz içinde çalışır olup olmadığını test etmek için.

1. Çözümü derleyin. Bu projeyi hata ayıklayıcısında çalıştırarak ikinci bir Visual Studio başlat.

2. Bir metin dosyası açın ve metin yazın.

3. Metinde bir yere sağ tıklayın ve ardından Kod Parçacığı **Ekle'ye tıklayın.**

4. Kod parçacığı seçici kullanıcı arabirimi, Test değiştirme alanları olan bir **açılır pencereyle görünmektedir.** Açılan pencereye çift tıklayın.

     Aşağıdaki kod parçacığı eklenemez.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     **Enter** veya Esc tuşuna **basma.**

5. **"first"** **ve**"second" arasında geçiş yapmak için Sekme ve Shift +  Sekmesi'ne basın.

6. Enter veya Esc tuşlarına basarak **eklemeyi** kabul **edin.**

7. Metnin farklı bir bölümünde "test" yazın ve Sekme tuşuna **basın.** "Test" kod parçacığı kısayolu olduğundan kod parçacığı yeniden eklenemez.

## <a name="next-steps"></a>Sonraki adımlar
