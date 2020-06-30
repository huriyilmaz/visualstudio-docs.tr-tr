---
title: 'CA1308: dizeleri büyük harfe Normalleştir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c068fcda7d03ae91435c040d2110d632668d832a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538742"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Dizeleri büyük harfe normalleştirin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir işlem, dizeyi küçük harfe normalleştirir.

## <a name="rule-description"></a>Kural Tanımı
 Dizeler büyük harfe normalleştirilmeli. Küçük bir karakter grubu, küçük harfe dönüştürüldüğünde, gidiş dönüş yapamaz. Gidiş dönüş yapmak için, karakterleri farklı bir yerel ayara dönüştürmek için karakter verilerinin farklı bir yerel ayara dönüştürülmesi ve sonra özgün karakterlerin dönüştürülmüş karakterlerden doğru şekilde alınması anlamına gelir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Dizelerin büyük harfe dönüştürülmesi için dizeleri küçük harfe dönüştüren işlemleri değiştirin. Örneğin, olarak değiştirin `String.ToLower(CultureInfo.InvariantCulture)` `String.ToUpper(CultureInfo.InvariantCulture)` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Sonuca göre güvenlik kararı verirken (örneğin, Kullanıcı arabiriminde görüntülerken) bir uyarı iletisini gizlemek güvenlidir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Genelleştirme Uyarıları](../code-quality/globalization-warnings.md)
