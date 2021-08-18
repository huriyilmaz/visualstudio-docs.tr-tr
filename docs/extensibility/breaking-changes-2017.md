---
title: Visual Studio 2017 genişletilebilirlikteki son değişiklikler
description: Visual Studio 2017 ' de genişletilebilirlik modelinde yapılan son değişikliklerin teknik ayrıntıları ve bunları ele almak için yapabilecekleriniz hakkında bilgi edinin.
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
ms.openlocfilehash: 00158c527ba4e5ea084836c49c5a8b7f5ba95366
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051319"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Visual Studio 2017 genişletilebilirliği içindeki değişiklikler

Visual Studio 2017, kullanıcılara yüklenen iş yükleri ve özellikler üzerinde daha fazla seçenek sunarak kullanıcı sistemlerindeki Visual Studio etkisini azaltan [daha hızlı, daha hafif Visual Studio bir yükleme deneyimi](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) sunar. Bu geliştirmeleri desteklemek için, bazı son değişiklikler dahil olmak üzere genişletilebilirlik modelinde değişiklikler yaptık. Bu makalede, bu değişikliklerin teknik ayrıntıları ve bunların ele getirilmesi için neler yapılabileceği açıklanmaktadır.

> [!NOTE]
> Bazı bilgiler, zaman içinde uygulama ayrıntılarıdır ve daha sonra değiştirilebilir.

## <a name="changes-affecting-vsix-format-and-installation"></a>VSıX biçimini ve yüklemeyi etkileyen değişiklikler

Visual Studio 2017, bir basit yükleme deneyimini desteklemek için vsıx v3 (sürüm 3) biçimini kullanıma sunmuştur.

VSıX biçimindeki değişiklikler şunları içerir:

* Kurulum önkoşulları bildirimi. hafif ve hızlı yükleme Visual Studio taahhüdüne ulaşmak için, yükleyici artık kullanıcılara daha fazla yapılandırma seçeneği sunar. Sonuç olarak, bir uzantının gerektirdiği özellik ve bileşenlerin yüklü olduğundan emin olmak için uzantıların bağımlılıklarını bildirmesi gerekir.

  * Visual Studio 2017 yükleyicisi, uzantınızı yüklemenin bir parçası olarak kullanıcı için gerekli bileşenleri edinmeyi ve yüklemeyi otomatik olarak sunmaktadır.
  * Kullanıcılar ayrıca, yeni VSıX v3 biçimi kullanılarak derlenmeyen bir uzantıyı yüklemeye çalışırken de uyarılabilirler. Bu dosyalar, hedef sürüm 15,0 olarak bildirimde işaretlenmiş olsalar bile

* VSıX biçimi için gelişmiş yetenekler. yan yana yüklemeleri de destekleyen Visual Studio [düşük etkili bir yüklemesine](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) iletmek için, artık çoğu yapılandırma verilerini sistem kayıt defterine kaydedemedik ve Visual Studio özel derlemeleri GAC 'den dışarı taşıdık. Ayrıca VSıX biçimi ve VSıX yükleme altyapısının yeteneklerini de geliştirdik. Bu özellik, bazı yükleme türlerine yönelik uzantılarınızı yüklemek için bir MSI veya EXE yerine bunu kullanmanıza olanak sağlar.

Yeni yetenekler şunlardır:

* belirtilen Visual Studio örneğine kayıt.
* [Uzantılar klasörü](set-install-root.md)dışında yükleme.
* İşlemci mimarisinin algılanması.
* Dile ayrılmış dil paketlerinde bağımlılık.
* [Ngen desteğiyle](ngen-support.md)yükleme.

## <a name="build-an-extension-for-visual-studio-2017"></a>Visual Studio 2017 için uzantı oluşturma

yeni vsıx v3 bildirim biçiminin yazılması için tasarımcı araçları Visual Studio 2017 ' de mevcuttur. tasarımcı araçlarının kullanılmasıyla ilgili ayrıntılı bilgi için bkz. [nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2017 'ye geçirme](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) veya projede el ile güncelleştirme yapma veya vsıx v3 uzantıları geliştirmeye yönelik bildirim.

## <a name="change-visual-studio-user-data-path"></a>değişiklik: Visual Studio kullanıcı veri yolu

daha önce, her makinede her bir Visual Studio ana sürümünün yalnızca bir yüklemesi bulunabilir. Visual Studio 2017 ' nin yan yana yüklemelerini desteklemek için, kullanıcının makinesinde Visual Studio için birden çok kullanıcı veri yolu bulunabilir.

Visual Studio işlemi içinde çalışan kod, Visual Studio Ayarlar Manager 'ı kullanacak şekilde güncelleştirilmeleri gerekir. Visual Studio işlemin dışında çalışan kod, [buradaki kılavuzu izleyerek](locating-visual-studio.md)belirli bir Visual Studio yüklemesinin kullanıcı yolunu bulabilir.

## <a name="change-global-assembly-cache-gac"></a>Değişiklik: genel bütünleştirilmiş kod önbelleği (GAC)

çoğu Visual Studio çekirdek derleme artık GAC 'ye yüklenmez. Visual Studio işleminde çalışan kodun çalışma zamanında gerekli derlemeleri hala bulabilmesini sağlamak için aşağıdaki değişiklikler yapılmıştır.

> [!NOTE]
> Aşağıdaki [ıNSTALLDIR], Visual Studio yükleme kök dizinine başvurur. *VSIXInstaller.exe* , bunu otomatik olarak dolduracaktır, ancak özel dağıtım kodu yazmak için lütfen [Visual Studio bulma](locating-visual-studio.md)konusunu okuyun.

* Yalnızca GAC 'ye yüklenmiş olan derlemeler:

  Bu derlemeler artık <em>[INSTALLDİR] \Common7\IDE \* , * [INSTALLDİR] \Common7\IDE\PublicAssemblies</em> veya *[INSTALLDİR] \Common7\IDE\PrivateAssemblies* altına yüklendi. bu klasörler Visual Studio işlemin yoklama yollarının bir parçasıdır.

* Yoklama dışı bir yola ve GAC 'ye yüklenmiş derlemeler:

  * GAC 'deki kopya kurulumdan kaldırılmıştır.
  * Derleme için bir kod tabanı girişi belirtmek üzere bir *. pkgdef* dosyası eklenmiştir.

    Örnek:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    çalışma zamanında, Visual Studio pkgdef alt sistemi bu girdileri Visual Studio işleminin çalışma zamanı yapılandırma dosyası ( *[VSAPPDATA] \devenv.exe.config*) öğesi olarak birleştirir [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) . bu, Visual Studio işleminin derlemeyi bulmasını sağlamak için önerilen yoldur, çünkü araştırma yolları arasında aramayı önler.

### <a name="reacting-to-this-breaking-change"></a>Bu son değişikliğe yeniden davranıyor

* uzantınız Visual Studio işlemi içinde çalışıyorsa:

  * kodunuz Visual Studio çekirdek bütünleştirilmiş kodlarını bulabilir.
  * Gerektiğinde derlemelerinize bir yol belirtmek için bir *. pkgdef* dosyası kullanmayı düşünün.

* uzantınız Visual Studio işlem dışında çalışıyorsa:

  yapılandırma dosyası veya derleme çözümleyici kullanarak <em>[ınstalldir] \Common7\IDE \* , * [ınstalldir] \Common7\IDE\PublicAssemblies</em> veya *[ınstalldir] \Common7\IDE\PrivateAssemblies* altında Visual Studio çekirdek bütünleştirilmiş kodları aramak için göz önünde bulundurun.

## <a name="change-reduce-registry-impact"></a>Değişiklik: kayıt defteri etkisini azaltma

### <a name="global-com-registration"></a>Genel COM kaydı

* daha önce, yerel COM kaydını desteklemek için HKEY_CLASSES_ROOT ve HKEY_LOCAL_MACHINE kovanına birçok kayıt defteri anahtarı Visual Studio. bu etkiyi ortadan kaldırmak için Visual Studio artık [COM bileşenleri için kayıt-ücretsiz etkinleştirmeyi](/previous-versions/dotnet/articles/ms973913(v=msdn.10))kullanır.
* Sonuç olarak,% ProgramFiles (x86)% \ Common Files\Microsoft Shared\MSEnv altındaki TLB/OLB/DLL dosyaları artık Visual Studio tarafından varsayılan olarak yüklenmez. bu dosyalar artık, Visual Studio ana bilgisayar işlemi tarafından kullanılan karşılık gelen Registration-Free COM bildirimleri ile [ınstalldir] altına yüklenir.
* sonuç olarak, Visual Studio COM arabirimleri için genel COM kaydına dayanan dış kod artık bu kayıtları bulamaz. Visual Studio işlemi içinde çalışan kod, bir fark görmez.

### <a name="visual-studio-registry"></a>Visual Studio kayıt defteri

* daha önce, Visual Studio birçok kayıt defteri anahtarını sistemin **HKEY_LOCAL_MACHINE** ve **HKEY_CURRENT_USER** kovanına Visual Studio özgü bir anahtar altına yüklemişti:

  * **Hklm\software\microsoft\visualstudio \{ Sürüm}**: MSI yükleyicileri ve makine başına uzantılar tarafından oluşturulan kayıt defteri anahtarları.
  * **Hkcu\software\microsoft\visualstudio \{ sürüm}**: kullanıcıya özgü ayarları depolamak için Visual Studio tarafından oluşturulan kayıt defteri anahtarları.
  * **Hkcu\software\microsoft\visualstudio \{ sürüm} _Config**: yukarıdaki Visual Studio HKLM anahtarının bir kopyası ve *. pkgdef* dosyalarından birleştirilmiş kayıt defteri anahtarları uzantılara göre.

* kayıt defterindeki etkiyi azaltmak için Visual Studio artık [regloadappkey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) işlevini kullanarak kayıt defteri anahtarlarını *[VSAPPDATA] \privateregistry.bin* altında özel bir ikili dosyada depolar. yalnızca çok az sayıda Visual Studio özel anahtar sistem kayıt defterinde kalır.
* Visual Studio işlemi içinde çalışan mevcut kod etkilenmez. Visual Studio, HKCU Visual Studio özgü anahtar altındaki tüm kayıt defteri işlemlerini özel kayıt defterine yönlendirir. Diğer kayıt defteri konumlarına okuma ve yazma, sistem kayıt defterini kullanmaya devam edecektir.
* dış kodun, Visual Studio kayıt defteri girdileri için bu dosyadan yüklenmesi ve okunması gerekir.

### <a name="react-to-this-breaking-change"></a>bu son değişikliğe React

* Dış kod, COM bileşenleri için Registration-Free etkinleştirme kullanacak şekilde dönüştürülmelidir.
* dış bileşenler, [buradaki kılavuzu izleyerek](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup)Visual Studio konumunu bulabilir.
* dış bileşenlerin, Visual Studio kayıt defteri anahtarlarına doğrudan okumak/yazmak yerine [dış Ayarlar yöneticisi](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) 'ni kullanmasını öneririz.
* Uzantınızın kullandığı bileşenlerin kayıt için başka bir teknik uygulanıp uygulanmadığını denetleyin. Örneğin, hata ayıklayıcı uzantıları New [msvsmon JSON-FILE com kaydından](migrate-debugger-COM-registration.md)faydalanabilir.