---
title: Kaynak denetimi eklentileri için uyarıları kapatma
description: Bir Kullanıcı, Visual Studio 'da kaynak denetimi kullanırken çeşitli uyumluluk uyarıları görebilir. Bu uyarıları devre dışı bırakmayı öğrenin.
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
ms.openlocfilehash: f5607f4a92a14b692f20d509e014991d461815bd
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993555"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Nasıl yapılır: kaynak denetimi eklentileri için uyumluluk uyarılarını kapatma

Bir kullanıcı içinde kaynak denetimi kullanırken çeşitli uyumluluk uyarıları görebilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Sunulan uyarılar, kaynak denetimi eklentisinin özelliklerine bağlıdır ve burada ayrıntılı olarak devre dışı bırakılabilir.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Uyarıyı devre dışı bırakmak için: "Visual Studio ile en iyi kaynak denetimi tümleştirmesini sağlamak Için"

- Aşağıdaki kayıt defteri girdisini ayarlayın (gerekirse değeri ekleyin):

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001**

   Bu uyarı tüm eklentiler için görüntülenir [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] .

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Bu uyarıyı devre dışı bırakmak için: "yüklenen kaynak denetimi sağlayıcısı tüm özellikleri desteklemiyor"

- Aşağıdaki iki kayıt defteri değerini ayarlayın (gerekirse değerleri ekleyin):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001**

     Bu uyarı, kaynak denetimi eklentisi birden çok proje için yeniden giriş (tek seferde yalnızca bir dosya ve Proje iade edebilir) açıkça desteklemiyorsa görüntülenir.

     Yeniden giriş (yetenek) desteklemek en iyisidir `SCC_CAP_REENTRANT` ; bunun yapılması, bu uyarıyı kaldırır. Ancak, bu destek mümkün değilse, bu kayıt defteri girdileri ayarlanabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yetenek bayrakları](../extensibility/capability-flags.md)
