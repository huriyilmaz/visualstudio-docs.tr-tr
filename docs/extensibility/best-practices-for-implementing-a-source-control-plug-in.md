---
title: Kaynak Kontrol Eklentisi Uygulamak İçin En İyi Uygulamalar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68491f22d63ae3ebb664b7c22188a661dccbf39a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740045"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Kaynak kontrol eklentisi uygulamak için en iyi uygulamalar
Aşağıdaki teknik ayrıntılar, bir kaynak denetim eklentisini güvenilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]bir şekilde uygulamanıza yardımcı olabilir.

## <a name="memory-management-issues"></a>Bellek yönetimi sorunları
 Çoğu durumda, arayan olan tümleşik geliştirme ortamı (IDE), belleği salgılar ve ayırır. Kaynak denetimi eklentisi, arayanın tahsis ettiği arabellekteki dizeleri ve diğer öğeleri döndürür. Özel durumlar, oluştukları belirli işlevlerin açıklamalarında belirtilir.

## <a name="arrays-of-file-names"></a>Dosya adlarının dizileri
 Bir dizi dosya geçirildiğinde, dosya adlarının bitişik bir dizi olarak geçirilir. Dosya adlarına işaretçiler dizisi olarak geçirilir. Örneğin, [SccGet'da,](../extensibility/sccget-function.md)dosya adları `lpFileNames` parametre tarafından geçirilir ve aslında `lpFileNames` `char **`bir . `lpFileNames`[0] ilk ada işaretçi, `lpFileNames`[1] ikinci adı işaretçi, ve benzeri.

## <a name="large-model"></a>Büyük model
 Tüm işaretçiler, 16 bit işletim sistemlerinde bile 32 bittir.

## <a name="fully-qualified-paths"></a>Tam nitelikli yollar
 Dosya adlarının veya dizinlerinin bağımsız değişken olarak belirtildiği durumlarda, bunlar bitiş eğik çizgileri olmadan tam nitelikli yollar veya UNC yolları olmalıdır. Temel kaynak denetim sisteminin bir gereksinimi yse, bunları göreli yollara çevirmek kaynak denetim eklentisinin sorumluluğundadır.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Kayıtlı DLL için tam nitelikli bir yol belirtin
 IDE artık göreli yollardan DL'ler yüklemez (örneğin, *.\NewProvider.dll).* DLL'nin tam bir yolu belirtilmelidir (örneğin, *C:\Providers\NewProvider.dll).* Bu gereksinim, yetkisiz veya taklit edilen kaynak denetimi DL'lerinin yüklenmesini engelleyerek IDE'nin güvenliğini güçlendirir.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Kaynak kontrol eklentinizi yüklerken varolan bir VSSCI eklentisi olup yok
 Kaynak denetimi eklentinizi yüklemeyi planlayan bir kullanıcının bilgisayarında zaten varolan bir kaynak denetim eklentisi yüklü olabilir. Oluşturduğunuz eklenti için yükleme (kurulum) programı, ilgili kayıt defteri anahtarları için varolan değerlerin olup olmadığını belirlemelidir. Bu anahtarlar zaten ayarlanmışsa, yükleme programınız kullanıcıdan eklentinizi varsayılan kaynak denetimi eklentisi olarak kaydedip kaydetmemenizi ve zaten yüklü olanın değiştirip değiştirmediğini sormalıdır.

## <a name="error-result-codes-and-reporting"></a>Hata sonuç kodları ve raporlama
 Kaynak `SCC_OK` denetim işlevinin iade kodu, işlemin tüm dosyalar için başarılı olduğunu gösterir. İşlem başarısız olursa, karşılaşılan son hata kodunu döndürmesi beklenir.

 Raporlama kuralı, IDE'de bir hata oluşursa, bunu bildirmekten IDE'nin sorumlu olduğudur. Kaynak denetim sisteminde bir hata oluşursa, kaynak denetim eklentisi bunu bildirmekten sorumludur. Örneğin, **şu anda seçili hiçbir dosya** IDE tarafından bildirilir, **ancak bu dosya zaten kullanıma alınmış** durumda, eklenti tarafından bildirilir.

## <a name="the-context-structure"></a>Bağlam yapısı
 [SccInitialize'a](../extensibility/sccinitialize-function.md)yapılan arama sırasında, `ppvContext` arayan parametreyi geçer, bu da bir boşluğa başlamayan bir tutamaçtır. Kaynak denetimi eklentisi bu parametreyi yoksayabilir veya herhangi bir yapıyı ayırıp geçen işaretçiye işaretçi koyabilir. IDE bu yapıyı anlamaz, ancak eklentideki diğer tüm çağrılara bu yapıya işaretçi geçirir. Bu, eklentiye, genel değişkenleri kullanmadan işlev çağrıları arasında devam eden genel durum bilgilerini korumak için kullanabileceği değerli bağlam önbelleği bilgileri sağlar. Eklenti, [SccUninitialize'a](../extensibility/sccuninitialize-function.md)yapılan bir çağrıda yapının serbest leştirilmesinden sorumludur.

 Eklenti `SCC_CAP_REENTRANT` [SccInitialize'daki](../extensibility/sccinitialize-function.md) biti ayarlarsa (özellikle `lpSccCaps` parametrede), açık olan tüm projeleri izlemek için birden çok bağlam yapısı kullanılır.

## <a name="bitflags-and-other-command-options"></a>Bit bayrakları ve diğer komut seçenekleri
 [SccGet](../extensibility/sccget-function.md)gibi her komut için IDE, komutun davranışını değiştiren birçok seçenek belirtebilir.

 `fOptions` API, parametre aracılığıyla Belirli seçeneklerin IDE tarafından ayarını destekler. Bu seçenekler, [belirli komutlar tarafından kullanılan Bit bayrakları](../extensibility/bitflags-used-by-specific-commands.md) ile etkiledikleri komutlarla açıklanır. Genel olarak, bunlar kullanıcıdan istenmeyeceği seçeneklerdir.

 Kaynak denetimi eklentileri arasında büyük farklılıklar gösterdiğinden, çoğu kullanıcı tarafından yapılandırılabilen ayar seçenekleri bu şekilde tanımlanmaz. Bu nedenle, önerilen mekanizma **Gelişmiş** bir düğmedir. Örneğin, **Al** iletişim kutusunda, IDE yalnızca anladığı bilgileri görüntüler, ancak eklentide bu komut için seçenekler varsa **Gelişmiş** düğmesi de görüntülenir. Kullanıcı **Gelişmiş** düğmesini tıklattığında, Kaynak denetimi eklentisini etkinleştirmek için [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) çağırır ve kullanıcıdan bit bayrakları veya tarih/saat gibi bilgi ister. Eklenti, bu bilgileri komut sırasında geri geçirilen bir `SccGet` yapıda döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentileri](../extensibility/source-control-plug-ins.md)
- [Kaynak kontrol eklentisi oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md)
