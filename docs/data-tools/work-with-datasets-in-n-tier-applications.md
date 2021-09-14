---
title: N katmanlı uygulamalarda veri kümeleriyle çalışma
description: N katmanlı uygulamalarda veri kümeleriyle çalışma hakkında bilgi öğrenin. N katmanlı veri uygulamaları, birden çok mantıksal katmana (veya katmana) ayrılmış veri merkezli uygulamalardır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1b3873b3348c78462943204b02f570a5510e927f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631016"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>N katmanlı uygulamalarda veri kümeleriyle çalışma

*N katmanlı veri uygulamaları,* birden çok mantıksal katmana (veya katmana) ayrılmış veri merkezli *uygulamalardır.* Başka bir deyişle n katmanlı veri uygulaması, veri erişim katmanı, iş mantığı katmanı ve sunum katmanı ile birden çok projeye ayrılmış bir uygulamadır. Daha fazla bilgi için bkz. [N Katmanlı veri uygulamalarına genel bakış.](../data-tools/n-tier-data-applications-overview.md)

TableAdapter'lar ve veri kümesi sınıfları ayrık projelerde oluşturulacak şekilde türe sahip veri kümeleri geliştirilmiştir. Bu, uygulama katmanlarını hızla ayırma ve n katmanlı veri uygulamaları oluşturma olanağı sağlar.

Türü belirtilen veri kümelerde N katmanlı destek, uygulama mimarisinin n katmanlı bir tasarıma iterative olarak geliştirilmesini sağlar. Ayrıca kodu el ile birden fazla projeye ayırma gereksinimini ortadan kaldırır. Veri Kümesi Tasarımcısı kullanarak veri **katmanını tasarlamaya Veri Kümesi Tasarımcısı.** Uygulama mimarisini n katmanlı bir tasarıma almaya hazır olduğunda, veri kümesi sınıfını ayrı bir projede oluşturmak için bir veri Project **DataSet** Project özelliğini ayarlayın.

## <a name="reference"></a>Başvuru

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Ayrıca bkz.

- [N Katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)
- [adım adım kılavuz: N katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [N katmanlı uygulamalarda TableAdapter’lara kod ekleme](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [N katmanlı uygulamalarda veri kümelerini kod ekleme](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [N katmanlı veri kümesine doğrulama ekleme](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Veri kümelerini ve TableAdapter'ları farklı projelere ayırma](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
- [TableAdapter’lar oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md)
- [LINQ to SQL ile N Katmanlı ve uzak LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)
