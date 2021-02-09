---
title: Ayrıntılı günlük dosyalarını belirtin (ClickOnce dağıtımları)
description: ClickOnce dağıtımını yüklemek, başlatmak, güncelleştirmek ve kaldırmak için ClickOnce 'ın koruduğu etkinlik günlüklerinin ayrıntı düzeyini belirtmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7adb711c77f4bb2dead3190d40065e148760b034
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887477"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Nasıl yapılır: ClickOnce dağıtımları için ayrıntılı günlük dosyaları belirtme
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tüm dağıtımlar için etkinlik günlüğü dosyalarını tutar. Bu, bir dağıtımı yükleme, başlatma, güncelleştirme ve kaldırma ile ilgili belge ayrıntılarını günlüğe kaydeder [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Bu günlük dosyalarına yazan ayrıntıyı artırmak için, ayrıntı düzeyini belirtmek Için kayıt defteri Düzenleyicisi 'ni (*regedit.exe*) kullanın.

> [!CAUTION]
> Kayıt Defteri Düzenleyicisi 'Ni yanlış kullanırsanız, işletim sistemini yeniden yüklemenizi gerektirebilecek önemli sorunlara neden olabilirsiniz. Kayıt Defteri Düzenleyicisi 'Ni kullanarak kendi sorumluluğunuzdadır.

 Aşağıdaki yordam, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] geçerli kullanıcı için günlük dosyaları için ayrıntı düzeyinin nasıl belirtileceğini açıklar. Ayrıntı düzeyini azaltmak için bu kayıt defteri değerini kaldırın.

### <a name="to-specify-verbose-log-files"></a>Ayrıntılı günlük dosyaları belirtmek için

1. *Regedit.exe* açın.

2. **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment** düğüme gidin.

3. Gerekirse adlı yeni bir dize değeri oluşturun `LogVerbosityLevel` .

4. `LogVerbosityLevel`Değerini olarak ayarlayın `1` .

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım sorunlarını giderme](../deployment/troubleshooting-clickonce-deployments.md)