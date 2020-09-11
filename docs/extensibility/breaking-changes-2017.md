---
title: Visual Studio 2017 genişletilebilirlikteki son değişiklikler
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d872003b319773401ef4da72c1fac8dc177ecbdb
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011794"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Visual Studio 2017 genişletilebilirlikteki değişiklikler

Visual Studio 2017, kullanıcı sistemlerinde Visual Studio 'nun etkisini azaltan [daha hızlı, daha hafif bir Visual Studio yükleme deneyimi](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) sağlar. bu sayede, kullanıcılara yüklenen iş yükleri ve Özellikler üzerinde daha fazla seçenek sunar. Bu geliştirmeleri desteklemek için, bazı son değişiklikler dahil olmak üzere genişletilebilirlik modelinde değişiklikler yaptık. Bu makalede, bu değişikliklerin teknik ayrıntıları ve bunların ele getirilmesi için neler yapılabileceği açıklanmaktadır.

> [!NOTE]
> Bazı bilgiler, zaman içinde uygulama ayrıntılarıdır ve daha sonra değiştirilebilir.

## <a name="changes-affecting-vsix-format-and-installation"></a>VSıX biçimini ve yüklemeyi etkileyen değişiklikler

Visual Studio 2017, basit yükleme deneyimini desteklemek için VSıX v3 (sürüm 3) biçimini kullanıma sunmuştur.

VSıX biçimindeki değişiklikler şunları içerir:

* Kurulum önkoşulları bildirimi. Hafif ve hızlı bir şekilde yüklenen Visual Studio 'nun taahhüdüne sunmak için, yükleyici artık kullanıcılara daha fazla yapılandırma seçeneği sunar. Sonuç olarak, bir uzantının gerektirdiği özellik ve bileşenlerin yüklü olduğundan emin olmak için uzantıların bağımlılıklarını bildirmesi gerekir.

  * Visual Studio 2017 yükleyicisi, uzantınızı yüklemenin bir parçası olarak Kullanıcı için gerekli bileşenleri edinmeyi ve yüklemeyi otomatik olarak sağlar.
  * Kullanıcılar ayrıca, yeni VSıX v3 biçimi kullanılarak derlenmeyen bir uzantıyı yüklemeye çalışırken de uyarılabilirler. Bu dosyalar, hedef sürüm 15,0 olarak bildirimde işaretlenmiş olsalar bile

* VSıX biçimi için gelişmiş yetenekler. Aynı zamanda yan yana yüklemeleri de destekleyen, Visual Studio 'nun [düşük etkili bir yüklemesine](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) sunmak için, çoğu yapılandırma verisini sistem kayıt defterine kaydedemedik ve Visual Studio 'ya özgü derlemeleri GAC 'den dışarı taşıdık. Ayrıca VSıX biçimi ve VSıX yükleme altyapısının yeteneklerini de geliştirdik. Bu özellik, bazı yükleme türlerine yönelik uzantılarınızı yüklemek için bir MSI veya EXE yerine bunu kullanmanıza olanak sağlar.

Yeni yetenekler şunlardır:

* Belirtilen Visual Studio örneğine kaydolma.
* [Uzantılar klasörü](set-install-root.md)dışında yükleme.
* İşlemci mimarisinin algılanması.
* Dile ayrılmış dil paketlerinde bağımlılık.
* [Ngen desteğiyle](ngen-support.md)yükleme.

## <a name="build-an-extension-for-visual-studio-2017"></a>Visual Studio 2017 için uzantı oluşturma

Yeni VSıX v3 bildirim biçiminin yazılması için tasarımcı araçları Visual Studio 2017 ' de kullanılabilir. Tasarımcı araçlarını kullanma hakkında ayrıntılı bilgi edinmek veya proje ve bildirimde VSıX v3 uzantıları geliştirmeye yönelik el ile güncelleştirme yapmak için bkz. [nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2017 'e geçirme](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) .

## <a name="change-visual-studio-user-data-path"></a>Değişiklik: Visual Studio Kullanıcı veri yolu

Daha önce her makinede, Visual Studio 'nun her bir ana sürümünün yalnızca bir yüklemesi bulunabilir. Visual Studio 2017 'nin yan yana yüklemelerini desteklemek için, kullanıcının makinesinde Visual Studio için birden çok kullanıcı veri yolu bulunabilir.

Visual Studio işlem içinde çalışan kodun Visual Studio Settings Manager 'ı kullanmak için güncelleştirilmeleri gerekir. Visual Studio işleminin dışında çalışan kod, [buradaki kılavuzu izleyerek](locating-visual-studio.md)belirli bir Visual Studio yüklemesinin Kullanıcı yolunu bulabilir.

## <a name="change-global-assembly-cache-gac"></a>Değişiklik: genel bütünleştirilmiş kod önbelleği (GAC)

Visual Studio temel derlemelerinin çoğu artık GAC 'ye yüklenmez. Visual Studio işleminde çalışan kodun çalışma zamanında gerekli derlemeleri bulmaya devam edebilmesi için aşağıdaki değişiklikler yapılmıştır.

> [!NOTE]
> Aşağıdaki [ıNSTALLDIR], Visual Studio 'nun yükleme kök dizinine başvurur. *VSIXInstaller.exe* , bunu otomatik olarak dolduracaktır, ancak özel dağıtım kodu yazmak Için lütfen [Visual Studio 'yu bulma](locating-visual-studio.md)makalesini okuyun.

* Yalnızca GAC 'ye yüklenmiş olan derlemeler:

  Bu derlemeler artık <em>[INSTALLDİR] \Common7\IDE \* , * [INSTALLDİR] \Common7\IDE\PublicAssemblies</em> veya *[INSTALLDİR] \Common7\IDE\PrivateAssemblies*altına yüklendi. Bu klasörler, Visual Studio işleminin yoklama yollarının bir parçasıdır.

* Yoklama dışı bir yola ve GAC 'ye yüklenmiş derlemeler:

  * GAC 'deki kopya kurulumdan kaldırılmıştır.
  * Derleme için bir kod tabanı girişi belirtmek üzere bir *. pkgdef* dosyası eklenmiştir.

    Örneğin:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    Çalışma zamanında, Visual Studio pkgdef alt sistemi bu girdileri Visual Studio işleminin çalışma zamanı yapılandırma dosyasında ( *[VSAPPDATA] \devenv.exe.config*) öğe olarak birleştirir [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) . Bu, Visual Studio işleminin ayrıştırma yollarında aramayı önlediği için derlemenizi bulmasını sağlamak için önerilen yoldur.

### <a name="reacting-to-this-breaking-change"></a>Bu son değişikliğe yeniden davranıyor

* Uzantınızın Visual Studio işleminde çalışıyor olması durumunda:

  * Kodunuz, Visual Studio temel derlemelerini bulabilecektir.
  * Gerektiğinde derlemelerinize bir yol belirtmek için bir *. pkgdef* dosyası kullanmayı düşünün.

* Uzantınızın Visual Studio işlemi dışında çalışıyor olması durumunda:

  Yapılandırma dosyası veya derleme çözümleyici <em>'yi kullanarak [INSTALLDİR] \Common7\IDE \* , * [INSTALLDİR] \Common7\IDE\PublicAssemblies</em> veya *[INSTALLDİR] \Common7\IDE\PrivateAssemblies* altında Visual Studio Core derlemelerini aramak isteyebilirsiniz.

## <a name="change-reduce-registry-impact"></a>Değişiklik: kayıt defteri etkisini azaltma

### <a name="global-com-registration"></a>Genel COM kaydı

* Daha önce, Visual Studio yerel COM kaydını desteklemek için HKEY_CLASSES_ROOT ve HKEY_LOCAL_MACHINE kovanına birçok kayıt defteri anahtarı yükledi. Bu etkiyi ortadan kaldırmak için, Visual Studio artık [com bileşenleri Için kayıtsız etkinleştirme](/previous-versions/dotnet/articles/ms973913(v=msdn.10))kullanır.
* Sonuç olarak,% ProgramFiles (x86)% \ Common Files\Microsoft Shared\MSEnv altındaki TLB/OLB/DLL dosyaları artık Visual Studio tarafından varsayılan olarak yüklenmez. Bu dosyalar artık, Visual Studio konak işlemi tarafından kullanılan ilgili kayıtsız COM bildirimleri ile [ıNSTALLDIR] altına yüklenir.
* Sonuç olarak, Visual Studio COM arabirimleri için genel COM kaydına dayanan dış kod artık bu kayıtları bulamaz. Visual Studio işleminin içinde çalışan kod, bir fark görmez.

### <a name="visual-studio-registry"></a>Visual Studio kayıt defteri

* Daha önce, Visual Studio, Visual Studio 'ya özgü bir anahtar altında sistem **HKEY_LOCAL_MACHINE** ve **HKEY_CURRENT_USER** kovanına birçok kayıt defteri anahtarı yükledi:

  * **Hklm\software\microsoft\visualstudio \{ Sürüm}**: MSI yükleyicileri ve makine başına uzantılar tarafından oluşturulan kayıt defteri anahtarları.
  * **Hkcu\software\microsoft\visualstudio \{ Sürüm}**: Visual Studio tarafından kullanıcıya özgü ayarları depolamak için oluşturulan kayıt defteri anahtarları.
  * **Hkcu\software\microsoft\visualstudio \{ Sürüm} _Config**: Yukarıdaki Visual STUDIO HKLM anahtarının bir kopyası, ve *. pkgdef* dosyalarından birleştirilmiş kayıt defteri anahtarları uzantılara göre.

* Kayıt defterindeki etkiyi azaltmak için, Visual Studio artık, kayıt defteri anahtarlarını *[VSAPPDATA] \privateregistry.bin*altında özel bir ikili dosyada depolamak üzere [Regloadappkey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) işlevini kullanır. Yalnızca çok az sayıda Visual Studio 'Ya özgü anahtar sistem kayıt defterinde kalır.
* Visual Studio işleminin içinde çalışan mevcut kod etkilenmez. Visual Studio, HKCU Visual Studio 'ya özgü anahtar altındaki tüm kayıt defteri işlemlerini özel kayıt defterine yönlendirir. Diğer kayıt defteri konumlarına okuma ve yazma, sistem kayıt defterini kullanmaya devam edecektir.
* Dış kodun, Visual Studio kayıt defteri girdileri için bu dosyadan yüklenmesi ve okunması gerekir.

### <a name="react-to-this-breaking-change"></a>Bu son değişikliğe tepki verme

* Dış kod, COM bileşenleri için de kayıt-ücretsiz etkinleştirmeyi kullanacak şekilde dönüştürülmelidir.
* Dış bileşenler, [buradaki Kılavuzu Izleyerek](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup)Visual Studio konumunu bulabilir.
* Dış bileşenlerin, doğrudan Visual Studio kayıt defteri anahtarlarına okumak/yazmak yerine [dış ayarlar yöneticisini](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) kullanmasını öneririz.
* Uzantınızın kullandığı bileşenlerin kayıt için başka bir teknik uygulanıp uygulanmadığını denetleyin. Örneğin, hata ayıklayıcı uzantıları New [msvsmon JSON-FILE com kaydından](migrate-debugger-COM-registration.md)faydalanabilir.