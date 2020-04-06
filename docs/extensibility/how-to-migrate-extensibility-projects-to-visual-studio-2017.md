---
title: "Nasıl Yapılır: Extensibility Projects'i Visual Studio 2017'ye Geçirin | Microsoft Dokümanlar"
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b0cae0261b185ee08400e5f3d25735634663f54a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710986"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Nasıl Yapılır: Genişletilebilirlik projelerini Visual Studio 2017'ye geçirin

Bu belge, genişletilebilirlik projelerinin Visual Studio 2017'ye nasıl yükseltilen olduğunu açıklar. Proje dosyalarının nasıl güncelleştirilenin yanı sıra, uzantı bildirimi sürüm 2'den (VSIX v2) yeni sürüm 3 VSIX manifesto formatına (VSIX v3) nasıl yükseltilir.

## <a name="install-visual-studio-2017-with-required-workloads"></a>Gerekli iş yükleri ile Visual Studio 2017'yi yükleyin

Yüklemenizin aşağıdaki iş yüklerini içerdiğinden emin olun:

* .NET masaüstü geliştirme
* Visual Studio uzantısı geliştirme

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Visual Studio 2017'de VSIX Çözümlerini Açın

Tüm VSIX projeleri Visual Studio 2017 için önemli bir sürüm tek yönlü yükseltme gerektirir.

Proje dosyası (örneğin **.csproj)* güncellenecektir:

* MinimumVisualStudioVersion - şimdi 15,0 olarak ayarlanır
* OldToolsVersion (daha önce varsa) - şimdi 14,0 olarak ayarlanır

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Microsoft.VSSDK.BuildTools NuGet paketini güncelleştirin

> [!Note]
> Çözümünüz Microsoft.VSSDK.BuildTools NuGet paketine başvurulmuyorsa, bu adımı atlayabilirsiniz.

Uzantınızı yeni VSIX v3 (sürüm 3) formatında oluşturmak için, çözümünüzün yeni VSSDK Build Tools ile oluşturulması gerekir. Bu, Visual Studio 2017 ile yüklenecektir, ancak VSIX v2 uzantınız NuGet aracılığıyla eski bir sürüme başvuruda bulunuyor olabilir. Bu nedenle, çözümünüz için Microsoft.VSSDK.BuildTools NuGet paketinin bir güncelleştirmesini el ile yüklemeniz gerekir.

NuGet başvurularını Microsoft.VSSDK.BuildTools'a güncellemek için:

* Çözüme sağ tıklayın ve **Çözüm için NuGet Paketlerini Yönet'i**seçin.
* **Güncelleştirmeler** sekmesine gidin.
* **Microsoft.VSSDK.BuildTools (en son sürüm) seçeneğini**belirleyin.
* **Basın Güncelleme**.

![VSSDK oluşturma araçları](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>VSIX uzantı bildiriminde değişiklik yapma

Kullanıcının Visual Studio yüklemesinin uzantıyı çalıştırmak için gereken tüm derlemelere sahip olduğundan emin olmak için, uzantı bildirimi dosyasındaki tüm ön koşul bileşenlerini veya paketlerini belirtin. Bir kullanıcı uzantıyı yüklemeye çalıştığında, VSIXInstaller tüm ön koşulların yüklü olup olmadığını denetler. Bazıları eksikse, kullanıcıdan eksik bileşenleri uzantı yükleme işleminin bir parçası olarak yüklemesi istenir.

> [!Note]
> En azından, tüm uzantıları bir ön koşul olarak Visual Studio çekirdek düzenleyici bileşeni belirtmelidir.

* Uzantı bildirimi dosyasını (genellikle *source.extension.vsixmanifest*olarak adlandırılır) edin.
* 15.0 içerir. `InstallationTarget`
* Gerekli yükleme ön koşulları ekleyin (aşağıdaki örnekte gösterildiği gibi).
  * Yükleme ön koşulları için yalnızca Bileşen taşırım'ları belirtmenizi öneririz.
  * Bileşen kimliklerini tanımlama yönergeleri için bu belgenin sonundaki [bölüme](#find-component-ids)bakın.

Örnek:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Seçenek: VSIX uzantı bildiriminde değişiklik yapmak için tasarımcıyı kullanın

Manifest XML'i doğrudan düzenlemek yerine, ön koşulları seçmek için Manifesto Tasarımcısı'ndaki yeni **Önkoşullar** sekmesini kullanabilirsiniz ve XML sizin için güncellenecektir.

> [!Note]
> Manifest Designer yalnızca geçerli Visual Studio örneğinde yüklü olan Bileşenleri (İş Yükleri veya Paketler değil) seçmenize izin verir. Şu anda yüklü olmayan bir iş yükü, paket veya bileşen için ön koşul eklemeniz gerekiyorsa, bildirim XML'i doğrudan edin.

* *Kaynak.extension.vsixmanifest [Tasarım]* dosyasını açın.
* **Önkoşullar** sekmesini seçin ve **Yeni** düğmesine basın.

   ![VSIX manifesto tasarımcısı](media/vsix-manifest-designer.png)

* **Yeni Önkoşul ekle** penceresi açılır.

   ![vsix önkoşul ekle](media/add-vsix-prerequisite.png)

* **Ad** için açılır sayfaya tıklayın ve istenen ön koşulu seçin.
* Gerekirse sürümü güncelleştirin.

   > [!Note]
   > Sürüm alanı, bileşenin bir sonraki ana sürümüne kadar uzanan (ancak dahil olmayan) bir aralıkla, şu anda yüklü olan bileşenin sürümüyle önceden doldurulacaktır.

   ![roslyn ön koşul eklemek](media/add-roslyn-prerequisite.png)

* **Tamam**'a basın.

## <a name="update-debug-settings-for-the-project"></a>Proje için Hata Ayıklama ayarlarını güncelleştirme

Visual Studio'nun deneysel bir örneğinde uzantınızı hata ayıklamak istiyorsanız, **Hata** > **Ayıklama Başlatma eylemi** için proje ayarlarının Başlangıç dış programına sahip olduğundan emin **olun:** Visual Studio 2017 kurulumunuzun *devenv.exe* dosyasına ayarlanmış değer.

Şu şekilde görünebilir: *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![harici programı başlatma](media/start-external-program.png)

> [!Note]
> Hata Ayıklama Başlangıç Eylemi genellikle *.csproj.user* dosyasında depolanır. Bu dosya genellikle *.gitignore* dosyasına dahil edilir ve bu nedenle, kaynak denetimine taahhüt edildiğinde normalde diğer proje dosyalarıyla birlikte kaydedilmez. Bu nedenle, çözümünüzü kaynak denetiminden yeni çıkardıysanız, büyük olasılıkla projenin Start Action için ayarlanmış değerleri olmayacaktır. Visual Studio 2017 ile oluşturulan yeni VSIX projelerinde varsayılan olarak geçerli Visual Studio yükleme dizinini işaret eden bir *.csproj.user* dosyası oluşturulacaktır. Ancak bir VSIX v2 uzantısı geçiş iseniz, *.csproj.user* dosyası önceki Visual Studio sürümü yükleme dizinine başvurular içerecektir muhtemeldir. **Hata Ayıklama** > **Başlatma eyleminin** değerini ayarlamak, uzantınızı hata ayıklamaya çalıştığınızda doğru Visual Studio deneme örneğinin başlatılmasını sağlar.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Uzantıncanın doğru bir şekilde inşa edilsin (VSIX v3 olarak)

* VSIX projesini oluşturun.
* Oluşturulan VSIX'nin zip'ini aç.
  * Varsayılan olarak, VSIX dosyası *bin/Debug* veya *bin/Release* as *[YourCustomExtension].vsix*içinde yaşar.
  * İçeriği kolayca görüntülemek için *.vsix'i* *.zip'e* yeniden adlandırın.
* Üç dosyanın varlığını denetleyin:
  * *Vsixmanifest*
  * *manifest.json*
  * *catalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Gerekli tüm ön koşulların ne zaman yüklendiğinde kontrol edin

VSIX'nin gerekli tüm ön koşullar yüklü bir makineye başarıyla yüklenmesini test edin.

> [!Note]
> Herhangi bir uzantı yüklemeden önce, lütfen Visual Studio'nun tüm örneklerini kapatın.

Uzantıyı yüklemeye çalış:

* Visual Studio 2017 Hakkında

![Visual Studio 2017'de VSIX yükleyici](media/vsixinstaller-vs-2017.png)

* İsteğe bağlı: Visual Studio'nun önceki sürümlerini kontrol edin.
  * Geriye dönük uyumluluğu kanıtlıyor.
  * Visual Studio 2012, Visual Studio 2013, Visual Studio 2015 için çalışmalıdır.
* İsteğe bağlı: VSIX Installer Version Checker'ın çeşitli sürümler sunduğunu kontrol edin.
  * Visual Studio'nun önceki sürümlerini içerir (yüklüyse).
  * Visual Studio 2017'yi içerir.

Visual Studio yakın zamanda açıldıysa, şu gibi bir iletişim kutusu görebilirsiniz:

![vs çalışma süreçleri](media/vs-running-processes.png)

İşlemlerin kapanmasını veya görevleri el ile sonlamasını bekleyin. İşlemleri listelenen ada göre veya parantez içinde listelenen PID ile bulabilirsiniz.

> [!Note]
> Visual Studio'nun bir örneği çalışırken bu işlemler otomatik olarak kapanmaz. Diğer kullanıcılar da dahil olmak üzere makinedeki Visual Studio'nun tüm örneklerini kapattığınızdan emin olun, ardından yeniden denemeye devam edin.

## <a name="check-when-missing-the-required-prerequisites"></a>Gerekli ön koşulları kaçırırken kontrol edin

* Önkoşullarda tanımlanan tüm bileşenleri içermeyen Visual Studio 2017'li bir makineye uzantıyı yüklemeye çalış (yukarıda).
* Yüklemenin eksik bileşeni/s'leri tanımladığını ve VSIXInstaller'da ön koşul olarak listeleyip listelemediğini denetleyin.
* Not: Herhangi bir ön koşul uzantısı ile yüklü olması gerekiyorsa yükseklik gereklidir.

![vsixinstaller eksik ön koşul](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Bileşenlere karar verin

Bağımlılıklarınızı ararken, bir bağımlılığın birden çok bileşenle eşlenebildiğini göreceksiniz. Ön koşul olarak hangi bağımlılıkları belirtmeniz gerektiğini belirlemek için, uzantınıza benzer bir işlevsellik olan bir bileşen seçmenizi ve ayrıca kullanıcılarınızı ve ne tür bileşenlerin yüklü olduğunu veya yüklemeyi sorun etmeyeceğini de göz önünde bulundurmanızı öneririz. Ayrıca, uzantılarınızı, gerekli ön koşulların yalnızca uzantınızın çalışmasına izin verecek minimum minimum tutarı karşılayacak şekilde oluşturmanızı ve belirli bileşenler algılanmadığı takdirde ek özelliklerin uykuda olmasını öneririz.

Daha fazla rehberlik sağlamak için, birkaç yaygın uzatma türü ve önerilen ön koşulları belirledik:

Uzantı Türü | Görünen Ad | Kimlik
--- | --- | ---
Düzenleyici | Visual Studio çekirdek editörü | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# ve Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Yönetilen Masaüstü İş Yükü Çekirdeği | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Hata Ayıklayıcısı | Tam Zamanında hata ayıklama | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Bileşen işlerini bulma

Visual Studio ürününe göre sıralanmış bileşenlerin listesi [Visual Studio 2017 iş yükü ve bileşen ii'lerindedir.](/visualstudio/install/workload-and-component-ids?view=vs-2019) Bu bileşen tünelerini, bildiriminizdeki ön koşul tüneleriniz için kullanın.

Hangi bileşenin belirli bir ikili içerdiğinden emin değilseniz, [Bileşen -> İkili eşleme tablosunu](https://aka.ms/vs2017componentid-binaries)indirin.

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Excel sayfasında dört sütun vardır: **Bileşen Adı**, **ComponentId**, **Sürüm**ve İkili / **Dosya Adları**.  Belirli bileşenleri ve ikilileri aramak ve bulmak için filtreleri kullanabilirsiniz.

Tüm başvurularınız için öncelikle hangilerinin çekirdek düzenleyici (Microsoft.VisualStudio.Component.CoreEditor) bileşeninde olduğunu belirleyin.  En azından, çekirdek düzenleyici bileşeninin tüm uzantılar için bir ön koşul olarak belirtilmesi gerekir. Çekirdek düzenleyicide olmayan başvurular arasında, bu başvuruların alt kümelerinden herhangi biri olan bileşenleri bulmak için **İkili / Dosya Adları** bölümüne filtreler ekleyin.

Örnekler:

* Hata ayıklayıcı uzantınız varsa ve projenizin *VSDebugEng.dll* ve *VSDebug.dll*adresine bir referansı olduğunu **biliyorsanız, İkili / Dosya Adları** üstbilgisindeki filtre düğmesini tıklatın.  "VSDebugEng.dll" için arama yapın ve *Tamam'ı*seçin.  Sonraki **tıklayarak İkili / Dosya Adları** başlığındaki filtre düğmesine tekrar tıklayın ve "VSDebug.dll" aramasını yapın.  Onay kutusunu seçin **Filtrelemek için geçerli seçimi ekle** ve **Tamam'ı**seçin.  Şimdi, uzantı türünüzle en çok ilişkili olan bir bileşeni bulmak için **Bileşen Adı'na** bakın. Bu örnekte, Just-In-Time hata ayıklama seçti ve vsixmanifest ekleyin.
* Projenizin hata ayıklama öğeleriyle ilgili olduğunu biliyorsanız, filtre arama kutusundaki "hata ayıklama" üzerinde arama yapabilir ve hangi bileşenlerin adına hata ayıklama içerdiğini görebilirsiniz.

## <a name="specify-a-visual-studio-2017-release"></a>Visual Studio 2017 sürümü belirtin

Uzantınız Visual Studio 2017'nin belirli bir sürümünü gerektiriyorsa, örneğin, 15.3'te yayımlanan bir özelliğe bağlıysa, VSIX **InstallationTarget'ınızdaki**yapı numarasını belirtmeniz gerekir. Örneğin, sürüm 15.3 '15.0.26730.3' bir yapı numarası vardır. [Burada](../install/visual-studio-build-numbers-and-release-dates.md)sayılar oluşturmak için bültenlerin eşleme görebilirsiniz. '15.3' sürüm numarasını kullanmak doğru çalışmaz.

Uzantınız 15.3 veya üzeri gerektiriyorsa, **InstallationTarget Sürümünü** [15.0.26730.3, 16.0) olarak bildirirsiniz:

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
