---
title: Dil Sunucusu Protokolü uzantısı ekleme | Microsoft Docs
description: Dil Sunucusu Protokolü'Visual Studio (LSP) temel alan bir dil sunucusunu tümleştiren bir uzantı oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 07/05/2021
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9daeb0358c1dfe638cf3ca49ad973ffd6dc19cc0
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2021
ms.locfileid: "122980793"
---
# <a name="add-a-language-server-protocol-extension"></a>Dil Sunucusu Protokolü uzantısı ekleme

Dil Sunucusu Protokolü (LSP), çeşitli kod düzenleyicilerine dil hizmeti özellikleri sağlamak için kullanılan JSON RPC v2.0 şeklinde ortak bir protokoldür. Geliştiriciler protokolü kullanarak tek bir dil sunucusu yazarak IntelliSense, hata tanılama, tüm başvuruları bulma gibi dil hizmeti özelliklerini LSP'yi destekleyen çeşitli kod düzenleyicilerine bulabilir. Geleneksel olarak Visual Studio dil hizmetleri, söz dizimi vurgulama gibi temel işlevler sağlamak için TextMate dil bilgisi dosyaları kullanılarak veya daha zengin veriler sağlamak için tam Visual Studio genişletilebilirlik API'lerini kullanan özel dil hizmetleri yazarak eklenebilir. LSP Visual Studio desteğiyle üçüncü bir seçenek vardır.

![Visual Studio'de dil sunucusu protokolü Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Dil Sunucusu Protokolü

![dil sunucusu protokol uygulaması](media/lsp-implementation.png)

Bu makalede LSP tabanlı bir Visual Studio kullanan bir uzantının nasıl oluşturul açıklanmıştır. Zaten LSP tabanlı bir dil sunucusu geliştirdiğini ve bunu yalnızca bu sunucuyla tümleştirip tümleştirip Visual Studio.

Dil sunucuları Visual Studio akış tabanlı iletim mekanizması aracılığıyla istemciyle (Visual Studio) iletişim kurabilir, örneğin:

* Standart giriş/çıkış akışları
* Adlandırılmış kanallar
* Yuvalar (yalnızca TCP)

LSP'nin amacı ve bu üründe Visual Studio ürünün parçası olan dil hizmetlerini Visual Studio etmektir. Bu hizmet, mevcut dil hizmetlerini (C#gibi) Visual Studio. Mevcut dilleri genişletmek için dil hizmetinin genişletilebilirlik kılavuzuna (örneğin, ["Roslyn" .NET Compiler Platform)](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)bakın veya bkz. Düzenleyiciyi ve dil [hizmetlerini genişletme.](../extensibility/extending-the-editor-and-language-services.md)

Protokolün kendisi hakkında daha fazla bilgi için buradaki belgelere [bakın.](https://github.com/Microsoft/language-server-protocol)

Örnek dil sunucusu oluşturma veya mevcut bir dil sunucusunu Visual Studio Code ile tümleştirin hakkında daha fazla bilgi için buradaki belgelere [bakın.](https://code.visualstudio.com/docs/extensions/example-language-server)

## <a name="language-server-protocol-supported-features"></a>Dil Sunucusu Protokolü tarafından desteklenen özellikler

Aşağıdaki tablolarda, aşağıdaki tabloda hangi LSP özelliklerinin destek Visual Studio:

İleti | Visual Studio desteğine sahip
--- | ---
Başlatmak | evet
Başlatılan | evet
kapatma | evet
Çıkış | evet
$/cancelRequest | evet
window/showMessage | evet
window/showMessageRequest | evet
window/logMessage | evet
telemetri/olay |
client/registerCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | evet
workspace/didChangeWatchedFiles | evet
çalışma alanı/sembol | evet
workspace/executeCommand | evet
workspace/applyEdit | evet
textDocument/publishDiagnostics | evet
textDocument/didOpen | evet
textDocument/didChange | evet
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | evet
textDocument/didClose | evet
textDocument/tamamlama | evet
tamamlama/çözümleme | evet
textDocument/hover | evet
textDocument/signatureHelp | evet
textDocument/references | evet
textDocument/documentHighlight | evet
textDocument/documentSymbol | evet
textDocument/formatting | evet
textDocument/rangeFormatting | evet
textDocument/onTypeFormatting |
textDocument/definition | evet
textDocument/codeAction | evet
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/rename | evet

## <a name="get-started"></a>başlarken

> [!NOTE]
> 2017 Visual Studio 15.8 sürümünden başlayarak, ortak Dil Sunucusu Protokolü desteği Visual Studio. Önizleme Dil Sunucusu [İstemciSI VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) sürümünü kullanarak LSP uzantıları yaptısanız, 15.8 veya daha yeni bir sürüme yükseltin. LSP uzantılarınızı yeniden çalışmak için aşağıdaki adımları gerçekleştirin:
>
> 1. Microsoft Visual Studio Dil Sunucusu Protokolü Önizleme VSIX'i kaldırın.
>
>    sürüm 15,8 ' den başlayarak, Visual Studio ' de bir yükseltme yaptığınızda, preview vsıx otomatik olarak algılanır ve kaldırılır.
>
> 2. NuGet başvurunuz için, [LSP paketlerinin](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)en son önizleme dışı sürümüne güncelleştirin.
>
> 3. vsıx bildiriminizde Microsoft Visual Studio Language Server protokol önizlemesi vsıx 'e bağımlılığı kaldırın.
>
> 4. vsıx 'in, ınstall target için alt sınır olarak Visual Studio 2017 sürüm 15,8 Preview 3 ' ü belirttiğinden emin olun.
>
> 5. Yeniden derleyin ve dağıtın.

### <a name="create-a-vsix-project"></a>VSıX projesi oluşturma

bir LSP tabanlı dil sunucusu kullanarak bir dil hizmeti uzantısı oluşturmak için önce, VS örneğiniz için **Visual Studio uzantısı geliştirme** iş yükünün yüklü olduğundan emin olun.

sonra, **dosya**  >  **yeni Project**  >  **Visual C#**  >  **genişletilebilirlik**  >  **vsıx Project**' a giderek yeni bir vsıx projesi oluşturun:

![VSIX projesi oluştur](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Dil sunucusu ve çalışma zamanı yüklemesi

varsayılan olarak, Visual Studio ' de LSP tabanlı dil sunucularını desteklemek üzere oluşturulan uzantılar, dil sunucularının kendisini veya bunları yürütmek için gereken çalışma zamanlarını içermez. Uzantı geliştiricileri, dil sunucularının ve gereken çalışma zamanlarının dağıtılmasından sorumludur. Bunu yapmak için birkaç yol vardır:

* Dil sunucuları VSıX 'e içerik dosyaları olarak katıştırılabilir.
* Dil sunucusunu ve/veya gerekli çalışma zamanlarını yüklemek için bir MSI oluşturun.
* Kullanıcılara çalışma zamanları ve dil sunucuları alma hakkında bilgi sağlayan Market hakkında yönergeler sağlar.

### <a name="textmate-grammar-files"></a>TextMate dilbilgisi dosyaları

LSP, diller için metin renklendirme sağlama hakkında belirtim içermez. Visual Studio diller için özel renklendirme sağlamak üzere, uzantı geliştiricileri bir textmate dilbilgisi dosyası kullanabilir. Özel TextMate dilbilgisi veya Tema dosyaları eklemek için aşağıdaki adımları izleyin:

1. Uzantınızın içinde "Dilmars" adlı bir klasör oluşturun (veya seçtiğiniz herhangi bir ad olabilir).

2. *Grammars* klasörü içinde, özel renklendirme sağlamak istediğiniz *\* . tmlanguage*, *\* . plist*, *\* . tmtheme* veya *\* . JSON* dosyalarını ekleyin.

   > [!TIP]
   > bir *. tmtheme* dosyası, kapsamların Visual Studio sınıflandırmalarla nasıl eşlendiğini tanımlar (renk anahtarları olarak adlandırılır). rehberlik için, *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ \<version> \\ \<SKU> \Common7\IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg* dizinindeki global *. tmtheme* dosyasına başvurabilirsiniz.

3. Bir *. pkgdef* dosyası oluşturun ve şuna benzer bir satır ekleyin:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Dosyalara sağ tıklayıp **Özellikler**' i seçin. **Derleme** eylemini **içerik** olarak değiştirin ve **VSIX içindeki Include** özelliğini **true** olarak değiştirin.

Önceki adımları tamamladıktan sonra, paketin Install dizinine ' MyLang ' adlı bir depo kaynağı olarak bir *Grammars* klasörü eklenir (' mylang ' yalnızca Kesinleştirme için bir addır ve herhangi bir benzersiz dize olabilir). Bu dizindeki tüm dilbilgisi (*. tmlanguage* dosyaları) ve Tema dosyaları (*. tmtheme* dosyaları), artırmasını olarak alınır ve TextMate ile birlikte sunulan yerleşik dilbilgisi ve bunların yerini alır. Dilbilgisi dosyası tarafından tanımlanan uzantılar, açılan dosyanın uzantısıyla eşleşiyorsa, TextMate ' de adım adım olur.

## <a name="create-a-simple-language-client"></a>Basit dil istemcisi oluşturma

### <a name="main-interface---ilanguageclient"></a>Ana arabirim- [ılanguageclient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)

vsıx projenizi oluşturduktan sonra, aşağıdaki NuGet paketlerini projenize ekleyin:

* [Microsoft. VisualStudio. LanguageServer. Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> önceki adımları tamamladıktan sonra NuGet paketine bir bağımlılık aldığınızda, Newtonsoft.Json ve streamjsonrpc paketleri de projenize eklenir. **bu yeni sürümlerin, uzantınızın hedeflediği Visual Studio sürümüne yüklenemediği durumlar dışında bu paketleri güncelleştirmeyin**. Derlemeler VSıX 'e dahil edilmez; bunun yerine, Visual Studio yükleme dizininden alınacaktır. Derlemelerin bir kullanıcının makinesine yüklenenden daha yeni bir sürümüne başvuruyorsam, uzantınız çalışmaz.

Daha sonra, bir LSP tabanlı dil sunucusuna bağlanan dil istemcileri için gereken ana arabirim olan [ılanguageclient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true) arabirimini uygulayan yeni bir sınıf oluşturabilirsiniz.

Aşağıda bir örnek verilmiştir:

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

Uygulanması gereken ana yöntemler [Onloadedadsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) ve [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true)' dir. Visual Studio uzantınızı yükledikten ve dil sunucunuz başlamaya hazırsanız [onloadedadsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) çağrılır. Bu yöntemde, dil sunucusunun başlatılması gerektiğini işaret etmek için [startasync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) temsilcisini hemen çağırabilir veya ek Logic ve [startasync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) ' ı daha sonra çalıştırabilirsiniz. **Dil sunucunuzu etkinleştirmek için, bir noktada StartAsync ' ı çağırmanız gerekir.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true) , sonunda [startasync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) temsilcisi çağırarak çağrılan yöntemdir. Dil sunucusunu başlatma ve bu bağlantıyı kurma mantığını içerir. Sunucuya yazmak ve sunucudan okumak için akışlar içeren bir bağlantı nesnesi döndürülmelidir. Burada oluşturulan özel durumlar yakalanıp Visual Studio bir bilgi çubuğu iletisi aracılığıyla kullanıcıya gösterilir.

### <a name="activation"></a>Etkinleştirme

dil istemci sınıfınız uygulandıktan sonra, Visual Studio ve etkinleştirilmesinin nasıl yükleneceğini tanımlamak için iki öznitelik tanımlamanız gerekir:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio, genişletilebilirlik noktalarını yönetmek için [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) kullanır. [Export](/dotnet/api/system.componentmodel.composition.exportattribute) özniteliği, bu sınıfın bir uzantı noktası olarak çekilmesi ve uygun zamanda yüklenmesi gerektiğini Visual Studio belirtir.

MEF kullanmak için VSıX bildiriminde bir varlık olarak MEF de tanımlamanız gerekir.

VSıX bildirim tasarımcısını açın ve **varlıklar** sekmesine gidin:

![MEF varlığı Ekle](media/lsp-add-asset.png)

Yeni bir varlık oluşturmak için **Yeni** ' ye tıklayın:

![MEF varlığını tanımla](media/lsp-define-asset.png)

* **Şunu yazın**: Microsoft. VisualStudio. MefComponent
* **Kaynak**: geçerli çözümdeki bir proje
* **Project**: [projeniz]

### <a name="content-type-definition"></a>İçerik türü tanımı

Şu anda, LSP tabanlı dil sunucusu uzantınızı yüklemeye yönelik tek yöntem dosya içerik türüne bağlıdır. Diğer bir deyişle, dil istemci sınıfınızı tanımlarken ( [ılanguageclient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)'yi uygular), açıldığında uzantınızın yüklenmesine neden olacak dosya türlerini tanımlamanız gerekecektir. Tanımlı içerik türü ile eşleşen hiçbir dosya açılmazsa, uzantınız yüklenmez.

Bu, bir veya daha fazla sınıf tanımlayarak yapılır `ContentTypeDefinition` :

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

Önceki örnekte, *. Bar* dosya uzantısıyla biten dosyalar için bir içerik türü tanımı oluşturulur. İçerik türü tanımına "Bar" adı verilir ve [Coderemotecontenttypename](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017&preserve-view=true)türevi olmalıdır.

Bir içerik türü tanımı ekledikten sonra dil istemci sınıfında dil istemci uzantınızı ne zaman yükleneceğini tanımlayabilirsiniz:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

LSP dil sunucuları için destek eklemek, Visual Studio kendi proje sisteminizi uygulamanızı gerektirmez. müşteriler, dil hizmetinizi kullanmaya başlamak için Visual Studio tek bir dosyayı veya bir klasörü açabilir. Aslında, LSP dil sunucuları için destek yalnızca açık klasör/dosya senaryolarında çalışacak şekilde tasarlanmıştır. Özel bir proje sistemi uygulanmışsa bazı özellikler (örneğin, ayarlar) çalışmaz.

## <a name="advanced-features"></a>Gelişmiş özellikler

### <a name="settings"></a>Ayarlar

Özel dil sunucusuna özel ayarlar için destek kullanılabilir, ancak hala geliştirilme sürecinde. Ayarlar, dil sunucusunun neleri desteklediğine özgüdür ve genellikle dil sunucusunun verileri nasıl yaydığı hakkında denetim sağlar. Örneğin, bir dil sunucusunun raporlanan en fazla hata sayısı için bir ayarı olabilir. Uzantı yazarları, belirli projeler için kullanıcılar tarafından değiştirilebilen varsayılan bir değer tanımlar.

LSP dil hizmeti uzantınızın ayarlarına yönelik destek eklemek için aşağıdaki adımları izleyin:

1. Projenize, ayarlarını ve varsayılan değerlerini içeren bir JSON dosyası (örneğin, *MockLanguageExtensionSettings.json*) ekleyin. Örnek:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. JSON dosyasına sağ tıklayın ve **Özellikler**' i seçin. **Derleme** eylemini "content" ve "VSIX 'te Ekle" özelliğini **true** olarak değiştirin.

3. configurationsections uygulayın ve JSON dosyasında tanımlanan ayarlar için ön ekler listesini döndürün (Visual Studio Code, bu, package.jsüzerinde yapılandırma bölümü adıyla eşlenir):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Projeye bir. pkgdef dosyası ekleyin (yeni metin dosyası ekleyin ve dosya uzantısını. pkgdef olarak değiştirin). Pkgdef dosyası şu bilgileri içermelidir:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Örnek:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. . Pkgdef dosyasına sağ tıklayın ve **Özellikler**' i seçin. **Derleme** eylemini **içerik** ve **VSIX 'e dahil et** özelliğini **true** olarak değiştirin.

6. *Source. Extension. valtmanifest* dosyasını açın ve **varlık** sekmesine bir varlık ekleyin:

   ![VSPackage varlığını Düzenle](media/lsp-add-vspackage-asset.png)

   * **Şunu yazın**: Microsoft. VisualStudio. VsPackage
   * **Kaynak**: dosya sisteminde dosyası
   * **Yol**: [ *. pkgdef* dosyanızın yolu]

### <a name="user-editing-of-settings-for-a-workspace&quot;></a>Çalışma alanının ayarlarını kullanıcı düzenlemesi

1. Kullanıcı, sunucunuzun sahip olduğu dosyaları içeren bir çalışma alanı açar.
2. Kullanıcı, içinde *VSWorkspaceSettings.js* adlı *. vs* klasörüne bir dosya ekler.
3. Kullanıcı, sunucunun sağladığı bir ayar için dosyadaki *VSWorkspaceSettings.js* bir satır ekler. Örnek:

    ```json
    {
        &quot;foo.maxNumberOfProblems&quot;: 10
    }
    ```

### <a name=&quot;enable-diagnostics-tracing&quot;></a>Tanılama izlemeyi etkinleştir

Tanılama izleme, istemci ve sunucu arasındaki tüm iletileri, hata ayıklama sırasında yararlı olabilecek bir şekilde çıkarmak için etkinleştirilebilir. Tanılama izlemeyi etkinleştirmek için aşağıdakileri yapın:

1. *VSWorkspaceSettings.js* çalışma alanı ayarları dosyasını açın veya oluşturun (bkz. &quot;bir çalışma alanı Için ayarları kullanıcı düzenlemesi").
2. Ayarlar JSON dosyasına aşağıdaki satırı ekleyin:

```json
{
    "foo.trace.server": "Off"
}
```

İzleme ayrıntı düzeyi için üç olası değer vardır:

* "Kapalı": izleme tamamen kapalı
* "İletiler": izleme açık, ancak yalnızca Yöntem adı ve yanıt KIMLIĞI izleniyor.
* "Ayrıntılı": izleme açık; Tüm RPC iletisi izleniyor.

İzleme açıldığında, içerik *%Temp%\visualstudio\lsp* dizinindeki bir dosyaya yazılır. Günlük *[LanguageClientName]-[DateTime damga]. log* adlandırma biçimini izler. Şu anda izleme yalnızca açık klasör senaryolarında etkinleştirilebilir. Bir dil sunucusunu etkinleştirmek için tek bir dosyanın açılması, Tanılama izleme desteğine sahip değildir.

### <a name="custom-messages"></a>Özel iletiler

::: moniker range="vs-2017"

Standart dil sunucusu protokolüne dahil olmayan dil sunucusuna ileti geçirmeyi ve iletileri almayı kolaylaştırmak için API 'Ler vardır. Özel iletileri işlemek için dil istemci sınıfınıza [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) arabirimini uygulayın. [Vs-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) kitaplığı, dil istemciniz ve dil sunucunuz arasında özel iletiler iletmek için kullanılır. LSP dil istemci uzantınız diğer Visual Studio uzantılarına benzer olduğundan, özel iletiler aracılığıyla uzantınızın Visual Studio (diğer Visual Studio apı 'leri kullanarak) ek özellikler eklemeye karar verebilirsiniz.

#### <a name="receive-custom-messages"></a>Özel iletiler al

Dil sunucusundan özel iletiler almak için, [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) üzerinde [Custommessagetarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017&preserve-view=true) özelliğini uygulayın ve özel iletilerinizi nasıl işleyeceğinizi bilen bir nesne döndürün. Aşağıdaki örneğe bakın:

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

#### <a name="send-custom-messages"></a>Özel iletiler gönder

Dil sunucusuna özel iletiler göndermek için [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true)üzerinde [Attachforcustommessageasync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017&preserve-view=true) metodunu uygulayın. Bu yöntem, dil sunucunuz başlatıldığında ve iletileri almaya hazırsa çağrılır. Bir [jsonrpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) nesnesi parametre olarak geçirilir, böylece [vs-streamjsonrpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API 'lerini kullanarak dil sunucusuna ileti gönderebilirsiniz. Aşağıdaki örneğe bakın:

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

Bazen bir uzantı geliştiricisi, dil sunucusuna gönderilen ve alınan LSP iletilerini ele almak isteyebilir. Örneğin, bir uzantı geliştiricisi belirli bir LSP iletisi için gönderilen ileti parametresini değiştirmek veya bir LSP özelliği için dil sunucusundan döndürülen sonuçları değiştirmek isteyebilir (örneğin, tamamlamalar). Bu gerekli olduğunda, uzantı geliştiricileri LSP iletilerini ele almak için MiddleLayer API 'sini kullanabilir.

Her bir LSP iletisinin, ele geçirme için kendi orta katman arabirimi vardır. Belirli bir iletiyi ele almak için, bu ileti için orta katman arabirimini uygulayan bir sınıf oluşturun. Ardından, dil istemci sınıfınıza [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) arabirimini uygulayın ve [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017&preserve-view=true) özelliğinde nesnenizin bir örneğini döndürün. Aşağıdaki örneğe bakın:

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

::: moniker-end

::: moniker range="vs-2019"

Standart dil sunucusu protokolüne dahil olmayan dil sunucusuna ileti geçirmeyi ve iletileri almayı kolaylaştırmak için API 'Ler vardır. Özel iletileri işlemek için dil istemci sınıfınıza [ILanguageClientCustomMessage2](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage2) arabirimini uygulayın. [Vs-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) kitaplığı, dil istemciniz ve dil sunucunuz arasında özel iletiler iletmek için kullanılır. LSP dil istemci uzantınız diğer Visual Studio uzantılarına benzer olduğundan, özel iletiler aracılığıyla uzantınızın Visual Studio (diğer Visual Studio apı 'leri kullanarak) ek özellikler eklemeye karar verebilirsiniz.

#### <a name="receive-custom-messages"></a>Özel iletiler al

Dil sunucusundan özel iletiler almak için, [ILanguageClientCustomMessage2](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage2) üzerinde [CustomMessageTarget] ((/DotNet/api/Microsoft.VisualStudio.languageserver.Client.ilanguageclientcustommessage.custommessagetarget) özelliğini uygulayın ve özel iletilerinizi nasıl işleyeceğinizi bilen bir nesne döndürün. Aşağıdaki örneğe bakın:

(/DotNet/api/Microsoft.VisualStudio.languageserver.Client.ilanguageclientcustommessage.custommessagetarget) özelliğini [ILanguageClientCustomMessage2](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage2) ve özel iletilerinizi nasıl işleyeceğinizi bilen bir nesne döndürür. Aşağıdaki örneğe bakın:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage2
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

#### <a name="send-custom-messages"></a>Özel iletiler gönder

Dil sunucusuna özel iletiler göndermek için [ILanguageClientCustomMessage2](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage2)üzerinde [Attachforcustommessageasync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage2.attachforcustommessageasync) metodunu uygulayın. Bu yöntem, dil sunucunuz başlatıldığında ve iletileri almaya hazırsa çağrılır. Bir [jsonrpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) nesnesi parametre olarak geçirilir, böylece [vs-streamjsonrpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API 'lerini kullanarak dil sunucusuna ileti gönderebilirsiniz. Aşağıdaki örneğe bakın:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage2
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

Bazen bir uzantı geliştiricisi, dil sunucusuna gönderilen ve alınan LSP iletilerini ele almak isteyebilir. Örneğin, bir uzantı geliştiricisi belirli bir LSP iletisi için gönderilen ileti parametresini değiştirmek veya bir LSP özelliği için dil sunucusundan döndürülen sonuçları değiştirmek isteyebilir (örneğin, tamamlamalar). Bu gerekli olduğunda, uzantı geliştiricileri LSP iletilerini ele almak için MiddleLayer API 'sini kullanabilir.

Belirli bir iletiyi ele almak için [ILanguageClientMiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientmiddlelayer) arabirimini uygulayan bir sınıf oluşturun. Ardından, dil istemci sınıfınıza [ILanguageClientCustomMessage2](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage2) arabirimini uygulayın ve [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage2.middlelayer) özelliğinde nesnenizin bir örneğini döndürün. Aşağıdaki örneğe bakın:

```csharp
public class MockLanguageClient : ILanguageClient, ILanguageClientCustomMessage2
{
  public object MiddleLayer => DiagnosticsFilterMiddleLayer.Instance;

  private class DiagnosticsFilterMiddleLayer : ILanguageClientMiddleLayer
  {
    internal readonly static DiagnosticsFilterMiddleLayer Instance = new DiagnosticsFilterMiddleLayer();

    private DiagnosticsFilterMiddleLayer() { }

    public bool CanHandle(string methodName)
    {
      return methodName == "textDocument/publishDiagnostics";
    }

    public async Task HandleNotificationAsync(string methodName, JToken methodParam, Func<JToken, Task> sendNotification)
    {
      if (methodName == "textDocument/publishDiagnostics")
      {
        var diagnosticsToFilter = (JArray)methodParam["diagnostics"];
        // ony show diagnostics of severity 1 (error)
        methodParam["diagnostics"] = new JArray(diagnosticsToFilter.Where(diagnostic => diagnostic.Value<int?>("severity") == 1));

      }
      await sendNotification(methodParam);
    }

    public async Task<JToken> HandleRequestAsync(string methodName, JToken methodParam, Func<JToken, Task<JToken>> sendRequest)
    {
      return await sendRequest(methodParam);
    }
  }
}
```

::: moniker-end

Orta katman özelliği hala geliştirme aşamasındadır ve henüz kapsamlı değildir.

## <a name="sample-lsp-language-server-extension"></a>Örnek LSP dil sunucusu uzantısı

Visual Studio ' de LSP istemci apı 'sini kullanarak örnek bir uzantının kaynak kodunu görmek için bkz. vssdk-Extensibility-Samples [LSP örneği](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>SSS

**Visual Studio ' de daha zengin özellik desteği sağlamak üzere LSP dil sunucunuzu tamamlamak üzere özel bir proje sistemi oluşturmak istiyorum, bunu yapmakla nasıl gidebilirim?**

Visual Studio ' de LSP tabanlı dil sunucuları desteği, [klasörü aç özelliğini](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) kullanır ve özel bir proje sistemi gerektirecek şekilde tasarlanmıştır. Aşağıdaki yönergeleri izleyerek kendi özel proje sisteminizi [oluşturabilirsiniz, ancak](https://github.com/Microsoft/VSProjectSystem)ayarlar gibi bazı özellikler çalışmayabilir. LSP dil sunucuları için varsayılan başlatma mantığı, şu anda açılmakta olan klasörün kök klasör konumunu geçirmektir, bu nedenle özel bir proje sistemi kullanıyorsanız, dil sunucunuzun düzgün şekilde başlayabilmesini sağlamak için başlatma sırasında özel mantık sağlamanız gerekebilir.

**Nasıl yaparım? hata ayıklayıcı desteği eklensin mi?**

Gelecekteki bir sürümde [ortak hata ayıklama Protokolü](https://code.visualstudio.com/docs/extensionAPI/api-debugging) için destek sağlayacağız.

**Daha önceden desteklenen bir dil hizmeti yüklüyse (örneğin, JavaScript), ek özellikler sunan bir LSP dil sunucu uzantısı yüklemeye devam edebilir miyim?**

Evet, ancak tüm özellikler düzgün çalışmayacak. LSP Language Server Extensions için Ultimate hedefi, Visual Studio tarafından yerel olarak desteklenmeyen dil hizmetlerini etkinleştirmektir. LSP dil sunucularını kullanarak ek destek sunan uzantılar oluşturabilirsiniz, ancak bazı özellikler (IntelliSense gibi) sorunsuz bir deneyim olmayacaktır. Genel olarak, LSP dil sunucu uzantılarının, mevcut olanları genişletmeden yeni dil deneyimleri sağlamak için kullanılması önerilir.

**Tamamlanmış LSP dil sunucusu VSıX 'i nerede yayımlayabilirim?**

Market yönergelerine [buradan](walkthrough-publishing-a-visual-studio-extension.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [diğer diller için Visual Studio düzenleyicisi desteği ekleyin](../ide/adding-visual-studio-editor-support-for-other-languages.md)
