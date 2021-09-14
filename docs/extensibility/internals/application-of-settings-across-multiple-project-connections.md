---
title: Ayarları birden çok proje bağlantısına uygulama
description: Toplu işlem yürütmek için kaynak denetimi eklentisini kullanarak ayarları birden çok proje bağlantısına nasıl uygulayacaklarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 21c1486855dba6906937f95f10cae2f323ff0383
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726932"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Ayarların birden çok proje bağlantısı arasında uygulaması
Kaynak Denetimi Eklentisi API'si Sürüm 1.2 kullanılarak yerleşik bir kaynak denetimi eklentisi, birden çok proje veya birden çok bağlantı bağlamında aynı kaynak denetimi işlemini yürütmek için bir toplu işlem kullanabilir. Toplu işler, kullanıcı deneyiminden yedekli, proje başına iletişim kutularını ortadan kaldırmak için kullanılabilir.

 Bir kullanıcı, Kaynak Denetimi Eklentisi API'si Sürüm 1.1 (örneğin, farklı dosya paylaşımı makinelerinde iki web projesi) kullanılarak bir kaynak denetimi eklentisinde birden fazla bağlantıya ait birden çok öğe seçerse ve bunları denetlerse, kullanıcı aynı iletişim kutusunu tekrar tekrar görür. Bu senaryo, IDE her  bağlantı bağlamı için durumunu sıfırlayana kadar kullanıcı iletişim kutusundaki Tüm Kullanıcılara Uygula onay kutusuna tıklasa bile oluşur.

## <a name="new-capability-flag"></a>Yeni yetenek bayrağı
 İşlev, `SccBeginBatch` bir toplu işlem devam ediyor olduğunu belirtmek için `SCC_CAP_BATCH` bayrağını ayarlar.

## <a name="new-functions"></a>Yeni işlevler
Aşağıdaki yeni işlevler toplu işlemi destekler:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

işlevi `SCCBeginBatch` bir kaynak denetimi işlemleri grubu başlatır. işlevi `SccEndBatch` grubu kapatır. Gruplar iç içe geçmiş olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API'si Sürüm 1.2'de neler var?](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
