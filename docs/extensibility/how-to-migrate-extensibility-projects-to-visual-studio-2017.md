---
title: Genişletilebilirlik Projelerini Visual Studio 2017’ye Geçirme
titleSuffix: ''
description: Visual Studio 2017 ' ye genişletilebilirlik projelerini yükseltmeyi ve uzantı bildirimi sürüm 2 ' den sürüm 3 vsıx bildirimi ' ne yükseltmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: d99c5142d078b6206064af26c0195767f9566367715d55585b62482496127a45
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376734"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2017 'ye geçirme

bu belgede, genişletilebilirlik projelerinin Visual Studio 2017 ' ye nasıl yükseltileceği açıklanmaktadır. Proje dosyalarının nasıl güncelleştirileceğini açıklayan ek olarak, aynı zamanda uzantı bildirimi sürüm 2 ' den (VSıX v2) yeni sürüm 3 VSıX bildirim biçimine (VSıX v3) nasıl yükseltileceğini açıklar.

## <a name="install-visual-studio-2017-with-required-workloads"></a>gerekli iş yükleriyle Visual Studio 2017 ' i yükler

Yüklemenizin aşağıdaki iş yüklerini içerdiğinden emin olun:

* .NET masaüstü geliştirme
* Visual Studio uzantısı geliştirme

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Visual Studio 2017 ' de vsıx çözümünü açın

tüm vsıx projeleri, Visual Studio 2017 ' ye tek yönlü bir sürüm yükseltmesi gerektirir.

Proje dosyası (örneğin, **. csproj*) güncelleştirilecektir:

* MinimumVisualStudioVersion-şimdi 15,0 olarak ayarlandı
* Oldaraçları sürümü (daha önce varsa)-Şimdi 14,0 olarak ayarlanır

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Microsoft. vssdk. buildtools NuGet paketini güncelleştirme

> [!Note]
> çözümünüz Microsoft. vssdk. buildtools NuGet paketine başvurmadığından, bu adımı atlayabilirsiniz.

Uzantınızı yeni VSıX v3 (sürüm 3) biçiminde derlemek için, çözümünüzün yeni VSSDK derleme araçlarıyla oluşturulması gerekir. bu, Visual Studio 2017 ile yüklenir, ancak vsıx v2 uzantınız NuGet aracılığıyla daha eski bir sürüme başvuru tutuyor olabilir. bu durumda, çözümünüz için Microsoft. vssdk. buildtools NuGet paketinin bir güncelleştirmesini el ile yüklemeniz gerekir.

NuGet başvurularını Microsoft. vssdk. buildtools ' a güncelleştirmek için:

* çözüme sağ tıklayın ve **çözüm için NuGet paketlerini yönet**' i seçin.
* **Güncelleştirmeler** sekmesine gidin.
* **Microsoft. VSSDK. BuildTools (en son sürüm)** seçeneğini belirleyin.
* **Güncelleştir**'e basın.

![VSSDK derleme araçları](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>VSıX uzantı bildiriminde değişiklik yapma

kullanıcının Visual Studio yüklemesinin uzantısı çalıştırmak için gereken tüm derlemelere sahip olduğundan emin olmak için, uzantı bildirim dosyasındaki tüm önkoşul bileşenlerini veya paketleri belirtin. Kullanıcı uzantıyı yüklemeyi denediğinde, Valtıyükleyicisi tüm önkoşulların yüklenip yüklenmediğini kontrol eder. Bazıları eksikse, kullanıcıdan Uzantı yükleme işleminin bir parçası olarak eksik bileşenleri yüklemesi istenir.

> [!Note]
> en azından, tüm uzantılar Visual Studio çekirdek düzenleyicisi bileşenini bir önkoşul olarak belirtmelidir.

* Uzantı bildirim dosyasını düzenleyin (genellikle *kaynak. uzantı. valtmanifest* olarak adlandırılır).
* `InstallationTarget`15,0 içerdiğinden emin olun.
* Gerekli yükleme önkoşullarını ekleyin (aşağıdaki örnekte gösterildiği gibi).
  * Yükleme önkoşulları için yalnızca bileşen kimliklerini belirtmenizi öneririz.
  * [Bileşen kimliklerini tanımlamaya ilişkin yönergeler](#find-component-ids)için bu belgenin sonundaki bölümüne bakın.

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Seçenek: VSıX uzantı bildiriminde değişiklik yapmak için tasarımcıyı kullanın

Bildirim XML 'sini doğrudan düzenlemeniz yerine, önkoşulları seçmek için bildirim tasarımcısında yeni **Önkoşullar** sekmesini KULLANABILIRSINIZ ve XML sizin için güncelleştirilir.

> [!Note]
> bildirim tasarımcısı yalnızca geçerli Visual Studio örneğine yüklenmiş bileşenleri (iş yükleri veya paketleri değil) seçmenizi sağlar. Şu anda yüklü olmayan bir iş yükü, paket veya bileşen için bir önkoşul eklemeniz gerekiyorsa, bildirim XML 'sini doğrudan düzenleyin.

* Açık *kaynak. Extension. valtmanifest [Tasarım]* dosyası.
* **Önkoşullar** sekmesini seçin ve **Yeni** düğmesine basın.

   ![VSıX bildirim Tasarımcısı](media/vsix-manifest-designer.png)

* **Yeni önkoşul Ekle** penceresi açılır.

   ![VSIX önkoşulu Ekle](media/add-vsix-prerequisite.png)

* **Ad** için aşağı açılan listeye tıklayın ve istenen önkoşulu seçin.
* Gerekirse sürümü güncelleştirin.

   > [!Note]
   > Sürüm alanı, bileşen 'nin bir sonraki ana sürümünü kapsayan (dahil değil) bir aralığa yayılmış, şu anda yüklü olan bileşenin sürümü ile önceden doldurulur.

   ![Roslyn önkoşulu ekleme](media/add-roslyn-prerequisite.png)

* **Tamam**'a basın.

## <a name="update-debug-settings-for-the-project"></a>Proje için hata ayıklama ayarlarını Güncelleştir

Visual Studio deneysel bir örneğinde uzantınızın hatalarını ayıklamak istiyorsanız, **hata ayıklama**  >  **başlatma eylemi** için proje ayarları ' nın Visual Studio 2017 yüklemenizin *devenv.exe* dosyasına ayarlandığından emin  olun.

Şöyle görünebilir: *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![dış programı Başlat](media/start-external-program.png)

> [!Note]
> Hata ayıklama başlatma eylemi genellikle *. csproj. User* dosyasında depolanır. Bu dosya genellikle *. gitignore* dosyasına dahil edilmiştir ve bu nedenle kaynak denetimine işlendiği sırada normalde diğer proje dosyalarıyla kaydedilmez. Bu nedenle, çözümünüzü kaynak denetiminden yeni aldıysanız, projenin başlangıç eylemi için ayarlanmış bir değeri olmayacaktır. Visual Studio 2017 ile oluşturulan yeni vsıx projelerinin geçerli Visual Studio install dizinine işaret eden varsayılanlar kullanılarak oluşturulan *. csproj. user* dosyası olur. ancak vsıx v2 uzantısını geçiriyorsanız, *. csproj. user* dosyası, önceki Visual Studio sürümünün install dizinine başvurular içeriyor olabilir. **hata ayıklama**  >  **başlatma eyleminin** değerini ayarlamak, uzantınızın hatalarını ayıklamaya çalıştığınızda doğru Visual Studio deneysel örneğinin başlatılmasını sağlar.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Uzantının doğru şekilde (VSıX v3 olarak) oluşturulup oluşturulmadığını denetleyin

* VSıX projesi oluşturun.
* Oluşturulan VSıX 'i sıkıştırmayı açın.
  * Varsayılan olarak, VSıX dosyası *bin/hata ayıklama* veya *bin/yayın* Içinde *[yourcustomexger]. VSIX* olarak bulunur.
  * İçeriği kolayca görüntülemek için *. vsix* öğesini *.zip* olarak yeniden adlandırın.
* Üç dosya olup olmadığını denetleyin:
  * *Extension. valtmanifest*
  * *Üzerindemanifest.js*
  * *Üzerindecatalog.js*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Gerekli tüm önkoşulların yüklü olup olmadığını denetle

VSıX 'in tüm gerekli önkoşulları yüklenmiş bir makineye başarıyla yüklendiğini test edin.

> [!Note]
> Herhangi bir uzantıyı yüklemeden önce lütfen tüm Visual Studio örneklerini kapatın.

Uzantıyı yüklemeyi deneyin:

* Visual Studio 2017

![Visual Studio 2017 ' de vsıx yükleyicisi](media/vsixinstaller-vs-2017.png)

* İsteğe bağlı: önceki Visual Studio sürümlerini denetleyin.
  * Doğru uyumluluk olduğunu kanıtlar.
  * Visual Studio 2012, Visual Studio 2013, Visual Studio 2015 için çalışmalıdır.
* İsteğe bağlı: VSıX yükleyicisi sürüm denetleyicisinin bir sürüm seçimi sunduğunu denetleyin.
  * Visual Studio önceki sürümlerini (yüklüyse) içerir.
  * Visual Studio 2017 içerir.

Visual Studio kısa süre önce açılırsa şöyle bir iletişim kutusu görebilirsiniz:

![vs çalışan süreçler](media/vs-running-processes.png)

İşlemlerin kapatılmasını bekleyin veya görevleri el ile sonlandırın. Bu işlemi listelenen ada veya parantez içinde listelenen PID ile bulabilirsiniz.

> [!Note]
> bu süreçler, bir Visual Studio örneği çalışırken otomatik olarak kapatılmaz. makinedeki tüm Visual Studio örneklerini (diğer kullanıcılardan olanlar da dahil) kapattığınızdan emin olun, sonra yeniden denemeye devam edin.

## <a name="check-when-missing-the-required-prerequisites"></a>Gerekli önkoşulların eksik olup olmadığını denetleyin

* önkoşulları, önkoşullardan (yukarıda) tanımlanan tüm bileşenleri içermeyen Visual Studio 2017 ' a sahip bir makineye yüklemeyi deneyin.
* Yüklemenin eksik bileşen/sn 'leri tanımladığından ve bunları Valtınstaller 'ta bir önkoşul olarak listelediğinden emin olun.
* Note: uzantıya sahip herhangi bir önkoşul yüklenmesi gerekiyorsa yükseltme gerekecektir.

![valtınstaller için önkoşul eksik](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Bileşenlere karar verme

Bağımlılıklarınız aranırken, bir bağımlılığın birden çok bileşene eşlenmesine ilişkin olduğunu fark edersiniz. Önkoşul olarak hangi bağımlılıklara belirtmeniz gerektiğini belirlemek için, uzantınıza benzer bir işlevselliğe sahip olan bir bileşen seçmenizi ve ayrıca kullanıcılarınızı ve ne tür bir bileşen yüklemiş veya yükleme düşünmeyeceğini düşünmenizi öneririz. Ayrıca, genişletmenizi gerekli önkoşulların yalnızca uzantınızın çalışmasına izin verecek olan en düşük değeri karşıladığı ve ek özellikler için belirli bileşenlerin algılanmadığı durumlarda devre dışı olduğu bir şekilde oluşturmayı öneririz.

Daha fazla rehberlik sağlamak için, birkaç ortak uzantı türü ve önerilen önkoşulları belirledik:

Uzantı türü | Görünen Ad | ID
--- | --- | ---
Düzenleyici | Visual Studio core düzenleyicisi | Microsoft. VisualStudio. Component. CoreEditor
Roslyn | C# ve Visual Basic | Microsoft. VisualStudio. Component. Roslyn. LanguageServices
WPF | Yönetilen masaüstü Iş yükü çekirdeği | Microsoft. VisualStudio. Component. ManagedDesktop. Core
Hata Ayıklayıcısı | Tam zamanında hata ayıklayıcı | Microsoft. VisualStudio. Component. Debugger. Adaıntime

## <a name="find-component-ids"></a>Bileşen kimliklerini bul

Visual Studio ürüne göre sıralanan bileşenlerin listesi [Visual Studio 2017 iş yüküne ve bileşen kimliklerine](../install/workload-and-component-ids.md?view=vs-2019&preserve-view=true)sahiptir. Bildiriminizde önkoşul kimlikleriniz için bu bileşen kimliklerini kullanın.

Hangi bileşenin belirli bir ikiliye sahip olduğundan emin değilseniz, [bileşen-> ikili eşleme elektronik tablosunu](https://aka.ms/vs2017componentid-binaries)indirin.

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Excel sayfasında dört sütun vardır: **bileşen adı**, **componentıd**, **sürüm** ve **ikili dosya adları**.  Filtreleri kullanarak belirli bileşenleri ve ikili dosyaları arayabilir ve bulabilirsiniz.

Tüm başvurularınız için, ilk olarak temel Düzenleyici (Microsoft. VisualStudio. Component. CoreEditor) bileşeninde hangilerinin olduğunu saptayın.  En azından, çekirdek Düzenleyici bileşeninin tüm uzantılar için bir önkoşul olarak belirtilmesini gerektiririz. Sol ana düzenleyicide bulunmayan başvurularda, bu başvuruların alt kümelerine sahip bileşenleri bulmak için **Ikili dosyaları/dosya adları** bölümüne filtre ekleyin.

Örnekler:

* Bir hata ayıklayıcı uzantınız varsa ve projenizin *VSDebugEng.dll* ve *VSDebug.dll* bir başvurusu olduğunu biliyorsanız, **ikili dosyalar/dosya adları** üstbilgisindeki filtre düğmesine tıklayın.  "VSDebugEng.dll" araması yapın ve *Tamam*' ı seçin.  Sonra, **Ikili dosyalar/dosya adları** üstbilgisindeki filtre düğmesine tıklayın ve "VSDebug.dll" araması yapın.  **Filtre uygulanacak geçerli seçimi Ekle** onay kutusunu seçin ve **Tamam**' ı seçin.  Uzantı yazdığınıza en çok ilişkili bir bileşeni bulmak için **bileşen adına** bakın. Bu örnekte, Just-In-Time hata ayıklayıcıyı seçtiniz ve bunu valtmanifest ' e eklersiniz.
* Projenizin hata ayıklayıcı öğeleriyle ilgili olduğunu biliyorsanız, hangi bileşenlerin adında hata ayıklayıcı içerdiğini görmek için filtre arama kutusundaki "hata ayıklayıcı" üzerinde arama yapabilirsiniz.

## <a name="specify-a-visual-studio-2017-release"></a>Visual Studio 2017 sürümü belirtin

uzantınız Visual Studio 2017 ' nin belirli bir sürümünü gerektiriyorsa, örneğin, 15,3 ' de yayınlanan bir özelliğe bağlı ise, vsıx **yüklemeortamınızda** yapı numarasını belirtmeniz gerekir. Örneğin, Release 15,3 ' 15.0.26730.3 ' derleme numarasına sahiptir. Sürüm numaralarını [burada](../install/visual-studio-build-numbers-and-release-dates.md)oluşturmak için bu sürümlerin eşlemesini görebilirsiniz. ' 15,3 ' yayın numarasını kullanmak düzgün çalışmayacak.

Uzantınız 15,3 veya daha yüksek bir sürüm gerektiriyorsa, **ınstalyüklemehedef sürümünü** [15.0.26730.3, 16,0) olarak bildirebilirsiniz:

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```