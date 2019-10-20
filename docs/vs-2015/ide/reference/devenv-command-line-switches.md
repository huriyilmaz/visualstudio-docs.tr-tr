---
title: Devenv komut satırı anahtarları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- builds [Team System], command-line
- applications [Visual Studio], executing
- compiling source code, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
- environment, Devenv commands
- compilers, Devenv commands
- switches
- Devenv, syntax and list of switches
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b8b0683024e2881f76bb6c54d9420d351fced08a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668724"
---
# <a name="devenv-command-line-switches"></a>Devenv Komut Satırı Anahtarları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Devenv, tümleşik geliştirme ortamı (IDE) için çeşitli seçenekler ayarlamanıza ve ayrıca, komut satırından proje oluşturma, hata ayıklama ve dağıtma işlemlerini yapmanızı sağlar. IDE 'yi bir komut dosyası veya. bat dosyasından çalıştırmak için, örneğin gecelik bir derleme betiği veya IDE 'yi belirli bir yapılandırmada başlatmak için bu anahtarları kullanın.

> [!NOTE]
> Derleme ile ilgili görevler için artık devenv yerine MSBuild kullanmanız önerilir. Daha fazla bilgi için bkz. [komut satırı başvurusu](../../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> [/Setup (devenv. exe)](../../ide/reference/setup-devenv-exe.md) ve [/ınstallvstempsyonlar (devenv. exe)](../../ide/reference/installvstemplates-devenv-exe.md) anahtarlarını kullanabilmeniz için devenv 'ı yönetici olarak çalıştırmalısınız.

## <a name="devenv-switch-syntax"></a>Devenv Switch sözdizimi
 Varsayılan olarak, devenv komutları anahtarları devenv.com yardımcı programına geçirir.

 Devenv.com yardımcı programı, `stdout` ve `stderr` gibi standart sistem akışları aracılığıyla çıktının teslimini sağlar ve örneğin bir. txt dosyasına çıktı yakaladığında uygun g/ç yeniden yönlendirmeyi belirler. @No__t_0 yerine başlayan komutlar aynı anahtarları kullanabilir, ancak devenv.com yardımcı programını atlayarak devenv. exe programına gönderilir.

 @No__t_0 anahtarlarının sözdizimi kuralları diğer DOS komut satırı yardımcı programlarına benzer. Aşağıdaki sözdizimi kuralları tüm `devenv` anahtarlar ve bunların bağımsız değişkenleri için geçerlidir:

- Komutlar `devenv` başlar.

- Anahtarlar büyük/küçük harfe duyarlı değildir.

- Bir çözüm veya proje belirtirken, ilk bağımsız değişken dosya yolu da dahil olmak üzere çözüm dosyasının veya proje dosyasının adıdır.

- İlk bağımsız değişken bir çözüm veya proje olmayan bir dosya ise, bu dosya, IDE 'nin yeni bir örneğinde uygun düzenleyicide açılır.

- Bir çözüm dosyası adı yerine bir proje dosya adı sağlarsanız, bir `devenv` komutu aynı ada sahip bir çözüm dosyası için proje dosyasının ana klasörünü arar. Örneğin, komut `devenv /build myproject1.vbproj` "myproject1. sln" adlı bir çözüm dosyası için üst klasörde arama yapılır.

    > [!NOTE]
    > Bu projeye başvuran bir ve yalnızca bir çözüm dosyası, üst klasöründe bulunmalıdır. Üst klasörde bu projeye başvuruda bulunan çözüm dosyası yoksa veya üst klasör ona başvuran iki veya daha fazla çözüm dosyası içeriyorsa, bu proje için adlandırılmış geçici bir çözüm dosyası oluşturulur ve buna başvurur.

- Dosya yolları ve dosya adları boşluk içeriyorsa, bunları çift tırnak işareti ("") içine almalısınız. Örneğin, "c:\Proje a \\".

- Aynı satırdaki anahtarlar ve bağımsız değişkenler arasına bir boşluk karakteri ekleyin. Örneğin, **devenv/log output. txt** komutu IDE 'yi açar ve bu oturuma yönelik tüm günlük bilgilerini çıktı. txt dosyasına çıkarır.

- @No__t_0 komutlarında kalıp eşleme söz dizimini kullanamazsınız.

## <a name="devenv-switches"></a>Devenv anahtarları
 IDE 'yi göstermek ve açıklanan görevi gerçekleştirmek için aşağıdaki komut satırı anahtarlarını kullanın.

|Komut satırı anahtarı|Açıklama|
|-------------------------|-----------------|
|[/Command (devenv. exe)](../../ide/reference/command-devenv-exe.md)|IDE 'yi başlatır ve belirtilen komutu yürütür.|
|[/DebugExe (devenv. exe)](../../ide/reference/debugexe-devenv-exe.md)|Hata ayıklayıcının denetimi altına bir [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] çalıştırılabilir dosyası yükler. Bu anahtar, [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../includes/csprcs-md.md)] yürütülebilir dosyaları için kullanılamaz. Daha fazla bilgi için bkz. [hata ayıklayıcıda otomatik olarak bir işlem başlatma](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|
|[/LCID (devenv. exe)](../../ide/reference/lcid-devenv-exe.md) veya `/l`|IDE için varsayılan dili ayarlar. Visual Studio yüklemenizde belirtilen dil yoksa, bu ayar yok sayılır.|
|[/Log (devenv. exe)](../../ide/reference/log-devenv-exe.md)|@No__t_0 başlatır ve tüm etkinlikleri günlük dosyasına kaydeder.|
|[/Run (devenv. exe)](../../ide/reference/run-devenv-exe.md) veya `/r`|Belirtilen çözümü derler ve çalıştırır.|
|[/Runexit (devenv. exe)](../../ide/reference/runexit-devenv-exe.md)|Belirtilen çözümü derler ve çalıştırır, çözüm çalıştırıldığında IDE 'yi en aza indirir ve çözümün çalışmasını tamamladıktan sonra IDE 'yi kapatır.|
|[/UseEnv (devenv. exe)](../../ide/reference/useenv-devenv-exe.md)|IDE 'nin, **Seçenekler** Iletişim kutusundaki **Projeler** seçeneklerinin VC + + dizinleri bölümünde belirtilen ayarlar yerıne [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] derleme için yol, ekleme ve LIB ortam değişkenlerini kullanmasına neden olur. Daha fazla bilgi için bkz [. komut satırı derlemeleri Için yolu ve ortam değişkenlerini ayarlama](https://msdn.microsoft.com/library/99389528-deb5-43b9-b99a-03c8773ebaf4)|
|[/Edit (devenv. exe)](../../ide/reference/edit-devenv-exe.md)|Belirtilen dosyaları bu uygulamanın çalışan bir örneğinde açar. Çalışan örnek yoksa, Basitleştirilmiş pencere düzenine sahip yeni bir örnek başlatır.|
|[/Resetaddın (devenv. exe)](../../ide/reference/resetaddin-devenv-exe.md)|Belirtilen eklentiyi yüklemeden Visual Studio IDE 'nin bir örneğini başlatır.|
|[/SafeMode (devenv. exe)](../../ide/reference/safemode-devenv-exe.md)|Güvenli modda [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] başlatır ve yalnızca varsayılan ortam ve hizmetleri ve üçüncü taraf paketlerin sevk edilen sürümlerini yükler.|
|[/ResetSkipPkgs (devenv. exe)](../../ide/reference/resetskippkgs-devenv-exe.md)|VSPackages 'e, bu sorunu karşıya yüklemeyi önlemek isteyen kullanıcılar tarafından VSPackages 'a eklenmiş olan tüm Skipyükleme etiketlerini temizler.|
|[/Setup (devenv. exe)](../../ide/reference/setup-devenv-exe.md)|Visual Studio 'Yu, mevcut tüm VSPackages 'tan menüleri, araç çubuklarını ve komut gruplarını açıklayan kaynak meta verileri birleştirmeye zorlar.|

 Açıklanan görevi gerçekleştirmek için aşağıdaki komut satırı anahtarlarını kullanın. Bu komut satırı anahtarları IDE 'yi görüntülemez.

|Komut satırı anahtarı|Açıklama|
|-------------------------|-----------------|
|[/? (devenv. exe)](../../ide/reference/q-devenv-exe.md)|**Komut istemi penceresinde**devenv anahtarlarına yönelik yardım görüntüler.<br /><br /> **Devenv/?**|
|[/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)|Belirtilen çözümü veya projeyi belirtilen çözümün yapılandırmasına göre oluşturur.<br /><br /> **Devenv myproj. csproj/Build**|
|[/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md)|Kaynak dosyalarını etkilemeden derleme komutu tarafından oluşturulan tüm dosyaları siler.<br /><br /> **Devenv myproj. csproj/Clean**|
|[/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md)|Çözümü, çözüm yapılandırmasına göre, dağıtım için gerekli dosyalarla birlikte oluşturur.<br /><br /> **Devenv myproj. csproj/Deploy**|
|[/Diff](../../ide/reference/diff.md)|İki dosyayı karşılaştırır.  Dört parametre alır: SourceFile, TargetFile, SourceDisplayName (isteğe bağlı), TargetDisplayName (isteğe bağlı).|
|[/Installvstempsyonlar (devenv. exe)](../../ide/reference/installvstemplates-devenv-exe.md)|*@No__t_1VisualStudioInstallDir >* \Common7\IDE\ProjectTemplates veya *\<VisualStudioInstallDir >* \Common7\IDE\ItemTemplates ' de bulunan proje veya öğe şablonlarını kaydettirir, böylece **Yeni proje** ve **Yeni öğe Ekle** iletişim kutuları.<br /><br /> **Devenv/ınstallvstempsyonlar**|
|[/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)|Oluştururken hata alacak bir dosya belirtmenizi sağlar.<br /><br /> **Devenv myproj. csproj/Build/Out log. txt**|
|[/Project (devenv. exe)](../../ide/reference/project-devenv-exe.md)|Derlenecek, temizleyen veya dağıtılacak proje. Bu anahtarı yalnızca/Build,/Rebuild,/Clean veya/Deploy anahtarını de sağladıysanız kullanabilirsiniz.|
|[/ProjectConfig (devenv. exe)](../../ide/reference/projectconfig-devenv-exe.md)|Derlemek veya dağıtmak için proje yapılandırmasını belirtir. Bu anahtarı yalnızca,/Project anahtarını da sağladıysanız kullanabilirsiniz.|
|[/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)|Belirtilen çözümü veya projeyi temizler ve belirtilen çözümün yapılandırmasına göre oluşturur.|
|[/ResetSettings (devenv. exe)](../../ide/reference/resetsettings-devenv-exe.md)|Visual Studio varsayılan ayarlarını geri yükler. İsteğe bağlı olarak ayarları belirtilen. vssettings dosyasına sıfırlar.|
|[/Updateconfiguration (devenv. exe)](../../ide/reference/updateconfiguration-devenv-exe.md)|Sistemdeki [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] paketlerini birleştirmek ve tüm değişiklikler için MEF önbelleğini denetlemek [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bildirir.|
|[/Upgrade (devenv. exe)](../../ide/reference/upgrade-devenv-exe.md)|Belirtilen çözüm dosyasını ve tüm proje dosyalarını veya belirtilen proje dosyasını, bu dosyalar için geçerli [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] biçimlerine yükseltir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
