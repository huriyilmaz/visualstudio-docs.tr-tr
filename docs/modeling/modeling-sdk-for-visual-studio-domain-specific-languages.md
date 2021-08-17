---
title: Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller
description: Visual Studio için Modelleme SDK'sı'Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 00e140b3191ef6d40fbd0ee519580dee46345e17
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047822"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller

Visual Studio sdk'sı için Modelleme SDK'sı kullanarak, bu sdk'larla tümleştirerek güçlü model tabanlı geliştirme Visual Studio. Aynı şekilde, bir veya daha fazla model tanımı oluşturabilir ve bir araç kümesiyle tümleştirebilirsiniz.

MSDK'nın merkezinde, iş alanınızdaki kavramları göstermek için oluşturabileceğiniz bir model tanımı bulunur. Modeli diyagram görünümü, kod oluşturma ve diğer yapıtlar oluşturma, modeli dönüştürme komutları ve kodla ve diğer nesnelerle etkileşim kurma gibi çeşitli araçlarla çevre Visual Studio. Modeli geliştirirken, geliştirmenizin merkezine yerleştirilen güçlü bir araç kümesi oluşturmak için onu diğer modellerle birleştirebilirsiniz.

MSDK, etki alanına özgü dil (DSL) biçiminde bir modeli hızlı bir şekilde geliştirmenize olanak sağlar. Graf gösterimli bir şema veya soyut sözdizimi tanımlamak için özelleştirilmiş bir düzenleyici kullanarak başlarsanız. Bu tanımından, VMSDK şunları oluşturur:

- İşlem tabanlı bir depoda çalışan, türü kesin belirlenmiş bir API ile model uygulaması.

- Ağaç tabanlı bir gezgin.

- Kullanıcıların tanımladığınız modeli veya bölümlerini görüntüleyebildiği bir grafik düzenleyici.

- Modellerinizi okunabilir XML biçiminde kaydeden serileştirme yöntemleri.

- Metin şablonu kullanarak program kodu ve diğer yapıları üretmek için olanaklar.

Bu özelliklerin tümünü özelleştirebilir ve genişletebilirsiniz. Uzantılarınız, DSL tanımını hala güncelleştirebileceğiniz ve uzantılarınızı kaybetmeden özellikleri yeniden üretebileceğiniz bir şekilde tümleştirilir.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[İlgili blog gönderileri](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
