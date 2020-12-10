---
title: Numaralandırıcılar | Microsoft Docs
description: Kaynak denetimi eklentisi API 'sindeki, komut kodu, Ileti, dosya durum kodu ve Dizin durum kodu gibi Numaralandırıcı veri türleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 55e124ce3d36e2b23ef53c376b660de05cd87043
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995817"
---
# <a name="enumerators"></a>Numaralandırıcılar
Bu bölüm, kaynak denetimi eklentisinin hakkında bilgi sahibi olması gereken kaynak denetimi eklentisi API 'sindeki Numaralandırıcı veri türlerini listeler.

## <a name="in-this-section"></a>Bu bölümde
- [Komut kodu](../extensibility/command-code-enumerator.md) [Sccgetcommandooptıons](../extensibility/sccgetcommandoptions-function.md) ve [SccPopulateList](../extensibility/sccpopulatelist-function.md) işlevlerinin seçeneklerini numaralandırır.

- [İleti](../extensibility/message-enumerator.md) PRINT callback, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)için kullanılan bayrakları numaralandırır.

- [Dosya durum kodu](../extensibility/file-status-code-enumerator.md) Kaynak denetimi altındaki bir dosyanın durumunu belirten adlandırılmış sabit değerleri içerir.

- [Dizin durum kodu](../extensibility/directory-status-code-enumerator.md) Kaynak denetimi altındaki bir dizinin durumunu belirten adlandırılmış sabit değerleri içerir.

## <a name="related-sections"></a>İlgili bölümler
- [Kaynak denetimi eklentisi oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md) Kaynak denetimi eklentisi SDK 'sını tanımlar ve dahil edilen kaynakları açıklar.

- [Sccgetcommandoseçenekler](../extensibility/sccgetcommandoptions-function.md) Kullanıcıdan verilen komutla ilgili gelişmiş seçenekleri ister.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Geçerli durumları için dosya listesini inceler. Ayrıca, `pfnPopulate` bir dosya ile ilgili ölçütlerle eşleşmediği zaman, çağrıyı yapana bildirmek için işlevini kullanır `nCommand` .

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) IDE aracılığıyla kaynak denetimi eklentisindeki iletileri göstermek için [SccOpenProject](../extensibility/sccopenproject-function.md) tarafından kullanılan geri çağırma işlevini açıklar.

- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md) Kaynak denetimi eklentisi API 'sindeki tüm öğelerin tam bir listesini sağlar.
