---
title: Genişletilebilirlik Projelerini Visual Studio 2017’ye Geçirme
titleSuffix: ''
description: Genişletilebilirlik projelerini Visual Studio 2017'ye yükseltmeyi ve uzantı bildirimi sürüm 2'den sürüm 3 VSIX bildirimine yükseltmeyi öğrenin.
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
ms.openlocfilehash: 9e10a9061eae777728b9874c959483edfc7abe15
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050344"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Nasıl yapılır: Genişletilebilirlik projelerini Visual Studio 2017'ye geçirme

Bu belgede, genişletilebilirlik projelerinin 2017'Visual Studio yükseltildi. Proje dosyalarının nasıl güncelleştirilerek uzantı bildirimi sürüm 2'den (VSIX v2) yeni sürüm 3 VSIX bildirim biçimine (VSIX v3) yükseltilenler de anlatılacaktır.

## <a name="install-visual-studio-2017-with-required-workloads"></a>Gerekli Visual Studio 2017'de yükleme

Yüklemenizin aşağıdaki iş yüklerini içerir:

* .NET masaüstü geliştirme
* Visual Studio uzantısı geliştirme

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Visual Studio 2017'de VSIX Çözümünü Açma

Tüm VSIX projeleri, 2017'de ana sürüme tek Visual Studio gerektirir.

Proje dosyası (örneğin**.csproj*) güncelleştirilir:

* MinimumVisualStudioVersion - artık 15.0 olarak ayarlanmış
* EskiToolsVersion (önceden varsa) - şimdi 14.0 olarak ayarlanır

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Microsoft.VSSDK.BuildTools NuGet güncelleştirme

> [!Note]
> Çözümünüz Microsoft.VSSDK.BuildTools NuGet başvurursa bu adımı atlayabilirsiniz.

Uzantınızı yeni VSIX v3 (sürüm 3) biçiminde derlemek için, çözümünüz yeni VSSDK Derleme Araçları ile derlemeniz gerekir. Bu, Visual Studio 2017 ile yüklenir, ancak VSIX v2 uzantınız bu sürüm aracılığıyla eski bir sürüme başvuru NuGet. Öyleyse, çözümünüz için Microsoft.VSSDK.BuildTools NuGet paketini el ile yüklemeniz gerekir.

Microsoft.VSSDK.BuildTools'a NuGet başvurularını güncelleştirmek için:

* Çözüme sağ tıklayın ve Çözüm için NuGet **Paketlerini Yönet'i seçin.**
* Güncelleştirmeler **sekmesine** gidin.
* **Microsoft.VSSDK.BuildTools (en son sürüm) öğesini seçin.**
* **Güncelleştir'e basın.**

![VSSDK derleme araçları](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>VSIX uzantı bildiriminde değişiklik yapma

Kullanıcının uzantı yüklemesinde uzantıyı çalıştırmak Visual Studio tüm derlemelere sahip olduğundan emin olmak için uzantı bildirim dosyasında tüm önkoşul bileşenlerini veya paketlerini belirtin. Kullanıcı uzantıyı yükleme girişiminde bulunsa VSIXInstaller tüm önkoşulların yüklü olup olduğunu kontrol edin. Bazıları eksikse, kullanıcıdan uzantı yükleme işleminin bir parçası olarak eksik bileşenleri yüklemesi istenir.

> [!Note]
> En azından, tüm uzantılar bir önkoşul Visual Studio temel düzenleyici bileşenini belirttir.

* Uzantı bildirim dosyasını düzenleyin (genellikle *source.extension.vsixmanifest olarak da adlandırılan).*
* `InstallationTarget`15.0'ın dahil olduğundan emin olmak.
* Gerekli yükleme önkoşullarını ekleyin (aşağıdaki örnekte gösterildiği gibi).
  * Yükleme önkoşulları için yalnızca Bileşen Kimliklerini belirtmenizi öneririz.
  * Bileşen kimliklerini tanımlama yönergeleri için bu belgenin [sonundaki bölümüne bakın.](#find-component-ids)

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

Bildirim XML'sini doğrudan düzenlemek yerine,  önkoşulları seçmek için Bildirim Tasarımcısı'nda yeni Önkoşullar sekmesini kullanabilirsiniz; xml sizin için güncelleştirilir.

> [!Note]
> Bildirim Tasarımcısı yalnızca geçerli örnek üzerinde yüklü Bileşenleri (İş Yükleri veya Paketler değil) seçmenize Visual Studio sağlar. Şu anda yüklü olan bir iş yükü, paket veya bileşen için önkoşul eklemeniz gerekirse, bildirim XML'sini doğrudan düzenleyin.

* Açık *source.extension.vsixmanifest [Tasarım]* dosyası.
* **Önkoşullar** sekmesini seçin ve Yeni **düğmesine** basın.

   ![VSIX bildirim tasarımcısı](media/vsix-manifest-designer.png)

* Yeni **Önkoşul Ekle** penceresi açılır.

   ![vsix önkoşulları ekleme](media/add-vsix-prerequisite.png)

* Ad açılan listesinden **istediğiniz önkolu** seçin.
* Gerekirse sürümü güncelleştirin.

   > [!Note]
   > Sürüm alanı, o anda yüklü olan bileşenin sürümüyle önceden doldurulur ve bileşenin sonraki ana sürümüne kadar yayılan (ancak dahil olmayan) bir aralık kullanılır.

   ![roslyn önkoşullarını ekleme](media/add-roslyn-prerequisite.png)

* **Tamam**'a basın.

## <a name="update-debug-settings-for-the-project"></a>Proje için Hata Ayıklama ayarlarını güncelleştirme

Uzantınıza deneysel bir Visual Studio örneğinde hata ayıklamak isterseniz, Hata Ayıklama Başlatma eylemi için proje ayarlarında Dış programı başlat: değerinindevenv.exe >   2017 yüklemenizin *Visual Studio* dosyasına ayarlanmış olduğundan emin olun. 

Şuna benzer olabilir: *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![dış programı başlatma](media/start-external-program.png)

> [!Note]
> Hata Ayıklama Başlangıç Eylemi genellikle *.csproj.user dosyasında* depolanır. Bu dosya genellikle *.gitignore* dosyasına dahil edilir ve bu nedenle kaynak denetimine işlendiklerde normalde diğer proje dosyalarıyla birlikte kaydedilamaz. Bu nedenle, çözümlerinizi kaynak denetiminden yeni aldıysanız, projenin Başlatma Eylemi için ayarlanmış bir değeri yoktur. Visual Studio 2017 ile oluşturulan yeni VSIX projelerinde, varsayılan olarak geçerli yükleme dizininin işaret Visual Studio *bir .csproj.user* dosyası oluşturulacak. Ancak, bir VSIX v2 uzantısını yüklüüyorsanız, *.csproj.user* dosyası büyük olasılıkla önceki Visual Studio sürümünün yükleme dizinine başvurular içerir. Hata Ayıklama Başlangıç **eyleminin**  >  **değerinin ayarı,** uzantınız Visual Studio deneme örneğinin başlatılması için doğru uygulamanın başlatılmasına olanak sağlar.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Uzantının doğru şekilde (VSIX v3 olarak) derlemeyi denetleyin

* VSIX projesini derleme.
* Oluşturulan VSIX'in sıkıştırması açın.
  * Varsayılan olarak VSIX dosyası *bin/Debug* veya *bin/Release* içinde *[YourCustomExtension].vsix olarak yer alır.*
  * İçeriği *kolayca görüntülemek için .vsix* *.zip* .vsix olarak yeniden adlandırabilirsiniz.
* Üç dosyanın varlığını kontrol edin:
  * *Vsixmanifest*
  * *manifest.js*
  * *catalog.js*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Tüm gerekli önkoşulların ne zaman yüklü olduğunu denetleme

Tüm gerekli önkoşulların yüklü olduğu bir makineye VSIX'in başarıyla yük yüklerini test edin.

> [!Note]
> Herhangi bir uzantıyı yüklemeden önce lütfen uygulamanın tüm Visual Studio.

Uzantıyı yükleme girişimi:

* Visual Studio 2017'de

![Visual Studio 2017'de VSIX yükleyicisi](media/vsixinstaller-vs-2017.png)

* İsteğe bağlı: Uygulamanın önceki sürümlerini Visual Studio.
  * Geriye dönük uyumluluğu kanıtlar.
  * Visual Studio 2012, Visual Studio 2013, Visual Studio 2015 için çalışmalı.
* İsteğe bağlı: VSIX Yükleyicisi Sürüm Denetleyicisi'nin bir sürüm seçeneği sunduğuna bakın.
  * Önceki sürüm sürümlerini Visual Studio (yüklüyse).
  * 2017 Visual Studio içerir.

Yeni Visual Studio açıksa, aşağıdakine benzer bir iletişim kutusuyla karşı karşına çıkıyor olabilir:

![vs çalışan işlemler](media/vs-running-processes.png)

İşlemlerin kapanmasını bekleyin veya görevleri el ile bitirin. İşlemleri listelenen adla veya PID parantez içinde listelenmiş olarak bulabilirsiniz.

> [!Note]
> Bir örnek çalışırken bu işlemler otomatik olarak Visual Studio kapatmayacak. Makinede bulunan ve diğer kullanıcıların Visual Studio tüm örneklerini kapatarak yeniden denemeyi sürdürebilirsiniz.

## <a name="check-when-missing-the-required-prerequisites"></a>Gerekli önkoşulların ne zaman eksik olduğunu denetleme

* Uzantıyı Önkoşullar (yukarıda) Visual Studio 2017'de tanımlanan tüm bileşenleri IÇERMİP 2017 sürümüne sahip bir makineye yükleyin.
* Yüklemenin eksik bileşenleri tanımp tanımlamadan VSIXInstaller'da bunları önkoşul olarak listeleyenin.
* Not: Uzantıyla herhangi bir önkoşul yüklü olması gerekirse yükseltme gerekir.

![vsixinstaller önkoşul eksik](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Bileşenlere karar verme

Bağımlılıklarınızı arıyorken, bir bağımlılığın birden çok bileşene eşlene bir olduğunu bulabilirsiniz. Önkoşul olarak hangi bağımlılıkları belirtmeniz gerektiğini belirlemek için, uzantınıza benzer bir işleve sahip bir bileşen seçmenizi ve kullanıcılarınızı ve büyük olasılıkla hangi tür bileşenleri yüklemiş veya yüklemeyi düşünmeyeceklerini göz önünde bulundurmanızı öneririz. Ayrıca, uzantılarınızı, gerekli önkoşulların yalnızca uzantınızı çalıştırmasına izin verecek en düşük düzeyde karşılaması ve bazı bileşenler algılanmazsa ek özelliklerin çalışmamalarını sağlayacak şekilde de binanızı öneririz.

Daha fazla rehberlik sağlamak için birkaç yaygın uzantı türü ve bunların önerilen önkoşullarını belirledik:

Uzantı Türü | Görünen Ad | ID
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