---
title: Hata Ayıklama Motoru | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4cb00796f8db23a43cd81a06d80d0fac40f075e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739057"
---
# <a name="debug-engine"></a>Hata ayıklama motoru
Hata ayıklama altyapısı (DE), yürütme denetimi, kesme noktaları ve ifade değerlendirmesi gibi hata ayıklama hizmetlerini sağlamak için yorumlayıcı veya işletim sistemiyle birlikte çalışır. DE, debugged olan bir programın durumunu izlemekten sorumludur. Bunu başarmak için DE, ister CPU'dan ister çalışma zamanı tarafından sağlanan API'lerden olsun, desteklenen çalışma zamanında kullanabileceği her türlü yöntemi kullanır.

 Örneğin, ortak dil çalışma zamanı (CLR) ICorDebugXXX arabirimleri üzerinden çalışan bir programı izlemek için mekanizmalar sağlar. CLR destekleyen bir DE, debugged olan yönetilen bir kod programını izlemek için uygun ICorDebugXXX arabirimlerini kullanır. Daha sonra, bu tür bilgileri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE'ye ileten oturum hata ayıklama yöneticisine (SDM) durum değişiklikleri iletir.

> [!NOTE]
> Hata ayıklama altyapısı belirli bir çalışma zamanını, yani programın hata ayıklandığı sistemi hedefler. CLR yönetilen kodun çalışma zamanıdır ve Win32 çalışma süresi yerel Windows uygulamaları içindir. Oluşturduğunuz dil bu iki çalışma zamanından [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birini hedeflenebiliyorsa, gerekli hata ayıklama motorlarını zaten sağlar. Uygulamanız gereken tek şey bir ifade değerlendiricisi.

## <a name="debug-engine-operation"></a>Hata ayıklama motoru çalışması
 İzleme hizmetleri DE arabirimleri üzerinden uygulanır ve hata ayıklama paketinin farklı çalışma modları arasında geçişine neden olabilir. Daha fazla bilgi için [Bkz. Operasyonel modlar.](../../extensibility/debugger/operational-modes.md) Çalışma zamanı ortamı başına genellikle yalnızca bir DE uygulaması vardır.

> [!NOTE]
> Transact-SQL ve [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)], VBScript için ayrı DE [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] uygulamaları olsa da ve tek bir DE paylaşın.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hata ayıklama hata ayıklama, hata ayıklama motorlarının iki şekilde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çalışmasını sağlar: kabukla aynı işlemde veya hedef programın debugged olduğu aynı işlemde. İkinci form genellikle debugged olan işlem aslında bir yorumlayıcı altında çalışan bir komut dosyası olduğunda oluşur. Hata ayıklama motoru, komut dosyasını izlemek için tercümanın yakın bilgisine sahip olmalıdır. Bu durumda, tercüman aslında bir çalışma zamanıdır; hata ayıklama motorları belirli çalışma zamanı uygulamaları içindir. Buna ek olarak, tek bir DE uygulaması işlem ve makine sınırları arasında bölünebilir (örneğin, uzaktan hata ayıklama).

 DE hata ayıklama arabirimlerini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ortaya çıkarır. Tüm iletişim COM üzerinden. DE ister işlem içi, ister işlem dışı ister başka bir bilgisayara yüklenirse de, bileşen iletişimini etkilemez.

 DE, ifadelerin sözdizimini anlamak için sözdizimini anlamak için sözdizimi nin sözdizimini anlamak için sözdizimi nin sözdizimini sağlamak için bir ifade değerlendirici bileşeniyle çalışır. DE ayrıca dil derleyicisi tarafından oluşturulan sembolik hata ayıklama bilgilerine erişmek için bir sembol işleyici bileşeni ile çalışır. Daha fazla bilgi için Ifade [değerlendiricisi](../../extensibility/debugger/expression-evaluator.md) ve [Sembol sağlayıcısına](../../extensibility/debugger/symbol-provider.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama bileşenleri](../../extensibility/debugger/debugger-components.md)
- [İfade değerlendiricisi](../../extensibility/debugger/expression-evaluator.md)
- [Sembol sağlayıcı](../../extensibility/debugger/symbol-provider.md)
