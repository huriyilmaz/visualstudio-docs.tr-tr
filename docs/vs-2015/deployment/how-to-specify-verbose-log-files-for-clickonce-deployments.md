---
title: 'Nasıl yapılır: ClickOnce dağıtımları için ayrıntılı günlük dosyaları belirtme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 78fa278952004348e035a675a1e159b2164285b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64832926"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Nasıl yapılır: ClickOnce Dağıtımları İçin Ayrıntılı Günlük Dosyası Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tüm dağıtımlar için etkinlik günlüğü dosyalarını tutar. Bu, bir dağıtımı yükleme, başlatma, güncelleştirme ve kaldırma ile ilgili belge ayrıntılarını günlüğe kaydeder [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Bu günlük dosyalarına yazan ayrıntıyı artırmak için, ayrıntı düzeyini belirtmek Için kayıt defteri Düzenleyicisi 'ni (**regedit.exe**) kullanın.  
  
> [!CAUTION]
> Kayıt Defteri Düzenleyicisi 'Ni yanlış kullanırsanız, işletim sistemini yeniden yüklemenizi gerektirebilecek önemli sorunlara neden olabilirsiniz. Kayıt Defteri Düzenleyicisi 'Ni kullanarak kendi sorumluluğunuzdadır.  
  
 Aşağıdaki yordam, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] geçerli kullanıcı için günlük dosyaları için ayrıntı düzeyinin nasıl belirtileceğini açıklar. Ayrıntı düzeyini azaltmak için bu kayıt defteri değerini kaldırın.  
  
### <a name="to-specify-verbose-log-files"></a>Ayrıntılı günlük dosyaları belirtmek için  
  
1. **Regedit.exe**açın.  
  
2. Düğüme gidin `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .  
  
3. Gerekirse adlı yeni bir dize değeri oluşturun `LogVerbosityLevel` .  
  
4. `LogVerbosityLevel`Değerini olarak ayarlayın `1` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Dağıtım Sorunlarını Giderme](../deployment/troubleshooting-clickonce-deployments.md)
