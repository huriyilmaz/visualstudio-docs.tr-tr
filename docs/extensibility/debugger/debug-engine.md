---
title: Hata ayıklama altyapısı | Microsoft Docs
description: Bir hata ayıklama altyapısının, yürütme denetimi, kesme noktaları ve ifade değerlendirmesi gibi hizmetleri sağlamak üzere yorumlayıcı veya işletim sistemiyle nasıl çalıştığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9e278b83e69a063c88b4cb3ff48d919d2b07ea6a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955170"
---
# <a name="debug-engine"></a>Hata ayıklama altyapısı
Hata ayıklama altyapısı (DE), yürütme denetimi, kesme noktaları ve ifade değerlendirmesi gibi hata ayıklama hizmetleri sağlamak için yorumlayıcı veya işletim sistemi ile birlikte kullanılır. Aynı hata ayıklanmakta olan bir programın durumunu izlemenin DE sorumluluğundadır. Bunu gerçekleştirmek için, bu, CPU 'dan veya çalışma zamanının sağladığı API 'lerden bağımsız olarak, desteklenen çalışma zamanında bu için kullanılabilen yöntemleri kullanır.

 Örneğin, ortak dil çalışma zamanı (CLR) ICorDebugXXX arabirimleri aracılığıyla çalışan bir programı izlemeye yönelik mekanizmalar sağlar. CLR 'yi destekleyen bir DE, hata ayıklamakta olan bir yönetilen kod programının izini tutmak için uygun ICorDebugXXX arabirimlerini kullanır. Daha sonra bu bilgileri IDE 'ye ileten oturum hata ayıklama Yöneticisi 'nde (SDM) tüm durum değişikliklerini iletişim kurar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

> [!NOTE]
> Bir hata ayıklama altyapısı belirli bir çalışma zamanını ve diğer bir deyişle, hata ayıklamakta olan programın çalıştırıldığı sistemi hedefler. CLR, yönetilen kod için çalışma zamanı ve Win32 çalışma zamanı yerel Windows uygulamaları içindir. Oluşturduğunuz dil bu iki çalışma zamanlarının birini hedefleyebilir, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerekli hata ayıklama altyapılarını zaten temin eder. Uygulamanız için tek bir ifade değerlendirici.

## <a name="debug-engine-operation"></a>Hata ayıklama altyapısı işlemi
 İzleme hizmetleri DE aynı arabirimler aracılığıyla uygulanır ve hata ayıklama paketinin farklı çalışma modları arasında geçişine neden olabilir. Daha fazla bilgi için bkz. [işletimsel modlar](../../extensibility/debugger/operational-modes.md). Çalışma zamanı ortamı başına genellikle yalnızca bir DE uygulama vardır.

> [!NOTE]
> Transact-SQL ve VBScript için ayrı uygulamalar olmakla kalmaz [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] ve [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] tek bir de paylaşabilirsiniz.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama, hata ayıklama altyapısının iki şekilde çalışmasını sağlar: [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kabukta aynı işlemde veya hata ayıklamakta olan hedef programla aynı işlemde. İkinci form genellikle hata ayıklamakta olan işlem aslında yorumlayıcı altında çalışan bir komut dosyası olduğunda oluşur. Betiği izlemek için hata ayıklama altyapısı yorumlayıcı intimate bilgisine sahip olmalıdır. Bu durumda, yorumlayıcı aslında bir çalışma zamanı; hata ayıklama motorları, belirli çalışma zamanı uygulamalarına yöneliktir. Buna ek olarak, tek bir DE uygulanması işlem ve makine sınırları genelinde bölünebilir (örneğin, uzaktan hata ayıklama).

 DE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama arabirimlerini kullanıma sunar. Tüm iletişimler COM üzerinden yapılır. Ayrıca, uygulamasının işlem içi, işlem dışı veya başka bir bilgisayarda yüklü olup olmadığı, bileşen iletişimini etkilemez.

 DE, söz konusu çalışma zamanının ifade sözdizimini anlaması için DE bir ifade değerlendirici bileşeniyle birlikte çalışarak. Ayrıca, dil derleyicisi tarafından oluşturulan sembolik hata ayıklama bilgilerine erişmek için bir sembol işleyici bileşeniyle de birlikte da kullanılır. Daha fazla bilgi için bkz. [ifade değerlendiricisi](../../extensibility/debugger/expression-evaluator.md) ve [sembol sağlayıcısı](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)
- [İfade değerlendirici](../../extensibility/debugger/expression-evaluator.md)
- [Sembol sağlayıcısı](../../extensibility/debugger/symbol-provider.md)
