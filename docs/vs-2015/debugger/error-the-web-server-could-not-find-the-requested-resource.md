---
title: 'Hata: Web sunucusu Istenen kaynağı bulamadı | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 555bb56ee84b7bc48f6b6453c11daef366f97e49
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845125"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Hata: Web Sunucusu İstenilen Kaynağı Bulamadı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Güvenlik konuları nedeniyle, IIS genel bir hata döndürdü.  
  
 Olası bir neden sunucunun güvenlik yapılandırması olabilir. IIS 6,0 ve önceki sürümler şüpheli ve hatalı biçimlendirilmiş istekleri filtrelemek için URLScan olarak bilinen bir eklenti programı kullandı. IIS 7,0 ' de aynı amaçla yerleşik Istek filtrelemesi vardır. Her iki durumda da aşırı kısıtlayıcı istek filtreleme, Visual Studio 'Nun sunucuda hata ayıklamasını engelleyebilir.  
  
 Bu hatanın çok sayıda olası nedeni vardır. En yaygın nedenler, IIS yüklemesi veya yapılandırması, Web sitesi yapılandırması veya dosya sistemindeki izinlerle ilgili bir sorun içerir. Kaynağa bir tarayıcıyla erişmeyi deneyebilirsiniz. IIS 'nin nasıl yapılandırıldığına bağlı olarak, sunucuda yerel bir tarayıcı kullanmanız veya ayrıntılı bir hata iletisi almak için IIS hata günlüğünü incelemeniz gerekebilir.  
  
 IIS sorunlarını giderme hakkında daha fazla bilgi için bkz. [IIS yönetimi ve yönetimi](https://www.iis.net/learn/manage/provisioning-and-managing-iis/iis-management-and-administration).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [URLScan güvenlik aracı](/iis/extensions/working-with-urlscan/urlscan-3-reference)   
 [Hata: Web Sunucusu Kilitli ve DEBUG Fiilini Engelliyor](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
