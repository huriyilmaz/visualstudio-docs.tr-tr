---
title: "CA2004: GC 'ye çağrıları kaldırın. Canlı tutma | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e34a8e7d4860a599155554410e13df5a6eb3bfe1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672487"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: GC.KeepAlive'a çağrıları kaldırın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Kategori|Microsoft. güvenilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Sınıflar `SafeHandle` kullanır, ancak yine de `GC.KeepAlive` çağrıları içerir.

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 kullanımı için dönüştürüyorsanız, tüm `GC.KeepAlive` (nesne) çağrılarını kaldırın. Bu durumda sınıfların `GC.KeepAlive` çağırmak zorunda olmaması gerekir. Bu, sonlandırıcılara sahip olmadıkları, ancak işletim sistemi tanıtıcısını tamamlaması için `SafeHandle` ' i kullanan bir.  @No__t_0 çağrısında bırakma maliyeti performansa göre ölçülebilse de, `GC.KeepAlive` bir çağrının gerekli olduğunu veya artık mevcut olmayan bir yaşam süresi sorununu gidermek için yeterli olması gerektiğini belirten bir durum, kodun bakımını daha zor hale getirir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 @No__t_0 çağrılarını kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu uyarıyı yalnızca sınıfınızın `SafeHandle` ' a dönüştürmek için teknik olarak doğru değilse gizleyebilirsiniz.
