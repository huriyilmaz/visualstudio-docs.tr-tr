---
title: Dil Sunucusu Protokolü uzantısı ekleme | Microsoft Docs
description: Dil Sunucusu Protokolü'Visual Studio (LSP) temel alan bir dil sunucusunu tümleştiren bir uzantı oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 250c164a6e9537b6ec972571ecb83efb2f0aebe3d8f7d9e1b02c5e84260158d6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435080"
---
# <a name="add-a-language-server-protocol-extension"></a>Dil Sunucusu Protokolü uzantısı ekleme

Dil Sunucusu Protokolü (LSP), çeşitli kod düzenleyicilerine dil hizmeti özellikleri sağlamak için kullanılan JSON RPC v2.0 şeklinde ortak bir protokoldür. Geliştiriciler protokolü kullanarak tek bir dil sunucusu yazarak IntelliSense, hata tanılama, tüm başvuruları bulma gibi dil hizmeti özelliklerini LSP'yi destekleyen çeşitli kod düzenleyicilerine bulabilir. Geleneksel olarak Visual Studio dil hizmetleri, söz dizimi vurgulama gibi temel işlevler sağlamak için TextMate dil bilgisi dosyaları kullanılarak veya daha zengin veriler sağlamak için tam Visual Studio genişletilebilirlik API'lerini kullanan özel dil hizmetleri yazarak eklenebilir. LSP Visual Studio desteğiyle birlikte üçüncü bir seçenek vardır.

![Visual Studio'de dil sunucusu protokolü Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Dil Sunucusu Protokolü

![dil sunucusu protokol uygulaması](media/lsp-implementation.png)

Bu makalede, LSP tabanlı Visual Studio kullanan bir uzantının nasıl oluşturularak nasıl oluşturul açıklanmıştır. Daha önce LSP tabanlı bir dil sunucusu geliştirdiğini ve bunu yalnızca bu sunucuyla tümleştirip Visual Studio.

Veri akışı Visual Studio için, dil sunucuları herhangi bir akış Visual Studio mekanizması aracılığıyla istemciyle (Visual Studio) iletişim kurabilir, örneğin:

* Standart giriş/çıkış akışları
* Adlandırılmış kanallar
* Yuvalar (yalnızca TCP)

LSP'nin amacı ve Visual Studio ürünün parçası Visual Studio dil hizmetleri Visual Studio. Bu hizmet, mevcut dil hizmetlerini (C#gibi) Visual Studio. Mevcut dilleri genişletmek için dil hizmetinin genişletilebilirlik kılavuzuna (örneğin, ["Roslyn" .NET Compiler Platform)](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)bakın veya bkz. Düzenleyiciyi ve dil [hizmetlerini genişletme.](../extensibility/extending-the-editor-and-language-services.md)

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
> 2017 Visual Studio 15.8 sürümünden itibaren, ortak Dil Sunucusu Protokolü desteği Visual Studio. Önizleme Dil Sunucusu İstemci [VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) sürümünü kullanarak LSP uzantıları yaptıysanız, 15.8 veya daha yeni bir sürüme yükseltin. LSP uzantılarınızı yeniden çalışmak için aşağıdaki adımları gerçekleştirin:
>
> 1. Microsoft Visual Studio Sunucusu Protokolü Önizleme VSIX'i kaldırın.
>
>    Sürüm 15.8'den başlayarak, sürümde her yükseltme Visual Studio VSIX önizlemesi otomatik olarak algılanır ve kaldırılır.
>
> 2. Nuget başvurularınızı LSP paketleri için en son önizleme dışı [sürüme güncelleştirin.](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)
>
> 3. VSIX bildiriminde Microsoft Visual Studio Sunucusu Protokolü Önizleme VSIX'e bağımlılığı kaldırın.
>
> 4. VSIX'inizin 2017 Visual Studio 15.8 Preview 3 sürümünü yükleme hedefi için alt sınır olarak belirtir.
>
> 5. Yeniden derleyin ve dağıtın.

### <a name="create-a-vsix-project"></a>VSIX projesi oluşturma

LSP tabanlı bir dil sunucusu kullanarak dil hizmeti uzantısı oluşturmak için öncelikle VS örneğine **Visual Studio** iş yükünün yüklü olduğundan emin olun.

Ardından, Visual C# Genişletilebilirlik VSIX dosyası için Dosya Yeni Project giderek yeni bir  >    >    >    >  **VSIX Project:**

![vsix projesi oluşturma](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Dil sunucusu ve çalışma zamanı yüklemesi

Varsayılan olarak, Visual Studio'de LSP tabanlı dil sunucularını desteklemek için oluşturulan uzantılar, dil sunucularını veya bunları yürütmek için gereken çalışma zamanlarını içermez. Uzantı geliştiricileri, gerekli dil sunucularını ve çalışma zamanlarını dağıtmakla sorumludur. Bunu yapmak için çeşitli yollar vardır:

* Dil sunucuları VSIX'e içerik dosyaları olarak katıştırabilirsiniz.
* Dil sunucusunu ve/veya gerekli çalışma zamanlarını yüklemek için bir MSI oluşturun.
* Kullanıcılara çalışma zamanlarını ve dil sunucularını nasıl edinecektir konusunda bilgi sağlayan Market yönergelerini sağlar.

### <a name="textmate-grammar-files"></a>TextMate dil bilgisi dosyaları

LSP, diller için metin renklendirmesi sağlama belirtimi eklemez. Uzantı geliştiricileri, Visual Studio dillere özel renklendirme sağlamak için TextMate dil bilgisi dosyasını kullanabilir. Özel TextMate dil bilgisi veya tema dosyaları eklemek için şu adımları izleyin:

1. Uzantınız içinde "Dilbilgisi" adlı bir klasör oluşturun (veya seçtiğiniz herhangi bir ad olabilir).

2. Grammars *klasörünün* içinde, özel renklendirme sağlamak istediğiniz *\* .tmlanguage*, *\* .plist*, *\* .tmtheme* veya *\* .json* dosyalarını dahil edin.

   > [!TIP]
   > *.tmtheme dosyası,* kapsamların sınıflandırmalar (renk anahtarları Visual Studio) ile nasıl eşle olduğunu tanımlar. Rehberlik için *%ProgramFiles(x86)%\Microsoft Visual Studio \\ \<version> \\ \<SKU> \Common7\IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg* dizinindeki genel *.tmtheme* dosyasına başvurabilirsiniz.

3. Bir *.pkgdef dosyası* oluşturun ve aşağıdakine benzer bir satır ekleyin:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Dosyalara sağ tıklayın ve Özellikler'i **seçin.** Derleme **eylemlerini** İçerik **olarak,** **VSIX'e Dahil Edin özelliğini ise** true olarak **değiştirme.**

Önceki adımları tamamladıktan sonra, paketin yükleme dizinine 'MyLang' adlı bir depo kaynağı olarak bir *Grammars* klasörü eklenir ('MyLang', yalnızca bir açıklama adıdır ve herhangi bir benzersiz dize olabilir). Bu dizinde yer alan tüm dil bilgisi (*.tmlanguage* dosyaları) ve tema dosyaları (*.tmtheme* dosyaları) potansiyel olarak toplanır ve TextMate ile sağlanan yerleşik dil bilgisi yer değiştirir. Dil bilgisi dosyasının bildirilen uzantıları, açılan dosyanın uzantısıyla eş olursa TextMate adımını atlar.

## <a name="create-a-simple-language-client"></a>Basit bir dil istemcisi oluşturma

### <a name="main-interface---ilanguageclient"></a>Ana arabirim - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)

VSIX projenizi oluşturduk sonra aşağıdaki NuGet paketlerini projenize ekleyin:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Önceki adımları tamamlandıktan sonra NuGet paketine bağımlılık edindikten sonra Newtonsoft.Jsve StreamJsonRpc paketleri de projenize eklenir. **Bu yeni sürümlerin uzantının hedeflediği** sürümde yüklü olacağını Visual Studio bu paketleri güncelleştirin. Derlemeler VSIX'inize dahil edilecektir; bunun yerine, bunlar yükleme dizininden Visual Studio olur. Derlemelerin kullanıcının makinesine yüklenmiş olandan daha yeni bir sürümüne başvurursanız, uzantınız çalışmaz.

Daha sonra, LSP tabanlı bir dil sunucusuna bağlanan dil istemcileri için gereken ana arabirim olan [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true) arabirimini uygulayan yeni bir sınıf oluşturabilirsiniz.

Aşağıda bir örnek ve ardından ve bir örnek ve bir örnek ve ardından ve daha sonra yer alan bir örnek

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

Uygulanması gereken ana yöntemler [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) ve [ActivateAsync'tir.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true) [OnLoadedAsync,](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) uzantınızı Visual Studio ve dil sunucunuz başlamaya hazır olduğunda çağrılır. Bu yöntemde, dil sunucusunun başlatılmalıdır sinyal için [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) temsilcisini hemen çağırabilirsiniz veya ek mantık çalıştırarak [StartAsync'i](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) daha sonra çağırabilirsiniz. **Dil sunucuyu etkinleştirmek için startAsync'i bir noktada çağırmanız gerekir.**

[ActivateAsync,](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true) [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) temsilcisi çağrılarak sonunda çağrılan yöntemdir. Dil sunucusunu başlatma ve bağlantı kurma mantığını içerir. Sunucuya yazma ve sunucudan okuma için akışlar içeren bir bağlantı nesnesi döndürüldü. Burada atılan tüm özel durumlar yakalanıp kullanıcıya bilgi çubuğu iletisiyle Visual Studio.

### <a name="activation"></a>Etkinleştirme

Dil istemci sınıfınız uygulamaya alındıktan sonra, istemci sınıfınıza nasıl yük olacağını ve etkinleştiril olacağını tanımlamak için iki Visual Studio gerekir:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio [genişletilebilirlik](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) noktalarını yönetmek için MEF (Managed Extensibility Framework) kullanır. Dışarı [Aktarma](/dotnet/api/system.componentmodel.composition.exportattribute) özniteliği, Visual Studio bu sınıfın bir uzantı noktası olarak top olmalı ve uygun zamanda yüklenmeli olduğunu gösterir.

MEF'i kullanmak için, VSIX bildiriminde MEF'i varlık olarak da tanımlamanız gerekir.

VSIX bildirim tasarımcınızı açın ve Varlıklar **sekmesine** gidin:

![MEF varlığı ekleme](media/lsp-add-asset.png)

Yeni **varlık oluşturmak** için Yeni'ye tıklayın:

![MEF varlığı tanımlama](media/lsp-define-asset.png)

* **Tür:** Microsoft.VisualStudio.MefComponent
* **Kaynak:** Geçerli çözümde bir proje
* **Project:**[Projeniz]

### <a name="content-type-definition"></a>İçerik türü tanımı

Şu anda LSP tabanlı dil sunucusu uzantınızı yüklemenin tek yolu dosya içerik türüne göredir. Yani, dil istemci sınıfınızı tanımlarken [(ILanguageClient'ı](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)uygulayan), açıldığında uzantının yüklemesini neden olacak dosya türlerini tanımlamanız gerekir. Tanımlı içerik türünüzle eşan hiçbir dosya açılamıyorsa uzantınız yüklenmez.

Bu, bir veya daha fazla sınıf tanımlayarak `ContentTypeDefinition` yapılır:

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

Önceki örnekte, *.bar* dosya uzantısıyla sona eren dosyalar için bir içerik türü tanımı oluşturulur. İçerik türü tanımına "bar" adı verilir ve [CodeRemoteContentTypeName'den türetilleri gerekir.](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017&preserve-view=true)

İçerik türü tanımı ekledikten sonra dil istemci sınıfına dil istemci uzantınızı ne zaman yükleyebilirsiniz?

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

LSP dil sunucuları için destek eklemek için bu sunucularda kendi proje sisteminizi Visual Studio. Müşteriler dil hizmetinizi kullanmaya başlamak için tek bir Visual Studio veya klasör açabilir. Aslında, LSP dil sunucuları desteği yalnızca açık klasör/dosya senaryolarında çalışacak şekilde tasarlanmıştır. Özel bir proje sistemi uygulanırsa bazı özellikler (ayarlar gibi) çalışmaz.

## <a name="advanced-features"></a>Gelişmiş özellikler

### <a name="settings"></a>Ayarlar

Özel dil sunucusuna özgü ayarlar için destek mevcuttur, ancak hala geliştirme sürecindedir. Ayarlar, dil sunucusunun neleri desteklediğine özgü ve genellikle dil sunucusunun verileri nasıl yaymalarını denetlemesi gerekir. Örneğin, bir dil sunucusunda bildirilen maksimum hata sayısı için bir ayar olabilir. Uzantı yazarları, kullanıcılar tarafından belirli projeler için değiştirilebilir bir varsayılan değer tanımlar.

LSP dil hizmeti uzantınıza ayarlar için destek eklemek için aşağıdaki adımları izleyin:

1. Projenize, ayarları ve varsayılan *MockLanguageExtensionSettings.js* içeren bir JSON dosyası (örneğin,MockLanguageExtensionSettings.js) ekleyin. Örnek:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. JSON dosyasına sağ tıklayın ve Özellikler'i **seçin.** Derleme **eylemlerini** "İçerik" ve "VSIX'e dahil edin" özelliğini true olarak **değiştirebilirsiniz.**

3. ConfigurationSections'ı uygulama ve JSON dosyasında tanımlanan ayarlar için ön eklerin listesini iade edin (Visual Studio Code'de bu, package.js'daki yapılandırma bölümü adıyla eşler):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Projeye bir .pkgdef dosyası ekleyin (yeni metin dosyası ekleyin ve dosya uzantısını .pkgdef olarak değiştirebilirsiniz). pkgdef dosyası şu bilgileri içermeli:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Örnek:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. .pkgdef dosyasına sağ tıklayın ve Özellikler'i **seçin.** Derleme **eylemlerini** İçerik **ve** **VSIX'e Dahil Edin özelliğini** true olarak **değiştirme.**

6. *source.extension.vsixmanifest dosyasını* açın ve Varlık sekmesinde bir **varlık** ekleyin:

   ![vspackage varlığı düzenleme](media/lsp-add-vspackage-asset.png)

   * **Tür:** Microsoft.VisualStudio.VsPackage
   * **Kaynak:** Dosya sistemi üzerinde dosya
   * **Yol:** *[.pkgdef dosyanıza* giden yol]

### <a name="user-editing-of-settings-for-a-workspace"></a>Çalışma alanı için ayarları kullanıcı düzenleme

1. Kullanıcı, sunucunuza ait dosyaları içeren bir çalışma alanını açar.
2. Kullanıcı , *.vs klasörüne üzerinde* VSWorkspaceSettings.js *ekler.*
3. Kullanıcı, sunucu tarafındanVSWorkspaceSettings.js *için* dosyanın dosya üzerinde dosyasına bir satır ekler. Örnek:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Tanılama izlemeyi etkinleştirme

Tanılama izleme, istemci ile sunucu arasındaki tüm iletilerin çıkışını yapmak için etkinleştirilebilir ve bu da hata ayıklama sırasında yararlı olabilir. Tanılama izlemeyi etkinleştirmek için şunları yapın:

1. Çalışma alanı ayarları dosyasını açın veya *VSWorkspaceSettings.jsaçın* ("Çalışma alanı için ayarları kullanıcı düzenleme".
2. Ayarlar json dosyasına aşağıdaki satırı ekleyin:

```json
{
    "foo.trace.server": "Off"
}
```

İzleme ayrıntılılığı için üç olası değer vardır:

* "Kapalı": izleme tamamen kapalı
* "İletiler": izleme açık ancak yalnızca yöntem adı ve yanıt kimliği izlandı.
* "Ayrıntılı": izleme açık; rpc iletinin tamamı izlandı.

İzleme açık olduğunda içerik *%temp%\VisualStudio\LSP* dizininde bir dosyaya yazılır. Günlük, *[LanguageClientName]-[Datetime Stamp].log adlandırma biçimini izler.* Şu anda izleme yalnızca açık klasör senaryoları için etkinleştirilebilir. Dil sunucusunu etkinleştirmek için tek bir dosya açmak için tanılama izleme desteğine sahip değildir.

### <a name="custom-messages"></a>Özel iletiler

İleti geçirmeyi ve standart Dil Sunucusu Protokolü'ne parçası olmayan dil sunucusundan iletileri almayı kolaylaştıran API'ler vardır. Özel iletileri işlemek için dil istemci [sınıfınıza ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) arabirimini kullanın. [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) kitaplığı, dil istemciniz ve dil sunucunuz arasında özel iletiler iletmek için kullanılır. LSP dil istemci uzantınız diğer tüm Visual Studio uzantıları gibi olduğu için, özel iletiler aracılığıyla uzantınıza Visual Studio 'ye (diğer Visual Studio API'lerini kullanarak) ek özellikler (LSP tarafından desteklenmiyor) eklemeye karar veebilirsiniz.

#### <a name="receive-custom-messages"></a>Özel iletiler alma

Dil sunucusundan özel iletiler almak [için, ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) üzerinde [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017&preserve-view=true) özelliğini kullanın ve özel iletilerinizi nasıl işley bilir bir nesne geri döner. Aşağıdaki örneğe bakın:

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

Dil sunucusuna özel iletiler göndermek için [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true)üzerinde [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017&preserve-view=true) yöntemini kullanın. Bu yöntem, dil sunucunuz başlatıldığında ve iletileri almaya hazır olduğunda çağrılır. Bir [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) nesnesi parametre olarak geçirildi. Daha sonra [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API'lerini kullanarak dil sunucusuna ileti göndermeye devam edersiniz. Aşağıdaki örneğe bakın:

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

Bazen uzantı geliştiricisi, dil sunucusuna gönderilen ve dil sunucusundan alınan LSP iletilerine müdahale etmek istiyor olabilir. Örneğin, uzantı geliştiricisi belirli bir LSP iletisi için gönderilen ileti parametresini değiştirmek veya bir LSP özelliği için dil sunucusundan döndürülen sonuçları değiştirmek (örneğin tamamlamalar) istiyor olabilir. Bu gerekli olduğunda uzantı geliştiricileri LSP iletilerine müdahale etmek için MiddleLayer API'sini kullanabilir.

Her LSP iletisi kesme için kendi orta katman arabirimine sahiptir. Belirli bir iletiyi araya etmek için, bu ileti için orta katman arabirimini uygulayan bir sınıf oluşturun. Ardından, [dil istemci sınıfınıza ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) arabirimini uygulayın ve [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017&preserve-view=true) özelliğinde nesnenizin bir örneğini dönüş. Aşağıdaki örneğe bakın:

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

Orta katman özelliği hala geliştirme aşamasındadır ve henüz kapsamlı değildir.

## <a name="sample-lsp-language-server-extension"></a>Örnek LSP dil sunucusu uzantısı

Visual Studio'de LSP istemci API'sini kullanarak örnek uzantının kaynak kodunu görmek için bkz. VSSDK-Genişletilebilirlik-Örnekler [LSP örneği.](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)

## <a name="faq"></a>SSS

**Visual Studio'da daha zengin özellik desteği sağlamak için LSP dil sunucuma ek olarak özel bir proje sistemi oluşturmak istiyorum, bunu nasıl yapabilirim?**

Visual Studio'de LSP tabanlı dil sunucuları için destek, [](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) klasör açma özelliğine dayalıdır ve özel bir proje sistemi gerektirmek için tasarlanmıştır. Buradaki yönergeleri izleyerek kendi özel proje [sisteminizi oluşturabilirsiniz,](https://github.com/Microsoft/VSProjectSystem)ancak ayarlar gibi bazı özellikler çalışmayabilirsiniz. LSP dil sunucuları için varsayılan başlatma mantığı, şu anda açık olan klasörün kök klasör konumunun geçmesidir, bu nedenle özel bir proje sistemi kullanıyorsanız, dil sunucunuza düzgün bir şekilde başlay için başlatma sırasında özel mantık sağlamanız gerekebilir.

**Nasıl yaparım? ayıklayıcı desteği ekliy misiniz?**

Gelecekteki bir sürümde ortak [hata ayıklama protokolü için](https://code.visualstudio.com/docs/extensionAPI/api-debugging) destek sağlıyoruz.

**Vs tarafından desteklenen bir dil hizmeti zaten yüklüyse (örneğin, JavaScript), yine de ek özellikler (linting gibi) sunan bir LSP dil sunucusu uzantısı yükleyebilir miyim?**

Evet, ancak tüm özellikler düzgün çalışmaz. LSP dil sunucusu uzantılarının nihai hedefi, yerel olarak desteklenen dil hizmetlerini etkinleştirmektir Visual Studio. LSP dil sunucularını kullanarak ek destek sunan uzantılar oluşturabilirsiniz, ancak bazı özellikler (IntelliSense gibi) sorunsuz bir deneyim olmayacaktır. Genel olarak, LSP dil sunucusu uzantılarının mevcut dil deneyimlerini genişletmek için değil, yeni dil deneyimleri sağlamak için kullanılmaları önerilir.

**Tamamlanmış LSP dil sunucum VSIX'i nerede yayımlarim?**

Market yönergelerine [buradan bakın.](walkthrough-publishing-a-visual-studio-extension.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Diğer Visual Studio için düzenleyici desteği ekleme](../ide/adding-visual-studio-editor-support-for-other-languages.md)
