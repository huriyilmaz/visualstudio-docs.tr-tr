---
title: Birden çok proje bağlantısı üzerinde ayarları uygula
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
ms.openlocfilehash: 5c88a5140bf72f6801d4c7a92ebd910f410aabfb
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741520"
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
