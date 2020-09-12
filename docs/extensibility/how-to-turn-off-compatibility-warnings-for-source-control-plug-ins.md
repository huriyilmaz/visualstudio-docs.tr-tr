---
title: Kaynak denetimi eklentileri için uyarıları kapatma
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 406d063bd2df6dd1d831c3a8220d8d513596a79a
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037191"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Nasıl yapılır: kaynak denetimi eklentileri için uyumluluk uyarılarını kapatma

Bir kullanıcı içinde kaynak denetimi kullanırken çeşitli uyumluluk uyarıları görebilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Sunulan uyarılar, kaynak denetimi eklentisinin özelliklerine bağlıdır ve burada ayrıntılı olarak devre dışı bırakılabilir.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Uyarıyı devre dışı bırakmak için: "Visual Studio ile en iyi kaynak denetimi tümleştirmesini sağlamak Için"

- Aşağıdaki kayıt defteri girdisini ayarlayın (gerekirse değeri ekleyin):

   **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001**

   Bu uyarı tüm eklentiler için görüntülenir [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] .

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Bu uyarıyı devre dışı bırakmak için: "yüklenen kaynak denetimi sağlayıcısı tüm özellikleri desteklemiyor"

- Aşağıdaki iki kayıt defteri değerini ayarlayın (gerekirse değerleri ekleyin):

     **HKEY_CURRENT_USER \Software\microsoft\visualstudio\8.0\sourcecontrol\warnedoldmssccıprovider = DWORD: 00000000**

    **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001**

     Bu uyarı, kaynak denetimi eklentisi birden çok proje için yeniden giriş (tek seferde yalnızca bir dosya ve Proje iade edebilir) açıkça desteklemiyorsa görüntülenir.

     Yeniden giriş (yetenek) desteklemek en iyisidir `SCC_CAP_REENTRANT` ; bunun yapılması, bu uyarıyı kaldırır. Ancak, bu destek mümkün değilse, bu kayıt defteri girdileri ayarlanabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yetenek bayrakları](../extensibility/capability-flags.md)
