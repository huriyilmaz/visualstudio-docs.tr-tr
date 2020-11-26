---
title: Birden çok proje bağlantısı üzerinde ayarları uygula
description: Bir toplu işlem yürütmek için bir kaynak denetimi eklentisi kullanarak birden çok proje bağlantısı arasında ayarları uygulamayı öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: cd5b7af98470c1d9a82eb0504c333e74de8c004f
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190115"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Birden çok proje bağlantısı üzerindeki ayarların uygulaması
Kaynak denetimi eklentisi API sürümü 1,2 kullanılarak oluşturulan bir kaynak denetimi eklentisi, birden fazla proje veya birden çok bağlantı bağlamı arasında aynı kaynak denetimi işlemini yürütmek için bir toplu işlem kullanabilir. Toplu işler, Kullanıcı deneyiminden proje başına gereksiz iletişim kutularını ortadan kaldırmak için kullanılabilir.

 Kullanıcı, kaynak denetimi eklentisi API sürümü 1,1 (örneğin, farklı dosya paylaşma makinelerinde iki Web projesi) kullanılarak oluşturulan bir kaynak denetim eklentisinde birden fazla bağlantıya ait birden çok öğeyi seçerse, Kullanıcı aynı iletişim kutusunu sürekli olarak görür. Bu senaryo, Kullanıcı iletişim kutusundaki **Tümüne Uygula** onay kutusuna tıksa bıle, IDE her bir bağlantı bağlamı için durumunu sıfırladığında meydana gelir.

## <a name="new-capability-flag"></a>Yeni yetenek bayrağı
 `SccBeginBatch`İşlevi, `SCC_CAP_BATCH` bir toplu işlemin devam ettiğini göstermek için bayrağı ayarlar.

## <a name="new-functions"></a>Yeni işlevler
Aşağıdaki yeni işlevler Batch işlemini destekler:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

`SCCBeginBatch`İşlevi, kaynak denetimi işlemleri grubunu başlatır. `SccEndBatch`İşlev grubu kapatır. Gruplar iç içe olamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API sürümü 1,2 ' deki yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
