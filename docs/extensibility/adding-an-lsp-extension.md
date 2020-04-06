---
title: Dil Sunucusu Protokolü uzantısı ekleme | Microsoft Dokümanlar
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef2093915538f09f425fc961420c4a3078043c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740235"
---
# <a name="add-a-language-server-protocol-extension"></a>Dil Sunucusu Protokolü uzantısı ekleme

Dil Sunucu Protokolü (LSP), JSON RPC v2.0 biçiminde, çeşitli kod editörlerine dil hizmeti özellikleri sağlamak için kullanılan ortak bir protokoldür. Protokolü kullanarak, geliştiriciler IntelliSense, hata tanılama, tüm başvuruları bulmak ve benzeri gibi dil hizmeti özellikleri sağlamak için lsp destekleyen çeşitli kod editörleri için tek bir dil sunucusu yazabilirsiniz. Geleneksel olarak, Visual Studio'daki dil hizmetleri, sözdizimi vurgulama gibi temel işlevleri sağlamak için TextMate dilbilgisi dosyaları kullanılarak veya daha zengin veriler sağlamak için Visual Studio genişletilebilirlik API'lerinin tam kümesini kullanan özel dil hizmetleri yazılarak eklenebilir. LSP için Visual Studio desteği ile, üçüncü bir seçenek var.

![Visual Studio dil sunucusu protokolü hizmeti](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Dil Sunucusu Protokolü

![dil sunucusu protokolü uygulaması](media/lsp-implementation.png)

Bu makalede, LSP tabanlı bir dil sunucusu kullanan bir Visual Studio uzantısı nasıl oluşturulacak açıklanmaktadır. LSP tabanlı bir dil sunucusu geliştirdiğinizi ve sadece Visual Studio'ya entegre etmek istediğinizi varsayar.

Visual Studio içinde destek için, dil sunucuları istemci (Visual Studio) ile herhangi bir akış tabanlı iletim mekanizması üzerinden iletişim kurabilir, örneğin:

* Standart giriş/çıkış akışları
* Adlandırılmış borular
* Soketler (yalnızca TCP)

LSP'nin amacı ve Visual Studio'da bunun için destek, Visual Studio ürününün bir parçası olmayan yerleşik dil hizmetleridir. Visual Studio'daki mevcut dil hizmetlerini (C# gibi) genişletmek için tasarlanmamıştır. Varolan dilleri genişletmek için, dil hizmetinin genişletilebilirlik kılavuzuna (örneğin, ["Roslyn" .NET Derleyici Platformu)](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)bakın veya [editör ve dil hizmetlerini genişlet'e](../extensibility/extending-the-editor-and-language-services.md)bakın.

Protokolün kendisi hakkında daha fazla bilgi [için, buradaki](https://github.com/Microsoft/language-server-protocol)belgelere bakın.

Örnek bir dil sunucusunun nasıl oluşturulacağı veya varolan bir dil sunucusunun Visual Studio Code'a nasıl entegre edilecek hakkında daha fazla bilgi için [buradaki](https://code.visualstudio.com/docs/extensions/example-language-server)belgelere bakın.

## <a name="language-server-protocol-supported-features"></a>Language Server Protocol desteklenen özellikler

Aşağıdaki tablolar Visual Studio'da hangi LSP özelliklerinin desteklenildiğigösterilmektedir:

İleti | Visual Studio'da Destek Var
--- | ---
Başlatmak | evet
Başlatılan | evet
kapatma | evet
Çıkış | evet
$/cancelRequest | evet
pencere/showMessage | evet
pencere/showMessageRequest | evet
pencere/logMessage | evet
telemetri/olay |
istemci/kayıtYeteneği |
istemci/kayıt dışıÖzellik |
çalışma alanı/didChangeConfiguration | evet
çalışma alanı/didChangeWatchedFiles | evet
çalışma alanı/sembol | evet
çalışma alanı/executeCommand | evet
çalışma alanı/uygulamalıEdit | evet
textBelge/yayımDiagin | evet
textDocument/didOpen | evet
textDocument/didChange | evet
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | evet
textDocument/didClose | evet
textBelge/tamamlama | evet
tamamlama/çözme | evet
textBelge/hover | evet
textBelge/imzaYardım | evet
textBelge/referanslar | evet
textBelge/belgeHighlight | evet
textBelge/belgeSembol | evet
textBelge/biçimlendirme | evet
textBelge/aralıkBiçimlendirme | evet
textDocument/onTypeFormatting |
textBelge/tanım | evet
textBelge/kodEylem | evet
textDocument/codeLens |
codeLens/çözüm |
textBelge/belgeLink |
documentLink/çözüm |
textBelge/yeniden adlandırma | evet

## <a name="get-started"></a>başlarken

> [!NOTE]
> Visual Studio 2017 sürüm 15.8 ile başlayarak, ortak Language Server Protocol desteği Visual Studio'da yerleşiktir. Önizleme [Language Server Client VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) sürümünü kullanarak LSP uzantıları nı oluşturmuşsanız, sürüm 15.8 veya daha yüksek bir yükseltme yaptığınızda çalışma durdurulacaktır. LSP uzantılarınızın yeniden çalışmasını sağlamak için aşağıdakileri yapmanız gerekir:
>
> 1. Microsoft Visual Studio Language Server Protocol Preview VSIX'yi kaldırın.
>
>    Sürüm 15.8 ile başlayarak, Visual Studio'da her yükseltme yaptığınızda önizleme VSIX otomatik olarak algılanır ve kaldırılır.
>
> 2. Nuget başvurunuzu [LSP paketleri](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)için en son önizleme olmayan sürümüyle güncelleyin.
>
> 3. VSIX bildiriminizde Microsoft Visual Studio Language Server Protocol Preview VSIX'ye olan bağımlılığı kaldırın.
>
> 4. VSIX'nizin Visual Studio 2017 sürüm 15.8 Preview 3'ü yükleme hedefi için alt sınır olarak belirttiğinden emin olun.
>
> 5. Yeniden derleyin ve dağıtın.

### <a name="create-a-vsix-project"></a>VSIX projesi oluşturma

LSP tabanlı bir dil sunucusu kullanarak bir dil hizmeti uzantısı oluşturmak için, öncelikle VS örneğiniz için **Visual Studio uzantısı geliştirme** İş Yükünün yüklü olduğundan emin olun.

Sonra, **Dosya** > **Yeni Proje** > **Görsel C #** > **Genişletilebilirlik** > **VSIX Projesi**gezinerek yeni bir VSIX projesi oluşturun:

![vsix projesi oluşturma](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Dil sunucusu ve çalışma zamanı yükleme

Varsayılan olarak, Visual Studio'daki LSP tabanlı dil sunucularını desteklemek için oluşturulan uzantılar, dil sunucularının kendilerini veya bunları yürütmek için gereken çalışma sürelerini içermez. Uzantı geliştiricileri, dil sunucularını ve gereken çalışma sürelerini dağıtmakla yükümlüdür. Bunu yapmanın birkaç yolu vardır:

* Dil sunucuları VSIX'ye içerik dosyası olarak katışdırılabilir.
* Dil sunucusunu ve/veya gerekli çalışma sürelerini yüklemek için bir MSI oluşturun.
* Market'te, kullanıcılara çalışma süreleri ve dil sunucularını nasıl elde edecekleri konusunda bilgi veren yönergeler sağlayın.

### <a name="textmate-grammar-files"></a>TextMate dilbilgisi dosyaları

LSP, diller için metin renklendirmesinin nasıl sağlanabilen belirtimini içermez. Visual Studio'daki diller için özel renklendirme sağlamak için uzantı geliştiricileri TextMate dilbilgisi dosyasını kullanabilir. Özel TextMate dilbilgisi veya tema dosyaları eklemek için aşağıdaki adımları izleyin:

1. Uzantınızın içinde "Gramerler" adlı bir klasör oluşturun (veya istediğiniz ad ne olursa olsun olabilir).

2. *Grammars* klasöründe, özel renklendirme sağlamak istediğiniz * \*.tmlanguage*, * \*.plist*, * \*.tmtheme*veya * \*.json* dosyaları içerir.

   > [!TIP]
   > *.tmtheme* dosyası, kapsamların Visual Studio sınıflandırmalarına (renk tuşları adlı) nasıl eşleşiş gösteriş yapılacağını tanımlar. Kılavuz için, *%ProgramFiles(x86)%\Microsoft Visual Studio sürümünde %ProgramFiles(x86)%\Microsoft Visual Studio\\\<sürümünde genel \\ \<.tmtheme dosyasına başvuruda bulunabilirsiniz>SKU>\Common7\IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg* dizinine. *.tmtheme*

3. *.pkgdef* dosyası oluşturun ve buna benzer bir satır ekleyin:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Dosyalara sağ tıklayın ve **Özellikler'i**seçin. **Yapı** eylemini **İçerik** olarak değiştirin ve **VSIX özelliğine Ekle** özelliğini **doğru**olarak değiştirin.

Önceki adımları tamamladıktan sonra, 'MyLang' ('MyLang' sadece bir anlam ayrımı için bir addır ve herhangi bir benzersiz dize olabilir) adlı bir depo kaynağı olarak paketin yükleme dizinine bir *Gramer* klasörü eklenir. Bu dizindeki tüm dilbilgisi *(.tmlanguage* files) ve tema dosyaları *(.tmtheme* dosyaları) potansiyel olarak alınır ve TextMate ile sağlanan yerleşik dilbilgisinin yerini alar. Dilbilgisi dosyasının bildirilen uzantıları, açılan dosyanın uzantısıile eşleşirse, TextMate devreye girecek.

## <a name="create-a-simple-language-client"></a>Basit bir dil istemcisi oluşturma

### <a name="main-interface---ilanguageclient"></a>Ana arayüz - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

VSIX projenizi oluşturduktan sonra, projenize aşağıdaki NuGet paketini ekleyin:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Önceki adımları tamamladıktan sonra NuGet paketine bağımlı olduğunuzda, Newtonsoft.Json ve StreamJsonRpc paketleri de projenize eklenir. **Bu yeni sürümlerin Visual Studio sürümüne uzantınızın hedeflediğiniz sürümüne yükleneceğinden emin olmadıkça bu paketleri güncellemeyin.** Derlemeler VSIX'nize dahil edilmeyecek; bunun yerine, Visual Studio yükleme dizininden alınacaktır. Derlemelerin daha yeni bir sürümüne, kullanıcının makinesine yüklenenden daha yeni bir sürümüne başvuruyorsanız, uzantınız çalışmaz.

Daha sonra, LSP tabanlı bir dil sunucusuna bağlanan dil istemcileri için gereken ana arabirim olan [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) arabirimini uygulayan yeni bir sınıf oluşturabilirsiniz.

Aşağıdaki bir örnektir:

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Uygulanması gereken ana yöntemler [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) ve [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)vardır. Visual Studio uzantınızı yüklediğinde ve dil sunucunuz başlatılımaya hazır olduğunda [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) adı verilir. Bu yöntemde, dil sunucusunun başlatılması gerektiğini bildirmek için hemen [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) temsilcini çağırabilir veya ek mantık yapabilir ve daha sonra [StartAsync'i](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) çağırabilirsiniz. **Dil sunucunuzu etkinleştirmek için bir noktada StartAsync'i aramanız gerekir.**

[ActivateAsync,](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) temsilcisini arayarak çağrılan yöntemdir. Dil sunucusunu başlatmak ve ona bağlantı kurmak için mantık içerir. Sunucuya yazma ve sunucudan okuma için akışlar içeren bir bağlantı nesnesi döndürülmelidir. Burada atılan tüm özel durumlar yakalanır ve Visual Studio'daki bir InfoBar iletisi aracılığıyla kullanıcıya görüntülenir.

### <a name="activation"></a>Etkinleştirme

Dil istemci sınıfınız uygulandıktan sonra, Visual Studio'ya nasıl yükleneceğini ve etkinleştirileceğini tanımlamak için iki öznitelik tanımlamanız gerekir:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio, genişletilebilirlik noktalarını yönetmek için [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Yönetilen Genişletilebilirlik Çerçevesi) kullanır. [Dışa](/dotnet/api/system.componentmodel.composition.exportattribute) Aktarma özniteliği Visual Studio'ya bu sınıfın bir uzantı noktası olarak alınması ve uygun zamanda yüklenmesi gerektiğini gösterir.

MEF'i kullanmak için, VSIX bildiriminde MEF'i bir Varlık olarak da tanımlamanız gerekir.

VSIX manifesto tasarımcınızı açın ve **Varlıklar** sekmesine gidin:

![MEF varlık ekleme](media/lsp-add-asset.png)

Yeni bir varlık oluşturmak için **Yeni'yi** tıklatın:

![MEF varlığını tanımlayın](media/lsp-define-asset.png)

* **Tür**: Microsoft.VisualStudio.MefComponent
* **Kaynak**: Geçerli çözümde bir proje
* **Proje**: [Projeniz]

### <a name="content-type-definition"></a>İçerik türü tanımı

Şu anda, LSP tabanlı dil sunucusu uzantınızı yüklemenin tek yolu dosya içeriği türüne göredir. Diğer bir de, dil istemci sınıfınızı tanımlarken [(iLanguageClient'ı](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)uygular), açıldığında uzantınızın yüklenmesine neden olacak dosya türlerini tanımlamanız gerekir. Tanımlı içerik türünüze uyan hiçbir dosya açılmazsa, uzantınız yüklenmez.

Bu, bir veya daha `ContentTypeDefinition` fazla sınıf tanımlayarak yapılır:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;

        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

Önceki örnekte, *.bar* dosya uzantısı ile biten dosyalar için içerik türü tanımı oluşturulur. İçerik türü tanımına "çubuk" adı verilir ve [CodeRemoteContentTypeName'den](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017)türemesi gerekir.

İçerik türü tanımı ekledikten sonra, dil istemcisi uzantınızı dil istemci sınıfına ne zaman yükleyebileceğinizi tanımlayabilirsiniz:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

LSP dil sunucuları için destek eklemek, Visual Studio'da kendi proje sisteminizi uygulamanızı gerektirmez. Müşteriler, dil hizmetinizi kullanmaya başlamak için Visual Studio'da tek bir dosya veya klasör açabilir. Aslında, LSP dil sunucuları için destek yalnızca açık klasör/dosya senaryolarında çalışacak şekilde tasarlanmıştır. Özel bir proje sistemi uygulanırsa, bazı özellikler (ayarlar gibi) çalışmaz.

## <a name="advanced-features"></a>Gelişmiş özellikler

### <a name="settings"></a>Ayarlar

Özel dil sunucusuna özgü ayarlar için destek kullanılabilir, ancak hala geliştirilme sürecindedir. Ayarlar, dil sunucusunun neyi desteklediğine özgür ve genellikle dil sunucusunun verileri nasıl yayışladığını denetler. Örneğin, bir dil sunucusunda bildirilen en fazla hata sayısı için bir ayar olabilir. Uzantı yazarları, belirli projeler için kullanıcılar tarafından değiştirilebilen varsayılan bir değer tanımlar.

LSP dil hizmeti uzantınıza ayarlar için destek eklemek için aşağıdaki adımları izleyin:

1. Projenize ayarları ve varsayılan değerlerini içeren bir JSON dosyası (örneğin *MockLanguageExtensionSettings.json)* ekleyin. Örnek:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. JSON dosyasına sağ tıklayın ve **Özellikler'i**seçin. **Yapı** eylemini "İçerik" ve "VSIX'ye Ekle" özelliğini **gerçek**olarak değiştirin.

3. ConfigurationSections uygulayın ve JSON dosyasında tanımlanan ayarların önekleri listesini döndürün (Visual Studio Code'da, bu paket.json'daki yapılandırma bölüm adı ile eşlenir):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Projeye bir .pkgdef dosyası ekleyin (yeni metin dosyası ekleyin ve dosya uzantısını .pkgdef olarak değiştirin). Pkgdef dosyası bu bilgileri içermelidir:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Örnek:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. .pkgdef dosyasına sağ tıklayın ve **Özellikler'i**seçin. **Yapı** eylemini **İçerik** ve **VSIX özelliğine dahil** etme eylemini gerçek **olarak**değiştirin.

6. *source.extension.vsixmanifest* dosyasını açın ve **Varlık** sekmesine bir varlık ekleyin:

   ![vspackage varlık edin](media/lsp-add-vspackage-asset.png)

   * **Türü**: Microsoft.VisualStudio.vsPackage
   * **Kaynak**: Dosya sistemindeki dosya
   * Yol : *[.pkgdef* dosyanıza giden **yol]**

### <a name="user-editing-of-settings-for-a-workspace"></a>Çalışma alanı ayarlarının kullanıcı düzenlemesi

1. Kullanıcı, sunucunuzun sahip olduğu dosyaları içeren bir çalışma alanı açar.
2. Kullanıcı *VSWorkspaceSettings.json*adlı *.vs* klasörüne bir dosya ekler.
3. Kullanıcı, sunucunun sağladığı bir ayar için *VSWorkspaceSettings.json* dosyasına bir satır ekler. Örnek:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Tanılama izlemesini etkinleştirme

Tanılama izleme istemci ve sunucu arasındaki tüm iletileri çıktı, hata ayıklama sorunları yararlı olabilir etkinleştirilebilir. Tanılama izlemeyi etkinleştirmek için aşağıdakileri yapın:

1. Çalışma alanı ayarları dosyasını açın veya oluşturun *VSWorkspaceSettings.json* (bkz. "Çalışma alanı için ayarların kullanıcı düzenlemesi").
2. Ayarlar json dosyasında aşağıdaki satırı ekleyin:

```json
{
    "foo.trace.server": "Off"
}
```

İzleme ayrıntılılığı için üç olası değer vardır:

* "Kapalı": izleme tamamen kapalı
* "İletiler": izleme açık, ancak yalnızca yöntem adı ve yanıt kimliği izlenir.
* "Verbose": izleme açık; tüm rpc iletisi izlenir.

İzleme açıklandığında içerik *%temp%\VisualStudio\LSP* dizininde bir dosyaya yazılır. Günlük adlandırma biçimini izler *[LanguageClientName]-[Datetime Stamp].log*. Şu anda, izleme yalnızca açık klasör senaryoları için etkinleştirilebilir. Bir dil sunucusu etkinleştirmek için tek bir dosya açma desteği izleme tanılama yok.

### <a name="custom-messages"></a>Özel mesajlar

Standart Language Server Protocol'un parçası olmayan dil sunucusuna ileti leri aktarmayı ve dil sunucusundan ileti almayı kolaylaştırmak için API'ler vardır. Özel iletileri işlemek için dil istemci sınıfınızda [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) arabirimini uygulayın. [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) kitaplığı, dil istemciniz ve dil sunucunuz arasında özel iletiler iletmek için kullanılır. LSP dil istemci uzantınız diğer Visual Studio uzantıları gibi olduğundan, özel mesajlar aracılığıyla uzantınıza Visual Studio'ya (diğer Visual Studio API'lerini kullanarak) ek özellikler eklemeye karar verebilirsiniz.

#### <a name="receive-custom-messages"></a>Özel iletiler alma

Dil sunucusundan özel iletiler almak için [ILanguageClientCustomMessage'da](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) özelliğini uygulayın ve özel iletilerinizi nasıl işleyeceğini bilen bir nesneyi döndürün. Aşağıdaki örnek:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="send-custom-messages"></a>Özel iletiler gönderme

Dil sunucusuna özel iletiler göndermek için [ILanguageClientCustomMessage'da](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) yöntemini uygulayın. Bu yöntem, dil sunucunuz başlatıldığında ve ileti almaya hazır olduğunda çağrılır. Bir [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) nesnesi, daha sonra [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API'lerini kullanarak dil sunucusuna ileti göndermeyi saklayabileceğiniz bir parametre olarak geçirilir. Aşağıdaki örnek:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>Orta katman

Bazen bir uzantı geliştiricisi, dil sunucusuna gönderilen ve alınan LSP iletilerini engellemek isteyebilir. Örneğin, bir uzantı geliştiricisi belirli bir LSP iletisi için gönderilen ileti parametresini değiştirmek veya dil sunucusundan döndürülen sonuçları bir LSP özelliği (örneğin tamamlamalar) için değiştirmek isteyebilir. Bu gerekli olduğunda, uzantı geliştiricileri LSP iletilerini engellemek için MiddleLayer API'sini kullanabilir.

Her LSP iletisinin durdurma için kendi orta katman arabirimi vardır. Belirli bir iletiyi engellemek için, bu ileti için orta katman arabirimini uygulayan bir sınıf oluşturun. Ardından, dil istemci sınıfınızda [iLanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) arabirimini uygulayın ve nesnenizin bir örneğini [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) özelliğine döndürün. Aşağıdaki örnek:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

Orta katman özelliği hala geliştirilmekte ve henüz kapsamlı değildir.

## <a name="sample-lsp-language-server-extension"></a>Örnek LSP dil sunucusu uzantısı

Visual Studio'daki LSP istemci API'sını kullanarak bir örnek uzantısının kaynak kodunu görmek için VSSDK-Extensibility-Samples [LSP örneğine](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)bakın.

## <a name="faq"></a>SSS

**Visual Studio'da daha zengin özellik desteği sağlamak için LSP dil sunucumu tamamlamak için özel bir proje sistemi oluşturmak istiyorum, bunu nasıl yapabilirim?**

Visual Studio'daki LSP tabanlı dil sunucuları desteği [açık klasör özelliğine](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) dayanır ve özel bir proje sistemi gerektirmeyecek şekilde tasarlanmıştır. [Burada](https://github.com/Microsoft/VSProjectSystem)yönergeleri izleyerek kendi özel proje sisteminizi oluşturabilirsiniz, ancak ayarlar gibi bazı özellikler çalışmayabilir. LSP dil sunucuları için varsayılan başlatma mantığı şu anda açılmakta olan klasörün kök klasör konumundan geçmektir, bu nedenle özel bir proje sistemi kullanıyorsanız, dil sunucunuzun düzgün başlatAbilmesini sağlamak için başlatma sırasında özel mantık sağlamanız gerekebilir.

**Hata ayıklama desteği nasıl eklenir?**

Biz gelecekteki bir sürümde [ortak hata ayıklama protokolü](https://code.visualstudio.com/docs/extensionAPI/api-debugging) için destek sağlayacaktır.

**Zaten vs destekli bir dil hizmeti yüklüyse (örneğin, JavaScript), ek özellikler (linting gibi) sunan bir LSP dil sunucusu uzantısı yükleyebilir miyim?**

Evet, ancak tüm özellikler düzgün çalışmaz. LSP dil sunucusu uzantıları için nihai hedef, Visual Studio tarafından doğal olarak desteklenmeyen dil hizmetlerini etkinleştirmektir. LSP dil sunucularını kullanarak ek destek sunan uzantılar oluşturabilirsiniz, ancak bazı özellikler (IntelliSense gibi) sorunsuz bir deneyim olmayacaktır. Genel olarak, LSP dil sunucusu uzantılarının varolandil lerini genişletmek için değil, yeni dil deneyimleri sağlamak için kullanılması önerilir.

**Tamamlanmış LSP dil sunucum VSIX'yi nerede yayımlarım?**

[Burada](walkthrough-publishing-a-visual-studio-extension.md)Pazar talimatlarına bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Diğer diller için Visual Studio düzenleyici desteği ekleme](../ide/adding-visual-studio-editor-support-for-other-languages.md)
