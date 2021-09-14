---
title: Yönetilen kod için Genelleştirme Kuralları kural kümesi
ms.date: 11/04/2016
description: Visual Studio, diller, yerel ayarlar ve kültürler ile ilgili sorunlara odaklanan genelleştirme kuralları kural kümesi hakkında bilgi edinin. Bkz. kural açıklamaları.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 74c0740faaf016e27a1a3824e728821f5d3c6d73
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632000"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Yönetilen kod için Genelleştirme Kuralları kural kümesi

Uygulamanızdaki verilerin farklı dillerde, yerel ayarlarda ve kültürlerde doğru görünmesini engelleyebilecek sorunlara odaklanmak için Microsoft Genelleştirme kuralları kural kümesini kullanın. Uygulamanız yerelleştirilmiş, Genelleştirilmiş veya her ikisi de varsa, bu kural kümesini eklemeniz gerekir.

|Kural|Description|
|----------|-----------------|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Harfleri yerelleştirilmiş parametreler olarak göndermeyin|
|[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304)|CultureInfo belirt|
|[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305)|IFormatProvider belirt|
|[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307)|Açıklık için StringComparison belirtin|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Dizeleri büyük harfe normalleştirin|
|[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309)|Sıralı StringComparison kullanın|
|[CA1310](/dotnet/fundamentals/code-analysis/quality-rules/ca1310)|Doğruluk için StringComparison belirtin|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|P/Invoke dize bağımsız değişkenleri için sıralama belirtin|
