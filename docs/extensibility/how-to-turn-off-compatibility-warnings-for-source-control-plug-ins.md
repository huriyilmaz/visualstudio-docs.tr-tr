---
title: Kaynak Kontrol Eklentileri için Uyumluluk Uyarılarını Kapat | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22dd3821426aa1dae6265c520ddac60dd93e1c5e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710722"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Nasıl yapilir: Kaynak denetimi eklentileri için uyumluluk uyarılarını kapatma
Bir kullanıcı, 'de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]kaynak denetimi kullanırken birkaç uyumluluk uyarısı görebilir. Sunulan uyarılar kaynak kontrol eklentisinin özelliklerine bağlıdır ve burada ayrıntılı olarak belirtildiği gibi devre dışı tutulabilir.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Uyarıyı devre dışı kalmak için: "Visual Studio ile en iyi kaynak kontrolü tümleştirmesini sağlamak için"

- Aşağıdaki kayıt defteri girişini ayarlayın (gerekirse değer ekleme):

   **HKEY_CURRENT_USER\Yazılım\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001**

   Bu uyarı,[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] eklenti olmayan tüm ler için görüntülenir.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Uyarıyı devre dışı kaldırmak için: "Yüklü kaynak denetim sağlayıcısı tüm yetenekleri desteklemez"

- Aşağıdaki iki kayıt defteri değerini ayarlama (gerekirse değerleri ekleme):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**

     Kaynak denetim eklentisi birden çok proje için yeniden canlandırmayı açıkça desteklemiyorsa (diğer bir anda yalnızca bir dosya ve projeyi iade edebilirse) bu uyarı görüntülenir.

     Bu reentrancy (yetenek)`SCC_CAP_REENTRANT` desteklemek için en iyisidir; bunu yapmak bu uyarıyı kaldırır. Ancak, bu destek mümkün değilse, bu kayıt defteri girişleri ayarlanabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yetenek bayrakları](../extensibility/capability-flags.md)
