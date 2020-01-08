---
title: Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller
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
ms.openlocfilehash: 2abb209943ff14969f71ebdca6982020f30a5d47
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590208"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller

Visual Studio için modelleme SDK'sını kullanarak Visual Studio ile tümleştirebileceğiniz model tabanlı güçlü geliştirme araçları oluşturabilirsiniz. Aynı şekilde, bir veya daha fazla model tanımı oluşturabilir ve bir araç kümesiyle tümleştirebilirsiniz.

MSDK'nın merkezinde, iş alanınızdaki kavramları göstermek için oluşturabileceğiniz bir model tanımı bulunur. Araçlar, bir grafiksel görünüm, kod ve diğer yapıtları, modeli dönüştürmek için komutlar oluşturulacak özelliği ve kod ve Visual Studio'daki diğer nesnelerle etkileşme yeteneği gibi çeşitli modeliyle çevreleyebilirsiniz. Modeli geliştirirken, geliştirmenizin merkezine yerleştirilen güçlü bir araç kümesi oluşturmak için onu diğer modellerle birleştirebilirsiniz.

MSDK, etki alanına özgü dil (DSL) biçiminde bir modeli hızlı bir şekilde geliştirmenize olanak sağlar. Graf gösterimli bir şema veya soyut sözdizimi tanımlamak için özelleştirilmiş bir düzenleyici kullanarak başlarsanız. Bu tanımından, VMSDK şunları oluşturur:

- İşlem tabanlı bir depoda çalışan, türü kesin belirlenmiş bir API ile model uygulaması.

- Ağaç tabanlı bir gezgin.

- Kullanıcıların tanımladığınız modeli veya bölümlerini görüntüleyebildiği bir grafik düzenleyici.

- Modellerinizi okunabilir XML biçiminde kaydeden serileştirme yöntemleri.

- Metin şablonu kullanarak program kodu ve diğer yapıları üretmek için olanaklar.

Bu özelliklerin tümünü özelleştirebilir ve genişletebilirsiniz. Uzantılarınız, DSL tanımını hala güncelleştirebileceğiniz ve uzantılarınızı kaybetmeden özellikleri yeniden üretebileceğiniz bir şekilde tümleştirilir.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[İlgili blog gönderileri](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
