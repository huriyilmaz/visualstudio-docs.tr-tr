---
title: .NET için veri araçları
description: Veritabanlarına Visual Studio, bellekte verileri modellemek ve kullanıcı arabiriminde verileri görüntülemek için API ve araç desteği sağlayan .NET için veri araçlarını gözden geçirme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: e04665d4cf05c8440681ebffbf2223ef1054fcced6d3608aa3c289546e8226c7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346627"
---
# <a name="visual-studio-data-tools-for-net"></a>.NET için Visual Studio veri araçları

Visual Studio ve .NET birlikte veritabanlarına bağlanmak, bellekte veri modellemek ve verileri kullanıcı arabiriminde görüntülemek için kapsamlı API ve araç desteği sağlar. Veri erişimi işlevselliği sağlayan .NET sınıfları, [ADO.NET.](/dotnet/framework/data/adonet/index) ADO.NET veri araçlarında olduğu gibi Visual Studio, birincil olarak ilişkisel veritabanlarını ve XML'yi destekleyecek şekilde tasarlanmıştır. Bu günlerde, birçok NoSQL veritabanı satıcı veya üçüncü taraf, ADO.NET sunar.

[.NET Core,](/dotnet/core/) ADO.NET kümeleri ve bunların ilgili türleri dışındaki tüm ağ türlerini destekler. .NET Core'a yönelik bir nesne ilişkisel eşleme (ORM) katmanına ihtiyaç [Entity Framework Core.](/ef/core/)

Aşağıdaki diyagramda temel mimarinin basitleştirilmiş bir görünümü yer almaktadır:

![ADO.NET Mimarisi](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Tipik iş akışı

Tipik iş akışı şu şekildedir:

1. Yerel makinenize bir geliştirme veya test veritabanı yükleyin. Bkz. [Veritabanı sistemlerini, araçlarını ve örneklerini yükleme.](../data-tools/installing-database-systems-tools-and-samples.md) Azure veri hizmeti kullanıyorsanız bu adım gerekli değildir.

2. Veritabanının (veya hizmetin veya yerel dosyanın) bağlantısını test Visual Studio. Bkz. [Yeni bağlantı ekleme.](../data-tools/add-new-connections.md)

3. (İsteğe bağlı) Araçları kullanarak yeni bir model oluşturma ve yapılandırma. Temel alınan Entity Framework, yeni uygulamalar için varsayılan öneridir. Model (hangisi kullanırsanız kullanın) uygulamanın etkileşim kurduğu veri kaynağıdır. Model, veritabanı veya hizmet ile uygulama arasında mantıksal olarak yer alır. Bkz. [Yeni veri kaynakları ekleme.](../data-tools/add-new-data-sources.md)

4. Veri kaynağını Veri  Kaynakları penceresinden Windows Forms, ASP.NET veya Windows Presentation Foundation tasarım yüzeyine sürükleyerek verileri belirttiğiniz şekilde kullanıcıya görüntüecek veri bağlama kodunu oluşturur. Bkz. [Denetimler için bkz. Visual Studio.](../data-tools/bind-controls-to-data-in-visual-studio.md)

5. İş kuralları, arama ve veri doğrulama gibi şeyler için veya temel alınan veritabanının ortaya çıkar olduğu özel işlevlerden yararlanmak için özel kod ekleyin.

3. adımı atlayıp bir .NET uygulamasını model kullanmak yerine doğrudan bir veritabanına komutlar yapmak üzere programlayabilirsiniz. Bu durumda, ilgili belgeleri burada bulabilirsiniz: [ADO.NET.](/dotnet/framework/data/adonet/index) Bellekte kendi nesnelerinizi  doldurmak ve ardından kullanıcı arabirimi denetimlerini bu nesnelere veri bağlamak için veri bağlama kodu oluşturmak üzere Veri Kaynağı Yapılandırma Sihirbazı'nı ve tasarımcıları kullanmaya devam edersiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
