---
title: 2017 genişletilebilirlik Visual Studio Yeni Değişiklikler
description: Visual Studio 2017'de genişletilebilirlik modelinde yapılan hataya neden olan değişikliklerin teknik ayrıntılarını ve bunları ele alan neleri yapabilirsiniz?
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: de83f2504f6810b00265b0abf7b4630e3e0c4cc2a1da98931a0518c4dd3ea12b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121308382"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>2017 genişletilebilirliği Visual Studio değişiklikleri

Visual Studio 2017, kullanıcılara yüklü iş yükleri ve [özellikler](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) üzerinde daha fazla seçenek sunarken Visual Studio'nin kullanıcı sistemleri üzerindeki etkisini azaltan daha hızlı, daha hafif bir Visual Studio yükleme deneyimi sağlar. Bu geliştirmeleri desteklemek için, bazı hataya neden olan değişiklikler de dahil olmak üzere genişletilebilirlik modelinde değişiklikler yaptık. Bu makalede, bu değişikliklerin teknik ayrıntıları ve bunları ele alan nelerin yap what can be be açıklanmıştır.

> [!NOTE]
> Bazı bilgiler, zaman içinde uygulama ayrıntılarıdır ve daha sonra değiştirilebilir.

## <a name="changes-affecting-vsix-format-and-installation"></a>VSIX biçimini ve yüklemesini etkileyen değişiklikler

Visual Studio 2017'de basit yükleme deneyimini desteklemek için VSIX v3 (sürüm 3) biçimi tanıtıldı.

VSIX biçiminde yapılan değişiklikler şunlardır:

* Kurulum önkoşullarının bildirimi. Yükleyici, basit ve hızlı bir yükleme seçeneği sunmak Visual Studio kullanıcılara daha fazla yapılandırma seçeneği sunmaktadır. Sonuç olarak, bir uzantının gerektirmiş olduğu özelliklerin ve bileşenlerin yüklü olduğundan emin olmak için uzantıların bağımlılıklarını bildirmiş olması gerekir.

  * Visual Studio 2017 yükleyicisi, uzantınızı yüklemenin bir parçası olarak kullanıcı için gerekli bileşenlerin alın ve yüklerini otomatik olarak sunar.
  * Ayrıca, bildiriminde sürüm 15.0'ı hedefleseler bile, yeni VSIX v3 biçimi kullanılarak kurulmamış bir uzantıyı yüklemeye çalışan kullanıcılar da uyarıldı.

* VSIX biçimi için gelişmiş özellikler. Yan yana [yüklemeleri](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) de destekleyen Visual Studio'nin düşük etkili bir yüklemesini sunmak için, artık çoğu yapılandırma verilerini sistem kayıt defterine kaydetmez ve Visual Studio'ye özgü derlemeleri GAC'nin dışında taşıdık. Ayrıca VSIX biçiminin ve VSIX yükleme altyapısının özelliklerini artırarak bazı yükleme türlerine yönelik uzantılarınızı yüklemek için MSI veya EXE yerine bu özelliği kullanabilirsiniz.

Yeni özellikler şunlardır:

* Belirtilen örnek için Visual Studio.
* extensions [klasörünün dışına yükleme.](set-install-root.md)
* İşlemci mimarisinin algılanması.
* Dille ayrılmış dil paketlerine bağımlılık.
* [NGEN desteğiyle yükleme.](ngen-support.md)

## <a name="build-an-extension-for-visual-studio-2017"></a>Visual Studio 2017 için uzantı oluşturma

Yeni VSIX v3 bildirim biçiminin yazması için tasarımcı aracı, Visual Studio 2017'de kullanılabilir. Tasarımcı araçlarını kullanma veya VSIX v3 uzantıları geliştirmek için proje ve bildirimde el ile güncelleştirmeler yapma hakkında ayrıntılı bilgi için genişletilebilirlik projelerini [Visual Studio 2017'ye](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) geçirme belgesine bakın.

## <a name="change-visual-studio-user-data-path"></a>Değiştir: Visual Studio veri yolunu değiştirme

Daha önce, her bir ana sürümün yalnızca Visual Studio makinede mevcut olabilirdi. Visual Studio 2017'nin yan yana yüklemelerini desteklemek için, Visual Studio için birden çok kullanıcı veri yolu kullanıcının makinesine mevcut olabilir.

Visual Studio Visual Studio, Visual Studio Ayarlar Manager'ın kullanımına güncelleştirilebilir. Bu işlem dışında Visual Studio kod, buradaki kılavuzu takip Visual Studio belirli bir [yüklemenin kullanıcı yolunu bulabilir.](locating-visual-studio.md)

## <a name="change-global-assembly-cache-gac"></a>Değişiklik: Genel Derleme Önbelleği (GAC)

Çoğu Visual Studio temel derlemeler artık GAC'ye yüklenmez. Bu işlemde çalışan kodun çalışma zamanında gerekli derlemeleri Visual Studio için aşağıdaki değişiklikler yapıldı.

> [!NOTE]
> Aşağıdaki [INSTALLDIR], uygulamanın yükleme kök dizinine Visual Studio. *VSIXInstaller.exe* bunu otomatik olarak doldurmakla birlikte özel dağıtım kodu yazmak için lütfen [Visual Studio.](locating-visual-studio.md)

* Yalnızca GAC'ye yüklenmiş derlemeler:

  Bu derlemeler <em>artık [INSTALLDIR]\Common7\IDE \* , *[INSTALLDIR]\Common7\IDE\PublicAssemblies</em> veya *[INSTALLDIR]\Common7\IDE\PrivateAssemblies* altına yüklenir. Bu klasörler, işlem Visual Studio yollarının bir parçası.

* Yoklama olmayan bir yola ve GAC'ye yüklenmiş derlemeler:

  * GAC'de kopya kurulumdan kaldırıldı.
  * Derleme için bir kod temel girdisi belirtmek için *bir .pkgdef* dosyası eklendi.

    Örnek:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    Çalışma zamanında, Visual Studio pkgdef alt sistemi bu girdileri Visual Studio işleminin çalışma zamanı yapılandırma dosyası *([VSAPPDATA]\devenv.exe.config* altında) öğeleri olarak [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) birleştirmektedir. Bu, araştırma yollarını aramayı önleye Visual Studio işlem derlemenizi bulmasına izin vermenin önerilen yoludur.

### <a name="reacting-to-this-breaking-change"></a>Bu yeni değişiklike tepki verme

* Uzantınız aşağıdaki işlemde Visual Studio:

  * Kodunuz, temel derlemeleri Visual Studio bulabilir.
  * Gerekirse derlemelerinize bir yol belirtmek için *bir .pkgdef* dosyası kullanmayı göz önünde bulundurabilirsiniz.

* Uzantınız işlem dışında Visual Studio:

  Yapılandırma dosyası veya derleme çözümleyicisi kullanarak <em>[INSTALLDIR]\Common7\IDE \* , *[INSTALLDIR]\Common7\IDE\PublicAssemblies</em> veya *[INSTALLDIR]\Common7\IDE\PrivateAssemblies* altında Visual Studio çekirdek derlemeleri aramayı göz önünde bulundurabilirsiniz.

## <a name="change-reduce-registry-impact"></a>Değişiklik: Kayıt defteri etkisini azaltma

### <a name="global-com-registration"></a>Genel COM kaydı

* Daha önce Visual Studio COM kaydını desteklemek için HKEY_CLASSES_ROOT ve HKEY_LOCAL_MACHINE hive'lara birçok kayıt defteri anahtarı yükleyemedik. Bu etkiyi ortadan kaldırmak Visual Studio com bileşenleri [için KayıtSız Etkinleştirme kullanıyor.](/previous-versions/dotnet/articles/ms973913(v=msdn.10))
* Sonuç olarak, %ProgramFiles(x86)%\Common Files\Microsoft Shared\MSEnv altındaki çoğu TLB / OLB / DLL dosyası artık varsayılan olarak Visual Studio. Bu dosyalar artık [INSTALLDIR] altında, konak işlemi Registration-Free com bildirimleriyle birlikte Visual Studio yüklenir.
* Sonuç olarak, Visual Studio COM arabirimleri için genel COM kaydına dayanan dış kod artık bu kayıtları bulamaz. Bu işlemde Visual Studio kodda bir fark olmaz.

### <a name="visual-studio-registry"></a>Visual Studio kayıt defteri

* Daha Visual Studio kayıt defteri anahtarlarını sistemin HKEY_LOCAL_MACHINE ve  HKEY_CURRENT_USER **hive'Visual Studio** anahtar altında yükleyemedik:

  * **HKLM\Software\Microsoft\VisualStudio \{ Sürüm}**: MSI yükleyicileri ve makine başına uzantılar tarafından oluşturulan kayıt defteri anahtarları.
  * **HKCU\Software\Microsoft\VisualStudio \{ Sürüm}**: Kullanıcıya özgü Visual Studio depolamak için oluşturulan kayıt defteri anahtarları.
  * **HKCU\Software\Microsoft\VisualStudio \{ Version}_Config:** Yukarıdaki bir Visual Studio HKLM anahtarının kopyası ve *.pkgdef* dosyalarından uzantılarla birleştirilen kayıt defteri anahtarları.

* Kayıt defteri üzerindeki etkiyi azaltmak için Visual Studio kayıt defteri anahtarlarını *[VSAPPDATA]\privateregistry.bin* altındaki özel bir ikili dosyada depolamak için [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) işlevini kullanıyor. Sistem kayıt defterinde yalnızca Visual Studio çok az sayıda anahtar kalır.
* Uygulama işleminin içinde Visual Studio kod etkilenmez. Visual Studio, HKCU anahtarı altındaki tüm kayıt Visual Studio özel kayıt defterine yeniden yönlendirecek. Diğer kayıt defteri konumlarını okuma ve yazma, sistem kayıt defterini kullanmaya devam eder.
* Dış kodun kayıt defteri girdilerini yüklemek ve bu dosyadan Visual Studio gerekir.

### <a name="react-to-this-breaking-change"></a>React değişiklikle ilgili önemli bir değişiklik

* Dış kod, COM bileşenleri için Registration-Free için de etkinleştirecek şekilde dönüştürülmesi gerekir.
* Dış bileşenler, buradaki Visual Studio [konumlarını bulabilir.](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup)
* Dış bileşenlerin kayıt defteri [anahtarlarına doğrudan okuma/yazma Ayarlar External](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) Visual Studio öneririz.
* Uzantınız tarafından kullanılan bileşenlerin kayıt için başka bir teknik uygulayıp uygulamadığını kontrol edin. Örneğin, hata ayıklayıcısı uzantıları yeni [msvsmon JSON dosyası COM kaydı'nın avantajını kullanabilir.](migrate-debugger-COM-registration.md)