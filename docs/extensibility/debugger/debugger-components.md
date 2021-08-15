---
title: Hata ayıklayıcı bileşenleri | Microsoft Docs
description: Visual Studio hata ayıklayıcı tarafından yönetilen ve vspackage olarak uygulanan bir hata ayıklama oturumu oluşturan öğeler hakkında bilgi edinin.
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
ms.openlocfilehash: d2ebe084538388174d1c205ab101ade465c694f955c3f481598edb0b1da60827
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121324151"
---
# <a name="debugger-components"></a>Hata ayıklayıcı bileşenleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Hata ayıklayıcı bir VSPackage olarak uygulanır ve hata ayıklama oturumunun tamamını yönetir. Hata ayıklama oturumu aşağıdaki öğeleri içerir:

- **Hata ayıklama paketi:** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hata ayıklayıcı, hata ayıklamanın ne olduğuna bakılmaksızın aynı kullanıcı arabirimini sağlar.

- **Oturum hata ayıklama Yöneticisi (SDM):** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Çeşitli hata ayıklama altyapısının yönetimi için hata ayıklayıcıya tutarlı bir programlama arabirimi sağlar. Tarafından uygulanır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **İşlem hata ayıklama Yöneticisi (PDM):** Tüm çalışan örnekleri için, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklanan veya hataları ayıklanabilecek tüm programların bir listesini yönetir. Tarafından uygulanır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **Hata ayıklama altyapısı (de):** Hata ayıklamakta olan bir programın izlenmesini, çalışan programın durumunu SDM ve PDM ile iletişimi ve bir programın bellek ve değişkenlerinin durumunun gerçek zamanlı analizini sağlamak için ifade değerlendirici ve sembol sağlayıcısıyla etkileşim kurmayı sağlamaktan sorumludur. Tarafından uygulanır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (desteklediği diller için) ve kendi çalışma süresini desteklemek isteyen üçüncü taraf satıcıları.

- **İfade değerlendirici (ee):** Bir program belirli bir noktada durdurulduğunda Kullanıcı tarafından sağlanan değişkenleri ve ifadeleri dinamik olarak değerlendirmek için destek sağlar. Tarafından uygulanır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (desteklediği diller için) ve kendi dillerini desteklemek isteyen üçüncü taraf satıcıları.

- **Sembol sağlayıcısı (SP):** Sembol işleyici olarak da bilinen, anlamlı bilgilerin sağlanması için bir programın hata ayıklama sembollerini programın çalışan bir örneğine eşler (örneğin, kaynak kodu düzeyinde hata ayıklama ve ifade değerlendirmesi). Tarafından uygulanır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (ortak dil çalışma zamanı [clr] sembolleri ve program veritabanı [pdb] sembol dosyası biçimi için) ve hata ayıklama bilgilerini depolamak için kendi özel bir yöntemine sahip üçüncü taraf satıcıları.

  aşağıdaki diyagramda Visual Studio hata ayıklayıcının bu öğeleri arasındaki ilişki gösterilmektedir.

  ![Hata ayıklama bileşenlerine genel bakış](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>Bu bölümde
 [Hata ayıklama paketi](../../extensibility/debugger/debug-package.md) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kabukta çalışan ve tüm Kullanıcı arabirimini işleyen hata ayıklama paketini açıklar.

 [İşlem hata ayıklama Yöneticisi](../../extensibility/debugger/process-debug-manager.md) PDM özelliklerine genel bir bakış sağlar. Bu, hata ayıklaması yapılan işlemlerin yöneticisidir.

 [Oturum hata ayıklama Yöneticisi](../../extensibility/debugger/session-debug-manager.md) IDE 'ye hata ayıklama oturumunun Birleşik bir görünümünü sağlayan SDM 'yi tanımlar. SDM, DE ' i yönetir.

 [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md) , Tarafından sağlanan hata ayıklama hizmetlerini belgeler.

 [İşletimsel modlar](../../extensibility/debugger/operational-modes.md) IDE 'nin çalışabileceği üç moda genel bakış sağlar: tasarım modu, çalıştırma modu ve kesme modu. Geçiş mekanizmaları de ele alınmıştır.

 [İfade değerlendirici](../../extensibility/debugger/expression-evaluator.md) çalışma zamanında EE amacını açıklar.

 [Sembol sağlayıcısı](../../extensibility/debugger/symbol-provider.md) Uygulamasının, sembol sağlayıcısının değişkenleri ve ifadeleri değerlendirme şeklini açıklar.

 [Tür görselleştiricisi ve özel Görüntüleyici](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Bir tür görselleştiricisi ve özel görüntüleyicisinin ne olduğunu ve her ikisini de desteklemek için ifade değerlendirici 'nin hangi rol üzerinde oynatılacağını açıklar.

## <a name="related-sections"></a>İlgili bölümler
 [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimarisi kavramlarını açıklar.

 [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md) Aynı anda kod, belge ve ifade değerlendirme bağlamlarının içinde nasıl çalıştığını açıklar. Üç bağlamın her biri için, bu konuyla ilgili konum, konum veya değerlendirmeyi açıklar.

 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md) Bir program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerinin bağlantılarını içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanmaya başlama](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
