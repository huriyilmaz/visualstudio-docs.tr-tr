---
title: Sembol Sağlayıcı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b90846d9494ee046cf9dc4a3e5de9ff033ea3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712817"
---
# <a name="symbol-provider"></a>Sembol sağlayıcı
Bir ifade değerlendirici uygulaması değişkenleri ve ifadeleri değerlendirmek için dil derleyicisi tarafından oluşturulan sembolik hata ayıklama bilgilerine erişmelidir. Bunu, sembol işleyicisi olarak da adlandırılan bir sembol sağlayıcısının (SP) arabirimlerini tüketerek yapar.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Program DataBase (PDB) sembolü dosya biçimini kullanarak yönetilen kod ve yerel kod için SPs sağlar. Programınızın özel bir biçimde depolanan sembolleri kullanmasına güçlü bir ihtiyaç olmadığı sürece, sp'leri kullanmanız [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]önerilir.

## <a name="implementation-notes"></a>Uygulama notları
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hata ayıklama motorları Ortak Dil Çalışma Zamanı (CLR) arabirimlerini kullanarak SP'lerle konuşmayı bekler. Sonuç olarak, Visual Studio hata ayıklama motorları ile çalışacak bir SP CLR desteklemesi gerekir. Tüm CLR hata ayıklama arabirimlerinin tam bir listesini debugref.doc, bir [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]parçası olan bulunabilir.

 SP'niz yalnızca özel hata ayıklama motorunuzla çalışacaksa, hata ayıklama motorunuzun gereksinimlerine bağlı olarak uygun gördüğünüz şekilde SP'yi uygulayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama bileşenleri](../../extensibility/debugger/debugger-components.md)
