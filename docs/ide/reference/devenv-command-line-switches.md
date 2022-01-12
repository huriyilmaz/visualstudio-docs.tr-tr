---
title: Devenv komut satırı anahtarları
description: Devenv komut satırı anahtarları hakkında bilgi edinmek ve bunların IDE seçeneklerini ayarlamak ve proje derlemek, hata ayıklamak ve dağıtmak için bunların nasıl kullanacağız hakkında bilgi edinmek için komut satırına bakın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: c8d24f0f4d446c4edfecd519f95bcf867d82bd1b
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803472"
---
# <a name="devenv-command-line-switches"></a>Devenv komut satırı anahtarları

Devenv, IDE için çeşitli seçenekler ayarlamaya, proje derlemeye, projelerde hata ayıklamaya ve komut satırına proje dağıtmaya olanak sağlar. IDE'i bir betikten veya bir .bat dosyasından (gecelik derleme betiği gibi) çalıştırmak veya belirli bir yapılandırmada IDE'ye başlamak için bu anahtarları kullanın.

> [!NOTE]
> Derlemeyle ilgili görevler için devenv yerine MSBuild önerilir. Daha fazla bilgi için [bkz. MSBuild satırı başvurusu.](../../msbuild/msbuild-command-line-reference.md)

VSPackage geliştirmeyle ilgili anahtarlar hakkında bilgi için bkz. VSPackage geliştirmesi için [Devenv komut satırı anahtarları.](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)

## <a name="devenv-switch-syntax"></a>Devenv anahtar söz dizimi

ile başlayan komutlar, ve gibi standart sistem akışları üzerinden çıkış `devenv` `devenv.com` teslimi olan yardımcı programı tarafından `stdout` `stderr` tanıtıcıdır. yardımcı programı, çıktıyı (örneğin, bir işletim sistemi dosyasına) yakalarken uygun .txt belirler.

Alternatif olarak, ile başlayan `devenv.exe` komutlar aynı anahtarları kullanabilir ancak `devenv.com` yardımcı program atlanır. doğrudan `devenv.exe` kullanmak, çıkışın konsolda görünmesini önler.

Anahtarlar için söz `devenv` dizimi kuralları, diğer DOS komut satırı yardımcı programlarının kurallarına benzer. Aşağıdaki söz dizimi kuralları tüm anahtarlar `devenv` ve bunların bağımsız değişkenleri için geçerlidir:

- Komutlar ile `devenv` başlar.

- Anahtarlar büyük/büyük/büyük harfe duyarlı değildir.

- Bir anahtarı, kısa çizgi ("-") veya eğik çizgi ("/") kullanarak belirtabilirsiniz.

- Bir çözüm veya proje belirtirken ilk bağımsız değişken, dosya yolu da dahil olmak üzere çözüm dosyasının veya proje dosyasının adıdır.

- İlk bağımsız değişken çözüm veya proje değil bir dosya ise, bu dosya yeni bir IDE örneğinde uygun düzenleyicide açılır.

- Bir çözüm dosyası adı yerine bir proje dosyası adı sağlarsanız, bir komut proje dosyasının üst klasöründe aynı adı içeren bir çözüm `devenv` dosyası arar. Örneğin, komutu `devenv myproject1.vbproj /build` üst klasörde adlı bir çözüm dosyası `myproject1.sln` arar.

  > [!NOTE]
  > Bu projeye başvurulan bir ve yalnızca bir çözüm dosyası üst klasöründe bulunarak. Üst klasörde bu projeye başvurulan bir çözüm dosyası yoksa veya üst klasörde ona başvurulan iki veya daha fazla çözüm dosyası varsa, geçici bir çözüm dosyası oluşturulur.

- Dosya yolları ve dosya adları boşluk içeriyorsa, bunları tırnak işaretleri ("") içine almanız gerekir. Örneğin, `"c:\project a\"`.

- Aynı satıra anahtarlar ve bağımsız değişkenler arasında bir boşluk karakteri ekler. Örneğin, komutu `devenv /log output.txt` IDE'i açar ve oturum için tüm günlük bilgilerini çıkış olarak output.txt.

- Komutlarda desen eşleştirme söz dizimi `devenv` kullanasınız.

## <a name="devenv-switches"></a>Devenv anahtarları

Aşağıdaki komut satırı anahtarları IDE'leri görüntüler ve açıklanan görevi yapar.

|Komut satırı anahtarı|Description|
| - |-----------------|
|[/Command](command-devenv-exe.md)|IDE'i başlatır ve belirtilen komutu yürütür.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Hata ayıklayıcı denetimi altında bir C++ yürütülebilir dosyası yükler. Bu anahtar, C# Visual Basic için kullanılamaz. Daha fazla bilgi için [bkz. Hata ayıklayıcıda otomatik olarak bir işlem başlatma.](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger)<br /><br /> `devenv /debugexe mysln.exe`|
|[/Diff](diff.md)|İki dosyanın karşılaştırması. Dört parametre alır: *SourceFile*, *TargetFile*, *SourceDisplayName* (isteğe bağlı) ve *TargetDisplayName* (isteğe bağlı).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|Herhangi bir proje yüklemeden belirtilen çözümü açar.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edit](edit-devenv-exe.md)|Belirtilen dosyaları bu uygulamanın çalışan bir örneğinde açar. Çalışan örnek yoksa, basitleştirilmiş pencere düzenine sahip yeni bir örnek başlatır.<br /><br /> `devenv /edit File1 File2`|
|[/LCID veya /L](lcid-devenv-exe.md)|IDE için varsayılan dili ayarlar. Belirtilen dil Visual Studio yüklemenize dahil Visual Studio yoksayılır.<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|Tüm Visual Studio günlüğe kaydeder ve günlük dosyasına kaydeder.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSoidh](nosplash-devenv-exe.md)|Giriş ekranı göstermeden IDE'i açar.<br /><br /> `devenv /nosplash File1 File2`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Varsayılan ayarları Visual Studio geri yükleme. İsteğe bağlı olarak ayarları belirtilen dosyaya `.vssettings` sıfırlar.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Run veya /R](run-devenv-exe.md)|Belirtilen çözümü derler ve çalıştırır.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|Belirtilen çözümü derler ve çalıştırır, çözüm çalıştır olduğunda IDE'nin en aza indirilmesine ve çözümün çalışması sona erdikten sonra IDE'nin kapanmasına neden olur.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Güvenli Visual Studio modunda başlatılır. Bu anahtar yalnızca varsayılan ortamı, varsayılan hizmetleri ve üçüncü taraf paketlerin gönderilen sürümlerini yükler.<br /><br /> Bu anahtar hiçbir bağımsız değişken alır.|
|/TfsLink|Dosya Takım Gezgini açar ve kaydedilmişse sağlanan yapıt URI'sini bir görüntüleyiciyi açar.|
|[/UseEnv](useenv-devenv-exe.md)|IDE'nin C++ derlemesi için PATH, INCLUDE, LIBPATH ve LIB ortam değişkenlerini kullanmalarına neden olur. Bu anahtar C++ ile **Masaüstü geliştirme iş yüküyle** birlikte yüklenir. Daha fazla bilgi için, [bkz. Setting the Path and Environment Variables for Command-Line Builds](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|

Aşağıdaki komut satırı anahtarları IDE'leri görüntülemez.

|Komut satırı anahtarı|Description|
| - |-----------------|
|[/?](q-devenv-exe.md)|Komut İstemi `devenv` penceresinde anahtarlar için yardım **görüntüler.**<br /><br /> Bu anahtar hiçbir bağımsız değişken alır.|
|[/Build](build-devenv-exe.md)|Belirtilen çözümün yapılandırmasına göre belirtilen çözümü veya projeyi derleme.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|Kaynak dosyaları etkilemeden derleme komutu tarafından oluşturulan tüm dosyaları siler.<br /><br /> `devenv mysln.sln /clean`|
|[/Deploy](deploy-devenv-exe.md)|Çözümü, çözümün yapılandırmasına göre dağıtım için gereken dosyalarla birlikte derleme.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|Derleme sırasında hataları almak için bir dosya belirtmenize olanak sağlar.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Project](project-devenv-exe.md)|Derleme, temizleme veya dağıtma projesi. Bu anahtarı yalnızca , , veya anahtarını da `/Build` `/Rebuild` `/Clean` sağdıysanız `/Deploy` kullanabilirsiniz.<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Derlemek veya dağıtmak için proje yapılandırmasını belirtir. Bu anahtarı yalnızca anahtarı da sağdıysanız `/Project` kullanabilirsiniz.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Rebuild](rebuild-devenv-exe.md)|Temizlenir ve ardından belirtilen çözümün yapılandırmasına göre belirtilen çözümü veya projeyi derleme.<br /><br /> `devenv mysln.sln /rebuild`|
|[/Upgrade](upgrade-devenv-exe.md)|Belirtilen çözüm dosyasını ve tüm proje dosyalarını veya belirtilen proje dosyasını bu dosyalar için geçerli Visual Studio biçimine yükselter.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](general-environment-options-dialog-box.md)
- [VSPackage geliştirme için Devenv komut satırı anahtarları](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
