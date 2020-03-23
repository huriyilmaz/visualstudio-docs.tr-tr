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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595715"
---
# <a name="devenv-command-line-switches"></a>Devenv komut satırı anahtarları

Devenv, IDE için çeşitli seçenekler belirlemenize, projeler oluşturmanıza, projeleri hata ayıklamanıza ve komut satırından proje dağıtmanıza olanak tanır. IDE'yi bir komut dosyasından veya .bat dosyasından (gece oluşturma komut dosyası gibi) çalıştırmak veya IDE'yi belirli bir yapılandırmada başlatmak için bu anahtarları kullanın.

> [!NOTE]
> Yapıyla ilgili görevler için devenv yerine MSBuild kullanmanız önerilir. Daha fazla bilgi için [MSBuild komut satırı başvurusuna](../../msbuild/msbuild-command-line-reference.md)bakın.

VSPackage geliştirme ile ilgili anahtarlar hakkında bilgi için, ayrıca [VSPackage geliştirme için Devenv komut satırı anahtarlarına](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)bakın.

## <a name="devenv-switch-syntax"></a>Devenv anahtarı sözdizimi

Bununla `devenv` başlayan komutlar, standart `devenv.com` sistem akışları aracılığıyla çıktı sağlayan yardımcı `stdout` program `stderr`tarafından işlenir. Yardımcı program, çıktıyı yakaladığında uygun G/Ç yönlendirmesini belirler, örneğin bir .txt dosyasına.

Alternatif olarak, ile `devenv.exe` başlayan komutlar aynı anahtarları kullanabilir, ancak `devenv.com` yardımcı program atlanır. Doğrudan `devenv.exe` kullanmak, çıktının konsolda görünmesini engeller.

Anahtarlar için `devenv` sözdizimi kuralları diğer DOS komut satırı yardımcı programları için kurallara benzer. Aşağıdaki sözdizimi kuralları `devenv` tüm anahtarlar ve bağımsız değişkenleri için geçerlidir:

- Komutlar `devenv`ile başlar.

- Anahtarlar büyük/küçük harf duyarlı değildir.

- Tire ("-") veya ileri eğik çizgi ("/") kullanarak bir anahtar belirtebilirsiniz.

- Bir çözüm veya proje belirtirken, ilk bağımsız değişken, dosya yolu da dahil olmak üzere çözüm dosyasının veya proje dosyasının adıdır.

- İlk bağımsız değişken çözüm veya proje olmayan bir dosyaysa, bu dosya Uygun düzenleyicide, IDE'nin yeni bir örneğinde açılır.

- Çözüm dosyası adı yerine bir proje dosyası adı `devenv` sağladığında, komut aynı ada sahip bir çözüm dosyası için proje dosyasının üst klasörünü arar. Örneğin, komut, `devenv myproject1.vbproj /build` adı geçen `myproject1.sln`bir çözüm dosyası için ana klasörü arar.

  > [!NOTE]
  > Bu projeye başvuruyapan bir ve tek çözüm dosyası, ana klasöründe bulunmalıdır. Ana klasörbu projeye başvurulan bir çözüm dosyası içermese veya üst klasörde başvuru yapan iki veya daha fazla çözüm dosyası varsa, geçici bir çözüm dosyası oluşturulur.

- Dosya yolları ve dosya adları boşluklar içeriyorsa, bunları tırnak işaretlerine (""") eklemeniz gerekir. Örneğin, `"c:\project a\"`.

- Anahtarlar ve bağımsız değişkenler arasında aynı satıra bir boşluk karakteri ekleyin. Örneğin, komut `devenv /log output.txt` IDE'yi açar ve bu oturuma ait tüm günlük bilgilerini output.txt'ye çıkarır.

- `devenv` Komutlarda desen eşleştirme sözdizimini kullanamazsınız.

## <a name="devenv-switches"></a>Devenv anahtarları

Aşağıdaki komut satırı anahtarları IDE'yi görüntüler ve açıklanan görevi yapar.

|Komut satırı anahtarı|Açıklama|
| - |-----------------|
|[/Komut](command-devenv-exe.md)|IDE'yi başlatır ve belirtilen komutu çalıştırın.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Hata ayıklamanın denetimi altında çalıştırılabilen bir C++ yükler. Bu anahtar Visual Basic veya C# çalıştırılabilirler için kullanılamaz. Daha fazla bilgi için [bkz.](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger)<br /><br /> `devenv /debugexe mysln.exe`|
|[/Diff](diff.md)|İki dosyayı karşılaştırır. Dört parametre alır: *SourceFile*, *TargetFile*, *SourceDisplayName* (isteğe bağlı) ve *TargetDisplayName* (isteğe bağlı).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|Belirtilen çözümü herhangi bir proje yüklemeden açar.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edit](edit-devenv-exe.md)|Bu uygulamanın çalışan bir örneğinde belirtilen dosyaları açar. Çalışan örnekler yoksa, basitleştirilmiş bir pencere düzeni ile yeni bir örnek başlatır.<br /><br /> `devenv /edit File1 File2`|
|[/LCID veya /L](lcid-devenv-exe.md)|IDE için varsayılan dili ayarlar. Belirtilen dil Visual Studio yüklemenize dahil edilmezse, bu ayar yoksayılır.<br /><br /> `devenv /l 1033`|
|[/Günlük](log-devenv-exe.md)|Visual Studio'yu başlatır ve tüm etkinlikleri günlük dosyasına kaydeder.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|Sıçrama ekranını göstermeden IDE'yi açar.<br /><br /> `devenv /nosplash File1 File2`|
|[/Çalıştır veya /R](run-devenv-exe.md)|Belirtilen çözümü derler ve çalıştırır.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|Belirtilen çözümü derler ve çalıştırır, çözüm çalıştırıldığında IDE'yi en aza indirir ve çözüm çalışma tamamlandıktan sonra IDE'yi kapatır.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Visual Studio'yı güvenli modda başlatır. Bu anahtar yalnızca varsayılan ortamı, varsayılan hizmetleri ve üçüncü taraf paketlerinin sevk edilen sürümlerini yükler.<br /><br /> Bu anahtar hiçbir argüman alır.|
|[/UseEnv](useenv-devenv-exe.md)|C++ derlemesi için IDE'nin PATH, INCLUDE, LIBPATH ve LIB ortam değişkenlerini kullanmasına neden olur. Bu anahtar, **C++** iş yüküne sahip Masaüstü geliştirme ile yüklenir. Daha fazla bilgi için, Komut Satırı Yapılar için [Yol ve Çevre Değişkenleri Ayarlama'ya](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds)bakın.|

Aşağıdaki komut satırı anahtarları IDE'yi görüntülemez.

|Komut satırı anahtarı|Açıklama|
| - |-----------------|
|[/?](q-devenv-exe.md)|**Komut İstemi penceresinde**anahtarlar için `devenv` yardım görüntüler.<br /><br /> Bu anahtar hiçbir argüman alır.|
|[/Yapı](build-devenv-exe.md)|Belirtilen çözümü veya projeyi belirtilen çözümün yapılandırmasına göre oluşturur.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|Kaynak dosyaları etkilemeden yapı komutu tarafından oluşturulan tüm dosyaları siler.<br /><br /> `devenv mysln.sln /clean`|
|[/Dağıt](deploy-devenv-exe.md)|Çözümün yapılandırmasına göre, dağıtım için gerekli dosyalarla birlikte çözümü oluşturur.<br /><br /> `devenv mysln.sln /deploy`|
|[/Çıkış](out-devenv-exe.md)|Oluştururken hata almak için bir dosya belirtmenizi sağlar.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Proje](project-devenv-exe.md)|Oluşturma, temizleme veya dağıtma projesi. Bu anahtarı `/Build`yalnızca , , `/Rebuild` `/Clean`, veya `/Deploy` switch'i de sağladıysanız kullanabilirsiniz.<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Oluşturmak veya dağıtmak için proje yapılandırmasını belirtir. Bu anahtarı yalnızca `/Project` anahtarı da sağladıysanız kullanabilirsiniz.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Yeniden Oluşturma](rebuild-devenv-exe.md)|Belirtilen çözümü veya projeyi, belirtilen çözümün yapılandırmasına göre temizler ve oluşturur.<br /><br /> `devenv mysln.sln /rebuild`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Visual Studio varsayılan ayarlarını geri yükler. İsteğe bağlı olarak, ayarları `.vssettings` belirtilen dosyaya sıfırlar.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Yükseltme](upgrade-devenv-exe.md)|Belirtilen çözüm dosyasını ve tüm proje dosyalarını veya belirtilen proje dosyasını bu dosyalar için geçerli Visual Studio biçimlerine yükseltir.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](general-environment-options-dialog-box.md)
- [VSPackage geliştirme için Devenv komut satırı anahtarları](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
