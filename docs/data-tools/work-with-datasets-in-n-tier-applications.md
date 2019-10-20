---
title: N katmanlı uygulamalarda veri kümeleriyle çalışma
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b96f2e51048216388eea50935a1ced536d8d230b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648027"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>N katmanlı uygulamalarda veri kümeleriyle çalışma

*N katmanlı veri uygulamaları* , birden çok mantıksal katmana *(veya katmana*) ayrılan veri merkezli uygulamalardır. Diğer bir deyişle, n katmanlı bir veri uygulaması, veri erişim katmanı, iş mantığı katmanı ve her biri kendi projesindeki sunum katmanı ile birden çok projeye ayrılmış bir uygulamadır. Daha fazla bilgi için bkz. [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md).

Türü belirtilmiş veri kümeleri, TableAdapters ve DataSet sınıflarının ayrı projelerde üretilebilmesi için geliştirilmiştir. Bu, uygulama katmanlarını hızlı bir şekilde ayırma ve n katmanlı veri uygulamaları oluşturma olanağı sağlar.

Türü belirtilmiş veri kümelerinde n katmanlı destek, uygulama mimarisinin n katmanlı bir tasarıma yinelemeli olarak geliştirilmesini sağlar. Ayrıca, kodu birden fazla projeye el ile ayıran gereksinimi ortadan kaldırır. **Veri kümesi Tasarımcısı**kullanarak veri katmanını tasarlamayı başlatın. Uygulama mimarisini n katmanlı bir tasarıma geçmeye hazırsanız, veri kümesi sınıfını ayrı bir projede oluşturmak için veri kümesi **Proje** özelliğini ayarlayın.

## <a name="reference"></a>Başvuru

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Ayrıca bkz.

- [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)
- [İzlenecek yol: n katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [N katmanlı uygulamalarda TableAdapter’lara kod ekleme](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [N katmanlı uygulamalarda veri kümelerine kod ekleme](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [N Katmanlı bir veri kümesine doğrulama ekleme](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Veri kümeleri ile TableAdapter’ları farklı projelere ayırma](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
- [TableAdapter’lar oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md)
- [LINQ to SQL ile N katmanlı ve uzak uygulamalar](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)