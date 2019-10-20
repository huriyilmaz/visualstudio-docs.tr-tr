---
title: .NET için Visual Studio veri araçları | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d591595c65f00e0198ded9492ae0b8399e363e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670096"
---
# <a name="visual-studio-data-tools-for-net"></a>.NET için Visual Studio veri araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ve .NET Framework birlikte, veritabanlarına bağlanmak, bellekteki verileri modellemesi ve Kullanıcı arabirimindeki verileri görüntülemek için kapsamlı API ve araç desteği sağlar.  Veri erişim işlevselliği sağlayan .NET Framework sınıfları [ADO.net](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx)olarak bilinir. Visual Studio 'daki veri araçlarının yanı sıra ADO.NET, birincil olarak ilişkisel veritabanlarını ve XML 'yi desteklemek için tasarlanmıştır. Bu günler, birçok NoSQL veritabanı satıcısı veya üçüncü taraf, ADO.NET sağlayıcıları sunmaktadır.

 Visual Studio 2015 güncelleştirme 2, Azure [SQL veritabanı](https://azure.microsoft.com/services/sql-database/) ve [SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016)' deki en son özellikler için desteği etkinleştiren [SQL Server veri araçları](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx)en son güncelleştirmeleri içerir. [.NET Core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project) , veri kümeleri ve ilgili türler hariç ADO.net destekler. .NET Core 'u hedefliyorsanız ve nesne ilişkisel eşleme (ORM) katmanı gerektiriyorsa, [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx)kullanın.

 Aşağıdaki diyagramda temel mimarinin basitleştirilmiş bir görünümü gösterilmektedir:

 ![ADO.NET Mimarisi](../data-tools/media/raddata-ado-net-architecture-diagram.png "radveri ADO.NET mimarisi diyagramı")

 Tipik iş akışı budur:

1. Yerel makinenize bir geliştirme veya test veritabanı yükler. Bkz. [veritabanı sistemlerini, araçları ve örnekleri yükleme](../data-tools/installing-database-systems-tools-and-samples.md). Azure Data Service kullanıyorsanız, bu adım gerekli değildir.

2. Visual Studio 'da veritabanına (veya hizmet ya da yerel dosya) bağlantıyı test edin. Bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

3. Seçim Yeni bir model oluşturmak ve yapılandırmak için araçları kullanın. Entity Framework göre modeller, yeni uygulamalar için varsayılan önersahiptir. Kullandığınız bir model, uygulamanın etkileşime girdiği veri kaynağıdır. Model, veritabanı veya hizmet ile uygulama arasında mantıksal olarak bulunur.  Bkz. [Yeni veri kaynakları ekleme](../data-tools/add-new-data-sources.md).

4. Verileri belirttiğiniz şekilde kullanıcıya görüntüleyecek veri bağlama kodunu oluşturmak için veri **kaynakları** penceresinden Windows Forms, ASP.NET veya Windows Presentation Foundation tasarım yüzeyine veri kaynağını sürükleyin. Bkz. [Visual Studio 'daki verilere denetimleri bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. İş kuralları, arama ve veri doğrulama gibi şeyler için veya temeldeki veritabanının sunduğu özel işlevlerden faydalanmak için özel kod ekleyin.

   Bir model kullanmak yerine, komutları doğrudan bir veritabanına vermek için adım 3 ' ü ve bir .NET uygulamasını programlayabilirsiniz. Bu durumda ilgili belgeleri burada bulabilirsiniz: [ADO.net](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Veri kaynağı Yapılandırma Sihirbazı 'Nı ve tasarımcılarını bellekte kendi nesnelerinizi doldurduktan sonra veri bağlama kodu oluşturmak için de kullanabileceğinizi ve bu nesnelere veri bağlamayı unutmayın.

## <a name="in-this-section"></a>Bu bölümde

- [ADO.NET kullanarak basit veri uygulaması oluşturma](../data-tools/create-a-simple-data-application-by-using-adonet.md)

- [Yeni bağlantı ekleme](../data-tools/add-new-connections.md)

- [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)

- [Visual Studio'daki Varlık Veri Modeli Araçları](../data-tools/entity-data-model-tools-in-visual-studio.md)

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)

- [Visual Studio'daki LINQ to SQL Araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)

- [Veri erişimi hatalarında sorun giderme için ek kaynaklar](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

- [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- [Visual Studio'da veritabanları ve veri katmanı uygulamaları oluşturma ve yönetme](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)

- [Veri erişimi hatalarında sorun giderme için ek kaynaklar](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
