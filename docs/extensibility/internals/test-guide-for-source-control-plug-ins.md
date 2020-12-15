---
title: Kaynak denetimi eklentileri için test Kılavuzu | Microsoft Docs
description: Visual Studio ile kaynak denetimi eklentisini test etme hakkında bilgi edinin. Bu genel bakışta ortak test bölgeleri bulunur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a288beb618b0b539f53270928366349f47aee9e9
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487731"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Kaynak Denetimi Eklentileri için Test Kılavuzu
Bu bölüm, kaynak denetimi eklentisini ile test etmek için rehberlik sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . En yaygın test alanlarının kapsamlı bir genel bakışı ve sorunlu olabilecek daha karmaşık alanlardan bazıları sağlanır. Bu genel bakış, test çalışmalarının ayrıntılı bir listesi olmak üzere tasarlanmamıştır.

> [!NOTE]
> En son IDE için bazı hata düzeltmeleri ve geliştirmeleri, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] önceki sürümleri kullanılırken daha önce karşılaşılan mevcut kaynak denetimi eklentileriyle ilgili sorunları ortaya çıkarabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Önceki sürümünden bu yana eklentide hiçbir değişiklik yapılmasa bile, bu bölümde numaralandırılan alanlara mevcut kaynak denetimi eklentisini test etmeniz önemle tavsiye edilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="common-preparation"></a>Ortak hazırlık
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Ve hedef kaynak denetimi eklentisinin yüklü olduğu bir makine gerekir. Benzer şekilde yapılandırılmış ikinci bir makine, kaynak denetimi testlerinde bazı açık bir şekilde kullanılabilir.

## <a name="definition-of-terms"></a>Koşulların tanımı
 Bu test kılavuzunun amacı için aşağıdaki terim tanımlarını kullanın:

 İstemci projesi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetimi tümleştirmesini destekler (örneğin,, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] veya [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ).

 Web projesi dört tür Web projesi vardır: dosya sistemi, yerel IIS, uzak siteler ve FTP.

- Dosya sistemi projeleri yerel bir yol üzerinde oluşturulur, ancak bir UNC yolu aracılığıyla dahili olarak erişildiği için Internet Information Services (IIS) yüklenmesini gerektirmez ve kaynak denetimi altına, istemci projeleri gibi IDE içinden yerleştirilebilecek.

- Yerel IIS projeleri, aynı makinede yüklü olan ve yerel makineye işaret eden bir URL ile erişilen IIS ile çalışır.

- Uzak siteler de bir IIS Hizmetleri altında oluşturulur, ancak bunlar, IDE 'nin içinden değil, IIS sunucu makinesine kaynak denetimi altına yerleştirilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

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

- [Test Alanı 6: Sil](../../extensibility/internals/test-area-6-delete.md)

- [Test Alanı 7: Paylaş](../../extensibility/internals/test-area-7-share.md)

- [Test Alanı 8: Eklenti Değiştirme](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Case 8A: Otomatik değişiklik

  - Durum 8B: çözüm tabanlı değişiklik

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../../extensibility/source-control-plug-ins.md)
