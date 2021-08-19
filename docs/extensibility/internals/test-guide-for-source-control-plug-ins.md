---
title: Kaynak Denetimi Eklentileri için Test Kılavuzu | Microsoft Docs
description: Kaynak denetimi eklentinizi Visual Studio. Bu genel bakış yaygın test alanlarını içerir.
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e91d96c00624b68feb2a6869c1bf3a595036e825
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158651"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Kaynak Denetimi Eklentileri için Test Kılavuzu
Bu bölüm ile kaynak denetimi eklentinizi test etmek için rehberlik [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sağlar. En yaygın test alanlarına kapsamlı bir genel bakış ve sorunlu olabilir daha karmaşık alanlardan bazıları sağlanmıştır. Bu genel bakış, test olaylarının kapsamlı bir listesi değildir.

> [!NOTE]
> En son IDE'ye yapılan bazı hata düzeltmeleri ve geliştirmeler, önceki sürümleri kullanırken daha önce karşılaşılmamış olan mevcut kaynak denetimi eklentileriyle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ilgili sorunları ortaya [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çıkarabiliyor. Önceki sürümünden bu yana eklentide değişiklik yapılmış olsa bile, mevcut kaynak denetimi eklentinizi bu bölümde numaralı alanlar için test etmek kesinlikle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] önerilir.

## <a name="common-preparation"></a>Ortak Hazırlık
 ve hedef [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetimi eklentisi yüklü bir makine gereklidir. Benzer şekilde yapılandırılmış ikinci bir makine, Kaynak Denetiminden Aç testlerinden bazıları için kullanılabilir.

## <a name="definition-of-terms"></a>Koşulların Tanımı
 Bu test kılavuzunun amacı doğrultusunda aşağıdaki terim tanımlarını kullanın:

 İstemci projesi Kaynak denetimi tümleştirmesini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] destekleyen herhangi bir proje türü (örneğin, , veya [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ).

 Web projesi Dört tür Web projesi vardır: Dosya Sistemi, Yerel IIS, Uzak Siteler ve FTP.

- Dosya Sistemi projeleri yerel bir yolda oluşturulur, ancak bir UNC yoluyla dahili olarak erişilen Internet Information Services (IIS) yüklemesini gerektirmez ve istemci projelerine çok benzer şekilde IDE'nin içinden kaynak denetimi altına konulmalıdır.

- Yerel IIS projeleri aynı makinede yüklü iis ile çalışır ve yerel makineyi işaret alan bir URL ile erişilir.

- Uzak Siteler projeleri bir IIS Hizmetleri altında da oluşturulur, ancak IDE'nin içinden değil, IIS sunucu makinesi üzerinde kaynak denetimi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] altına yerleştirilir.

- FTP projelerine uzak bir FTP sunucusu üzerinden erişilir, ancak kaynak denetimi altına yerleştirilemezler.

  Listele Kaynak denetimi altındaki çözüm veya proje için başka bir terim.

  Sürüm Deposu Kaynak Denetimi Eklentisi API'si aracılığıyla erişilen kaynak denetim veritabanı.

## <a name="test-areas-covered-in-this-section"></a>Bu Bölümde Ele Alan Test Alanları

- [Test Alanı 1: Kaynak Denetimine Ekleme/Kaynak Denetiminden Açma](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Durum 1a: Kaynak Denetimine Çözüm Ekleme

  - Durum 1b: Kaynak Denetiminden Çözümü Açma

  - Durum 1c: Kaynak Denetiminden Çözüm Ekleme

- [Test Alanı 2: Kaynak Denetiminden Alma](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Test Alanı 3: Kullanıma Alma/Kullanıma Almayı Geri Alma](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Durum 3: Kullanıma Alma/Kullanıma Almayı Geri Alma

  - Olay 3a: Göz At

  - Olay 3b: Bağlantısı Kesilmiş Ödeme

  - Durum 3c: Sorgu Düzenleme/Sorgu Kaydetme (QEQS)

  - Olay 3d: Sessiz Onay

  - Durum 3e: Kullanıma Almayı Geri Alma

- [Test Alanı 4: İade Etme](../../extensibility/internals/test-area-4-check-in.md)

  - Durum 4a: Değiştirilen öğeler

  - Olay 4b: Dosya ekleme

  - Olay 4c: Proje ekleme

- [Test Alanı 5: Kaynak Denetimini Değiştirme](../../extensibility/internals/test-area-5-change-source-control.md)

  - Durum 5a: Bağlama

  - Olay 5b: Bindirin

  - Durum 5c: Yeniden bindir

- [Test Alanı 6: Sil](../../extensibility/internals/test-area-6-delete.md)

- [Test Alanı 7: Paylaş](../../extensibility/internals/test-area-7-share.md)

- [Test Alanı 8: Eklenti Değiştirme](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Durum 8a: Otomatik Değişiklik

  - Durum 8b: Çözüm Tabanlı Değişiklik

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../../extensibility/source-control-plug-ins.md)
