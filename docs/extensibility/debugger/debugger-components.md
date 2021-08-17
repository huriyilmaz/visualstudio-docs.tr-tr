---
title: Hata Ayıklayıcı Bileşenleri | Microsoft Docs
description: VSPackage olarak uygulanan Visual Studio hata ayıklayıcısı tarafından yönetilen bir hata ayıklama oturumunun öğelerini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: d4e2eb0e0b702bfa97485bd943da7b9dcc59c328
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073376"
---
# <a name="debugger-components"></a>Hata ayıklayıcısı bileşenleri
Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayıklayıcısı VSPackage olarak uygulanır ve hata ayıklama oturumunun tamamını yönetir. Hata ayıklama oturumu aşağıdaki öğelerden oluşur:

- **Pakette Hata Ayıklama:** Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayıklayıcı, hangi hata ayıklandı olursa olsun aynı kullanıcı arabirimini sağlar.

- **Oturum hata ayıklama yöneticisi (SDM):** Çeşitli hata ayıklama altyapılarının yönetimi için Hata Ayıklayıcı'ya tutarlı bir program [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arabirimi sağlar. Tarafından [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uygulanır.

- **İşlem hata ayıklama yöneticisi (PDM):** tüm çalışan örnekleri için, hata ayıklandı veya hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayıklandı olan tüm programların listesini yönetir. Tarafından [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uygulanır.

- **Hata ayıklama altyapısı (DE):** Hata ayıklaması yapılan bir programı izlemek, çalışan programın durumunu SDM ve PDM'ye ile iletişim kurmak ve bir programın belleğinin ve değişkenlerinin durumunun gerçek zamanlı analizini sağlamak için ifade değerlendiricisi ve sembol sağlayıcısıyla etkileşim kurmakla sorumludur. Kendi çalışma zamanlarını desteklemek isteyen (desteklediği diller için) ve üçüncü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] taraf satıcılar tarafından uygulanır.

- **İfade değerlendirici (EE):** Bir program belirli bir noktada durdurulmuş olduğunda kullanıcı tarafından sağlanan değişkenleri ve ifadeleri dinamik olarak değerlendirme desteği sağlar. Kendi dillerini desteklemek isteyen (desteklediği diller için) ve üçüncü taraf [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] satıcılar tarafından uygulanır.

- **Sembol sağlayıcısı (SP):** Sembol işleyicisi olarak da adlandırılan bu program, hata ayıklama sembollerini programın çalışan bir örneğine eşler; böylece anlamlı bilgiler sağlanmalıdır (kaynak kodu düzeyinde hata ayıklama ve ifade değerlendirmesi gibi). Bu, (Ortak Dil Çalışma Zamanı [CLR] sembolleri ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Program DataBase [PDB] sembol dosyası biçimi için) ve hata ayıklama bilgilerini depolamak için kendi özel yöntemine sahip üçüncü taraf satıcılar tarafından uygulanır.

  Aşağıdaki diyagramda, hata ayıklayıcının bu öğeleri arasındaki Visual Studio gösterir.

  ![Hata Ayıklama Bileşenlerine Genel Bakış](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>Bu bölümde
 [Pakette hata ayıklama](../../extensibility/debugger/debug-package.md) Kabukta çalışan ve tüm kullanıcı arabirimini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ele alan hata ayıklama paketini ele almaktadır.

 [İşlem hata ayıklama yöneticisi](../../extensibility/debugger/process-debug-manager.md) Hata ayıklaması yapılan işlemlerin yöneticisi olan PDM'nin özelliklerine genel bir bakış sağlar.

 [Oturum hata ayıklama yöneticisi](../../extensibility/debugger/session-debug-manager.md) IDE'de hata ayıklama oturumunun birleşik bir görünümünü sağlayan SDM'i tanımlar. SDM, DE'i yönetir.

 [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md) DE'nin sağladığı hata ayıklama hizmetlerini belgeler.

 [İşletimsel modlar](../../extensibility/debugger/operational-modes.md) IDE'nin çalışabiliyor olduğu üç moda genel bakış sağlar: tasarım modu, çalıştırma modu ve kesme modu. Geçiş mekanizmaları da ele alınmıştır.

 [İfade değerlendirici](../../extensibility/debugger/expression-evaluator.md) Çalışma zamanında EE açıklar.

 [Sembol sağlayıcısı](../../extensibility/debugger/symbol-provider.md) Sembol sağlayıcısının uygulamada değişkenleri ve ifadeleri nasıl değerlendirip değerlendirip değerlendirmeyi ele almaktadır.

 [Tür görselleştiricisi ve özel görüntüleyici](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Bir tür görselleştiricinin ve özel görüntüleyicinin ne olduğunu ve ifade değerlendiricinin her ikisini desteklemede oynadığı rolü tartışmaktadır.

## <a name="related-sections"></a>İlgili bölümler
 [Hata ayıklayıcısı kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimari kavramlarını açıklar.

 [Hata ayıklayıcısı bağlamları](../../extensibility/debugger/debugger-contexts.md) DE'nin kod, belge ve ifade değerlendirme bağlamları içinde aynı anda nasıl çalış olduğunu açıklar. Üç bağlamın her biri için ilgili konum, konum veya değerlendirmeyi açıklar.

 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md) Program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerinin bağlantılarını içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanmaya başlama](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
