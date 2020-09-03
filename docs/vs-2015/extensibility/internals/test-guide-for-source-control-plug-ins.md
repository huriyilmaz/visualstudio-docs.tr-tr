---
title: Kaynak denetimi eklentileri için test Kılavuzu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6790e61eddc81045bb168028ee7aeef7a0492e3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825742"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Kaynak Denetimi Eklentileri için Test Kılavuzu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu bölüm, kaynak denetimi eklentisini ile test etmek için rehberlik sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . En yaygın test alanlarının kapsamlı bir genel bakışı ve sorunlu olabilecek daha karmaşık alanlardan bazıları sağlanır. Bu genel bakış, test çalışmalarının ayrıntılı bir listesi olmak üzere tasarlanmamıştır.  
  
> [!NOTE]
> En son IDE için bazı hata düzeltmeleri ve geliştirmeleri, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] önceki sürümleri kullanılırken daha önce karşılaşılan mevcut kaynak denetimi eklentileriyle ilgili sorunları ortaya çıkarabilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Önceki sürümünden bu yana eklentide hiçbir değişiklik yapılmasa bile, bu bölümde numaralandırılan alanlara mevcut kaynak denetimi eklentisini test etmeniz önemle tavsiye edilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="common-preparation"></a>Ortak hazırlık  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Ve hedef kaynak denetimi eklentisinin yüklü olduğu bir makine gerekir. Benzer şekilde yapılandırılmış ikinci bir makine, kaynak denetimi testlerinde bazı açık bir şekilde kullanılabilir.  
  
## <a name="definition-of-terms"></a>Koşulların tanımı  
 Bu test kılavuzunun amacı için aşağıdaki terim tanımlarını kullanın:  
  
 İstemci projesi  
 Kaynak denetimi tümleştirmesini destekleyen ' de bulunan herhangi bir proje türü [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (örneğin, [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , [!INCLUDE[csprcs](../../includes/csprcs-md.md)] veya [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] ).  
  
 Web projesi  
 Dört tür Web projesi vardır: dosya sistemi, yerel IIS, uzak siteler ve FTP.  
  
- Dosya sistemi projeleri yerel bir yol üzerinde oluşturulur, ancak bir UNC yolu aracılığıyla dahili olarak erişildiği için Internet Information Services (IIS) yüklenmesini gerektirmez ve kaynak denetimi altına, istemci projeleri gibi IDE içinden yerleştirilebilecek.  
  
- Yerel IIS projeleri, aynı makinede yüklü olan ve yerel makineye işaret eden bir URL ile erişilen IIS ile çalışır.  
  
- Uzak siteler de bir IIS Hizmetleri altında oluşturulur, ancak bunlar, IDE 'nin içinden değil, IIS sunucu makinesine kaynak denetimi altına yerleştirilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- FTP projelerine uzak bir FTP sunucusu üzerinden erişilir, ancak bunlar kaynak denetimi altına yerleştirilemez.  
  
  Sayıyor  
  Kaynak denetimi altındaki çözüm veya proje için başka bir terim.  
  
  Sürüm deposu  
  Kaynak denetimi eklentisi API 'SI üzerinden erişilmekte olan kaynak denetim veritabanı.  
  
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

## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentileri](../../extensibility/source-control-plug-ins.md)
