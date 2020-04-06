---
title: Birden Çok Proje Bağlantısı Arasında Ayarların Uygulanması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcaed0f7f2380dd36bcbffd776839025fe9efa16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710054"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Ayarların birden çok proje bağlantısı arasında uygulanması
Kaynak Denetimi Eklentisi API Sürüm 1.2 kullanılarak oluşturulmuş bir kaynak denetim eklentisi, aynı kaynak denetimi işlemini birden çok proje veya birden çok bağlantı bağlamında yürütmek için bir toplu iş leyebilir. Toplu iş, kullanıcı deneyiminden gereksiz, proje başına iletişim kutularını ortadan kaldırmak için kullanılabilir.

 Bir kullanıcı Kaynak Denetimi Eklentisi API Sürüm 1.1 (örneğin, farklı dosya paylaşım lı makinelerde iki web projesi) kullanılarak oluşturulmuş bir kaynak denetim eklentisinde birden fazla bağlantıya ait birden çok öğe seçer ve bunları denetlerse, kullanıcı aynı iletişim kutusunu tekrar tekrar görür. IDE her bağlantı bağlamı için durumunu sıfırladığı için, kullanıcı iletişim kutusundaki Tüm onay **kutusuna Uygula'yı** tıklatsa bile bu senaryo oluşur.

## <a name="new-capability-flag"></a>Yeni yetenek bayrağı
 İşlev, `SccBeginBatch` `SCC_CAP_BATCH` bir toplu iş işleminin devam ettiğini belirtmek için bayrağı ayarlar.

## <a name="new-functions"></a>Yeni işlevler
Aşağıdaki yeni işlevler toplu işleyişi destekler:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

İşlev `SCCBeginBatch` bir kaynak denetim işlemleri grubu başlatır. İşlev `SccEndBatch` grubu kapatır. Gruplar iç içe geçmeyebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API Sürüm 1.2'deki yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
