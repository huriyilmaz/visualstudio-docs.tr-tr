---
description: Güvenlik konuları nedeniyle, IIS genel bir hata döndürdü.
title: Web sunucusu Istenen kaynağı bulamadı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e0e179cc3d16769d955ff4d3e26a44fedfa99c42
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097211"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Hata: Web Sunucusu İstenilen Kaynağı Bulamadı
Güvenlik konuları nedeniyle, IIS genel bir hata döndürdü.

Olası bir neden sunucunun güvenlik yapılandırması olabilir. IIS 6,0 ve önceki sürümler şüpheli ve hatalı biçimlendirilmiş istekleri filtrelemek için URLScan olarak bilinen bir eklenti programı kullandı. IIS 7,0 ' de aynı amaçla yerleşik Istek filtrelemesi vardır. her iki durumda da aşırı kısıtlayıcı istek filtreleme Visual Studio sunucuda hata ayıklamasını engelleyebilir.

Bu hatanın bir diğer olası nedeni, IIS için W3SVC hizmetinin başlatılmamasına neden olur. Hizmetler penceresinde (*Services. msc*) Bu hizmetin başlatıldığını (gri) denetleyin.

Bu hatanın çok sayıda olası nedeni vardır. En yaygın nedenler, IIS yüklemesi veya yapılandırması, Web sitesi yapılandırması veya dosya sistemindeki izinlerle ilgili bir sorun içerir. Kaynağa bir tarayıcıyla erişmeyi deneyebilirsiniz. IIS 'nin nasıl yapılandırıldığına bağlı olarak, sunucuda yerel bir tarayıcı kullanmanız veya ayrıntılı bir hata iletisi almak için IIS hata günlüğünü incelemeniz gerekebilir.

 IIS sorunlarını giderme hakkında daha fazla bilgi için bkz. [IIS yönetimi ve yönetimi](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).

## <a name="see-also"></a>Ayrıca bkz.
- [Hata: Web sunucusu kilitli ve hata ayıklama fiilini engelliyor](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
