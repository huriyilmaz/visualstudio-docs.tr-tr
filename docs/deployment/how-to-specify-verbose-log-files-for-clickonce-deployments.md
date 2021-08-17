---
title: Ayrıntılı günlük dosyalarını belirtme (ClickOnce dağıtımları)
description: Bir dağıtım yükleme, başlatma, güncelleştirme ve kaldırma ClickOnce bakımları yapılan etkinlik günlükleri için ayrıntılı ClickOnce öğrenin.
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
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 6b7760aa8f7916d14b7d3f5ee03978f1e2d2193a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080487"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Nasıl kullanılır: Dağıtımlar için ayrıntılı günlük ClickOnce belirtme
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tüm dağıtımlar için etkinlik günlüğü dosyalarını sürdürür. Bu günlükler bir dağıtımı yükleme, başlatma, güncelleştirme ve kaldırma ile ilgili ayrıntıları [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] belgeletir. Bu günlük dosyalarına yazan ayrıntıları artırmak için Kayıt Defteri [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Düzenleyicisi'ni (*regedit.exe*) kullanarak ayrıntı düzeyini belirtin.

> [!CAUTION]
> Kayıt Defteri Düzenleyicisi'ni yanlış kullanırsanız, işletim sistemini yeniden yüklemeniz gerektirabilecek ciddi sorunlara neden olabilir. Kendi risk altında Kayıt Defteri Düzenleyicisi'ni kullanın.

 Aşağıdaki yordam, geçerli kullanıcı için günlük dosyaları için ayrıntılılık [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] düzeyinin nasıl belirtil olduğunu açıklar. Ayrıntılılık düzeyini azaltmak için bu kayıt defteri değerini kaldırın.

### <a name="to-specify-verbose-log-files"></a>Ayrıntılı günlük dosyalarını belirtmek için

1. *Regedit.exe.*

2. uygulamanın düğümüne **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment.**

3. Gerekirse adlı yeni bir dize değeri `LogVerbosityLevel` oluşturun.

4. değerini `LogVerbosityLevel` olarak `1` ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım sorunlarını giderme](../deployment/troubleshooting-clickonce-deployments.md)