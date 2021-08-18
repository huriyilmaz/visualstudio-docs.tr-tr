---
title: Sembol sağlayıcısı | Microsoft Docs
description: bir ifade değerlendirici 'nin değişkenleri ve ifadeleri değerlendirmesini sağlamak için Visual Studio sağladığı sembol sağlayıcıları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 49f26713bcda948220fabdefaa62032e10fde8a2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152594"
---
# <a name="symbol-provider"></a>Sembol sağlayıcısı
Bir ifade değerlendirici uygulamasının, değişkenleri ve ifadeleri değerlendirmek için dil derleyicisi tarafından oluşturulan sembolik hata ayıklama bilgilerine erişmesi gerekir. Bu, sembol işleyicisi olarak da adlandırılan bir sembol sağlayıcısı (SP) arabirimlerini tüketerek olur.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Program veritabanı (PDB) sembol dosyası biçimini kullanarak, yönetilen kod için SPs ve yerel kod sağlar. Programınızın özel bir biçimde depolanan sembolleri kullanması için güçlü bir gereksinim olmadığı müddetçe, tarafından sağlanan SPs 'yi kullanmanız önerilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>Uygulama notları
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Hata ayıklama motorları, ortak dil çalışma zamanı (CLR) arabirimlerini kullanarak SPS ile iletişim kurmasını bekler. sonuç olarak, Visual Studio hata ayıklama altyapılarıyla çalışacak bir SP, CLR 'yi desteklemelidir. Tüm CLR hata ayıklama arabirimlerinin listesi, öğesinin bir parçası olan debugref.doc bulunabilir [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 SP 'niz yalnızca özel hata ayıklama altyapımız ile çalışıyorsa, hata ayıklama altyapılarınızın ihtiyaçlarına bağlı olarak uygun gördüğünüz gibi SP 'yi uygulayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)
