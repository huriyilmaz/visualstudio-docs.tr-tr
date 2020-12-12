---
title: Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller
description: Visual Studio için modelleme SDK 'sını kullanarak Visual Studio ile tümleştirebileceğinizi güçlü model tabanlı geliştirme araçları oluşturabileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a032e5f6b3f9eda302f65a4d04b196ef55a225f6
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360786"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller

Visual Studio için modelleme SDK 'sını kullanarak, Visual Studio ile tümleştirebileceğinizi güçlü model tabanlı geliştirme araçları oluşturabilirsiniz. Aynı şekilde, bir veya daha fazla model tanımı oluşturabilir ve bir araç kümesiyle tümleştirebilirsiniz.

MSDK'nın merkezinde, iş alanınızdaki kavramları göstermek için oluşturabileceğiniz bir model tanımı bulunur. Modeli diagrammatik görünüm, kod ve diğer yapıtlar oluşturma özelliği, modeli dönüştürme komutları ve Visual Studio 'da kod ve diğer nesnelerle etkileşim kurma gibi çeşitli araçlarla çevreleyebilirsiniz. Modeli geliştirirken, geliştirmenizin merkezine yerleştirilen güçlü bir araç kümesi oluşturmak için onu diğer modellerle birleştirebilirsiniz.

MSDK, etki alanına özgü dil (DSL) biçiminde bir modeli hızlı bir şekilde geliştirmenize olanak sağlar. Graf gösterimli bir şema veya soyut sözdizimi tanımlamak için özelleştirilmiş bir düzenleyici kullanarak başlarsanız. Bu tanımından, VMSDK şunları oluşturur:

- İşlem tabanlı bir depoda çalışan, türü kesin belirlenmiş bir API ile model uygulaması.

- Ağaç tabanlı bir gezgin.

- Kullanıcıların tanımladığınız modeli veya bölümlerini görüntüleyebildiği bir grafik düzenleyici.

- Modellerinizi okunabilir XML biçiminde kaydeden serileştirme yöntemleri.

- Metin şablonu kullanarak program kodu ve diğer yapıları üretmek için olanaklar.

Bu özelliklerin tümünü özelleştirebilir ve genişletebilirsiniz. Uzantılarınız, DSL tanımını hala güncelleştirebileceğiniz ve uzantılarınızı kaybetmeden özellikleri yeniden üretebileceğiniz bir şekilde tümleştirilir.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[İlgili blog gönderileri](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
