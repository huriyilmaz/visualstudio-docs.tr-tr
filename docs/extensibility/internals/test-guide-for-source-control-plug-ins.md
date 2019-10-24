---
title: Kaynak denetimi eklentileri için test Kılavuzu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51595708bf30472fd001bde394c7d8c80e39ad45
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722409"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Kaynak Denetimi Eklentileri için Test Kılavuzu
Bu bölüm, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ile kaynak denetimi eklentisini test etmeye yönelik rehberlik sağlar. En yaygın test alanlarının kapsamlı bir genel bakışı ve sorunlu olabilecek daha karmaşık alanlardan bazıları sağlanır. Bu genel bakış, test çalışmalarının ayrıntılı bir listesi olmak üzere tasarlanmamıştır.

> [!NOTE]
> En son [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 'deki bazı hata düzeltmeleri ve geliştirmeleri, daha önce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] önceki sürümleri kullanılırken daha önce karşılaşılmayan mevcut kaynak denetimi eklentileriyle ilgili sorunları ortaya çıkarabilir. Önceki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sürümünde bu yana eklentide hiçbir değişiklik yapılmasa bile, bu bölümde numaralandırılan alanlara mevcut kaynak denetimi eklentisini test etmeniz önemle tavsiye edilir.

## <a name="common-preparation"></a>Ortak hazırlık
 @No__t_0 ve hedef kaynak denetimi eklentisinin yüklü olduğu bir makine gerekir. Benzer şekilde yapılandırılmış ikinci bir makine, kaynak denetimi testlerinde bazı açık bir şekilde kullanılabilir.

## <a name="definition-of-terms"></a>Koşulların tanımı
 Bu test kılavuzunun amacı için aşağıdaki terim tanımlarını kullanın:

 İstemci projesi kaynak denetimi tümleştirmesini destekleyen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bulunan tüm proje türleri (örneğin, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] veya [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).

 Web projesi dört tür Web projesi vardır: dosya sistemi, yerel IIS, uzak siteler ve FTP.

- Dosya sistemi projeleri yerel bir yol üzerinde oluşturulur, ancak bir UNC yolu aracılığıyla dahili olarak erişildiği için Internet Information Services (IIS) yüklenmesini gerektirmez ve kaynak denetimi altına, istemci projeleri gibi IDE içinden yerleştirilebilecek.

- Yerel IIS projeleri, aynı makinede yüklü olan ve yerel makineye işaret eden bir URL ile erişilen IIS ile çalışır.

- Uzak siteler de bir IIS Hizmetleri altında oluşturulur, ancak bunlar IIS sunucu makinesine kaynak denetimi altına yerleştirilir ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 'nin içinden değildir.

- FTP projelerine uzak bir FTP sunucusu üzerinden erişilir, ancak bunlar kaynak denetimi altına yerleştirilemez.

  Kaynak denetimi altındaki çözüm veya proje için başka bir terim listeleme.

  Sürüm, kaynak denetimi eklentisi API 'SI aracılığıyla erişilmekte olan kaynak denetim veritabanını depolar.

## <a name="test-areas-covered-in-this-section"></a>Bu bölümde kapsanan test bölgeleri

- [Test Alanı 1: Kaynak Denetimine Ekleme/Kaynak Denetiminden Açma](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Durum 1a: kaynak denetimine çözüm ekleme

  - Durum 1B: kaynak denetiminden çözüm aç

  - Case 1C: kaynak denetiminden çözüm ekleme

- [Test Alanı 2: Kaynak Denetiminden Alma](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Test Alanı 3: Kullanıma Alma/Kullanıma Almayı Geri Alma](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Durum 3: kullanıma almayı denetleme/geri alma

  - Case 3A: kullanıma alma

  - Durum 3B: bağlantısı kesik teslim alma

  - Durum 3c: sorgu düzenleme/sorgu kaydetme (QEQS)

  - Durum 3B: sessiz kullanıma alma

  - Durum 3e: kullanıma almayı geri alma

- [Test Alanı 4: İade Etme](../../extensibility/internals/test-area-4-check-in.md)

  - Durum 4A: değiştirilen öğeler

  - Durum 4B: dosya ekleme

  - Durum 4c: proje ekleme

- [Test Alanı 5: Kaynak Denetimini Değiştirme](../../extensibility/internals/test-area-5-change-source-control.md)

  - Case 5A: bağlama

  - Case 5B: ciltten çıkar

  - Case 5c: yeniden bağlama

- [Test Alanı 6: Silme](../../extensibility/internals/test-area-6-delete.md)

- [Test Alanı 7: Paylaşma](../../extensibility/internals/test-area-7-share.md)

- [Test Alanı 8: Eklenti Değiştirme](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Case 8A: Otomatik değişiklik

  - Durum 8B: çözüm tabanlı değişiklik

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../../extensibility/source-control-plug-ins.md)
