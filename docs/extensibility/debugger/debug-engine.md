---
title: Hata Ayıklama Altyapısı | Microsoft Docs
description: Yürütme denetimi, kesme noktaları ve ifade değerlendirmesi gibi hizmetler sağlamak için hata ayıklama altyapısının yorumlayıcı veya işletim sistemiyle nasıl çalıştığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4836141f50f2db13ad0fd303168d291b56ab1643
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111755"
---
# <a name="debug-engine"></a>Hata ayıklama altyapısı
Hata ayıklama altyapısı (DE), yürütme denetimi, kesme noktaları ve ifade değerlendirmesi gibi hata ayıklama hizmetleri sağlamak için yorumlayıcı veya işletim sistemiyle birlikte çalışır. DE, hata ayıklaması yapılan bir programın durumunu izlemekle sorumludur. Bunu yapmak için DE, desteklenen çalışma zamanında kullanılabilir olan yöntemleri (ister CPU'dan ister çalışma zamanı tarafından sağlanan API'lerden) kullanır.

 Örneğin, ortak dil çalışma zamanı (CLR), ICorDebugXXX arabirimleri aracılığıyla çalışan bir programı izlemek için mekanizmalar sağlar. CLR'i destekleyen bir DE, hata ayıklaması yapılan yönetilen kod programını izlemek için uygun ICorDebugXXX arabirimlerini kullanır. Ardından, durum değişikliklerini oturum hata ayıklama yöneticisine (SDM) iletir ve bu da bu bilgileri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE'ye iletir.

> [!NOTE]
> Hata ayıklama altyapısı belirli bir çalışma zamanının hedefini, yani hata ayıklama yapılan programın çalıştır olduğu sistemi hedefler. CLR, yönetilen kodun çalışma zamanıdır ve Win32 çalışma zamanı yerel Windows için kullanılır. Oluştursanız dil bu iki çalışma zamanından birini hedefleyeblirse, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerekli hata ayıklama altyapılarını zaten sağlar. Tek uygulayan bir ifade değerlendiricidir.

## <a name="debug-engine-operation"></a>Hata ayıklama altyapısı işlemi
 İzleme hizmetleri DE arabirimleri aracılığıyla uygulanır ve hata ayıklama paketinin farklı işlem modları arasında geçişe neden olabilir. Daha fazla bilgi için bkz. [İşletim modları.](../../extensibility/debugger/operational-modes.md) Çalışma zamanı ortamı başına genellikle yalnızca bir DE uygulaması vardır.

> [!NOTE]
> Transact-SQL ve VBScript için ayrı DE uygulamaları vardır ve [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] tek bir DE paylaşır.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama, hata ayıklama altyapılarının iki şekilden birini çalıştırmasını sağlar: kabukla aynı işlemde veya hata ayıklama yapılan hedef [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] programla aynı işlemde. İkinci form genellikle hata ayıklama işlemi aslında yorumlayıcı altında çalışan bir betik olduğunda oluşur. Betiği izlemek için hata ayıklama altyapısının yorumlayıcı hakkında bilgi sahibi olması gerekir. Bu durumda yorumlayıcı aslında bir çalışma zamanıdır; hata ayıklama altyapıları belirli çalışma zamanı uygulamalarına yöneliktir. Ayrıca, tek bir DE'nin uygulanması işlem ve makine sınırları (örneğin, uzaktan hata ayıklama) arasında bölünebiliyor.

 DE, hata ayıklama [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arabirimlerini gösterir. Tüm iletişim COM üzerindendir. DE'nin işlem içinde, işlem dışı veya başka bir bilgisayarda yüklü olup olmadığı, bileşen iletişimini etkilemez.

 DE, ifadelerin söz dizimlerini anlamak için söz konusu çalışma zamanının DE'sini etkinleştirmek üzere bir ifade değerlendirici bileşeniyle çalışır. DE, dil derleyicisi tarafından oluşturulan sembolik hata ayıklama bilgilerine erişmek için bir sembol işleyici bileşeniyle de çalışır. Daha fazla bilgi için [bkz. İfade değerlendiricisi](../../extensibility/debugger/expression-evaluator.md) ve [Sembol sağlayıcısı.](../../extensibility/debugger/symbol-provider.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcısı bileşenleri](../../extensibility/debugger/debugger-components.md)
- [İfade değerlendirici](../../extensibility/debugger/expression-evaluator.md)
- [Sembol sağlayıcısı](../../extensibility/debugger/symbol-provider.md)
