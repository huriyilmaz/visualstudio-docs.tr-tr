---
title: Visual Studio 2017 Genişletilebilirliğinde Son Dakika Değişiklikleri
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b3a04c925ef897171de51c73c90973a12c3b17d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739976"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Visual Studio 2017 genişletilebilirlik değişiklikleri

Visual Studio 2017, Visual Studio'nun kullanıcı sistemleri üzerindeki etkisini azaltan daha hızlı ve hafif bir [Visual Studio yükleme deneyimi](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) sunarken, kullanıcılara yüklenen iş yükleri ve özellikler üzerinde daha fazla seçenek sunar. Bu geliştirmeleri desteklemek için, bazı kırılma değişiklikleri de dahil olmak üzere genişletilebilirlik modelinde değişiklikler yaptık. Bu makalede, bu değişikliklerin teknik ayrıntıları ve bunları gidermek için neler yapılabileceğini açıklayabilirsiniz.

> [!NOTE]
> Bazı bilgiler nokta zamanlı uygulama ayrıntılarıdır ve daha sonra değiştirilebilir.

## <a name="changes-affecting-vsix-format-and-installation"></a>VSIX biçimini ve kurulumunu etkileyen değişiklikler

Visual Studio 2017, hafif kurulum deneyimini desteklemek için VSIX v3 (sürüm 3) formatını tanıttı.

VSIX biçiminde yapılan değişiklikler şunlardır:

* Kurulum ön koşullarının bildirisi. Hafif ve hızlı yüklenen Visual Studio sözünü yerine getirmek için yükleyici artık kullanıcılara daha fazla yapılandırma seçeneği sunuyor. Sonuç olarak, bir uzantın tarafından gerekli olan özelliklerin ve bileşenlerin yüklendiğinden emin olmak için uzantıların bağımlılıklarını bildirmeleri gerekir.

  * Visual Studio 2017 yükleyicisi, uzantınızın bir parçası olarak kullanıcı için gerekli bileşenleri otomatik olarak edinmenizi ve yüklemeyi sunar.
  * Kullanıcılar, yeni VSIX v3 biçimini kullanarak oluşturulmayan bir uzantıyı yüklemeye çalışırken, bildirimlerinde 15.0'ı hedefleme olarak işaretlenmiş olsalar bile uyarılır.

* VSIX formatı için geliştirilmiş özellikler. Yan yana yüklemeleri de destekleyen Visual Studio'nun [düşük etkili yüklemesini](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) sağlamak için, yapılandırma verilerinin çoğunu artık sistem kayıt defterine kaydetmeyiz ve Visual Studio'ya özgü derlemeleri GAC dışına taşıdık. Ayrıca VSIX formatı ve VSIX kurulum motorunun yeteneklerini artırarak, uzantılarınızı bazı kurulum türleri için yüklemek için MSI veya EXE yerine kullanmanıza olanak sağladık.

Yeni yetenekler şunlardır:

* Belirtilen Visual Studio örneğine kaydolun.
* [Uzantılar klasörü](set-install-root.md)dışında yükleme.
* İşlemci mimarisinin algılanması.
* Dilden ayrılmış dil paketlerine bağımlılık.
* [NGEN desteği](ngen-support.md)ile kurulum.

## <a name="build-an-extension-for-visual-studio-2017"></a>Visual Studio 2017 için bir uzantı oluşturun

Yeni VSIX v3 manifesto formatının yazıları için tasarım aracıVisual Studio 2017'de mevcuttur. Aşağıdaki belgeye bakın Nasıl Olunacak: Tasarımcı araçlarını kullanma veya projede manuel güncellemeler yapma ve VSIX v3 uzantıları geliştirmek için bildirimde bulunma hakkında ayrıntılı bilgi için [genişletilebilirlik projelerini Visual Studio 2017'ye geçirin.](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)

## <a name="change-visual-studio-user-data-path"></a>Değişiklik: Visual Studio kullanıcı veri yolu

Daha önce, Visual Studio her büyük sürümü sadece bir yükleme her makinede mevcut olabilir. Visual Studio 2017'nin yan yana kurulumlarını desteklemek için, Visual Studio için birden çok kullanıcı veri yolu kullanıcının makinesinde bulunabilir.

Visual Studio işlemi içinde çalışan kod Visual Studio Ayarlar Yöneticisi'ni kullanmak üzere güncelleştirilmelidir. Visual Studio işleminin dışında çalışan [kod, buradaki kılavuzu izleyerek](locating-visual-studio.md)belirli bir Visual Studio yüklemesinin kullanıcı yolunu bulabilir.

## <a name="change-global-assembly-cache-gac"></a>Değişiklik: Genel Montaj Önbelleği (GAC)

Çoğu Visual Studio çekirdek derlemeleri artık GAC'ye yüklenmemaktadır. Visual Studio işleminde çalışan kod hala çalışma zamanında gerekli derlemeleri bulabilirsiniz, böylece aşağıdaki değişiklikler yapıldı.

> [!NOTE]
> [INSTALLDIR] aşağıda Visual Studio'nun kurulum kök dizini anlamına gelir. *VSIXInstaller.exe* otomatik olarak bu doldurmak, ancak özel dağıtım kodu yazmak için, [Visual Studio bulma](locating-visual-studio.md)okuyun .

* Yalnızca GAC'ye yüklenen derlemeler:

  Bu derlemeler artık <em>\*[INSTALLDIR]\Common7\IDE , *[INSTALLDIR]\Common7\IDE\PublicAssemblies</em> veya *[INSTALLDIR]\Common7\IDE\PrivateAssemblies*altında yüklenir. Bu klasörler Visual Studio işleminin sondalama yollarının bir parçasıdır.

* Sondalama olmayan bir yola ve GAC'ye yüklenen derlemeler:

  * GAC'deki kopya kurulumdan kaldırıldı.
  * Derleme için kod tabanı girişi belirtmek için *bir .pkgdef* dosyası eklendi.

    Örnek:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    Çalışma zamanında, Visual Studio pkgdef alt sistemi bu girişleri Visual Studio işleminin çalışma zamanı yapılandırma dosyasında *([VSAPPDATA]\devenv.exe.config*altında) öğe olarak [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) birleştirir. Bu, Visual Studio işleminin derlemenizi bulmasına izin vermenin önerilen yoludur, çünkü sondalama yollarında arama yapılmasını önler.

### <a name="reacting-to-this-breaking-change"></a>Bu kırılma değişikliğine tepki

* Uzantınız Visual Studio işlemi içinde çalışıyorsa:

  * Kodunuz Visual Studio çekirdek derlemelerini bulabilecektir.
  * Gerekirse derlemelerinize bir yol belirtmek için *.pkgdef* dosyası kullanmayı düşünün.

* Uzantınız Visual Studio işleminin dışında çalışıyorsa:

  <em>\*[INSTALLDIR]\Common7\IDE , *[INSTALLDIR]\Common7\IDE\PublicAssemblies</em> veya *[INSTALLDIR]\Common7\IDE\PrivateAssemblies* altında Visual Studio çekirdek derlemeleri aramayı düşünün yapılandırma dosyası veya montaj çözümleyicisi kullanarak.

## <a name="change-reduce-registry-impact"></a>Değişiklik: Kayıt defteri etkisini azaltın

### <a name="global-com-registration"></a>Global COM kaydı

* Daha önce, Visual Studio yerel COM kaydı desteklemek için HKEY_CLASSES_ROOT ve HKEY_LOCAL_MACHINE kovanları içine birçok kayıt defteri anahtarları yüklü. Bu etkiyi ortadan kaldırmak için Visual Studio artık [COM bileşenleri için Kayıtsız Etkinleştirme](https://msdn.microsoft.com/library/ms973913.aspx)kullanır.
* Sonuç olarak, %ProgramFiles(x86)%\Common Files\Microsoft Shared\MSEnv altında çoğu TLB / OLB / DLL dosyaları artık Visual Studio tarafından varsayılan olarak yüklenir. Bu dosyalar artık Visual Studio ana bilgisayar işlemi tarafından kullanılan ilgili Kayıt-Free COM bildirimleri ile [INSTALLDIR] altında yüklenir.
* Sonuç olarak, Visual Studio COM arabirimleri için global COM kaydına dayanan dış kod artık bu kayıtları bulamaz. Visual Studio işlemi içinde çalışan kod bir fark görmez.

### <a name="visual-studio-registry"></a>Visual Studio kayıt defteri

* Daha önce, Visual Studio, Visual Studio'ya özgü bir anahtar altında sistemin **HKEY_LOCAL_MACHINE** ve **HKEY_CURRENT_USER** kovanları içine birçok kayıt defteri anahtarı yükledi:

  * **HKLM\Software\Microsoft\VisualStudio\{Version}**: MSI yükleyiciler ve makine başına uzantıları tarafından oluşturulan kayıt defteri anahtarları.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}**: Visual Studio tarafından kullanıcıya özel ayarları depolamak için oluşturulan kayıt defteri anahtarları.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}_Config**: Yukarıdaki Visual Studio HKLM anahtarının bir kopyası, ayrıca *.pkgdef* dosyalarından uzanarak birleştirilmiş kayıt defteri anahtarları.

* Kayıt defteri üzerindeki etkisini azaltmak için Visual Studio artık kayıt defteri anahtarlarını *[VSAPPDATA]\privateregistry.bin*altında özel bir ikili dosyada depolamak için [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) işlevini kullanır. Sistem kayıt defterinde yalnızca çok az sayıda Visual Studio'ya özgü anahtar kalır.
* Visual Studio işlemi içinde çalışan varolan kod etkilenmez. Visual Studio, HKCU Visual Studio'ya özgü anahtar altında yer alan tüm kayıt işlemlerine özel kayıt defterine yönlendirecektir. Diğer kayıt konumlarına okuma ve yazma sistem kayıt defterini kullanmaya devam edecektir.
* Dış kodu yüklemek ve Visual Studio kayıt girişleri için bu dosyadan okumak gerekir.

### <a name="react-to-this-breaking-change"></a>Bu kırılma değişikliğine tepki ver

* Dış kod, COM bileşenleri için de Kayıt-Free etkinleştirme kullanmak için dönüştürülmelidir.
* Harici bileşenler visual studio konumunu [burada kılavuzu izleyerek](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup)bulabilirsiniz.
* Harici bileşenlerin doğrudan Visual Studio kayıt defteri anahtarlarına okuma/yazma yerine [Dış Ayarlar Yöneticisi'ni](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) kullanmalarını öneririz.
* Uzantınızın kullandığı bileşenlerin kayıt için başka bir teknik uygulamış olup olmadığını kontrol edin. Örneğin, hata ayıklama uzantıları yeni [msvsmon JSON-dosya COM kaydından](migrate-debugger-COM-registration.md)yararlanabilir.
