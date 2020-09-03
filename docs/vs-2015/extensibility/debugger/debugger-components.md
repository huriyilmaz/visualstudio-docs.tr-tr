---
title: Hata ayıklayıcı bileşenleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12f865e7d4c44cfa4002b330ed85ec95f95a8ef9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200679"
---
# <a name="debugger-components"></a>Hata Ayıklayıcı Bileşenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Hata ayıklayıcı bir VSPackage olarak uygulanır ve hata ayıklama oturumunun tamamını yönetir. Hata ayıklama oturumu aşağıdaki öğeleri içerir:  
  
- **Hata ayıklama paketi:** [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Hata ayıklayıcı, hata ayıklamanın ne olduğuna bakılmaksızın aynı kullanıcı arabirimini sağlar.  
  
- **Oturum hata ayıklama Yöneticisi (SDM):** [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Çeşitli hata ayıklama altyapısının yönetimi için hata ayıklayıcıya tutarlı bir programlama arabirimi sağlar. Tarafından uygulanır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- **İşlem hata ayıklama Yöneticisi (PDM):** Tüm çalışan örnekleri için, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hata ayıklanan veya hataları ayıklanabilecek tüm programların bir listesini yönetir. Tarafından uygulanır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- **Hata ayıklama altyapısı (de):** Hata ayıklamakta olan bir programın izlenmesini, çalışan programın durumunu SDM ve PDM ile iletişimi ve bir programın bellek ve değişkenlerinin durumunun gerçek zamanlı analizini sağlamak için ifade değerlendirici ve sembol sağlayıcısıyla etkileşim kurmayı sağlamaktan sorumludur. Tarafından uygulanır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (desteklediği diller için) ve kendi çalışma süresini desteklemek isteyen üçüncü taraf satıcıları.  
  
- **İfade değerlendirici (ee):** Bir program belirli bir noktada durdurulduğunda Kullanıcı tarafından sağlanan değişkenleri ve ifadeleri dinamik olarak değerlendirmek için destek sağlar. Tarafından uygulanır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (desteklediği diller için) ve kendi dillerini desteklemek isteyen üçüncü taraf satıcıları.  
  
- **Sembol sağlayıcısı (SP):** Sembol işleyici olarak da bilinen, anlamlı bilgilerin sağlanması için bir programın hata ayıklama sembollerini programın çalışan bir örneğine eşler (örneğin, kaynak kodu düzeyinde hata ayıklama ve ifade değerlendirmesi). Tarafından uygulanır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (ortak dil çalışma zamanı [clr] sembolleri ve program veritabanı [pdb] sembol dosyası biçimi için) ve hata ayıklama bilgilerini depolamak için kendi özel bir yöntemine sahip üçüncü taraf satıcıları.  
  
  Aşağıdaki diyagramda, Visual Studio hata ayıklayıcının bu öğeleri arasındaki ilişki gösterilmektedir.  
  
  ![Hata ayıklama bileşenlerine genel bakış](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Paket Hatalarını Ayıklama](../../extensibility/debugger/debug-package.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Kabukta çalışan ve tüm Kullanıcı arabirimini işleyen hata ayıklama paketini açıklar.  
  
 [İşlem Hata Ayıklama Yöneticisi](../../extensibility/debugger/process-debug-manager.md)  
 PDM özelliklerine genel bir bakış sağlar. Bu, hata ayıklaması yapılan işlemlerin yöneticisidir.  
  
 [Oturum Hata Ayıklama Yöneticisi](../../extensibility/debugger/session-debug-manager.md)  
 IDE 'ye hata ayıklama oturumunun Birleşik bir görünümünü sağlayan SDM 'yi tanımlar. SDM, DE ' i yönetir.  
  
 [Hata Ayıklama Altyapısı](../../extensibility/debugger/debug-engine.md)  
 , Tarafından sağlanan hata ayıklama hizmetlerini belgeler.  
  
 [Çalışma Modları](../../extensibility/debugger/operational-modes.md)  
 IDE 'nin çalışabileceği üç moda genel bakış sağlar: tasarım modu, çalıştırma modu ve kesme modu. Geçiş mekanizmaları de ele alınmıştır.  
  
 [İfade Değerlendirici](../../extensibility/debugger/expression-evaluator.md)  
 Çalışma zamanında EE 'ın amacını açıklar.  
  
 [Sembol Sağlayıcısı](../../extensibility/debugger/symbol-provider.md)  
 Uygulamasının, sembol sağlayıcısının değişkenleri ve ifadeleri değerlendirme şeklini açıklar.  
  
 [Tür Görselleştiricisi ve Özel Görüntüleyici](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Bir tür görselleştiricisi ve özel görüntüleyicisinin ne olduğunu ve her ikisini de desteklemek için ifade değerlendirici 'nin hangi rol üzerinde oynatılacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklayıcı Kavramları](../../extensibility/debugger/debugger-concepts.md)  
 Ana hata ayıklama mimarisi kavramlarını açıklar.  
  
 [Hata Ayıklayıcı Bağlamları](../../extensibility/debugger/debugger-contexts.md)  
 Aynı anda kod, belge ve ifade değerlendirme bağlamlarının içinde nasıl çalıştığını açıklar. Üç bağlamın her biri için, bu konuyla ilgili konum, konum veya değerlendirmeyi açıklar.  
  
 [Hata Ayıklama Görevleri](../../extensibility/debugger/debugging-tasks.md)  
 Bir program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerinin bağlantılarını içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
