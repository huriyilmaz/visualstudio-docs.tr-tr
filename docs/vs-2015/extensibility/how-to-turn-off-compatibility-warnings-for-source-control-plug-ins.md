---
title: 'Nasıl yapılır: kaynak denetimi eklentileri için uyumluluk uyarılarını kapatma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4397b2710a7de4addd97bfcbdb4f8e80e2b9c70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204057"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Nasıl Yapılır: Kaynak Denetimi Eklentileri için Uyumluluk Uyarılarını Kapatma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir kullanıcı içinde kaynak denetimi kullanırken çeşitli uyumluluk uyarıları görebilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Sunulan uyarılar, kaynak denetimi eklentisinin özelliklerine bağlıdır ve burada ayrıntılı olarak devre dışı bırakılabilir.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Uyarıyı devre dışı bırakmak için: "Visual Studio ile en iyi kaynak denetimi tümleştirmesini sağlamak Için..."  
  
- Aşağıdaki kayıt defteri girdisini ayarlayın (gerekirse değeri ekleyin):  
  
     HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001  
  
     Bu uyarı tüm eklentiler için görüntülenir [!INCLUDE[vsvss](../includes/vsvss-md.md)] .  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Bu uyarıyı devre dışı bırakmak için: "yüklenen kaynak denetimi sağlayıcısı tüm özellikleri desteklemiyor..."  
  
- Aşağıdaki iki kayıt defteri değerini ayarlayın (gerekirse değerleri ekleyin):  
  
     HKEY_CURRENT_USER \Software\microsoft\visualstudio\8.0\sourcecontrol\warnedoldmssccıprovider = DWORD: 00000000  
  
     HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001  
  
     Bu uyarı, kaynak denetimi eklentisi birden çok proje için yeniden giriş (tek seferde yalnızca bir dosya ve Proje iade edebilir) açıkça desteklemiyorsa görüntülenir.  
  
     Yeniden giriş (yetenek) desteklemek en iyisidir `SCC_CAP_REENTRANT` ; bunun yapılması, bu uyarıyı kaldırır. Ancak, bu destek mümkün değilse, bu kayıt defteri girdileri ayarlanabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellik Bayrakları](../extensibility/capability-flags.md)
