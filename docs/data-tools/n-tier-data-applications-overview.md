---
title: N Katmanlı Veri Uygulamalarına Genel Bakış
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 80b6f89d9c074d7d17c258263c03e97334e6fd90
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648271"
---
# <a name="n-tier-data-applications-overview"></a>N katmanlı veri uygulamalarına genel bakış
*N katmanlı* veri uygulamaları *, birden fazla*katmana ayrılan veri uygulamalarıdır. Ayrıca, "dağıtılmış uygulamalar" ve "çok katmanlı uygulamalar" olarak da bilinen n katmanlı uygulamalar, istemci ile sunucu arasında dağıtılan ayrı katmanlara ayrı işlem ayırır. Veriye erişen uygulamalar geliştirirken, uygulamayı oluşturan çeşitli katmanlar arasında açık bir ayrımı olması gerekir.

Tipik n katmanlı bir uygulama, bir sunum katmanı, orta katman ve veri katmanı içerir. N katmanlı bir uygulamadaki çeşitli katmanları ayırmanın en kolay yolu, uygulamanıza dahil etmek istediğiniz her katman için ayrı projeler oluşturmaktır. Örneğin, sunum katmanı bir Windows Forms uygulaması olabilir, ancak veri erişim mantığı Orta katmanda bulunan bir sınıf kitaplığı olabilir. Ayrıca, sunu katmanı, bir Web hizmeti gibi bir hizmet aracılığıyla orta katmandaki veri erişim mantığı ile iletişim kurabilir. Uygulama bileşenlerini ayrı katmanlara ayırmak, uygulamanın bakım ve ölçeklenebilirlik düzeyini artırır. Bu, tüm çözümü yeniden tasarlama gereksinimi olmadan tek bir katmana uygulanabilecek yeni teknolojilerin kullanımını daha kolay benimseyerek etkinleştirir. Bunlara ek olarak, n katmanlı uygulamalar genellikle hassas bilgileri Orta katmanda depolar ve bu da sunum katmanından yalıtımı korur.

Visual Studio, geliştiricilerin n katmanlı uygulamalar oluşturmalarına yardımcı olacak çeşitli özellikler içerir:

- Veri kümesi, veri kümesini (veri varlık katmanını) ve TableAdapters (veri erişim katmanı) ayrı projelere ayırmanızı sağlayan bir **veri kümesi proje** özelliği sağlar.

- [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) , farklı ad alanlarına DataContext ve veri sınıfları oluşturmak için ayarlar sağlar. Bu, veri erişimi ve veri varlığı katmanlarının mantıksal olarak ayrılmasını mümkün bir şekilde sunar.

- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) , bir uygulamadaki farklı katmanlardan DataContext 'i bir araya getirmenize olanak tanıyan <xref:System.Data.Linq.Table%601.Attach%2A> yöntemi sağlar. Daha fazla bilgi için, [LINQ to SQL Ile N katmanlı ve uzak uygulamalar](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)bölümüne bakın.

## <a name="presentation-tier"></a>Sunum katmanı
*Sunum katmanı* , kullanıcıların bir uygulamayla etkileşimde bulunduğu katmandır. Genellikle ek uygulama mantığı da içerir. Tipik sunum katmanı bileşenleri şunları içerir:

- @No__t_0 ve <xref:System.Windows.Forms.BindingNavigator> gibi veri bağlama bileşenleri.

- Sunum katmanında kullanılmak üzere [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) varlık sınıfları gibi verilerin nesne temsilleri.

Sunu katmanı genellikle bir hizmet başvurusu (örneğin, bir [Windows Communication Foundation Hizmetleri ve Visual Studio uygulamasındaki WCF veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) ) kullanarak Orta katmana erişir. Sunum katmanı, veri katmanına doğrudan erişemez. Sunum katmanı, orta katmandaki veri erişim bileşeni yoluyla veri katmanıyla iletişim kurar.

## <a name="middle-tier"></a>Orta katman
*Orta katman* , sunum katmanının ve veri katmanının birbirleriyle iletişim kurmak için kullandığı katmandır. Tipik orta katman bileşenleri şunları içerir:

- İş kuralları ve veri doğrulama gibi iş mantığı.

- Aşağıdakiler gibi veri erişimi bileşenleri ve Logic:

  - [TableAdapters](create-and-configure-tableadapters.md) ve [DataAdapter ve DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

  - [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) varlık sınıfları gibi verilerin nesne temsilleri.

  - Kimlik doğrulama, yetkilendirme ve kişiselleştirme gibi ortak uygulama hizmetleri.

Aşağıdaki çizimde, Visual Studio 'da bulunan ve n katmanlı bir uygulamanın orta katmanına uyabilecek Özellikler ve teknolojiler gösterilmektedir.

![Middle katman bileşenleri orta katman ](../data-tools/media/ntiermid.png)

Orta katman tipik olarak veri katmanına veri bağlantısı kullanarak bağlanır. Bu veri bağlantısı genellikle veri erişimi bileşeninde depolanır.

## <a name="data-tier"></a>Veri katmanı
*Veri katmanı* temel olarak bir uygulamanın verilerini depolayan bir sunucu (örneğin, SQL Server çalıştıran bir sunucu).

Aşağıdaki çizimde, Visual Studio 'da bulunan ve n katmanlı bir uygulamanın veri katmanına uyabilecek Özellikler ve teknolojiler gösterilmektedir.

![Data katman bileşenleri ](../data-tools/media/ntierdatatier.png) veri katmanı

Veri katmanına, sunu katmanındaki istemciden doğrudan erişilemez. Bunun yerine, orta katmandaki veri erişim bileşeni, sunum ve veri katmanları arasındaki iletişim için kullanılır.

## <a name="help-for-n-tier-development"></a>N katmanlı geliştirme için yardım
Aşağıdaki konular, n katmanlı uygulamalarla çalışma hakkında bilgi sağlar:

[Veri kümeleri ile TableAdapter’ları farklı projelere ayırma](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

[İzlenecek yol: n katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

[LINQ to SQL ile N katmanlı ve uzak uygulamalar](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: n katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
