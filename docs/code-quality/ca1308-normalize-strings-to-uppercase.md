---
title: 'CA1308: Dizeleri büyük harfe normalleştirin'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a217e3882cbf90365f507623347a3846ed30187a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444312"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Dizeleri büyük harfe normalleştirin

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Kategori|Microsoft. Globalization|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
Bir işlem, dizeyi küçük harfe normalleştirir.

## <a name="rule-description"></a>Kural açıklaması
Dizeler büyük harfe normalleştirilmeli. Küçük bir karakter grubu, küçük harfe dönüştürüldüğünde, gidiş dönüş yapamaz. Gidiş dönüş yapmak için, karakterleri farklı bir yerel ayara dönüştürmek için karakter verilerinin farklı bir yerel ayara dönüştürülmesi ve sonra özgün karakterlerin dönüştürülmüş karakterlerden doğru şekilde alınması anlamına gelir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Dizelerin büyük harfe dönüştürülmesi için dizeleri küçük harfe dönüştüren işlemleri değiştirin. Örneğin, `String.ToLower(CultureInfo.InvariantCulture)` ' ı `String.ToUpper(CultureInfo.InvariantCulture)` ' e değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Sonuca göre güvenlik kararı verirken (örneğin, Kullanıcı arabiriminde görüntülerken) bir uyarı iletisini gizlemek güvenlidir.

## <a name="see-also"></a>Ayrıca bkz.
[Genelleştirme Uyarıları](../code-quality/globalization-warnings.md)
