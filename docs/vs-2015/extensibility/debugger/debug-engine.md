---
title: Hata ayıklama altyapısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e81a95cffebc9e26821b9cc6157627100343452
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807706"
---
# <a name="debug-engine"></a>Hata Ayıklama Altyapısı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama altyapısı (DE), yürütme denetimi, kesme noktaları ve ifade değerlendirmesi gibi hata ayıklama hizmetleri sağlamak için yorumlayıcı veya işletim sistemi ile birlikte kullanılır. Aynı hata ayıklanmakta olan bir programın durumunu izlemenin DE sorumluluğundadır. Bunu gerçekleştirmek için, bu, CPU 'dan veya çalışma zamanının sağladığı API 'lerden bağımsız olarak, desteklenen çalışma zamanında bu için kullanılabilen yöntemleri kullanır.  
  
 Örneğin, ortak dil çalışma zamanı (CLR) ICorDebugXXX arabirimleri aracılığıyla çalışan bir programı izlemeye yönelik mekanizmalar sağlar. CLR 'yi destekleyen bir DE, hata ayıklamakta olan bir yönetilen kod programının izini tutmak için uygun ICorDebugXXX arabirimlerini kullanır. Daha sonra bu bilgileri IDE 'ye ileten oturum hata ayıklama Yöneticisi 'nde (SDM) tüm durum değişikliklerini iletişim kurar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
> [!NOTE]
> Bir hata ayıklama altyapısı belirli bir çalışma zamanını ve diğer bir deyişle, hata ayıklamakta olan programın çalıştırıldığı sistemi hedefler. CLR, yönetilen kod için çalışma zamanı ve Win32 çalışma zamanı yerel Windows uygulamaları içindir. Oluşturduğunuz dil bu iki çalışma zamanlarının birini hedefleyebilir, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gerekli hata ayıklama altyapılarını zaten temin eder. Uygulamanız için tek bir ifade değerlendirici.  
  
## <a name="debug-engine-operation"></a>Hata ayıklama altyapısı Işlemi  
 İzleme hizmetleri DE aynı arabirimler aracılığıyla uygulanır ve hata ayıklama paketinin farklı çalışma modları arasında geçişine neden olabilir. Daha fazla bilgi için bkz. [Işletimsel modlar](../../extensibility/debugger/operational-modes.md). Çalışma zamanı ortamı başına genellikle yalnızca bir DE uygulama vardır.  
  
> [!NOTE]
> Transact-SQL ve VBScript için ayrı uygulamalar olmakla kalmaz [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] ve [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] tek bir de paylaşabilirsiniz.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hata ayıklama, hata ayıklama altyapısının iki şekilde çalışmasını sağlar: [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kabukta aynı işlemde veya hata ayıklamakta olan hedef programla aynı işlemde. İkinci form genellikle hata ayıklamakta olan işlem aslında yorumlayıcı altında çalışan bir betiktir ve hata ayıklama altyapısı, betiği izlemek için yorumlayıcıdaki intimate bilgisine sahip olmalıdır. Bu durumda, yorumlayıcı gerçekten bir çalışma zamanı olduğunu unutmayın; hata ayıklama motorları, belirli çalışma zamanı uygulamalarına yöneliktir. Buna ek olarak, tek bir DE uygulanması işlem ve makine sınırları genelinde bölünebilir (örneğin, uzaktan hata ayıklama).  
  
 DE [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hata ayıklama arabirimlerini kullanıma sunar. Tüm iletişimler COM üzerinden yapılır. Ayrıca, uygulamasının işlem içi, işlem dışı veya başka bir bilgisayarda yüklü olup olmadığı, bileşen iletişimini etkilemez.  
  
 Aynı zamanda, ifadelerin sözdizimini anlamak için o belirli çalışma zamanının DE kullanımını etkinleştirmek üzere bir ifade değerlendirici bileşeniyle çalışır. Ayrıca, dil derleyicisi tarafından oluşturulan sembolik hata ayıklama bilgilerine erişmek için bir sembol işleyici bileşeniyle de birlikte da kullanılır. Daha fazla bilgi için bkz. [Ifade Değerlendiricisi](../../extensibility/debugger/expression-evaluator.md) ve [sembol sağlayıcısı](../../extensibility/debugger/symbol-provider.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)   
 [İfade değerlendirici](../../extensibility/debugger/expression-evaluator.md)   
 [Sembol Sağlayıcısı](../../extensibility/debugger/symbol-provider.md)
