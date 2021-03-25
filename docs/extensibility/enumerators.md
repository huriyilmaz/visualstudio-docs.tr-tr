---
title: Numaralandırıcılar | Microsoft Docs
description: Kaynak denetimi eklentisi API 'sindeki, komut kodu, Ileti, dosya durum kodu ve Dizin durum kodu gibi Numaralandırıcı veri türleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0bdc42901cbdad3b30bb6739ec93b8979b0d56ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075282"
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
