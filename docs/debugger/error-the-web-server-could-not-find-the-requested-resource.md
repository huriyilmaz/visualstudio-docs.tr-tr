---
description: Güvenlikle ilgili dikkat edilmesi gerekenler nedeniyle IIS genel bir hata döndürür.
title: Web Sunucusu İstenen Kaynak Kaynağını | Microsoft Docs
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
ms.openlocfilehash: 00d59b08a98a66afce7ddbeb5f78d6e5d5f90c0734e74777f9c24cbc8132f98f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419981"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Hata: Web Sunucusu İstenilen Kaynağı Bulamadı
Güvenlikle ilgili dikkat edilmesi gerekenler nedeniyle IIS genel bir hata döndürür.

Olası nedenlerinden biri sunucunun güvenlik yapılandırmasıdır. IIS 6.0 ve önceki sürümler, şüpheli ve yanlış biçimlendirilmiş istekleri filtrelemek için URLScan olarak bilinen bir eklenti programı kullandı. IIS 7.0'da aynı amaç için yerleşik İstek Filtrelemesi vardır. Her iki durumda da aşırı kısıtlayıcı istek filtrelemesi, Visual Studio hata ayıklamasını önlenebilir.

Bu hatanın bir diğer olası nedeni, IIS için W3SVC hizmetinin başlatımamadır. Bu hizmetin Hizmetler penceresinde *(services.msc ) başlatıla (gri renkte) olduğunu kontrol edin.*

Bu hatanın çok sayıda ek olası nedeni vardır. En yaygın nedenlerden bazıları IIS yüklemesi veya yapılandırması, web sitesi yapılandırması veya dosya sistemi izinleri ile ilgili bir sorundur. Kaynağa bir tarayıcı ile erişmeyi ebilirsiniz. IIS'nin nasıl yapılandırıldıklarına bağlı olarak, sunucuda yerel bir tarayıcı kullanmak veya ayrıntılı bir hata iletisi almak için IIS hata günlüğünü incelemeniz gerekir.

 IIS sorunlarını giderme hakkında daha fazla bilgi için bkz. [IIS Yönetimi ve Yönetimi.](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration)

## <a name="see-also"></a>Ayrıca bkz.
- [Hata: Web Sunucusu Kilitlendi ve DEBUG Fiilini Engelliyor](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
