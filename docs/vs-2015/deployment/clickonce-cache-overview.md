---
title: ClickOnce önbelleğine genel bakış | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58ea758ea10e2c58ff123a2bc991f14191db0aa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151661"
---
# <a name="clickonce-cache-overview"></a>ClickOnce Önbelleğine Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Yerel olarak yüklenmiş veya çevrimiçi olarak barındırılan tüm uygulamalar, istemci bilgisayarda bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama *önbelleğinde*depolanır. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Önbellek, geçerli kullanıcının belgeler ve ayarlar klasörünün yerel ayarlar dizininde bulunan gizli dizinlerin bir ailesidir. Bu önbellek derlemeler, yapılandırma dosyaları, uygulama ve Kullanıcı ayarları ve veri dizini dahil tüm uygulama dosyalarını barındırır. Önbellek, uygulamanın veri dizinini en son sürüme geçirmeden de sorumludur. Veri taşıma hakkında daha fazla bilgi için bkz. [ClickOnce uygulamalarında yerel ve uzak verilere erişme](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Uygulama depolaması için tek bir konum sağlayarak, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] kullanıcıdan bir uygulamanın fiziksel yüklemesini yönetme görevini devralır. Önbellek Ayrıca, tüm uygulamalar için derlemeleri ve veri dosyalarını ve bunların farklı sürümlerini birbirinden ayrı tutarak uygulamaları yalıtmaya yardımcı olur. Örneğin, bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamayı yükselttiğinizde, bu sürüm ve veri kaynakları önbellekte kendi dizinleriyle birlikte sağlanır.  
  
## <a name="cache-storage-quota"></a>Önbellek depolama kotası  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] çevrimiçi olarak barındırılan uygulamalar, önbelleğin boyutunu kısıtlayan bir kota ile kaplayabilecekleri alan miktarı ile sınırlıdır [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Önbellek boyutu kullanıcının tüm çevrimiçi uygulamalarına uygulanır; tek bir kısmen güvenilen çevrimiçi uygulama, kota alanının yarısını kaplayan bir şekilde sınırlandırılmıştır. Yüklü uygulamalar önbellek boyutuyla sınırlı değildir ve önbellek sınırına göre sayılmaz. Tüm [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamalar için önbellek yalnızca geçerli sürümü ve daha önce yüklenen sürümü korur.  
  
 Varsayılan olarak, istemci bilgisayarlarda çevrimiçi uygulamalar için 250 MB depolama alanı vardır [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Veri dosyaları bu sınıra doğru sayılmaz. Bir sistem yöneticisi, önbellek boyutunu kilobayt cinsinden ifade eden bir DWORD değeri olan \Software\classes\software\microsoft\windows\currentversion\deployment\onlineappquocontainer KB HKEY_CURRENT_USER kayıt defteri anahtarını değiştirerek bu kotayı belirli bir istemci bilgisayarda büyütebilir veya azaltabilir. Örneğin, önbellek boyutunu 50 MB olarak azaltmak için bu değeri 51200 olarak değiştirirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Uygulamalarında Yerel ve Uzak Veri Erişimi](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
