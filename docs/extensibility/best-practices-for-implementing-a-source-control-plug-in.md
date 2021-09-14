---
title: Kaynak denetimi eklentisi uygulama - en iyi yöntemler
description: Kaynak denetimi eklentisini güvenilir bir şekilde uygulamanıza yardımcı olması için bu teknik ayrıntıları gözden Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8333179533bec73379944cead37e359ecf8ae609
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725324"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Kaynak denetimi eklentisi uygulamaya yönelik en iyi yöntemler
Aşağıdaki teknik ayrıntılar, içinde bir kaynak denetimi eklentisini güvenilir bir şekilde uygulamanıza yardımcı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olabilir.

## <a name="memory-management-issues"></a>Bellek yönetimi sorunları
 Çoğu durumda çağıran olan tümleşik geliştirme ortamı (IDE) bellek serbest bırakarak bellek ayırır. Kaynak denetimi eklentisi, çağıranın ayıracağı arabelleklerde dizeleri ve diğer öğeleri döndürür. Özel durumlar, ortaya çıktıları belirli işlevlerin açıklamalarında not edildi.

## <a name="arrays-of-file-names"></a>Dosya adları dizileri
 Bir dosya dizisi geçir geldiğinde, bitişik bir dosya adı dizisi olarak geçirlanmaz. Dosya adlarının işaretçileri dizisi olarak geçirildi. Örneğin, [SccGet içinde](../extensibility/sccget-function.md)dosya adları parametresi tarafından `lpFileNames` geçirildi, burada `lpFileNames` aslında bir `char **` işaretçisi. `lpFileNames`[0] ad işaretçisi, [1] ise ikinci adın işaretçisi ve `lpFileNames` bu şekilde devam etti.

## <a name="large-model"></a>Büyük model
 Tüm işaretçiler 16 bit işletim sistemlerinde bile 32 bittir.

## <a name="fully-qualified-paths"></a>Tam yollar
 Dosya adları veya dizinler bağımsız değişken olarak belirtildikleri yerde, son backslashes olmadan tam yollar veya UNC yolları olması gerekir. Temel alınan kaynak denetim sisteminin bir gereksinimi ise, bunları göreli yollara çevirmek kaynak denetimi eklentisinin sorumluluğundadır.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Kayıtlı DLL için tam yol belirtme
 IDE artık göreli yollardan (örneğin, *.\NewProvider.dll) URL'leri yüklemez.* DLL'nin tam yolu belirtilmelidir (örneğin, *C:\Providers\NewProvider.dll).* Bu gereksinim, yetkisiz veya kimliğine bürünülen kaynak denetimi URL'lerinin yüklenmesini engelerek IDE'nin güvenliğini güçlendirir.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Kaynak denetimi eklentinizi yüklenirken var olan bir VSSCI eklentisini denetleme
 Kaynak denetimi eklentinizi yüklemeyi plan eden bir kullanıcı zaten bilgisayarda yüklü bir kaynak denetimi eklentisine sahip olabilir. Eklentinin yükleme (kurulum) programı, ilgili kayıt defteri anahtarları için mevcut değerler olup olmadığını belirlemeli. Bu anahtarlar zaten ayarlanmışsa, yükleme programınız kullanıcıdan eklentinizi varsayılan kaynak denetimi eklentisi olarak kaydetmesini ve zaten yüklü olan eklentiyi değiştirmesini istemesi gerekir.

## <a name="error-result-codes-and-reporting"></a>Hata sonuç kodları ve raporlama
 Bir `SCC_OK` kaynak denetim işlevinin dönüş kodu, tüm dosyalar için işlemi başarılı olduğunu gösterir. İşlem başarısız olursa, karşılaşılan son hata kodunun dönmesi beklenir.

 Raporlama kuralı, IDE'de bir hata oluşursa IDE'nin bunu raporlamadan sorumlu olduğu kuralıdır. Kaynak denetim sisteminde bir hata oluşursa, bunu raporlamak kaynak denetim eklentisinin sorumluluğundadır. Örneğin, **Şu anda hiçbir** dosya seçili değil IDE  tarafından raporlansa da Bu dosya zaten kullanıma alınmış durumdayken eklenti tarafından rapor edilir.

## <a name="the-context-structure"></a>Bağlam yapısı
 [SccInitialize](../extensibility/sccinitialize-function.md)çağrısı sırasında çağıran, bir void için ilklanmamış tanıtıcı `ppvContext` olan parametresini iletir. Kaynak denetimi eklentisi bu parametreyi yoksayabilirsiniz veya herhangi bir türden bir yapı ayırarak geçirilen işaretçiye bu yapıya bir işaretçi koyabilirsiniz. IDE bu yapıyı anlamaz, ancak eklentide diğer çağrılara bu yapıya bir işaretçi iletir. Bu, eklentiye, genel değişkenleri kullanmadan işlev çağrılarında kalıcı olan genel durum bilgilerini korumak için kullanabileceği değerli bağlam önbelleği bilgileri sağlar. Eklenti, [SccUninitialize](../extensibility/sccuninitialize-function.md)çağrısında yapıyı serbestleştirmekten sorumludur.

 Eklenti `SCC_CAP_REENTRANT` [SccInitialize](../extensibility/sccinitialize-function.md) içinde biti ayarlarsa (özellikle parametresinde), açık olan tüm projeleri izlemek için birden `lpSccCaps` çok bağlam yapısı kullanılır.

## <a name="bitflags-and-other-command-options"></a>Bit bayrakları ve diğer komut seçenekleri
 [SccGet](../extensibility/sccget-function.md)gibi her komut için IDE, komutun davranışını değiştirecek birçok seçenek belirtebilirsiniz.

 API, parametresi aracılığıyla IDE tarafından belirli seçeneklerin ayarını `fOptions` destekler. Bu seçenekler, [etkilediği komutlarla birlikte belirli komutlar tarafından kullanılan Bit](../extensibility/bitflags-used-by-specific-commands.md) bayrakları altında açıklanmıştır. Genel olarak, bunlar kullanıcıya sorulmayacak seçeneklerdir.

 Çoğu kullanıcı tarafından yapılandırılabilir ayar seçeneği bu şekilde tanımlanmaz çünkü bunlar kaynak denetimi eklentileri arasında büyük ölçüde farklılık gösterir. Bu nedenle önerilen mekanizma bir Gelişmiş **düğmedir.** Örneğin, Al **iletişim** kutusunda IDE yalnızca anlayacaktır bilgileri görüntüler, ancak eklentide bu komut için seçenekler varsa bir Gelişmiş düğmesi de görüntülenir.  Kullanıcı Gelişmiş düğmesine  tıkladığında IDE, kaynak denetimi eklentisini etkinleştiren [SccGetCommandOptions'ı](../extensibility/sccgetcommandoptions-function.md) çağırarak kullanıcıdan bit bayrakları veya tarih/saat gibi bilgileri ister. Eklenti, bu bilgileri komut sırasında geri geçirilen bir yapıda `SccGet` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
- [Kaynak denetimi eklentisi oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md)
