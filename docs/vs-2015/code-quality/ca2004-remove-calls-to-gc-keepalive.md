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
ms.openlocfilehash: 53fa5f61cb7c503502956831452bc3eca1a9fece
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521205"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: GC.KeepAlive'a çağrıları kaldırın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Kategori|Microsoft. güvenilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Sınıflar kullanır, `SafeHandle` ancak yine de çağrıları içerir `GC.KeepAlive` .

## <a name="rule-description"></a>Kural Tanımı
 Kullanım alanına dönüştürüyorsanız `SafeHandle` tüm `GC.KeepAlive` (nesne) çağrılarını kaldırın. Bu durumda, `GC.KeepAlive` bir sonlandırıcısının olmadığı varsayıldığında, ancak `SafeHandle` işletim sistemi tanıtıcısını tamamlamaya yönelik açık olan, bu durumda sınıfların çağrı yapması gerekmez.  Bir çağrıda bırakma maliyeti `GC.KeepAlive` performansa göre ölçülerek göz ardı edilebilir olsa da, bir çağrının, `GC.KeepAlive` artık mevcut olmayan bir yaşam süresi sorununu gidermek için gerekli veya yeterli olması, kodun bakımını daha zor hale getirir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Çağrıları kaldırın `GC.KeepAlive` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu uyarıyı yalnızca sınıfınızın kullanımına dönüştürmek için teknik olarak doğru değilse gizleyebilirsiniz `SafeHandle` .
