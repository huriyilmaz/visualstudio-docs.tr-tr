---
title: ClickOnce Önbelleğe Genel Bakış | Microsoft Docs
description: Uygulamaların depolandığı ClickOnce gizli dizinleri içeren uygulama önbelleği hakkında bilgi ClickOnce öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: c88c3e641869e9f58111fee28742d0ebeaafd9ab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051683"
---
# <a name="clickonce-cache-overview"></a>ClickOnce önbelleğine genel bakış
Yerel olarak yüklenmiş veya çevrimiçi olarak barındırılan tüm uygulamalar, istemci bilgisayarda bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] önbelleğinde *depolanır.* Önbellek, geçerli kullanıcının Documents ve Ayarlar klasörünün Local Ayarlar dizininde yer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] alan gizli Ayarlar ailesidir. Bu önbellek derlemeler, yapılandırma dosyaları, uygulama ve kullanıcı ayarları ve veri dizini dahil olmak üzere uygulamanın tüm dosyalarını tutar. Önbellek, uygulamanın veri dizinini en son sürüme de yapmaktan sorumludur. Veri geçişi hakkında daha fazla bilgi için [bkz. ClickOnce Uygulamalarında Yerel ve Uzak Verilere Erişme.](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)

 Uygulama depolama için tek bir konum sağlayarak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir uygulamanın fiziksel yüklemesini kullanıcıdan yönetme görevini üst alır. Önbellek ayrıca tüm uygulamalar için derlemeleri ve veri dosyalarını ve bunların ayrı sürümlerini birbirinden ayırarak uygulamaları yalıtmanıza yardımcı olur. Örneğin, bir uygulamayı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yükseltin, bu sürüm ve onun veri kaynakları önbellekte kendi dizinleri ile sağlanır.

## <a name="cache-storage-quota"></a>Önbellek depolama kotası
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] çevrimiçi barındırılan uygulamalar, önbellek boyutunu kısıtlayacak bir kotayla kaplayacakları alan miktarıyla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kısıtlanır. Önbellek boyutu tüm kullanıcının çevrimiçi uygulamaları için geçerlidir; Kısmen güvenilen tek bir çevrimiçi uygulama, kota alanı yarısını kaplayacak şekilde sınırlıdır. Yüklü uygulamalar önbellek boyutuyla sınırlı değildir ve önbellek sınırına göre sayılmaz. Tüm uygulamalar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] için önbellek yalnızca geçerli sürümü ve önceden yüklenmiş sürümü korur.

 Varsayılan olarak, istemci bilgisayarlar çevrimiçi uygulamalar için 250 MB depolama alanına [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sahiptir. Veri dosyaları bu sınıra doğru sayılmaz. Sistem yöneticisi, önbellek boyutunu kilobayt cinsinden ifade eden bir DWORD değeri olan **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB** kayıt defteri anahtarını değiştirerek belirli bir istemci bilgisayarda bu kotayı büyütebilir veya azaltabilirsiniz. Örneğin, önbellek boyutunu 50 MB'a düşürmek için bu değeri 51200 olarak değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarında yerel ve uzak veri erişimi](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)