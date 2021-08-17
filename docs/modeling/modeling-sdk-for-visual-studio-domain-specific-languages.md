---
title: Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller
description: Visual Studio için modelleme SDK 'sını kullanarak, Visual Studio tümleştirilebilen güçlü model tabanlı geliştirme araçları oluşturabileceğiniz hakkında bilgi edinin.
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
ms.openlocfilehash: d50d1520bac84674fafb4441618b7118a033a3806d23ade0f8f02d9d1a7c92cb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121385828"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller

Visual Studio için modelleme SDK 'sını kullanarak, Visual Studio tümleştirilebilen güçlü model tabanlı geliştirme araçları oluşturabilirsiniz. Aynı şekilde, bir veya daha fazla model tanımı oluşturabilir ve bir araç kümesiyle tümleştirebilirsiniz.

MSDK'nın merkezinde, iş alanınızdaki kavramları göstermek için oluşturabileceğiniz bir model tanımı bulunur. Modeli diagrammatik görünüm, kod ve diğer yapıtlar oluşturma, modeli dönüştürme komutları ve Visual Studio kod ve diğer nesnelerle etkileşim kurma özelliği gibi çeşitli araçlarla çevreleyebilirsiniz. Modeli geliştirirken, geliştirmenizin merkezine yerleştirilen güçlü bir araç kümesi oluşturmak için onu diğer modellerle birleştirebilirsiniz.

MSDK, etki alanına özgü dil (DSL) biçiminde bir modeli hızlı bir şekilde geliştirmenize olanak sağlar. Graf gösterimli bir şema veya soyut sözdizimi tanımlamak için özelleştirilmiş bir düzenleyici kullanarak başlarsanız. Bu tanımından, VMSDK şunları oluşturur:

- İşlem tabanlı bir depoda çalışan, türü kesin belirlenmiş bir API ile model uygulaması.

- Ağaç tabanlı bir gezgin.

- Kullanıcıların tanımladığınız modeli veya bölümlerini görüntüleyebildiği bir grafik düzenleyici.

- Modellerinizi okunabilir XML biçiminde kaydeden serileştirme yöntemleri.

- Metin şablonu kullanarak program kodu ve diğer yapıları üretmek için olanaklar.

Bu özelliklerin tümünü özelleştirebilir ve genişletebilirsiniz. Uzantılarınız, DSL tanımını hala güncelleştirebileceğiniz ve uzantılarınızı kaybetmeden özellikleri yeniden üretebileceğiniz bir şekilde tümleştirilir.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[İlgili blog gönderileri](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
