---
title: Devenv komut satırı anahtarları
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3ed82bd8ba3845541d7dce628f99fb78b62ab9f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595715"
---
# <a name="devenv-command-line-switches"></a>Devenv komut satırı anahtarları

Devenv, komut satırından IDE için çeşitli seçenekler ayarlamanıza, projeler oluşturmanıza, projelerde hata ayıklamanıza ve proje dağıtmanıza imkan tanır. IDE 'yi bir komut dosyası veya. bat dosyasından (gecelik derleme betiği gibi) çalıştırmak veya IDE 'yi belirli bir yapılandırmada başlatmak için bu anahtarları kullanın.

> [!NOTE]
> Derleme ile ilgili görevler için devenv yerine MSBuild kullanmanız önerilir. Daha fazla bilgi için [MSBuild komut satırı başvurusu](../../msbuild/msbuild-command-line-reference.md).

VSPackage geliştirmeyle ilgili anahtarlar hakkında daha fazla bilgi için bkz. [VSPackage geliştirmesi Için Devenv komut satırı anahtarları](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

## <a name="devenv-switch-syntax"></a>Devenv anahtarı sözdizimi

İle başlayan komutlar `devenv` tarafından işlenen `devenv.com` gibi standart sistem akışları çıkışını sunan yardımcı program `stdout` ve `stderr`. Çıktı, örneğin bir .txt dosyasına yakaladığında yardımcı programı uygun g/ç yönlendirmesi belirler.

Alternatif olarak, `devenv.exe` ile başlayan komutlar aynı anahtarları kullanabilir, ancak `devenv.com` yardımcı programı atlanır. Kullanarak `devenv.exe` doğrudan çıkış konsolda görüntülenmesini engeller.

`devenv` anahtarların sözdizimi kuralları, diğer DOS komut satırı yardımcı programları için kurallara benzer. Aşağıdaki sözdizimi kurallarını tümüne uygula `devenv` anahtarlar ve bunların bağımsız değişkenleri:

- İle başlayan komutlar `devenv`.

- Anahtarlar büyük/küçük harfe duyarlı değildir.

- Bir anahtarı, kısa çizgi ("-") veya eğik çizgi ("/") kullanarak belirtebilirsiniz.

- Bir çözüm veya proje belirtirken, ilk bağımsız değişken çözüm dosyası veya dosya yolu da dahil olmak üzere proje dosyasının adıdır.

- İlk bağımsız değişken bir çözüm veya proje olmayan bir dosya ise, bu dosya, IDE 'nin yeni bir örneğinde uygun düzenleyicide açılır.

- Bir proje dosyası adı bir çözüm dosyası adı yerine sağladığında bir `devenv` komut aynı ada sahip bir çözüm dosyası için proje dosyasının üst klasörü arar. Örneğin, komut `devenv myproject1.vbproj /build` `myproject1.sln`adlı bir çözüm dosyası için üst klasörü arar.

  > [!NOTE]
  > Bu projeye başvuran bir ve yalnızca bir çözüm dosyası, kendi üst klasörde bulunmalıdır. Üst klasör herhangi bir çözüm dosyası içeriyorsa bu projeye başvuran ya da üst klasör ona başvuran iki veya daha fazla çözüm dosyası içeriyorsa, ardından bir geçici çözüm dosyası oluşturulur.

- Dosya yolları ve dosya adı boşluklar, bunları tırnak içine almalısınız (""). Örneğin: `"c:\project a\"`.

- Anahtarlar ve bağımsız değişkenler aynı satırda arasında bir boşluk karakteri Ekle. Örneğin, komut `devenv /log output.txt` IDE 'yi açar ve bu oturuma ait tüm günlük bilgilerini çıktı. txt dosyasına çıkarır.

- `devenv` komutlarında kalıp eşleme söz dizimini kullanamazsınız.

## <a name="devenv-switches"></a>Devenv anahtarları

Aşağıdaki komut satırı anahtarları IDE 'yi görüntüler ve açıklanan görevi yapar.

|Komut satırı anahtarı|Açıklama|
| - |-----------------|
|[/Command](command-devenv-exe.md)|IDE'yi başlatır ve belirtilen komutu yürütür.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Hata ayıklayıcının denetiminin altında bir C++ yürütülebilir dosyayı yükler. Bu anahtar Visual Basic veya C# yürütülebilir dosyalar için kullanılamaz. Daha fazla bilgi için [otomatik olarak hata ayıklayıcıda bir işlem başlatmak](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).<br /><br /> `devenv /debugexe mysln.exe`|
|[/Diff](diff.md)|İki dosyayı karşılaştırır. Dört parametre alır: *SourceFile*, *TargetFile*, *sourcedisplayname* (isteğe bağlı) ve *targetdisplayname* (isteğe bağlı).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|Herhangi bir proje yüklemeden belirtilen çözümü açar.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edit](edit-devenv-exe.md)|Belirtilen dosyalar, bu uygulamanın çalışan bir örneğini açar. Varsa çalışan örnek yoksa Basitleştirilmiş pencere düzenini ile yeni bir örneğini başlatır.<br /><br /> `devenv /edit File1 File2`|
|[/LCıD veya/L](lcid-devenv-exe.md)|IDE için varsayılan dili ayarlar. Visual Studio yüklemenize belirtilen dil dahil değilse, bu ayar yok sayılır.<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|Visual Studio başlatılır ve tüm etkinlik günlük dosyasına kaydeder.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|Giriş ekranını göstermeden IDE 'yi açar.<br /><br /> `devenv /nosplash File1 File2`|
|[/Run veya/R](run-devenv-exe.md)|Derler ve belirtilen çözüm çalıştırır.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|Derler ve belirtilen çözüm çalıştırır, çözüm çalıştırılır ve çözüm çalışması bittikten sonra IDE'yi kapatır, IDE'nin en aza indirir.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Visual Studio 'Yu güvenli modda başlatır. Bu anahtar yalnızca varsayılan ortamı, varsayılan Hizmetleri ve üçüncü taraf paketlerin sevk edilen sürümlerini yükler.<br /><br /> Bu anahtar bağımsız değişken almaz.|
|[/UseEnv](useenv-devenv-exe.md)|IDE 'nin derleme için C++ Path, ıNCLUDE, LıBPATH ve LIB ortam değişkenlerini kullanmasına neden olur. Bu anahtar ile birlikte yüklenir **C++ ile masaüstü geliştirme** iş yükü. Daha fazla bilgi için [komut satırı derlemeleri için yolu ve ortam değişkenlerini ayarlama](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|

Aşağıdaki komut satırı anahtarları IDE 'yi görüntülemez.

|Komut satırı anahtarı|Açıklama|
| - |-----------------|
|[/?](q-devenv-exe.md)|**Komut istemi penceresinde**`devenv` anahtarlarına yönelik yardım görüntüler.<br /><br /> Bu anahtar bağımsız değişken almaz.|
|[/Build](build-devenv-exe.md)|Belirtilen çözüm veya projeyi yapılandırmasına göre belirtilen çözümü derler.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|Kaynak dosyaları etkilemeden oluşturma komutu tarafından oluşturulan tüm dosyaları siler.<br /><br /> `devenv mysln.sln /clean`|
|[/Deploy](deploy-devenv-exe.md)|Çözümü, çözümün yapılandırmasına göre, dağıtım için gerekli dosyalarla birlikte oluşturur.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|Oluşturma sırasında hatalar almak için bir dosya belirtmenizi sağlar.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Project](project-devenv-exe.md)|Projeyi oluşturmak için temizlemek veya dağıtmak. Bu anahtarı yalnızca `/Build`, `/Rebuild`, `/Clean`veya `/Deploy` anahtarını da sağladıysanız kullanabilirsiniz.<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Derleme veya dağıtım için proje yapılandırmasını belirtir. Bu anahtarı yalnızca `/Project` anahtarını da sağladıysanız kullanabilirsiniz.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Rebuild](rebuild-devenv-exe.md)|Temizler ve daha sonra belirtilen çözüm veya projeyi yapılandırmasına göre belirtilen çözümü derler.<br /><br /> `devenv mysln.sln /rebuild`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Visual Studio varsayılan ayarlarına geri yükler. İsteğe bağlı olarak ayarları belirtilen `.vssettings` dosyasına sıfırlar.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Upgrade](upgrade-devenv-exe.md)|Bu dosyalar için geçerli Visual Studio biçimlerinde belirtilen çözüm dosyasını ve tüm proje dosyaları ya da belirtilen proje dosyasını yükseltir.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](general-environment-options-dialog-box.md)
- [VSPackage geliştirmesi için Devenv komut satırı anahtarları](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
