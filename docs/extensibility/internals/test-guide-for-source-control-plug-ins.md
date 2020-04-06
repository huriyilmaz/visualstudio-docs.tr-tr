---
title: Kaynak Kontrol Eklentileri Için Test Rehberi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: e6b3f8e76e977472a3459697a650b32dae657c22
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704384"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Kaynak Denetimi Eklentileri için Test Kılavuzu
Bu bölümde, kaynak denetim eklentinizi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. En yaygın test alanlarının yanı sıra sorunlu olabilecek daha karmaşık alanlardan bazılarına kapsamlı bir genel bakış sağlanır. Bu genel bakış, test çalışmalarının kapsamlı bir listesi değildir.

> [!NOTE]
> Bazı hata düzeltmeleri ve en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] son IDE'deki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]iyileştirmeler, önceki sürümlerini kullanırken daha önce karşılaşılan mevcut kaynak denetimi eklentileriyle ilgili sorunları ortaya çıkarabilir. Bir önceki sürümünden bu yana eklentide herhangi bir değişiklik yapılmamış olsa bile, bu bölümde numaralandırılmış alanlar için mevcut kaynak kontrol [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]eklentinizi test etmeniz önerilir.

## <a name="common-preparation"></a>Ortak Hazırlık
 Bir makine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve hedef kaynak kontrol eklentisi yüklü, gereklidir. Benzer şekilde yapılandırılan ikinci bir makine, Kaynak Denetimi testlerinden Açık'ın bazıları için kullanılabilir.

## <a name="definition-of-terms"></a>Şartların Tanımı
 Bu test kılavuzunun amacı için aşağıdaki terim tanımlarını kullanın:

 İstemci projesi Kaynak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] denetim tümleştirmesini destekleyen [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]herhangi [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]bir [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]proje türü (örneğin, , , veya ).

 Web projesi Dört tür Web projesi vardır: Dosya Sistemi, Yerel IIS, Uzak Siteler ve FTP.

- Dosya Sistemi projeleri yerel bir yolda oluşturulur, ancak internet bilgi hizmetlerinin (IIS) unc yolu üzerinden dahili olarak erişildiğinden ve istemci projeleri gibi IDE içinden kaynak denetimi altına yerleştirilebildikleri için yüklenmesini gerektirmezler.

- Yerel IIS projeleri, aynı makineye yüklenen ve yerel makineyi gösteren bir URL ile erişilen IIS ile çalışır.

- Uzak Siteler projeleri de bir IIS Hizmetleri altında oluşturulur, ancak IIS sunucu makinesinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetimi altına alınır, IDE içinden değil.

- FTP projelerine uzak bir FTP sunucusu ndan erişilir, ancak kaynak denetimi altına alınamaz.

  Listment Kaynak denetimi altında çözüm veya proje için başka bir terim.

  Sürüm Deposu Kaynak Denetimi Eklentisi API'si aracılığıyla erişilen kaynak denetim veritabanı.

## <a name="test-areas-covered-in-this-section"></a>Bu Bölümde Kapsanan Test Alanları

- [Test Alanı 1: Kaynak Denetimine Ekle/Aç](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Örnek 1a: Kaynak Denetimine Çözüm Ekle

  - Örnek 1b: Kaynak Kontrolünden Açık Çözüm

  - Büyük/Küçük Harf 1c: Kaynak Denetiminden Çözüm Ekle

- [Test Alanı 2: Kaynak Denetiminden Alma](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Test Alanı 3: Check Out/Geri Ödeme](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Örnek 3: Check Out/Geri Ödeme

  - Örnek 3a: Kullanıma Son

  - Örnek 3b: Bağlantısızlar Ödeme

  - Büyük/Küçük Harf 3c: Sorgu Lat/Sorgu Kaydet (QEQS)

  - Örnek 3d: Sessiz Ödeme

  - Örnek 3e: Ödemeyi Geri Le

- [Test Alanı 4: İade Etme](../../extensibility/internals/test-area-4-check-in.md)

  - Örnek 4a: Değiştirilmiş öğeler

  - Örnek 4b: Dosya ekleme

  - Örnek 4c: Proje ekleme

- [Test Alanı 5: Kaynak Denetimini Değiştirme](../../extensibility/internals/test-area-5-change-source-control.md)

  - Örnek 5a: Bağlama

  - Örnek 5b: Unbind

  - Örnek 5c: Rebind

- [Test Alanı 6: Silme](../../extensibility/internals/test-area-6-delete.md)

- [Test Alanı 7: Paylaşma](../../extensibility/internals/test-area-7-share.md)

- [Test Alanı 8: Eklenti Değiştirme](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Büyük/Küçük Harf 8a: Otomatik Değişim

  - Örnek 8b: Çözüm tabanlı değişim

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../../extensibility/source-control-plug-ins.md)
