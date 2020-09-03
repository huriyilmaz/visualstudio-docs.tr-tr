---
title: N katmanlı veri uygulamalarına genel bakış | Microsoft Docs
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
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f124e997669370e71819cf37423d0c2d6a414d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658065"
---
# <a name="n-tier-data-applications-overview"></a>N Katmanlı Veri Uygulamalarına Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N katmanlı * veri uygulamaları *, birden fazla*katmana ayrılan veri uygulamalarıdır. Ayrıca, "dağıtılmış uygulamalar" ve "çok katmanlı uygulamalar" olarak da bilinen n katmanlı uygulamalar, istemci ile sunucu arasında dağıtılan ayrı katmanlara ayrı işlem ayırır. Veriye erişen uygulamalar geliştirirken, uygulamayı oluşturan çeşitli katmanlar arasında açık bir ayrımı olması gerekir.

 Tipik n katmanlı bir uygulama, bir sunum katmanı, orta katman ve veri katmanı içerir. N katmanlı bir uygulamadaki çeşitli katmanları ayırmanın en kolay yolu, uygulamanıza dahil etmek istediğiniz her katman için ayrı projeler oluşturmaktır. Örneğin, sunum katmanı bir Windows Forms uygulaması olabilir, ancak veri erişim mantığı Orta katmanda bulunan bir sınıf kitaplığı olabilir. Ayrıca, sunu katmanı, hizmet gibi bir hizmet aracılığıyla orta katmandaki veri erişim mantığı ile iletişim kurabilir. Uygulama bileşenlerini ayrı katmanlara ayırmak, uygulamanın bakım ve ölçeklenebilirlik düzeyini artırır. Bu, tüm çözümü yeniden tasarlama gereksinimi olmadan tek bir katmana uygulanabilecek yeni teknolojilerin kullanımını daha kolay benimseyerek etkinleştirir. Bunlara ek olarak, n katmanlı uygulamalar genellikle hassas bilgileri Orta katmanda depolar ve bu da sunum katmanından yalıtımı korur.

 Visual Studio, geliştiricilerin n katmanlı uygulamalar oluşturmalarına yardımcı olacak çeşitli özellikler içerir:

- Veri kümesi Tasarımcısı, veri kümesini (veri varlık katmanını) ve s 'yi (veri erişim katmanını) ayrı projelere ayırmanızı sağlayan bir **veri kümesi proje** özelliği sağlar `TableAdapter` .

- [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) , farklı ad alanlarına DataContext ve veri sınıfları oluşturmak için ayarlar sağlar. Bu, veri erişimi ve veri varlığı katmanlarının mantıksal olarak ayrılmasını mümkün bir şekilde sunar.

- [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) , <xref:System.Data.Linq.Table%601.Attach%2A> bir uygulamadaki farklı katmanlardan DataContext 'i bir araya getirmenizi sağlayan yöntemini sağlar. Daha fazla bilgi için, [LINQ to SQL Ile N katmanlı ve uzak uygulamalar](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)bölümüne bakın.

## <a name="presentation-tier"></a>Sunum Katmanı
 *Sunum katmanı* , kullanıcıların bir uygulamayla etkileşimde bulunduğu katmandır. Genellikle ek uygulama mantığı da içerir. Tipik sunum katmanı bileşenleri şunları içerir:

- Ve gibi veri bağlama bileşenleri <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator> .

- Sunum katmanında kullanılmak üzere [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) varlık sınıfları gibi verilerin nesne temsilleri.

  Sunu katmanı genellikle bir hizmet başvurusu (örneğin, bir [Windows Communication Foundation Hizmetleri ve Visual Studio uygulamasındaki WCF veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) ) kullanarak Orta katmana erişir. Sunum katmanı, veri katmanına doğrudan erişemez. Sunum katmanı, orta katmandaki veri erişim bileşeni yoluyla veri katmanıyla iletişim kurar.

## <a name="middle-tier"></a>Orta katman
 *Orta katman* , sunum katmanının ve veri katmanının birbirleriyle iletişim kurmak için kullandığı katmandır. Tipik orta katman bileşenleri şunları içerir:

- İş kuralları ve veri doğrulama gibi iş mantığı.

- Aşağıdakiler gibi veri erişimi bileşenleri ve Logic:

  - [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) ve [DataAdapter ve DataReaders](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

  - [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) varlık sınıfları gibi verilerin nesne temsilleri.

  - Kimlik doğrulama, yetkilendirme ve kişiselleştirme gibi ortak uygulama hizmetleri.

  Aşağıdaki çizimde, Visual Studio 'da bulunan ve n katmanlı bir uygulamanın orta katmanına uyabilecek Özellikler ve teknolojiler gösterilmektedir.

  ![Orta katman bileşenleri](../data-tools/media/ntiermid.png "NtierMid") Orta katman

  Orta katman tipik olarak veri katmanına veri bağlantısı kullanarak bağlanır. Bu veri bağlantısı genellikle veri erişimi bileşeninde depolanır.

## <a name="data-tier"></a>Veri Katmanı
 *Veri katmanı* temel olarak bir uygulamanın verilerini depolayan bir sunucu (örneğin, çalıştıran bir sunucu [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ).

 Aşağıdaki çizimde, Visual Studio 'da bulunan ve n katmanlı bir uygulamanın veri katmanına uyabilecek Özellikler ve teknolojiler gösterilmektedir.

 ![Veri katmanı bileşenleri](../data-tools/media/ntierdatatier.png "ntierdatatier") Veri katmanı

 Veri katmanına, sunu katmanındaki istemciden doğrudan erişilemez. Bunun yerine, orta katmandaki veri erişim bileşeni, sunum ve veri katmanları arasındaki iletişim için kullanılır.

## <a name="help-for-n-tier-development"></a>N katmanlı geliştirme için yardım
 Aşağıdaki konular, n katmanlı uygulamalarla çalışma hakkında bilgi sağlar:

 [Veri kümelerini ve TableAdapters farklı projelere ayır](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

 [İzlenecek Yol: N Katmanlı Bir Veri Uygulaması Oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

 [İzlenecek yol: N katmanlı bir veri uygulamasına doğrulama ekleme](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)

 [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Data.Linq.ITable.Attach%2A>[Izlenecek yol: Visual Studio 'Da N katmanlı veri uygulaması](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md) veri [kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md) oluşturma [Visual Studio 'da verilere erişme](../data-tools/accessing-data-in-visual-studio.md)
