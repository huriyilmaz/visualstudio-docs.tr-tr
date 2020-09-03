---
title: 'CA2228: serbest bırakılmamış kaynak biçimlerini teslim etme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4adcae1c1cc616cdbcf5a7aa15342d221c2f4300
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540588"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Yayımlanmamış kaynak biçimlerini yollamayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir kaynak dosyası, şu anda desteklenmeyen bir sürümü kullanılarak oluşturuldu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="rule-description"></a>Kural Tanımı
 Yayın öncesi sürümleri kullanılarak oluşturulan kaynak dosyaları, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .NET Framework desteklenen sürümleri tarafından kullanılamayabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, bir k sürümünün desteklenen bir sürümünü kullanarak kaynağı oluşturun [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.
