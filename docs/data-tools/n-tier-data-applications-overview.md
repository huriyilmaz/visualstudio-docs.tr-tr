---
title: N Katmanlı Veri Uygulamalarına Genel Bakış
description: N katmanlı veri uygulamasına genel bakış makalelerini okuyun. Dağıtılmış uygulamalar veya çok katmanlı uygulamalar olarak da adlandırılan bu uygulamalar, birçok katmana ayrılmış veri uygulamalarıdır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4e713fe3afa88fffee002561bc1ab687be0dcd40
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075196"
---
# <a name="n-tier-data-applications-overview"></a>N katmanlı veri uygulamalarına genel bakış
*N katmanlı veri* uygulamaları, birden çok katmana ayrılmış veri *uygulamalarıdır.* "Dağıtılmış uygulamalar" ve "çok katmanlı uygulamalar" olarak da adlandırılan n katmanlı uygulamalar, işlemeyi istemci ve sunucu arasında dağıtılan ayrı katmanlara ayırıyor. Verilere erişen uygulamalar geliştirirken, uygulamayı ortaya alan çeşitli katmanlar arasında net bir ayrım olması gerekir.

Tipik bir n katmanlı uygulama sunum katmanı, orta katman ve veri katmanı içerir. N katmanlı bir uygulamada çeşitli katmanları ayırmanın en kolay yolu, uygulamanıza eklemek istediğiniz her katman için ayrı projeler oluşturmaktır. Örneğin, sunu katmanı bir Windows Forms uygulaması, veri erişim mantığı ise orta katmanda bulunan bir sınıf kitaplığı olabilir. Ayrıca sunu katmanı, web hizmeti gibi bir hizmet aracılığıyla orta katmandaki veri erişim mantığıyla iletişim kurabilir. Uygulama bileşenlerini ayrı katmanlara ayırmak, uygulamanın bakım ve ölçeklenebilirliğini artırır. Bunu, çözümün tamamını yeniden tasarlamaya gerek kalmadan tek bir katmana uygulanacak yeni teknolojilerin daha kolay benimsenmesi sağlayarak yapar. Ayrıca n katmanlı uygulamalar genellikle hassas bilgileri orta katmanda depolar ve sunum katmanından yalıtım sağlar.

Visual Studio, geliştiricilerin n katmanlı uygulamalar oluşturması için çeşitli özellikler içerir:

- Veri kümesi, veri Project (veri varlık katmanı) ve TableAdapter'ları (veri erişim katmanı) ayrı projelere ayırmanıza olanak sağlayan bir **DataSet** Project özelliği sağlar.

- Veri [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) DataContext ve veri sınıflarını ayrı ad alanlarında oluşturmak için ayarlar sağlar. Bu, veri erişimi ve veri varlığı katmanlarının mantıksal olarak ayrılmasını sağlar.

- [LINQ to SQL,](/dotnet/framework/data/adonet/sql/linq/index) <xref:System.Data.Linq.Table%601.Attach%2A> bir uygulamanın farklı katmanlarından DataContext'i bir araya getirmeniz için bir yöntem sağlar. Daha fazla bilgi için [bkz. N Katmanlı ve uzak uygulamalar LINQ to SQL.](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="presentation-tier"></a>Sunum katmanı
Sunum *katmanı,* kullanıcıların bir uygulamayla etkileşim kurduğu katmandır. Genellikle ek uygulama mantığı da içerir. Tipik sunu katmanı bileşenleri şunları içerir:

- ve gibi veri bağlama <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator> bileşenleri.

- Sunum katmanında kullanmak üzere [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) varlık sınıfları gibi verilerin nesne gösterimleri.

Sunu katmanı genellikle bir hizmet başvurusu kullanarak orta katmana erişer (örneğin, Windows Communication Foundation Services ve WCF Veri Hizmetleri bir [Visual Studio).](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) Sunu katmanı, veri katmanına doğrudan erişmez. Sunu katmanı, orta katmandaki veri erişim bileşeniyle veri katmanıyla iletişim kurar.

## <a name="middle-tier"></a>Orta katman
Orta *katman,* sunum katmanının ve veri katmanının birbirleriyle iletişim kurmak için kullanabileceği katmandır. Tipik orta katman bileşenleri şunlardır:

- İş kuralları ve veri doğrulama gibi iş mantığı.

- Veri erişimi bileşenleri ve mantığı, örneğin:

  - [TableAdapters](create-and-configure-tableadapters.md) ve [DataAdapters ve DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

  - Veri varlık sınıfları gibi verilerin [nesne LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) temsilleri.

  - Kimlik doğrulaması, yetkilendirme ve kişiselleştirme gibi yaygın uygulama hizmetleri.

Aşağıdaki çizimde, Visual Studio ve n katmanlı bir uygulamanın orta katmanına sığma durumlarında kullanılabilen özellikler ve teknolojiler gösterilmiştir.

![Orta katman bileşenleri ](../data-tools/media/ntiermid.png) Orta katman

Orta katman genellikle veri bağlantısı kullanarak veri katmanına bağlanır. Bu veri bağlantısı genellikle veri erişim bileşeninde depolanır.

## <a name="data-tier"></a>Veri katmanı
Veri *katmanı temelde* bir uygulamanın verilerini depolar (örneğin, uygulama çalıştıran bir sunucu) SQL Server.

Aşağıdaki çizimde, Visual Studio ve n katmanlı bir uygulamanın veri katmanına sığma durumlarında kullanılabilen özellikler ve teknolojiler gösterilmiştir.

![Veri katmanı bileşenleri ](../data-tools/media/ntierdatatier.png) Veri katmanı

Veri katmanına doğrudan sunu katmanında istemciden erişilemez. Bunun yerine orta katmandaki veri erişim bileşeni sunu ve veri katmanları arasındaki iletişim için kullanılır.

## <a name="help-for-n-tier-development"></a>N katmanlı geliştirme yardımı
Aşağıdaki konular n katmanlı uygulamalarla çalışma hakkında bilgi sağlar:

[Veri kümelerini ve TableAdapter'ları farklı projelere ayırma](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

[Adım adım kılavuz: N katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

[LINQ to SQL ile N katmanlı ve uzak LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="see-also"></a>Ayrıca bkz.

- [Adım adım kılavuz: N katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
