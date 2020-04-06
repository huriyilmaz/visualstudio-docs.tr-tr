---
title: Hata Ayıklama Bileşenleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03c400fd03c5ee0f2629e9f436b65f53f8f2ac8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739016"
---
# <a name="debugger-components"></a>Hata ayıklama bileşenleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hata ayıklama bir VSPackage olarak uygulanır ve tüm hata ayıklama oturumunu yönetir. Hata ayıklama oturumu aşağıdaki öğeleri içerir:

- **Hata Ayıklama Paketi:** Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayıklama, ne olursa olsun aynı kullanıcı arabirimini sağlar.

- **Oturum hata ayıklama yöneticisi (SDM):** Çeşitli hata ayıklama motorlarının yönetimi için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hata Ayıklama'ya tutarlı bir programlı arabirim sağlar. Tarafından [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]uygulanır.

- **İşlem hata ayıklama yöneticisi (PDM):** Yönetir, tüm çalışan örnekleri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]için, tüm programların bir listesi olabilir veya debugged ediliyor. Tarafından [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]uygulanır.

- **Hata ayıklama motoru (DE):** Bir programın debugged izlenmesinden, SDM ve PDM için çalışan programın durumunu iletişim ve ifade değerlendirici ve sembol sağlayıcı ile bir programın bellek ve değişkenlerin durumunun gerçek zamanlı analizini sağlamak için etkileşim sorumludur. (desteklediği diller [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için) ve kendi çalışma sürelerini desteklemek isteyen üçüncü taraf satıcılar tarafından uygulanır.

- **İfade değerlendirici (EE):** Belirli bir noktada bir program durdurulduğunda kullanıcı tarafından sağlanan değişkenleri ve ifadeleri dinamik olarak değerlendirmek için destek sağlar. (desteklediği diller [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için) ve kendi dillerini desteklemek isteyen üçüncü taraf satıcılar tarafından uygulanır.

- **Sembol sağlayıcı (SP):** Sembol işleyicisi olarak da adlandırılır, anlamlı bilgilerin sağlanabilmesi için (kaynak kodu düzeyinde hata ayıklama ve ifade değerlendirmesi gibi) programın çalışan bir örneğine programın hata ayıklama sembollerini eşler. (Ortak Dil [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Çalışma Zamanı [CLR] sembolleri ve Program DataBase [PDB] sembolü dosya biçimi için) ve hata ayıklama bilgilerini depolamak için kendi özel yöntemi olan üçüncü taraf satıcılar tarafından uygulanır.

  Aşağıdaki diyagram, Visual Studio hata ayıklama bu öğeler arasındaki ilişkiyi gösterir.

  ![Hata Ayıklama Bileşenlerine Genel Bakış](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>Bu bölümde
 [Hata ayıklama paketi](../../extensibility/debugger/debug-package.md) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kabukta çalışan ve tüm UI'yi işleyen hata ayıklama paketini tartışır.

 [İşlem hata ayıklama yöneticisi](../../extensibility/debugger/process-debug-manager.md) Debugged olabilir süreçlerin yöneticisi olan PDM, özellikleri genel bir bakış sağlar.

 [Oturum hata ayıklama yöneticisi](../../extensibility/debugger/session-debug-manager.md) Hata ayıklama oturumunun IDE'ye birleşik bir görünümünü sağlayan SDM'yi tanımlar. SDM DE yönetir.

 [Hata ayıklama motoru](../../extensibility/debugger/debug-engine.md) DE'nin sağladığı hata ayıklama hizmetlerini belgeler.

 [Çalışma modları](../../extensibility/debugger/operational-modes.md) IDE'nin çalışabileceği üç modun genel görünümünü sağlar: tasarım modu, çalışma modu ve kesme modu. Geçiş mekanizmaları da tartışılıyor.

 [İfade değerlendiricisi](../../extensibility/debugger/expression-evaluator.md) EE'nin çalışma zamanındaki amacını açıklar.

 [Sembol sağlayıcı](../../extensibility/debugger/symbol-provider.md) Sembol sağlayıcısının değişkenleri ve ifadeleri nasıl değerlendirdığını uygulama sırasında tartışır.

 [Görselleştirici ve özel görüntüleyici yazın](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Bir tür görselleştirici ve özel görüntüleyici nin ne olduğunu ve ifade değerlendiricinin her ikisini de desteklemede nasıl bir rol oynadığını tartışır.

## <a name="related-sections"></a>İlgili bölümler
 [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimari kavramları açıklar.

 [Hata ayıklama bağlamları](../../extensibility/debugger/debugger-contexts.md) DE'nin kod, belge ve ifade değerlendirme bağlamlarında aynı anda nasıl çalıştığını açıklar. Üç bağlamın her biri için, bununla ilgili konumu, konumu veya değerlendirmeyi açıklar.

 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md) Program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerine bağlantılar içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [başlarken](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
