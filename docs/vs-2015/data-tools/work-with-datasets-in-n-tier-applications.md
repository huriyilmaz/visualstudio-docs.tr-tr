---
title: N katmanlı uygulamalarda veri kümeleriyle çalışma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f7be307ec94b15871da20ace8055fc7121d5d92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657809"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>N katmanlı uygulamalarda veri kümeleriyle çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N katmanlı veri uygulamaları * birden çok mantıksal katmana *(veya katmana*) ayrılan veri merkezli uygulamalardır. Diğer bir deyişle, n katmanlı bir veri uygulaması, veri erişim katmanı, iş mantığı katmanı ve her biri kendi projesindeki sunum katmanı ile birden çok projeye ayrılmış bir uygulamadır. Daha fazla bilgi için bkz. [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md).

 Türü belirtilmiş veri kümeleri, TableAdapters ve DataSet sınıflarının ayrı projelerde üretilebilmesi için geliştirilmiştir. Bu, uygulama katmanlarını hızlı bir şekilde ayırma ve n katmanlı veri uygulamaları oluşturma olanağı sağlar.

 Türü belirtilmiş veri kümelerinde n katmanlı destek, uygulama mimarisinin n katmanlı bir tasarıma yinelemeli olarak geliştirilmesini sağlar. Ayrıca, kodu birden fazla projeye el ile ayıran gereksinimi ortadan kaldırır. Veri Kümesi Tasarımcısı kullanarak veri katmanını tasarlamayı başlatın. Uygulama mimarisini n katmanlı bir tasarıma geçmeye hazırsanız, veri kümesi sınıfını ayrı bir projede oluşturmak için veri kümesi **Proje** özelliğini ayarlayın.

## <a name="in-this-section"></a>Bu Bölümde
 [Veri kümelerini ve TableAdapters farklı projelere ayır](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md) Oluşturulan veri kümesi sınıfının oluşturulan TableAdapter sınıflarını içeren projenin dışına ve yeni bir projeye nasıl taşınacağını açıklar.

 [N katmanlı uygulamalarda TableAdapters 'e kod ekleme](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md) N katmanlı bir TableAdapter için kodun eklenebileceği kısmi bir sınıfın nasıl oluşturulacağını açıklar.

 [N katmanlı uygulamalardaki veri kümelerine kod ekleme](../data-tools/add-code-to-datasets-in-n-tier-applications.md) N katmanlı veri kümesi için kodun eklenebileceği kısmi bir sınıfın nasıl oluşturulacağını açıklar.

 [N katmanlı bir veri kümesine doğrulama ekleme](../data-tools/add-validation-to-an-n-tier-dataset.md) Değişen verilerde doğrulama gerçekleştirmek için kodun nereye ekleneceğini açıklar.

 [Izlenecek yol: N katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md) Türü belirtilmiş bir veri kümesi oluşturmak ve TableAdapter ve dataset kodunu birden çok projeye ayırmak için adım adım yönergeler sağlar.

 [Izlenecek yol: N katmanlı bir veri uygulamasına doğrulama ekleme](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265) N katmanlı veri uygulaması gözden geçirmesinde oluşturulan uygulamaya doğrulama eklemek için adım adım yönergeler sağlar.

## <a name="reference"></a>Başvuru
 <xref:System.Data.DataSet>

 <xref:System.Data.TypedTableBase%601>

## <a name="related-sections"></a>İlgili Bölümler

- [N Katmanlı Veri Uygulamalarına Genel Bakış](../data-tools/n-tier-data-applications-overview.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)