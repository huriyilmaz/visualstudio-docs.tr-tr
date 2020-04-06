---
title: Sayısalatörler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee48d064612e5519d5ad7e5eaf04de6c5a697837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711851"
---
# <a name="enumerators"></a>Numaralandırıcılar
Bu bölümde, Kaynak Denetimi Eklentisi API'sindeki kaynak denetimi eklentisinin bilmesi gereken yerlandırıcı veri türleri listelenebilmelidir.

## <a name="in-this-section"></a>Bu bölümde
- [Komut kodu](../extensibility/command-code-enumerator.md) [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) ve [SccPopulateList](../extensibility/sccpopulatelist-function.md) işlevleri için seçenekleri listeler.

- [İleti](../extensibility/message-enumerator.md) Yazıcı geri araması, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)için kullanılan bayrakları listeler.

- [Dosya durum kodu](../extensibility/file-status-code-enumerator.md) Kaynak denetimi altındaki bir dosyanın durumunu belirten adlandırılmış sabit değerleri içerir.

- [Dizin durum kodu](../extensibility/directory-status-code-enumerator.md) Kaynak denetimi altında bir dizinin durumunu belirten adlandırılmış sabit değerleri içerir.

## <a name="related-sections"></a>İlgili bölümler
- [Kaynak kontrol eklentisi oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md) Kaynak Denetim Eklentisi SDK'yı tanımlar ve eklenen kaynakları açıklar.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Verilen komut için gelişmiş seçenekler için kullanıcı ister.

- [SccPopulateListesi](../extensibility/sccpopulatelist-function.md) Geçerli durumları için dosyaların listesini inceler. Buna ek olarak, bir dosya için ölçütleri eşleşmiyor zaman arayan bildirmek için `pfnPopulate` işlevi `nCommand`kullanır.

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) IDE aracılığıyla kaynak denetim eklentisinden gelen iletileri görüntülemek için [SccOpenProject](../extensibility/sccopenproject-function.md) tarafından kullanılan geri arama işlevini açıklar.

- [Kaynak kontrol eklentileri](../extensibility/source-control-plug-ins.md) Kaynak Denetimi Eklentisi API'sindeki tüm öğelerin tam bir listesini sağlar.
